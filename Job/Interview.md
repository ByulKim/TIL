## 기술 면접 준비

### 객체 지향 설계

- 설계에 대한 질문을 받으면 누가/어떻게 사용하는 것인지 질문을 던져야 한다. (필요시에는 육하원칙 모두)
- 핵심 객체 설계 → 핵심이 되는 객체들을 나열하고 설계하기
- 관계 분석 → 객체 간의 관계를 파악하고 상속 또는 관계 맺기
- 핵심 행동 파악 → 어떤 행위들을 해야하는지
- \+ 디자인패턴
    - 싱글톤
        - 클래스가 오직 하나의 객체만을 가짐
        - 싱글톤이 단위테스트에 방해가 되는 요인이다?
    - 팩터리 메서드
        - 어떤 구현체를 선택할 것인지를 정의한 팩터리 메서드를 통해 객체를 생성


### 재귀, 동적 프로그래밍

- 재귀적 해법
    - 부분 문제에 대한 해법을 통해 완성된다.
    - n번째~~, 모든~~ 등의 문제를 보면 재귀로 풀기를 고민해 볼 수 있다.
    - 상향식 접근법
        - 하나, 둘, 셋 간단한 문제부터 하나씩 해결해 나가는 과정
    - 하향식 접근법
        - 어떻게 N에 대한 문제를 나눌지를 생각해서 해결해 나가는 과정
    - 반반 접근법
        - 데이터를 절반으로 나누어서 해결해 나가는 과정
            - 이진탐색, 병합정렬

    - 공간 효율성이 나빠질 수 있다 → 재귀 호출 발생 시마다 스택에 새로운 레이어를 추가해야 하기 때문 O(n)
        - 순환적 해법

            - 순환적으로 구현하면 코드가 더 어렵고 복잡해질 수 있다.


### 시스템 설계 및 규모 확장성

- 실제 일을 하듯 질문하고, 장단점을 토론하기 → 면접관을 끌어들이는 것이 중요하다.
- 처음에는 포괄적으로 접근하기
- 화이트 보드를 사용하기
- 가정을 명확하게 언급하기
- 적극적으로 문제 해결에 뛰어들기
- 문제의 범위를 한정하기
- 핵심 문제점 찾기
- 설계 수정하기
- 규모 확장성 고려하기
    - 처음엔 현실적 제약을 무시하기
    - 현실로 돌아와 적용하기
- 핵심 개념
    - 수평적 , 수직적 규모 확장
        - 수평적: 노드의 개수를 늘리는 방법 (ex. 서버를 한대 더 추가해서 부하를 줄임)
        - 수직적: 특정 노드의 자원을 늘리는 방법 (ex. 서버에 메모리를 추가, 스펙을 업)
            - 메모리 또는 디스크를 추가할 수 있어 제한적임

    - 서버 부하 분산 장지 (로드 밸런서)
        - 로드밸런서를 통해 여러 서버에 요청을 나눠 보내고, 부하를 분산시킨다.
    - 데이터베이스 역정규화
        - 관계형 디비의 JOIN연산은 시스템이 커질수록 굉장히 느려진다.
        - 관계로 데이터를 분리하지 말고 하나의 테이블에 그 데이터를 추가시킴
        - NoSQL을 사용해 연관이 없는 방식으로 처리할 수도 있음
    - 데이터베이스 분할(샤딩)
        - 데이터를 여러 서버에 나눠서 저장, 어떤 데이터가 어디에 저장되어 있는지 알고 있어 찾을 수 있음
            - 수직적 분할: 자료의 특성 별로 분할 (개인정보, 메시지 등)
            - 키 혹은 해시 기반 분할: 해시 함수를 이용해 N개의 서버에 분할 저장
                - 사실상 서버의 수가 고정되어 있어야 함, 서버 추가 시 재분배 비용이 큼
            - 디렉터리 기반 분할: 조회테이블을 유지

    - 캐싱
        - 인메모리 캐시를 사용하여 결과를 빠르게 조회한다.
            - 쿼리 결과를 캐싱하거나 특정 객체를 캐시에 저장할 수도 있다.
        - 실제 데이터 저장소와 애플리케이션 사이에 위치
    - 비동기식 처리 & 큐
        - (이상적이라면) 속도가 느린 연산은 비동기로 처리해야 한다.
            - 연산이 끝날때까지 한참을 기다려야 하기 때문
        - 어떤 경우에는 연산을 미리 해 놓을 수도 있다.
            - 실시간으로 처리해야 하는 작업이 아니라면 미리 연산을 해서 큐에 쌓아두고 가져오는 작업이 나을 수도 있다.
        - 작업이 완료되면 나중에 알림을 통해 알려줄 수도 있다.
    - 네트워크 성능 척도
        - 대역폭
            - 단위 시간에 전송할 수 있는 데이터의 최대치 (초당 몇 비트)
        - 처리량
            - 단위 시간에 실제로 전송된 데이터의 양
        - 지연속도
            - 데이터를 전송하는 데 걸리는 시간

    - MapReduce
        - key, value 쌍의 데이터를 처리함
        - 병렬로 처리할 수 있도록 도와준다.

