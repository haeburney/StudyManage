# 클래스와 객체

### 클래스와 객체의 정의와 용도

> **클래스의 정의** : 클래스란 객체를 정의해 놓은 것이다.
**클래스의 용도** : 클래스는 객체를 생성하는데 사용된다.

**객체의 정의** : 실제로 존재하는 것. 사물 또는 개념
**객체의 용도** : 객체가 가지고 있는 기능과 속성에 따라 다름

**유형의 객체** : 책상, 의자, 자동차, TV와 같은 사물
**무형의 객체** : 수학공식, 프로그램 에러와 같은 논리나 개념
> 

<br/><br/><br/>

ex) 

**클래스** : 붕어빵 틀 

**객체** : 붕어빵 (실제로 찍어서 나온 붕어빵) 

그리고 객체 지향에서 객체는 사물과 같은 유형적인 것 뿐만 아니라, 개념이나 논리와 같은 무형적인 것들도 객체로 간주한다. 

우리가 원하는 건 붕어빵(객체)가 필요한 것이지, 붕어빵틀(클래스)가 필요한 것은 아니다. 

붕어빵틀(클래스)는 붕어빵(객체)을 만드는데 사용될 뿐이다. 

<br/><br/><br/>

**❓클래스를 정의하고, 클래스로 객체를 생성하는 이유❓**

설계도(클래스)를 통해서 제품(객체)을 만들기 위해서이다. 

클래스를 한 번만 잘 만들어 놓기만 하면, 매번 객체를 생성할 때마다 어떻게 객체를 만들어야 할지를 고민하지 않아도 된다. 

(클래스에서 바로 객체를 찍어내면 되는 것이다) 

<br/><br/><br/><br/><br/>

---

### 객체와 인스턴스

클래스의 인스턴스화(instantiate) → 클래스로부터 객체를 만드는 과정

클래스의 인스턴스(instance) → 어떤 클래스로부터 만들어진 객체

→  객체 = 인스턴스 거의 동일

<br/><br/>

📺 📺 📺 📺 📺

각각 tv는 **인스턴스**라고 하고,

이 모든 인스턴스를 대표하는 것이 **객체**이다. 

<br/><br/><br/><br/><br/>

---

### 객체의 구성요소 - 속성과 기능

객체는 속성과 기능의 집합이다. 

> **속성(property)** : 멤버변수(member variable), 특성(attribute), 필드(field), 상태(state)
**기능(function)** : 메서드(method), 함수(function), 행위(behavior)
> 

<br/><br/>

예시)

**속성** : 크기, 길이, 높이, 색상, 볼륨, 채널 등

**기능** : 켜기, 끄기, 볼륨 높이기, 볼륨 낮추기, 채널 변경하기 등

<br/><br/><br/><br/><br/>

---

### 인스턴스의 생성과 사용

**1️⃣ Tv 인스턴스 생성해보기**

```java
class Tv {
    // Tv 속성
    String color;
    boolean power;
    int channer;

    // Tv의 기능
    void power(){
        power = !power;

        String onOff = (power) ? "on" : "off";
        System.out.println("전원 "+ onOff);
    }

    void channelUp() {
        ++channer;
        System.out.println("채널 "+ channer);
    }

    void channelDown() {
        --channer;
        System.out.println("채널 "+ channer);
    }
}

public class TvTest {
    public static void main(String[] args){
        Tv t = new Tv(); // Tv인스턴스 생성
        t.channer = 7;
        t.power = false;
        // 채널 7에 전원은 꺼져있는 상태

        t.power(); // 전원 on
        t.channelDown();  // 채널 6
    }
}

```

<br/>

`Tv t` → Tv 클래스 타입의 참조변수 t 선언. 아직 인스턴스가 생성되지 않았으므로 아무것도 못한다.

`t = new Tv();` → new에 의해 Tv 클래스의 인스턴스가 메모리의 빈 공간에 생성된다. 

<br/><br/>

> 인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야 한다.
> 

→ 너무 어렵게 써놨다. 

→ TV를 사용하려면 TV리모콘으로, 붕어빵을 만들려면 붕어빵 틀을 이용해야 한다는 말 


<br/><br/><br/>

**2️⃣ 인스턴스 2개 생성하기 & 대입하기**  

```java
public class TvTest {
    public static void main(String[] args){
        Tv t1 = new Tv(); // Tv인스턴스1 생성
        Tv t2 = new Tv(); // Tv인스턴스2 생성

        t2 = t1;
        t1.channer=7;

        System.out.println(t1.channer); // 7
        System.out.println(t2.channer); // 7
    }
}
```
<br/><br/><br/><br/>



![image](https://github.com/haeburney/StudyManage/assets/76997276/d268fc94-95fc-452e-b5e4-ce69e2c2a357)


`**t2 = t1;**` 을 하면 위 사진처럼 된다.

<br/>

**t2**와 **t1** 둘 다 **t1이 참조하고 있던 인스턴스**를 같이 참조하게 되고, t2가 원래 참조하고 있던 인스턴스는 더 이상 **사용할 수 없게** 된다.

→ 이렇게 참조변수가 하나도 없는 인스턴스는 더 이상 사용되어질 수 없으므로 ‘**가비지 컬렉터**(Garbage Collector)에 의해서 **자동적으로 메모리에서 제거**된다. 

<br/><br/><br/><br/><br/>

---

### 객체 베열

```java
class Tv {
    // Tv 속성
    String color;
    boolean power;
    int channel;

    // Tv의 기능
    void power() {
        power = !power;
    }

    void channelUp() {
        ++channel;
    }

    void channelDown() {
        --channel;
    }
}

public class TvTest {
    public static void main(String[] args) {
        Tv[] tvArr = new Tv[3];
        // Tv클래스의 인스턴스를 저장할 수 있는 공간을 3개 만든 것. 

        for (int i = 0; i < tvArr.length; i++) {
            tvArr[i] = new Tv();
            // 왜 이렇게 낯설지? 
            tvArr[i].channel = i + 10;
        }

        for (int i = 0; i < tvArr.length; i++) {
            tvArr[i].channelUp();
            System.out.println(i + " : " + tvArr[i].channel + "번");
        }

    }
}

```

<br/><br/><br/><br/><br/>

---

### 클래스의 또 다른 정의

자바와 같은 객체 지향 언어에서는 변수(데이터)와 함수를 하나의 클래스에 정의하여 서로 관계가 깊은 변수와 함수들을 함께 다룰 수 있게 했다. 

<br/>

**사용자정의 타입(user-defined type)**

프로그래밍언어에서 제공하는 자료형(primitive type)외에 프로그래머가 **서로 관련된 변수**들을 **묶어서** **하나의 타입으로** 새로 추가하는 것을 사용자정의 타입이라고 한다.

<br/>

**EX)**

```java
class Time {
	int hour;
	int minute;
	float second; 
}
```

<br/><br/>
