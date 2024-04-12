# 변수와 메서드

# 선언 위치에 따른 변수의 종류

### **1️⃣ 클래스 변수 (Class Variables)**

```java
public class Student {
    static String schoolName; // 클래스 변수

    String name; // 인스턴스 변수
    int age; // 인스턴스 변수

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public static void main(String[] args) {
        // 클래스 변수 값 설정
        Student.schoolName = "ABC High School";

        // 각각의 인스턴스는 개별적인 값을 가집니다.
        Student student1 = new Student("Alice", 18);
        Student student2 = new Student("Bob", 17);

        // 출력
        System.out.println("Student 1 - Name: " + student1.name + ", Age: " + student1.age + ", School: " + Student.schoolName);
        System.out.println("Student 2 - Name: " + student2.name + ", Age: " + student2.age + ", School: " + Student.schoolName);
    
		    /*
		    Student 1 - Name: Alice, Age: 18, School: ABC High School
				Student 2 - Name: Bob, Age: 17, School: ABC High School
				*/
    }
}

```

<br/>

**클래스 변수**는 **모든 인스턴스**가 **공통된 저장공간(변수)**을 공유하게 된다.

**클래스 변수**는 인스턴스변수와 달리 인스턴스를 생성하지 않고도 **언제라도 바로 사용**할 수 있다는 특징이 있으며, `클래스이름.클래스변수` 와 같은 형식으로 사용한다. 

<br/><br/>

**❓언제 생성돼❓**

**클래스**가 **메모리에 ‘로딩(loading)’될 때** 생성되어 프로그램이 **종료될 때까지 유지**되며, **public**을 앞에 붙이면 같은 프로그램 내에서 **어디서나** 접근할 수 있는 전역변수의 성격을 갖는다. 

<br/><br/><br/><br/><br/>

### 2️⃣ **인스턴스 변수 (Instance Variables)**

**클래스 영역**에 선언된다.

인스턴스는 **독립적인 저장공간**을 가지므로 **서로 다른 값**을 가질 수 있다. 

<br/>

**❓언제 사용❓** 

인스턴스마다 고유한 상태를 유지해야 하는 속성의 경우, 인스턴스 변수로 선언한다.

<br/>

**❓언제 생성돼❓**

해당 클래스의 **객체가 생성될 때 생성**되고, 객체의 생명주기에 따라 유지된다.

<br/><br/><br/><br/><br/>

### **3️⃣ 지역 변수 (Local Variables)**

```java
public class Example {
    public static void main(String[] args) {
        int a = 5; // 지역 변수

        System.out.println("Value of a: " + a);
    }
}

```

<br/>

**❓언제 생성돼❓**

해당 **블록이 실행**될 때 생성되고 **블록의 범위가 종료**될 때 소멸된다. 

<br/>

**❓그럼 클래스 변수랑 인스턴스 변수랑 생성되는 시간 차이가 얼마나 나는거지❓**

<br/><br/><br/><br/><br/>

## **클래스의 생명주기**

### 1️⃣ **로딩(Loading) : 클래스 파일이 메모리에 로드되는 단계**

- 클래스 파일의 **바이너리 데이터**를 읽어와 **JVM 내의 메모리**에 올린다.
- 이 과정에서 **클래스의 코드를 검증**하고, **필요한 자원을 준비**

### 2️⃣ **링크(Linking) : 로딩된 클래스 파일이 필요한 다른 클래스와 연결되는 단계**

- 로딩 단계에서 읽어온 클래스의 바이너리 데이터를 **메모리에 올린 후**, JVM 내부의 런타임 상수 풀에 해당하는 클래스에 대한 참조를 해결
- 이 단계에서는 **클래스 변수와 메소드의 실제 메모리 주소**가 할당

### 3️⃣ **초기화(Initialization) : static 변수가 초기화되는 단계**

- 클래스 변수(static 변수)가 해당 클래스의 인스턴스화 없이 사용될 때 초기화
- 클래스 변수는 해당 클래스가 로딩되고 링크된 후에 초기화
- 클래스의 초기화 블록 및 static 변수들이 선언된 순서대로 초기화

### **4️⃣ 인스턴스화(Instantiation) : 클래스의 객체가 생성되는 단계**

- **`new`** 키워드를 사용하여 클래스의 **객체(인스턴스)**가 생성
- 이때 **`new`** 키워드로 생성된 인스턴스는 **힙(heap) 메모리**에 할당
- 인스턴스 변수는 해당 객체가 생성될 때마다 생성되고, 인스턴스의 초기화 블록이나 생성자에 의해 초기화

### 5️⃣ **사용(Usage)**

### 6️⃣ **소멸(Garbage Collection)**

더 이상 사용되지 않는 객체는 메모리에서 제거된다.

<br/><br/><br/><br/><br/>

---

# 메서드

