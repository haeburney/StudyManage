# 생성자

### 생성자란?

인스턴스가 생성될 때 호출되는 **‘인스턴스 초기화 메서드’**이다.

```java
public class Car {
    String brand;
    String model;
    int year;
    
    
    // 매개변수가 없는 생성자
    public Car() { }
    
    // 매개변수가 있는 생성자
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }
    
    // 메서드
    public void displayInfo() {
        System.out.println("Brand: " + brand);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
    }
    
    public static void main(String[] args) {
        // 생성자를 사용하여 Car 객체 생성
        Car myCar = new Car("Toyota", "Camry", 2022);
        myCar.displayInfo();
    }
}

```
<br/><br/><br/>

### 생성자의 조건

> 생성자의 이름은 클래스의 이름과 같아야 한다.
생성자는 리턴 값이 없다.
> 

<br/>

생성자도 **오버로딩이 가능**하므로 **하나의 클래스**에 **여러개의 생성자가 존재**할 수 있다. 

`Car myCar = new Car("Toyota", "Camry", 2022);` 

그리고 연산자 **new가 인스턴스를 생성**하는 것이지 ~~생성자가 인스턴스를 생성하는 것~~이 아니다. 

‘생성자’라는 단어 때문에 생성한다라고 오해할 수 있는데, 생성자는 단순히 인스턴스 변수들의 초기화에 사용되는 조금 특별한 메서드일 뿐이다. 

<br/>

```java
Car c = mew Car();
```

<br/><br/>

1️⃣ 연산자 **new**에 의해서 **메모리(heap)**에 **Car클래스의 인스턴스가 생성**된다. 

2️⃣ 생성자 **Car()**가 호출되어 수행된다.

3️⃣ 연산자 **new**의 결과로, 생성된 **Car 인스턴스의 주소**가 반환되어 **참조변수 c에 저장**된다.

<br/><br/><br/><br/><br/>

### 기본 생성자(default constructor)

사실 **모든 클래스**에는 **반드시 하나 이상의 생성자**가 정의되어 있어야 한다.

그러나 지금까지는 **컴파일러**가 제공하는 ‘**기본 생성자**’ 덕분에 생성자를 정의하지 않고도 인스턴스를 생성할 수 있었다. 

<br/>

```java
class Data1 {
	int value;
}

class Data2 {
	int value;
	
	Data2(int x){
		value = x;
	}
}

class ConstructorTest {
	public static void main(String[] args) {
		Data1 d1 = new Data1();
		Data2 d2 = new Data2();  // compile error 발생 
		Data2 d3 = new Data2(7); // 이렇게 써야 함
	}
}
```

Data1에는 정의되어 있는 생성자가 하나도 없으므로 컴파일러가 기본 생성자를 추가해줫다.

하지만 Data2에는 이미 생성자 Data2(int x) 가 정의되어 있으므로 기본 생성자가 추가되지 않았기 때문에 에러가 발생한 것이다. 

<br/><br/><br/><br/><br/>

### 매개변수가 있는 생성자

```java
class Car {
	String color;
	String gearType;
	int door;
	
	Car() {}
	Car(String c, String g, int d) {
		color = c;
		gearType = g;
		door = d;
	}
}
```

이렇게 매개변수를 사용한 초기화를 만들어줬다. 

<br/>

만약 초기화가 없는 경우 

```java
Car c = new Car();
c.color = "white";
c.gearType = "auto";
c.door = 4; 
```

초기화가 있는 경우 

```java
Car c = new Car("white", "auto", 4);
```

로 초기화를 했을 때 보다 더 직관적이고 간결하게 만들 수 있다. 

<br/><br/><br/><br/><br/>

### 생성자에서 다른 생성자 호출하기 - this(), this

같은 클래스의 멤버들 간에 서로 호출할 수 있는 것처럼 생성자 간에도 서로 호출이 가능하다. 

단, 다음의 두 조건을 만족시켜야 한다. 

> 생성자의 이름으로 클래스이름 대신 this를 사용한다. 
한 생성자에서 다른  생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다.
> 

<br/><br/>

**❓ 첫 줄에서만 호출이 가능한 이유 ❓**

초기화 작업의 순서를 보장하기 위해서이다.

객체를 사용하기 전에 초기화를 먼저 해야 하기 때문에 규칙을 그렇게 정한 것이다. 

```java
Car(String color) {
	door = 5;  // 
	Car(color, "auto", 4); // 에러1. 생성자의 두 번째 줄에서 다른 생성자 호출 
}  // 에러2. this(color, "auto", 4);로 해야 함 
```

```java
Car (String c, String g, int d) {
	color = c;
	gearType = g;
	door = d; 
}
```

```java
Car(String color, String gearType, int door) {
	this.color = color;
	this.gearType = gearType;
	this.door = door;
}
```

매개변수로 선언된 변수의 이름이 color로 인스턴스변수 color와 같을 경우에는 이름만으로는 두 변수가 서로 구별이 안 된다.

이런 경우에는 인스턴스 변수 앞에 ‘this’를 사용하면 된다. 

`color = color` 이렇게 하면 둘 다 지역변수로 간주된다.

`this` 는 참조변수로 인스턴스 자신을 가리킨다.

참조변수를 통해 인스턴스의 멤버에 접근할 수 있는 것처럼, `this` 로 인스턴스변수에 접근할 수 있는 것이다. 

static메서드에서는 인스턴스 멤버들을 사용할 수 없는 것처럼, `this` 역시 사용할 수 없다.

사실 생성자를 포함한 모든 인스턴스메서드에는 자신이 관련된 인스턴스를 가리키는 참조변수 `this` 가 지역변수로 숨겨진 채로 존재한다. 

일반적으로 인스턴스메서드는 특정 인스턴스와 관련된 작업을 하기 때문에 자신과 관련된 인스턴스의 정보가 필요하지만, static메서드는 인스턴스와 관련 없는 작업을 하므로 인스턴스에 대한 정보가 필요 없기 때문이다.

<br/><br/>

> **this** 인스턴스 자신을 가리키는 참조변수. 인스턴스의 주소가 저장되어 있다.
       모든 인스턴스메서드에 지역변수로 숨겨진 채로 존재한다.
**this(), this(매개변수)** 생성자, 같은 클래스의 다른 생성자를 호출 할 때 사용한다.
> 

<br/><br/><br/><br/><br/>

### 생성자를 이용한 인스턴스의 복사

```java
class Car {
	String color;
	String gearType;
	int door;
	
	Car() {
		this("white", "auto", 4);
	}
	
	Car(Car c) {
		color = c.color;
		gearType = c.gearType;
		door = c.door;
	}
	
	Car(String color, String gearType, int door) {
		this.color = color;
		this.gearType = gearType;
		this.door = door; 
	}
}
```

기존 객체의 상태를 복사하여 새로운 객체를 생성하고자 할 때 사용된다.
<br/><br/>