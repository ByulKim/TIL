## 생성자

### 생성자란

---
- 객체 생성 시에 멤버변수 초기화를 진행하는 메서드
- 인스턴스를 생성한 후 바로 호출된다.
- 객체 생성 시 `new Student();` 괄호의 이유이다.
- 규칙
  - 클래스명과 동일한 이름으로 메서드를 정의해야 한다.
  - 반환타입을 지정하지 않고 메서드를 정의해야 한다.
- 생성자의 장점
  - 멤버 변수를 생성시에 초기화 해주어 초기화 해주는 코드를 중복으로 호출하지 않아도 된다.
  - 값을 무조건 초기화 하도록 제약을 걸 수 있다. (필수값 입력을 보장)
- 기본 생성자
  - 매개변수가 없는 생성자
  - 정의하지 않으면 컴파일 시에 자바 컴파일러가 자동으로 생성해준다.
  (자동으로 해주지 않으면 필요하지 않아도 매번 직접 정의해야 함 -> 번거로움 해결)

### this

---
- 인스턴스 자신의 참조값
- 하나의 클래스 안에서 같은 이름의 변수가 존재하면 호출시에 가까운 스코프(범위)의 변수를 호출하는데,
  멤버 변수를 호출하고 싶다면 `this.{멤버변수}` 로 호출한다.
- `this.{멤버변수}`의 경우 멤버변수를 호출한다는 것을 구분하기 위해 사용하는데,   
  IDE에서는 색으로 멤버변수와 지역변수를 구분해주기 때문에 중복되지 않은 부분에서는 생략해도 좋다. (필요한 경우에만! 구분하기)
- 생성자 오버로딩 : `this()`
  - 매개변수가 다른 생성자를 여러개 만들 수 있는데, 중복되는 코드를 가진 생성자가 존재한다면 `this()`로 호출하여 사용할 수 있다.
  - 규칙 : 생성자 메서드 안에서 첫줄에만 사용이 가능하다.

### 패키지

---
- 연관이 있는 클래스의 묶음, 카테고리
- 디렉토리(폴더)를 생성하여 패키지를 정의한다.
- 규칙
  - 패키지 명은 폴더의 이름과 동일하게 설정한다.
  - 이름은 모두 소문자를 사용한다. (관례)
  - 패키지 이름의 가장 앞에는 일반적으로 서비스 도메인의 이름을 거꾸로 사용한다. (관례)
  - 외부 라이브러리를 사용하다보면 같은 이름의 클래스가 존재할 수 있고 이와 구분하기 위해 개발하고 있는 서비스의 패키지 명을 지정해준다.
- 다른 패키지의 클래스를 호출
  - 사용하는 곳에서 패키지명.클래스명 으로 바로 호출
  - 코드 상단의 현재 패키지 정의 아래에 `import 패키지명.클래스명`을 정의해두고 사용하는 곳에서 클래스명으로 호출
- 클래스 명이 같더라도 패키지명이 다르면 구분과 사용이 가능하다.
- 같은 이름의 클래스를 여러개 import 하는 것은 불가하여,
  가장 많이 사용하는 클래스를 import 하고 다른 클래스는 사용하는 곳에서 경로를 포함하여 호출한다.
- 계층 구조를 이루더라도 패키지는 모두 별개이다.
  - 다른 패키지의 클래스를 사용하려면 항상 import 해주어야 한다.