> 특정 작업을 수행하는 일련의 문장들을 하나로 묶은 것. 
기본적으로 수학의 함수와 유사
> 

<br/><br/><br/>

### 메서드를 사용하는 이유

**1️⃣ 높은 재사용성(reusability)**

**2️⃣ 중복된 코드의 제거**

**3️⃣ 프로그램의 구조화** 

<br/><br/>

```java
int add (int x, int y) // 선언부
{                      // 구현부
	int result = x + y;
	
	return result; 
}                       // 구현부
```

<br/>

`int` : 반환타입(출력)

`add` : 메서드 이름 

`(int x, int y)` : 매개변수 선언(입력) 

`return` : 결과를 반환 

메서드의 반환 타입이 void가 아닌 경우, 구현부{} 안에 ‘return 반환값;’이 반드시 포함되어 있어야 한다. 

반환값은 최대 **하나만** 허용

<br/><br/><br/>

```java
int add(int x, int y) { ... } // OK.
int add(int x, y) { ... }     // 에러. 매개변수 y의 타입이 없다. 
```

<br/><br/><br/><br/><br/>

### void도 return; 필요했었다.

```java
void helloWorld(){
	System.out.println("Hellow World!!");
	
	return; // 반환 타입이 void이므로 생략 가능. 컴파일러가 자동추가
}
```

**컴파일러**가 **자동**으로 추가해줬던 것. 

그냥 아무 생각 없이 쓰고 있었다. 

<br/><br/><br/><br/><br/>

### 매개변수의 유효성 검사

메서드의 구현부{}를 작성할 때, 제일 먼저 해야 하는 일이 **매개변수의 값이 적절한 것인지 확인**하는 것이다. 

‘호출하는 쪽에서 알아서 적절한 값을 넘겨주겠지.’라는 생각을 절대로 가져서는 안 된다.

```java
float divide(int x, int y) {
	// 작업하기 전에 나누는 수가 0인지 확인해야 한다. 
	if ( y == 0 ) {
		System.out.println("0으로 나눌 수 없습니다.");
		return 0; 
	}
}
```

<br/><br/><br/><br/><br/>

---

# JVM의 메모리 구조

> 1️⃣ Method Area
2️⃣ Call Stack
3️⃣ Heap
> 

<br/><br/><br/>

### 1️⃣ **Method Area**
프로그램 실행 중 어떤 클래스가 사용되면, JVM은 해당 클래스의 클래스 파일(*.class)을 읽어서 분석하여 **클래스에 대한 정보**(클래스 데이터)를 이곳에 저장한다.

클래스의 클래스변수(class variable)도 이 영역에 함께 생성된다.

<br/>

**❓클래스에 대한 정보❓**

```java
public class MyClass {
    private int myField;
    
    public MyClass() {
        myField = 0;
    }
    
    public void setMyField(int value) {
        myField = value;
    }
    
    public int getMyField() {
        return myField;
    }
    
    public static void staticMethod() {
        System.out.println("This is a static method.");
    }
}

```

<br/>

1. 클래스의 이름: **`MyClass`**
2. 필드: **`myField`**
3. 생성자: **`MyClass()`**
4. 메서드: **`setMyField(int value)`**, **`getMyField()`**, **`staticMethod()`**

이런 정보들을 저장한다. 

<br/><br/><br/>

### **2️⃣ Call Stack(호출 스택 또는 execution stack)**

메서드의 작업에 필요한 **메모리 공간**을 제공한다.

메서드가 작업을 수행하는 동안 지역변수들과 연산의 중간 결과 등을 저장하는데 사용된다.

그리고 메서드가 작업을 마치면 할당되었던 메모리공간은 반환되어 비워진다. 

<br/>

**특징**

- 메서드가 호출되면 수행에 필요한 만큼의 **메모리**를 **스택에 할당**받는다.
- 메서드가 수행을 마치고나면 사용했던 **메모리를 반환**하고 **스택에서 제거**된다.
- 호출스택의 **제일 위에 있는 메서드**가 **현재 실행 중인 메서드**이다.
- 아래에 있는 메서드가 바로 위의 메서드를 호출한 메서드이다.

<br/><br/><br/>

### 3️⃣ **Heap**

**인스턴스**가 생성되는 공간 (인스턴스변수들이 생성되는 공간)

<br/><br/><br/><br/><br/>

## 기본형 매개변수와 참조형 매개변수

> 기본형 매개변수 : 변수의 값을 읽기만 할 수 있다. (read only)
참조형 매개변수 : 변수의 값을 읽고 변경할 수 있다. (read & wrtie)
> 

참조형이면 인스턴스의 주소가 복사된다.

주소를 알 수 있기 때문에 값을 읽어 오는 것은 물론 값을 변경하는 것도 가능하다.

