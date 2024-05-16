# 변수의 초기화

### 변수의 초기화

**변수의 초기화** : 변수를 선언하고 처음으로 값을 저장하는 것

> 멤버 변수(클래스 변수와 인스턴스 변수)와 배열의 초기화는 선택적이지만, 지역변수의 초기화는 필수적이다.
> 

<br/>

```java
class InitTest{
	int x;     // 인스턴스 변수
	int y = x; // 인스턴스 변수
	
	void method1() {
		int i;     // 지역변수
		int j = i; // 에러. 지역변수를 초기화하지 않고 사용
	}
}
```

<br/><br/><br/><br/><br/>

## 멤버 변수의 초기화 방법

> 1️⃣ **명시적 초기화(explicit initialization)** 
2️⃣ **생성자(constructor)**
3️⃣ **초기화 블럭(initialization block)**
     - 인스턴스 초기화 블럭 : 인스턴스변수 초기화 하는데 사용
     - 클래스 초기화 블럭 : 클래스변수를 초기화 하는데 사용
> 

<br/><br/><br/><br/><br/>

### 1️⃣ **명시적 초기화(explicit initialization)**

**명시적**(明示的)

1.**뚜렷하게 드러나 보이는 것**

2.**숨김이나 감춤이 없이 분명하게 나타내는 것**

3.**어떤 일을 분명하게 드러내는 것**

변수를 선언과 동시에 초기화하는 것을 명시적 초기화라고 한다. 

가장 기본적이면서도 간단한 초기화 방법이므로 여러 초기화 방법 중에서 가장 우선적으로 고려되어야 한다.

<br/>

```java
class Car {
	int door = 4; // 기본형(primitive type) 변수의 초기화
	Engine e = new Engine(); // 참조형(reference type) 변수의 초기화 
}
```

<br/><br/><br/><br/><br/>

### 3️⃣ **초기화 블럭(initialization block)**

> **클래스 초기화 블럭** : 클래스변수의 복잡한 초기화에 사용된다.
**인스턴스 초기화 블럭** : 인스턴스변수의 복잡한 초기화에 사용된다.
> 

<br/>

```java
class InitBlock {
	static { /* 클래스 초기화블럭 입니다. */ }
	
	{ /* 인스턴스 초기화블럭 입니다. */ }
}
```

<br/>

`**클래스 초기화 블럭**` 은 클래스가 **메모리에 처음 로딩될 때 한번만** 수행되며, `**인스턴스 초기화 블럭**`은 **생성자와 같이 인스턴스를 생성할 때 마다** 수행된다.

그리고 생성자보다 인스턴스 초기화 블럭이 먼저 수행된다. 

<br/>

```java
Car() {
	count++;
	serialNo = count;
	color = "White";
	gearType = "auto";
}

Car(String color, String gearType) {
	count++;
	serialNo = count;
	this.color = color;
	this.gearType = gearType;
}
```

```java
{
	count++;
	serialNo = count;
}

Car() {
	color = "White";
	gearType = "auto";
}

Car(String color, String gearType) {
	this.color = color;
	this.gearType = gearType;
}
```

윗쪽에서 밑쪽으로 간결하게 작성할 수 있다.

코드의 중복을 제거하는 것은 코드의 신뢰성을 높여 주고, 오류의 발생가능성을 줄여준다. 

<br/>

> **클래스변수의 초기화시점** : 클래스가 처음 로딩될 때 단 한번 초기화 된다. 
**인스턴스변수의 초기화시점** : 인스턴스가 생성될 때마다 각 인스턴스별로 초기화가 이루어진다.

**클래스변수의 초기화순서** : 기본값 → 명시적초기화 → 클래스 초기화 블럭
**인스턴스변수의 초기화순서** : 기본값 → 명시적초기화 → 인스턴스 초기화 블럭 → 생성자
>