- 시스템 설계 시 고려 사항
    - 실패
        - 실패 포인트와 대비책을 고려해야 한다.
    - 가용성
        - 사용 가능한 시스템의 시간을 백분율로 나타낸 것
    - 신뢰성
        - 특정 단위 시간에 시스템이 사용 가능할 확률을 나타낸 것
    - 읽기 중심 vs 쓰기 중심
        - 읽는 연산이 많다면 캐시를, 쓰는 연산이 많다면 큐를 이용해 처리하는 것을 고려해보기
    - 보안


### 정렬과 탐색

- 버블정렬
    - 첫 원소부터 순차적으로 검색하면서 다음 원소의 값과 비교하여 자리를 바꿈
    - 시간 O(n2), 메모리 O(1)
- 선택 정렬
    - 전체 중에 가장 작은 데이터를 찾아 가장 앞으로 보내는 것을 반복
    - 시간 O(n2), 메모리 O(1)
- 병합 정렬
    - 배열을 절반씩 나누어 정렬하고 이를 다시 합쳐서 재정렬
    - 병합 대상이 되는 배열의 두 부분을 임시 배열에 복사하고 시작 지점들끼리 비교하여 원래 배열에 복사해서 넣음
    - 시간 O(nlogn), 메모리 - 상황에 따라 다름
- 퀵 정렬
    - 무작위로 선정한 한 원소를 사용하여 배열을 분할, 그 원소를 기준으로 작은 원소들은 앞으로, 큰 원소들은 뒤로 보내며 정렬한다.
    - 시간 O(nlogn), 최악O(n2), 메모리 O(logn)
- 기수정렬
    - 데이터가 정수와 같이 유한한 비트로 구성되어 있는 경우에 사용된다.
    - 자릿수를 기준으로 정렬을 수행한다.
    - 시간 O(kn)
- 이진탐색
    - 가운데에 있는 데이터보다 작으면 왼쪽 크면 오른쪽을 탐색한다.



### 테스트

- 큰 그림을 이해하고 있는지 - 어떤 것을 테스트 해야하는지 우선 순위를 정한다던지
- 소프트웨어가 어떻게 동작하는지, 어떤 생채계의 일부로 귀속되는지
- 문제에 구조적으로 접근하고 있는지
    - 범주를 나누고 각 구조별로 테스트
- 실제로 적용 가능한, 합리적인 테스트 계획을 세울 수 있는지
- 수작업 테스트인지, 자동화 테스트인지
- 블랙박스 테스트
    - 주어진 그대로 테스트 해야함
- 화이트박스 테스트
    - 내부의 개별 함수들에 접근해서 테스트 해야함


### 자바

- 오버로딩: 매개변수가 다른 함수를 여러개 정의하는 것
    - 반환타입과는 관계가 없다