```java
class Data { int x; }
class ReferenceParamEx {
	public static void main(String[] args) {
		Data d = new Data();
		d.x = 10;
		change(d);
		System.out.println(d.x) // 1000 
	}
	
	static void change(Data d){
		d.x = 1000;
	}
}
```

<br/><br/><br/><br/><br/>

### 참조형 반환타입

매개변수뿐만 아니라 반환타입도 참조형이 될 수 있다.

> 반환타입이 **참조형**이라는 것은 메서드가 **객체의 주소**를 반환한다는 것을 의미한다.
> 

<br/><br/><br/><br/><br/>

### 재귀호출(recursive call)

```java
void method() {
	method(); // 재귀호출. 메서드 자신을 호출한다. 
}
```

반복문보다 **재귀호출**의 수행시간이 **더 오래** 걸린다. 

→ **반복문**은 그저 같은 문장을 반복해서 수행하는 것이지만,

**메서드**를 호출하는 것은 반복문보다 **몇 가지 과정이 추가로** 필요하기 때문이다.

(ex. 매개변수 복사와 종료 후 복귀할 주소저장 등)

<br/><br/>

**❓그렇다면 굳이 왜? 사용할까?❓**

→ 재귀호출이 주는 **논리적 간결함** 때문이다.
반복문보다 더 단순한 구조로 바뀔 수도 있다. 

알아보기 쉽게 작성하는 것이 (비효율적이더라도) 논리적 오류가 발생할 확률도 줄어들고 나중에 수정하기도 좋다. 

그래서 먼저 반복문으로 작성을 해보고, 재귀호출로 간단히 할 수 없는지 고민해볼 필요가 있다. 

<br/><br/>

```java
f(n) = n * f(n-1), 단 f(1) =1 
```

팩토리얼은 재귀호출을 사용하기 좋은 예제이다. 

<br/><br/><br/><br/><br/>

### 클래스 메서드(static메서드)와 인스턴스 메서드

**클래스 메서드**도 클래스변수처럼, **객체를 생성하지 않고도** ‘클래스이름.메서드이름(매개변수)’와 같은 식으로 호출이 가능하다.

반면에 **인스턴스 메서드**는 반드시 **객체를 생성해야만** 호출할 수 있다. 

<br/><br/><br/>

```java
class MyMath2 {
	long a, b;
	
	// 인스턴스변수 a, b만을 이용해서 작업하므로 매개변수가 필요 없다.
	long add() {
		return a + b;
	}
	
	// 인스턴스 변수와 관계없이 매개변수만으로 작업이 가능하다.
	static long add(long a, long b) {
		return a+ b;
	}
}

class MyMathTest2{
	public static void main(String args[]) {
		// 클래스메서드 호출. 인스턴스 생성없이 호출가능
		System.out.println(MyMath2.add(200L, 100L));
		
		MyMath2 mm = new MyMath2(); // 인스턴스를 생성
		mm.a = 200L;
		mm.b = 100L;
		// 인스턴스메서드에서는 객체생성 후에만 호출이 가능함 
		System.out.println(mm.add()); 
	}
}
```

<br/><br/><br/><br/><br/>

### 클래스 멤버와 인스턴스 멤버간의 참조와 호출

**클래스멤버**는 **언제나 참조** 또는 **호출**이 가능! 

하지만 **인스턴스 멤버**는 반드시 **객체를 생성한 후에만 참조 또는 호출**이 가능하기 때문에 클래스멤버가 인스턴스 멤버를 참조, 호출하기 위해서는 객체를 생성하여야 한다. 

<br/><br/>

```java
class MemberCall {
	int iv = 10;
	static int cv = 20;
	
	int iv2 = cv;
	// static int cv2 = iv; // 에러. 클래스변수는 인스턴스 변수를 사용할 수 없음 
	static int cv2 = new MemberCall().iv; // 이처럼 객체를 생성해야 사용가능.
	
	static void staticMethod1() {
		System.out.println(cv);
		// System.out.println(iv); // 에러. 클래스메서드에서 인스턴스변수를 사용불가.
		MemberCall c = new MemberCall();
		System.out.println(c.iv); // 객체를 생성한 후에야 인스턴스변수의 참조가능.
	}
	
	void instanceMethod1() {
		System.out.println(cv);
		System.out.println(iv); // 인스턴스메서드에서는 인스턴스변수를 바로 사용가능.
	}
	
	static void staticMethod2() {
		ststicMethod1();
		// instanceMethod1(); // 에러. 클래스메서드에서는 인스턴스메서드를 호출할 수 없음.
		MemberCall c =new MemberCall();
		c.instanceMethod1(); // 인스턴스를 생성한 후에야 호출할 수 있음. 
	}

	void instanceMethod2() { 
	// 인스턴스메서드에서는 인스턴스메서드와 클래스메서드 모두 인스턴스 생서없이 바로 호출이 가능하다.
		staticMethod1(); 
		instanceMethod1();
	}
}
```

<br/><br/><br/>