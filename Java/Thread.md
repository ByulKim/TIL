# Thread

### Thread (쓰레드)

---
- 자바 프로그램을 실행시키는 순간, 자바 프로세스가 시작되고, main() 메서드가 수행되면서 하나의 쓰레드가 시작된다.
- 직접 쓰레드를 추가로 생성하지 않아도, JVM을 관리하기 위한 여러 쓰레드가 존재한다. (GC)
- 하나의 프로세스 안에서 여러개의 쓰레드가 동작한다.
- 프로세스의 자원을 공유하며 여러 작업을 실행 = 쓰레드
- 생성
    - Runnable(인터페이스), Thread(클래스) in java.lang
    - run() 메서드 하나를 가지고 있음
    - 구현한 메서드는 run(), 쓰레드를 시작하는 메서드는 start() (자바에서 알아서 run()을 수행함)
    - 다른 클래스를 상속받아야 하는데 쓰레드를 사용해야 하는 경우 러너블 인터페이스를 구현하고,
      다른 클래스를 상속 받지 않아도 된다면 쓰레드 클래스를 상속받는다.
    - start()가 호출되면 실행이 끝날때까지 기다리는 것이 아니라 다음에 선언된 로직으로 넘어가고 run()이 실행되어 종료되면 해당 쓰레드가 종료된다.
- 모든 쓰레드는 이름을 가지고 있고, 설정하지 않으면 Thread-n 으로 생성된다. (n은 생성 순서에 따라 증가하는 번호)
- ThreadGroup : 생성하는 쓰레드를 그룹으로 묶을 수 있다.
    - 쓰레드의 관리를 용이하게 하기 위한 클래스
    - 트리 구조를 가진다.
    - enumerate() : 쓰레드/쓰레드 그룹의 목록을 배열로 저장하고, 개수를 리턴한다.
        - 쓰레드의 개수를 파악해 배열을 생성해야 한다.
- sleep() 메서드 (static) : 대기한다.
    - 예외가 발생할 수 있어 사용시에는 try-catch 로 묶어 주어야 한다.
- 메인 메서드의 수행이 끝나더라도, 시작한 쓰레드가 종료되지 않으면 자바 프로세스는 끝나지 않는다.
    - 데몬 쓰레드는 예외
        - 데몬쓰레드는 수행여부와 상관없이 JVM이 종료될 수 있다.
        - 쓰레드 시작전에 설정되어야 데몬 쓰레드로 동작한다.
        - 모니터링과 같이 부가적인 작업을 수행하는 쓰레드를 생성할 때 데몬 쓰레드로 설정한다.
- 쓰레드의 우선 순위
    - 기본값은 5이다.
    - 기본으로 정해진 것을 사용하는 것이 좋다. (직접 설정했다가 장애가 발생할 수 있음)
- 쓰레드의 상태를 통제하는 메서드
    - getState() : 쓰레드의 상태를 확인한다.
    - join() / join(long millis) : 수행중인 쓰레드가 중지될 때까지 대기한다.
    - interrupt : 수행중인 쓰레드에 중지 요청을 한다.
        - InterruptedException 을 발생시키면서 종료된다.
        - join(), sleep() 과 같은 대기 상태에서 사용할 수 있다.
- Object 클래스에 선언된 쓰레드 관련 메서드
    - wait() : 쓰레드를 대기 상태로 만든다.
    - notify(), notifyAll() : 쓰레드의 대기 상태를 해제한다.

### sunchronized, 동기화

---
- 같은 객체를 참조할 때에만 유효하다.
- 여러 쓰레드에서 하나의 객체에 있는 인스턴스 변수를 처리할 때 발생하는 문제를 해결하기 위해 필요한 것
- 쓰레드에 안전하다 → 주요 데이터 처리 부분을 synchronized 로 감싸두었다.
- 쓰레드에 안전하지 않다. → synchronized 를 사용하지 않았다.
- 메서드를 선언
    ```java
    public synchronized void test() {
    }
    ```
    - 한 순간에는 하나의 쓰레드만 이 메서드를 실행한다.
- 블럭으로 선언 : 필요한 부분만 묶어서 선언
    ```java
    public void test() {
        synchronized(lock) {
            // 동시에 실행되면 안될 부분 정의
        }
    }
    ```
    - 메서드 길이가 길어지면 기다리는 시간이 길어지기 때문에 필요한 부분만 묶어주는게 효율적일 수 있다.
    - 블럭의 매개변수는 잠금 처리를 위한 객체를 선언한다.
    - 해당 객체를 참조하는 변수가 있다면, 다른 변수는 참조하지 못한다는 의미이다.