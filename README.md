#  객체와 클래스

### 1. 객체란

![](http://pds25.egloos.com/pds/201211/04/39/f0183439_5095e560e1d39.png)

- 물리적으로 존재하거나 추상적으로 생각할 수 있는 것 중에서 자신의 속성을 가지고 있고 다른 것과 식별 가능한 것을 '객체'라고 한다.
- 이는 실존하는 모든 것을 객체화할 수 있음을 의미한다. 그래서 OOP 프로그래밍은 철저히 현실 사고를 기반으로 이뤄진다.
- 하나의 객체는 **'속성(필드)**'와 **'동작(메소드)'**로 구성되어 있다.



### 2. 클래스

![](http://pds21.egloos.com/pds/201211/04/39/f0183439_5095e5617055b.png)


- 클래스란 객체를 만들기 위한 설계도이다.
- 클래스에는 객체를 생성하기 위한 **'필드**'와 **'메소드'**가 정의되어 있다.

```java
public class ClassName {

	// 필드 (클래스 멤버) - 객체 생성 시 호출할 필드값 저장
    // 선언 형식 식별자 선언과 동일 ex) int a; int b = 10; ...
  
	public ClassName {
   
    // Constructor (생성자) - 객체 생성 시 초기화 담당
    // 생성자의 이름은 클래스 이름과 동일하다.
    
    }
    
	public void methodName(dataType params) {
    
    // 객체의 동작 담당
    
    }
}
```
> 클래스 코드 예시

```java
public class Car{
  
  // 1. Car class의 속성(멤버 변수)
  int carAxel;
  int seatCount;
  String color;
  int carId;
  int speed;
  
  // 2. Car class의 생성자
  public Car(int seatCount, String color, int carId){
    this.seatCount = seatCount;
    this.color = color;
    this.carId = carId;
  }
  
  // 3. Car class의 기능(메소드)
  void break(){--speed;}
  void axcel(){++speed;}
  
}
```

##### 2.1. 필드 (클래스 멤버 변수, 전역변수)

- 필드는 객체 고유의 데이터, 부품 객체, 상태 정보 등을 저장하는 공간이다.
- 선언 형태는 변수 선언과 비슷하다.
- 필드는 생성자와 메소드 전체에서 사용되며 객체가 소멸되지 않는 한 객체와 함께 존재한다.





##### 2.2. 생성자

```java
public class Car{
  // 멤버 변수 생략...
  
  //Car class의 생성자
  public Car(int seatCount, String color, int carId){
    this.seatCount = seatCount;
    this.color = color;
    this.carId = carId; 
} 
  /* 생성자 오버로딩 */
  // '생성자 오버로딩'이란 - 매개변수를 달리하는 생성자를 여러 개 선언하는 것을 의미한다.
  // '생성자 오버로딩'의 필요성 - 클래스 외부에서 사용할 정확한 데이터들을 모르기 때문에 생성자를 Overloading 해	둘 필요도 있다.
  public Car(int seatCount, String color){
    this.seatCount = seatCount;
    this.color = color;
  }


  }
```



- 객체를 인스턴스화 할 시에 new 연산자를 호출하면서 함께 호출되는 중괄호 {} 블록이다.
- 객체 호출 (인스턴스화) 시, heap 영역에 로드된다.
- 생성자의 역할은 객체 생성 시, 초기화를 담당한다.
- 생성자를 별도 선언하지 않았다면 자바 코드 상에선 보이지 않지만 default 생성자가 자동 추가된다.
- 클래스명과 같은 이름으로 첫 글자 대문자로 명명해줘야한다.
- 생성자를 new를 하지 못하게 접근제한자를 활용하여 private하게 만들 수 있다. ex) 싱글톤 패턴 (single ton)





##### 2.3. 메소드

- 객체의 동작을 담당하는 코드 블록
- 일종의 기능을 구현해둔 코드 블록이며 객체 간의 데이터 전달 수단으로 사용된다.
- 외부로부터 매개값을 받을 수도 있고, 실행 후 어떤 값을 리턴할 수도 있다.

```java
public void setAge(int a){

	// [접근제어자 리턴값 이름] 순으로 작성
  	// 리턴값이 없을 경우 'void'로 작성해준다.

	}

public int plus(int a, int b){
  // 리턴값이 있을 경우, 리턴 '데이터타입'을 작성해준다.
  return a + b;
}
```



### 3. static method 와 static 변수 (정적 메소드와 정적 변수)

- static method와 변수들은 정말 필요한 것들로 구성해놓고 클래스 생성 후, 메모리에 먼저 로드되게 설계한다.
- 객체가 생성되는 순간 static을 해제할 방법이 없다. (즉, 제어할 방법이 없음을 의미한다.) > rsc 낭비를 야기할 수도 있기에 적절히 사용
- 클래스 자체가 static 속성을 띄고 있으므로 클래스는 정적 변수가 존재하지 않는다.
  - 객체 생성 시, 바로 메모리 힙(heap) 영역에 올라가기 때문이다. 

  ​

### 4. 접근 제한자 (Access modifier)
- main() 메소드를 가지지 않는 대부분의 클래스는 외부 클래스에서 이용할 목적으로 설계된 라이브러리 클래스
- 객체 생성을 막기 위해 생성자를 호출하지 못하게 하거나 객체의 특정 데이터를 보호하기 위해 해당 필드에 접근하지 못하도록 제어할 필요와 특정 메소드를 호출할 수 없도록 제한할 필요가 있음
- **'접근제한자 리턴타입 함수명() {}'** 과 같이 메소드 작성
- 접근제한자 생략 시, 자동 defaul 가 붙음 (따로 표기되진 않음. 내부에서 자동 동작)
- 아래 표를 참고하면 더 자세히 알 수 있음

![](http://cfile27.uf.tistory.com/image/27689B3A5791BC1D1D35C6)
```java
public class ArraySub {
	
	int a;
	public int b;
	private int c;
	
	/*
	 접근제한자 리턴타입 함수명();
	 접근제한자 써도되고 안써도
	 */
	
	// void 앞에 'default'라는 자동 접근제한자 붙
	// defalt 접근제한자 - 패키지가 다를 경우 사용할 수 없음
    // 어떤 함수를 사용할 때, 나만 사용(내 패키지 안에서)하겠다고 의도적으로 제한하고 싶을 때 적절히 사용
	// 패키지가 다를 경우에도 쓰고 싶을 때, public (모든 곳에서 접근 가능) 사용해줘야함 
	public void pirintNumber() {
		System.out.println(a);
	}
	
	// 접근제한자 default로 자동 지정되어 있는 상황
	void sum(int a, int b) {
		
		
	}
}
```

