## static
- 인스턴스 생성 없이도 사용 가능한 클래스의 변수 / 메서드 를 정의



### static 변수

---

- 인스턴스 간에 공유하는 공통 변수
- = 정적 변수
- = 클래스 변수
- 힙 영역에서 인스턴스별로 보관되는 것이 아니라, 메서드 영역에 보관된다.
- 정의할 때는 자료형 앞에 static 을 선언한다.
- 접근시에는 {클래스명.변수명} 으로 호출한다.
- 인스턴스를 생성하여 접근도 가능하지만, 사용 코드를 봐서 static 변수라는 구분이 되지 않기에 권장하지 않는다. 

### static 메서드

---

- 인스턴스 생성없이 사용 가능한 메서드
- = 클래스 메서드
- 인스턴스 생성의 의미가 없는 경우(멤버변수를 사용하지 않거나 특정 기능 제공의 목적) 주로 사용한다. (ex. 유틸리티성 클래스)
- static 메서드 안에서는 static 변수와 static 메서드만 사용 가능하다.
- (인스턴스 변수와 인스턴스 메서드는 객체를 생성하여 사용해야 하기 때문)
- 호출시에는 {클래스명.메서드명()} 으로 호출한다.
- `public static void main(String[] args)`
  - 자바의 시작 함수인 main 메서드는 대표적인 static 메서드이다.
  - 자신의 클래스 내에서 다른 메서드를 사용하려면 해당 메서드도 static 으로 정의해 주어야 한다.