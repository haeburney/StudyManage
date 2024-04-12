# 오버로딩

### 오버로딩

한 클래스 내에 **같은 이름의 메서드를 여러개 정의하는 것**을 ‘**메서드 오버로딩**(method overloading)’ 또는 간단히 ‘**오버로딩(overloading)**’이라 한다. 

<br/><br/><br/>

### 오버로딩의 조건

> 1️⃣ **메서드 이름**이 같아야 한다.
2️⃣ 매개변수의 **개수** 또는 **타입**이 **달라야** 한다.
> 

<br/><br/><br/><br/><br/>

**오버로딩 성립❌**

```java
int add(int a, int b) { return a + b; }
int add(int x, int y) { return x + y; }
```

매개변수의 이름만 다를 뿐 매개변수의 타입이 같기 때문에 오버로딩이 성립하지 않는다. 

<br/><br/>

**오버로딩 성립❌**

```java
int add(int a, int b) { return a + b; }
long add(int a, int b) { return (long)(a + b); }
```

add(3,3) 과 같이 호출해도 뭘 호출한 건지 알 수 없기 때문에 성립이 안된다. 

컴파일을 하면

```java
add(int, int) is already defined(이미 같은 메서드가 정의되어 있다.)
```

라는 에러 메세지가 뜬다. 

<br/><br/>

**오버로딩 성립**⭕

```java
int add(int a, int b) { return a + b; }
long add(long a, long b) { return (long)(a + b); }
```

add(3, 3L) → 첫 번째 메서드 호출

add(3L, 3) → 두 번째 메서드 호출

add(3,3)은 불가능하다. 

→ 어떤 걸 호출했는지 알 수 없기 때문에 호출하지 못한다. 

<br/><br/><br/><br/><br/>

### 오버로딩 장점

오버로딩이 없다면 이름을 짓기 어렵고, 메서드를 사용하는 쪽에서는 이름을 일일이 구분해서 기억해야 하기 때문에 부담이 된다. 

→ 기억하기 쉽고, 이름도 짧게 할 수 있다.

그리고 메서드의 이름을 절약할 수 있다. 

<br/><br/><br/><br/><br/>

### 가변인자(varargs)와 오버로딩

**가변인자(variable argument)** : 함수나 메소드가 호출될 때 전달되는 인자의 개수가 일정하지 않은 경우를 말한다.

가변인자는 ‘타입 … 변수명’과 같은 형식으로 선언하며, PrintStream클래스의 printf()가 대표적인 예이다. 

<br/>

```java
public PrintStream printf(String format, Object... args) { ... }
```

가변인자는 제일 마지막에 선언해야 한다. 

<br/><br/>

```java
String concatenate (String s1) { ... }
String concatenate (String s1, String s2) { ... }
String concatenate (String s1, String s2, String s3) { ... }
String concatenate (String s1, String s2, String s3, String s4) { ... }
```

위와 같은 메서드를 가변인자를 통해 간단히 나타낼 수 있다. 

 <br/><br/>

```java
String concatemate(String... arr) { ... } // 가변인자를 사용하면 매개변수를 생략할 수 없다. 
```

가변인자는 내부적으로 배열을 이용하는 것이다. 

그래서 가변인자가 선언된 메서드를 호출할 때마다 배열이 새로 생성된다.

가변인자가 편리하지만, 이런 비효율이 숨어있으므로 꼭 필요한 경우에만 가변인자를 사용하는 것이 좋다.

그리고 가능하면 가변인자를 사용한 메서드는 오버로딩하지 않는 것이 좋다.

<br/><br/>