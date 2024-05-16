# 배열

### 배열(array)이란?

> 배열은 같은 타입의 여러 변수를 **하나의 묶음**으로 다루는 것
> 

<br/><br/><br/>

```java
int[] score;
int number[];
       
score = new int[5];
number = new int[5];
```

위처럼 

`타입[] 변수이름;` 이나 `타입 변수이름[];` 으로 두 가지 방법으로 선언해도 된다. 

<br/><br/><br/><br/><br/>

### 배열의 길이와 인덱스

> 인덱스(index)의 범위는 0부터 ‘배열길이-1’까지
> 

길이가 **0**인 배열도 생성이 가능하다. 

<br/>

```java
int[] arr= new int[0];
```

<br/><br/>

**TIPS**

배열을 선언할 때 배열의 크기가 커질 것 같다면,

기존의 2배정도의 길이로 생성하는 것이 좋다.

<br/>

> **배열의 길이를 변경하는 방법**
1. 더 큰 배열을 새로 생성한다.
2. 기존 배열의 내용을 사로운 배열에 복사한다.
> 

이런 방법이 있지만, 이 작업들은 꽤나 비용이 만이 들기 때문에 처음 생성할 때 잘 생성하는 것이 중요하다. 

<br/><br/><br/><br/><br/>

### 배열 초기화

```java
int[] score = new int[] {60, 70, 90, 70, 80};
int[] score = {60, 70, 90, 70, 80}; // new int[] 생략 가능
```

배열의 생성과 초기화를 동시에 진행했다. 

`{ }` 안의 값의 개수에 의해 배열의 길이가 자동으로 결정되기 때문에 괄호 `[ ]`  안에 배열의 길이는 안 적어도 된다. 

<br/><br/><br/>

```java
int[] score;
score = new int[] {60, 70, 90, 70, 80}; // ⭕
score = {60, 70, 90, 70, 80};           // ❌
```

다만, **배열의 선언과 생성을 따로 하는 경우에는 생략할 수 없다.**

자바 언어에서는 메소드의 매개변수로 배열을 전달할 때에는 배열을 직접 인라인으로 선언하여 전달하는 것을 허용하지 않는다.

이는 자바 언어의 문법적 규칙 중 하나이다.

<br/><br/><br/>

```java
public static void int add(int[] arr){
	int sum=0;
	
	for(int i = 0; i < arr.length(); i++){
		sum += arr[i];
	}
	
	return sum;
}

public static void main(String[] args) {
	int result = add( new int[] {60, 70, 90, 70, 80}); // ⭕
	int result = add({60, 70, 90, 70, 80});            // ❌
}
```

매개변수로 int배열을 받는 add메서드가 정의되어 있다.

이 경우 역시 `**new 타입[]**` 을 생략할 수 없다. 

**인라인 방식(Inline)** 은 코드 내에서 다른 코드의 일부분을 직접 삽입하는 방식을 의미한다.

이것은 주로 코드의 가독성을 높이거나 실행 속도를 높이기 위해 사용된다.

예) int result = add( new int[] {60, 70, 90, 70, 80}); 

<br/><br/><br/><br/><br/>

### Arrays.toString(배열이름)

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args){
        int[] score = {60, 70, 90, 70, 80};
       
        System.out.println(Arrays.toString(score)); 
        // [60, 70, 90, 70, 80]
        
	      System.out.println(score);
        // [I@4eec7777
    }
}
```

I@4eec7777 → `**타입@주소**` 의 식으로 생겼는데, 

여기서 I는 1차원의 int배열이라는 의미이다.

@ 뒤에 나오는 16진수는 배열의 주소이다. 

실제 주소가 아닌 내부 주소이다. (가상 메모리 주소이다.)

그리고 @뒤의 숫자는 실행할 때마다 달라질 수 있다.

그리고 자바에서 배열 또는 객체의 주소를 16진수로 표현하는 이유는 메모리 주소를 간결하게 표현하기 위해서이다.

단, char은 예외 (아니 통일좀 하지)

```java
char[] chArr = {'a','b','c'};
System.out.println(chArr);
// abc
```

<br/><br/><br/><br/><br/>

### 배열의 복사

> 배열의 복사는 for문보다 System.arraycopy()를 사용하는 것이 효율적이다.
> 

```java
for(int i = 0; i < num.length; i++) {
	newNum[i] = num[i];
}
```

위에서 밑으로 사용할 수 있다. 

<br/><br/><br/>

```java
System.arraycopy(num, 0, newNum, 0, num.length);
```

num[0]에서 newNum[0]으로 num.length;개의 데이터를 복사한다는 말이다.