- 오버라이딩: 같은 함수를 하위의 클래스가 재정의하는것
- 컬렉션 프레임워크
    - ArrayList: 동적으로 크기가 조절되는 배열
    - Vector: ArrayList와 비슷하지만 동기화 되어 있다는 차이가 있다.
    - LinkedList: 연결리스트
        - iterator
            - 요소를 제거할 수 있다.
            - 전통적인 명령적 접근 방식
        - stream API
            - 요소의 직접적인 변경이 불가능하다.
            - 함수형 프로그래밍 지원 (람다, 메서드 참조)

    - HashMap: key-value형태로 데이터를 저장하고, key값을 해시함수를 통해 해시코드로 변환하여 관리한다.
        - 해시테이블의 한 구현체 중 하나이다.


### 데이터베이스

- 명시적 JOIN, 묵시적 JOIN
    - join을 쿼리에 문법적으로 명시하는지, \[from 테이블1, 테이블2 where 조인조건\] 으로 묵시적으로 하는지의 차이
- 비정규화
    - 읽는 시간을 최적화 하도록 설계된 데이터베이스
    - 데이터를 중복해서 저장할 수 있음
    - 대규모 데이터베이스 설계 시 많이 사용된다.

- 정규화
    - 데이터베이스 중복을 최소화하도록 설계된 데이터베이스
    - 관계형디비


### 스레드와 락

- 자바의 모든 스레드는 java.lang.Thread 클래스 객체에 의해 생성되고 제어된다.
- 구현 방법
    - Runnable 인터페이스 구현하기
        - run() 메서드를 구현 후 start() 메서드를 호출한다.
    - Thread 클래스를 상속받기
        - run() 메서드를 오버라이드하고, 하위 클래스의 생서자는 상위 클래스의 생성자를 명시적으로 호출해야 한다.
        - 상속은 하나만 받을 수 있기 때문에 다른 클래스를 함께 상속받아야 하는 경우 Runnable 인터페이스를 사용하는 것이 좋다.

- 동기화와 락
    - 스레드들이 서로 데이터를 공유하기 때문에 두 스레드가 자원을 동시에 변경하는 경우 문제가 발생할 수 있다.
    - 동기화 방법 (Synchronization)
        - synchronized 키워드를 사용하면 공유 자원에 대한 접근을 제한한다.
            - 메서드, 특정 코드 블럭 등에 적용할 수 있다.
            - 같은 인스턴스의 메서드를 동시에 호출하는 것은 불가하다.
            - 정적 메서드

                - 클래스 락에 의해 동기화된다.
                - 같은 클래스에 있는 정적 메서드들은 두 스레드에서 동시에 실행될 수 없다. (각각 다른 메서드를 호출하더라도)

        - 락
            - 접근 시에 락을 획득하고, 사용 후 반납한다.
            - Lock 타입의 ReentrantLock 인스턴스를 생성하고, `lock.lock();` / `lock.unlock()` 방식으로 사용한다.
            - 세밀하게 동기화를 제어하고 싶을 때 사용한다.
            - 교착상태 (deadlock)
                - 서로가 가진 자원을 사용하기 위해 계속 대기하는 상태 → 무한 대기 상태
                - 조건
                    - 한번에 한 프로세스만 사용할 수 있음
                    - 자신이 가진 자원을 반납하지 않고 다른 자원에 접근을 요청할 수 있음
                    - 다른 프로세스의 자원 접근을 강제로 취소할 수 없음
                    - 2개 이상의 프로세스가 자원접근을 기다리는데 그 관계에 사이클이 존재 \*\* → 이것을 해결해야 함


### Thread Safe

- 멀티 스레드 환경에서 동기화 문제가 발생하지 않는다.
    - 동기화 처리
    - 원자적 연산
    - 불변 객체
- 안전성과 일관성을 유지
- 성능 저하 (lock획득과 반납 등), 복잡성 증가


### JVM

