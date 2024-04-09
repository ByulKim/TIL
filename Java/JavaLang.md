> [자바의 신] 서적을 읽으며 공부한 내용 기록

# java.lang

### java.lang 패키지란?

---
- import 없이 사용 가능한 패키지이다.
- 여러 클래스에서 공통적으로 사용할 수 있는 많은 기능들을 가지고 있다.
- 분류
    - 언어, 문자열 관련
        - String, …
    - 기본 자료형 및 숫자 관련
        - Boolean, Integer, Double, …
    - 어노테이션
      - Override, ...
    - 쓰레드, 예외, 런타임 관련
        - Thread
        - Throwable, Exception
        - OutOfMemoryError
          - 메모리가 부족하여 발생하는 오류
        - StackOverflowError
          - 스택에 쌓을 수 있는 메서드 호출 정보의 한계를 넘었을 때 발생하는 오류

### 래퍼클래스

---
- 기본형 변수인 int, double, boolean 과 같은 변수를 객체형으로 포장한 것이다.
  - int -> Integer, double -> Double, boolean -> Boolean
- 필요시 기본 자료형 처럼 사용할 수 있고, 객체를 생성하지 않아도 값을 할당할 수 있다.
- 참조형 변수의 경우 null 로 지정이 가능하기에, 기본형 변수를 사용하는데 null 값으로 값을 지정해야 할 경우 사용할 수 있다. 
- 연관된 메서드를 함께 가지고 있어, 필요시에 사용할 수 있다.
- 숫자 클래스의 경우 MIN_VALUE, MAX_VALUE 와 같은 범위내 최소/최대값을 상수로 가지고 있어 필요시에 사용할 수 있다.

### System 클래스

---
- 많이 사용하는 `System.out.println();` 출력 부분은 System 클래스를 이용한 것이다.
    - PrintStrem 이라는 클래스의 메서드이다.
    - println() 은 매개변수가 없는 메서드가 존재하여 줄바꿈만을 실행할 시 호출할 수 있다.
      - 객체를 출력할 때 toString()으로 출력한다면 참조 변수의 값이 null인 경우 오류가 발생한다.   
        → valueOf() 메서드를 사용해 값을 출력하기 때문에 null인 경우에도 출력이 가능하다.
- 기능
  - GC 수행
    - 메모리는 자바가 알아서 관리하기 때문에 직접 처리하는 메서드를 사용하면 안된다.
  - JVM 종료
    - JVM을 강제로 종료시키면 시스템에 큰 장애가 발생할 수 있기 때문에 사용하면 안된다.
  - 현재 시간 관리
  - 시스템 속성값 관리
  - 환경값 조회
      - 시스템 속성 값은 추가 및 변경이 가능하지만, 환경값은 조회만 가능하다.
      