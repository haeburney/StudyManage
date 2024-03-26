# String배열

### String배열의 선언와 생성

```java
String[] name = new String[3];
```

3개의 String타입의 참조변수를 저장하기 위한 공간이 마련되고 참조형 변수의 기본값은 null이므로 각 요소의 값은 null로 초기화 된다.

<br/>

**자바에서 null**
- 어떠한 객체도 가리키고 있지 않다
- 아무 것도 없음

<br/><br/><br/>

**변수의 타입에 따른 기본값**

| 자료형 | 기본값 |
| --- | --- |
| boolean | false |
| char | ‘\u0000’ |
| byte, short, int | 0 |
| long | 0L |
| float | 0.0f |
| double | 0.0d 또는 0.0 |
| 참조형 변수 | null |

<br/><br/><br/><br/><br/>

### String VS char

> String클래스는 char배열에 기능(메서드)을 추가한 것이다.
> 

<br/><br/><br/>

**String과 char의 중요한 차이점 한 가지**

→ String객체는 읽을수만 있을 뿐 내용을 변경할 수 없다.

<br/><br/><br/>

```
int i = 1;
(char)( i + '0');   // '1'

i = 55;
(char)( 55 + '0');  // 'g'
```

정수 i(i=1)에 '0'을 더하면 문자 '1'이 된다. 
<br/><br/><br/>
