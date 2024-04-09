> [자바의 신] 서적을 읽으며 공부한 내용 기록


# 제네릭


### 제네릭 타입

---

- 내부에서 사용할 변수의 타입을 객체를 생성할 때나 메서드를 호출할 때 지정해 주는 것을 의미한다.
- 클래스 선언시에 클래스명 옆의<>꺽쇠로 제네릭 클래스를 표현한다. (타입을 나타내는 문자는 어떤것이든 상관없음)
```java
  public class GenericSample<T> {
    T value;
    
    public void setValue(T value) {
        this.value = value;
    }
    
    public T getValue() {
        return value;
    }
  }
```
- 기본적으론 어떤 타입이든 넣을 수 있다.
- 제네릭으로 클래스를 정의하면, 상위 타입이 같지 않은 인스턴스라도 같은 클래스의 기능을 가질 수 있다.
- 형변환 시에 발생하는 문제(실제 참조하는 객체가 무엇인지 확인하지 못해 발생하는)를 방지할 수 있다.
- 매개변수로 여러 타입의 멤버를 가진 객체를 받고 싶다면 wildcard 타입`<?>`을 사용하면 된다.
  - wildcard 타입은 매개변수에서만 주로 사용한다.   
    ```java
    public void test(GenericSample<?> g) {
    }
    ```
  - 무엇인지 모르는 타입으로 변수를 지정할 수 없기 때문이다. (X)  
    ```java
    GenericSample<?> sample = new GenericSamle<String>();
    ```
- 기본적으로 어떤 타입이든 넣을 수 있지만 wildcard 타입을 이용해 범위를 지정할 수 있다.
    ```java
    public void test(GenericSample<? extends Animal> g) {
    }
    ```
    - 해당 형식을 Bounded Wildcard라고 한다.
    - Animal클래스를 상속받은 타입만 받을 수 있다.


### 제네릭 메서드

---
- 인스턴스와 그 타입의 값을 함께 받을 수 있게 정의한 메서드이다.
- 리턴 타입 앞에 <타입>을 선언하고 매개변수를 추가한다.
- 설정한 제네릭 타입이 여러개라면 , 를 통해 구분할 수 있다.

```java
  public <T> void test(GenericSample<T> g, T addValue) {
  }
```