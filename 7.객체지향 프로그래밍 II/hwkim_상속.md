# 상속

### 상속이란

> 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것이다.
> 

<br/><br/>

**❓왜 써❓**

적은 양의 코드로 새로운 클래스 작성 가능

코드를 **공통적**으로 **관리**할 수 있음 → 코드의 **추가** 및 **변경**이 매우 용이 

<br/><br/>

```java
class Parent {
	int age;
}

class Child extends Parent {
	void play() {
		System.out.println("놀자~");
	}
}
```

**자손 클래스**는 조상 클래스의 모든 멤버를 상속 받으므로 **항상 조상 클래스보다 같거나 많은 멤버를 갖는다.** 

상속받는다 = 조상클래스를 확장한다

라는 의미로 해석할 수 있어서 키워드가 `extends` 인 것도 있다. 

<br/><br/><br/>


```java
class Parent {
	int age;
}

class Child1 extends Parent {
	void play() {
		System.out.println("놀자~");
	}
}

class Child2 extends Parent {
	void eat() {
		System.out.println("떡볶희 먹으러 가자~");
	}
}
```

Child1, Child2 둘 다 Parent클래스를 상속받고 있지만,

클래스 Child1과 Child2 간에는 서로 아무런 관계도 성립되지 않는다.  (독립) 


<br/><br/><br/>


### 포함관계

한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언하는 것을 말한다. 

```java
class Circle {
	int x;
	int y;
	int r;
}
```

<br/>

```java
class Point {
	int x;
	int y;
}

class Circle {
	Point c = new Point();
	int r;
}
```

두번째 코드를 포함관계라고 한다. 

<br/><br/>

❓**포함관계를 쓸지 VS 상속을 쓸지❓**

`~은 ~이다(is-a)` 와 `~은 ~을 가지고 있다(has-a)`  를 넣어서 문장을 만들어 보면 된다. 

> **상속** 원은 점이다. - Circle is a Point. <br/>
**포함** 원은 점을 가지고 있다.  - Circle has a Point. <br/>
> 

이 경우에는 두 번째 문장이 더 옳다.

그래서 상속보단 **포함관계**로 쓰는 것이 좋다. 

예를 들어 원은 도형이고(is) 원은 점을 가지고(has) 있다. 

<br/><br/><br/>

```java
class Shape {
	String color = "black";
}

class Circle extends Shape {
}

class Circle extends Shape {
	Point center;
	int r;
}
```

<br/><br/><br/><br/><br/>

### 단일 상속(single inheritance)

C++에서는 다중 상속을 허용하지만 **자바에서는** **오직 단일 상속만**을 허용한다.

<br/>

```java
class TVCR extends TV, VCR { // 에러. 조상은 하나만 허용된다.
	// ... 
}
```

<br/><br/>

**다중 상속의 장점**

여러 클래스로부터 상속받을 수 있기 때문에 복합적인 기능을 가진 클래스를 쉽게 작성할 수 있다. 

<br/>

**다중 상속의 단점**

클래스간의 관계가 매우 복잡해짐

서로 다른 클래스로부터 상속받은 멤버간의 이름이 같은 경우 구별할 수 있는 방법이 없다. 

(예 : TV클래스에도 power() 메서드가, VCR 클래스에도 power()라는 메서드가 있을 때 자손은 TVCR클래스는 어느 조상클래스의 power()를 상속받게 되는 것일까? 된다해도 어떻게 구별할 것인가?)

위의 단점으로 인하여 자바에서는 단일상속만을 허용한다. 

<br/><br/><br/><br/><br/>

### Object클래스 - 모든 클래스의 조상

Object 클래스는 모든 클래스 상속계층도의 최상위에 있는 조상클래스이다.

<br/>

```java
class Tv {
	...
}
```

<br/>

```java
class Tv extends Object {
	...
}
```

컴파일을 하면 컴파일러가 자동으로 최상위 조상인 Object 클래스를 추가해 준다. 

toString()이나 equals와 같은 메서드를 따로 정의하지 않고도 사용할 수 있었던 이유는 이 메서드들이 Object 클래스에 정의된 것들이기 때문이다.