- java 어플리케이션을 실행하는 가상 컴퓨터
- 자바 컴파일러: 자바 언어를 바이트코드로 컴파일하여 파일 생성
- 자동 메모리 관리
    - 메모리 영역을 메서드/스택/힙 으로 나누어 관리
    - GC
        - 가비지 컬렉터가 사용하지 않는(참조되지 않는) 인스턴스를 관리

- 클래스 로딩
    - 클래스를 로드하여 필요한 메모리 영역에 배치
- 개발
    - JDK
        - JVM, Java 컴파일러 등이 포함된 개발 키트
        - 개발, 디버깅, 테스트 등이 필요하면 설치해야 함

- 실행
    - JRE
        - JVM, 표준 Java 클래스 라이브러리
        - 개발이 아닌 실행이 목적인 경우 설치하면 됨

- 플랫폼 독립성
    - 실행시를 의미한다.
    - 컴파일된 바이트코드만 있으면 JVM이 설치된 어떤 플랫폼에서도 실행이 가능


### 스프링 프레임워크, 스프링 부트

- Spring Framework
    - 자바 어플리케이션을 개발하기 위한 프레임워크
    - DI, IoC, AOP, MVC 등의 기능을 가짐
    - 설정을 수동으로 해야함
- Spring Boot
    - 스프링 프레임워크의 설정과 배포를 간소화 하기 위해 설계된 도구
    - 자동 구성, 스타터 의존성 관리
    - 임베디드 서버 - 독립된 jar 파일로 추출 가능
    - @SpringBootApplication
        - 기본적으로 애플리케이션의 메인 클래스가 위치한 패키지와 그 하위 패키지를 자동으로 스캔한다.
        - 설정 클래스로 동작하여 bean을 설정할 수 있다.


### JPA, Spring Data JPA

- JPA
    - 자바에서 객체-관계 매핑(ORM)을 제공하는 표준 API
        - 기능을 수행하는 데 필요한 메서드와 규약을 정의
    - 구현객체: Hibernate
        - 표준 API의 인터페이스를 구현하여 실제 기능을 제공하는 코드
    - 엔티티 관리 @Entity
    - 영속성 컨텍스트
    - 객체-테이블 매핑

- Spring Data JPA
    - JPA를 더 쉽게 사용할 수 있도록 돕는 프로젝트
    - 레포지토리 추상화
        - 레포지토리 인터페이스를 통해 구현하지 않아도 이미 정의되어 있는 주요 기능들을 사용할 수 있다.
        - 어플리케이션 실행 시점에 구현부를 자동으로 생성
        - 커스텀 쿼리 @Query , 페이징 처리 등 가능


### 애자일 방법론

- 소프트웨어의 작은 구성 요소를 신속하게 개발하여 제공
- 개발 주기를 짧게 가져가고, 테스트/피드백을 통해 보완해 나가는 방식
- 고객의 만족도를 개선
- CI/CD, TDD
- 스크럼
    - 작업을 스프린트라는 단위로 나눠 짧게 처리
    - 하나의 기능을 위한 디자인-개발-테스트 작업 단위
- 모든 요구사항을 한번에 개발하는 것이 아니기에 변화에 대응이 쉽고우선 중요 기능을 배포한 다음 추가해 나갈 수 있음

- 개발 선언
    - 공정과 도구보다 **개인과 상호작용을**
    - 포괄적인 문서보다 **작동하는 소프트웨어를**
    - 계약 협상보다 **고객과의 협력을**
    - 계획을 따르기보다 **변화에 대응하기를**

- vs 워터폴
    - 순차적인 진행, 명확한 요구사항을 기반으로 전체를 개발
    - 요구사항정의(설계) → 디자인 → 개발 → 테스트 → 배포
    - 업무 분담과 순차적인 진행으로 명확함
    - 속도가 느리고 유연하지 못함
    - 계속 기다려야 하거나 다 만들었는데 필요가 없어지는 경우 다반사
    - 변경사항에 대응이 어려움