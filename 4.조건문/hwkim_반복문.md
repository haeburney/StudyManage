# 반복문

### 향상된 for문

```java
for( 타입 변수명 : 배열 또는 컬렉션) {
	// 반복할 문장
}
```

<br/><br/>

**예제1)**

기존에 쓰던 for문

```java
for(int i=0; i < arr.length; i++) {
	System.out.println(arr[i]);
}
```
<br/>

향상된 for문

```java
for(int tmp : arr) {
	System.out.println(tmp);
}
```

하지만 향상된 for문은 일반적인 for문과 달리 배열이나 컬렉션에 저장된 요소들을 읽어오는 용도로만 사용할 수 있다는 제약이 있다. 

<br/><br/><br/><br/><br/>

### while문

**for문보다 while문이 더 적합한 예제들**

**1) 숫자의 각 자리 합을 구하기** 

```java
class FlowEx25 {
	public static void main(String[] args){
		int num = 12345, sum = 0;
		
		while(num != 0){
			// num을 10으로 나눈 나머지를 sum에 더함
			sum += num%10;
			System.out.printf("sum=%3d num=%d%n", sum, num);
			
			num /= 10;
		}
		
		System.out.println("각 자리수의 합:" + sum);
	}
}

// sum=  5 num= 12345
// sum=  9 num= 1234
// sum= 12 num= 123
// sum= 14 num= 12
// sum= 15 num= 1
```
<br/><br/><br/>
입력받기 (단, 특정 키 입력시 종료) 

```java
int num;
int sum = 0;
boolean flag = true;
Scanner scanner = new Scanner(System.in);

while(flag) { 
	System.out.print(">");
	
	num = Integer.parseInt(scanner.nextLine());
	
	if(num!=0){ 
		sum += num; // 0이 아니라면 sum에 더해주기 (총합 구하기) 
	} else { // num=0 이라면 flag = flase를 주어서 while문에서 벗어나기 
		flag = false;
	}
	
}

System.out.println("합계:" + sum);

// > 100
// > 200
// > 300
// > 400
// > 0
// 합계:1000
```
<br/><br/><br/>

### do-while문

do-while문은 while문의 변형으로 기본적인 구조는 while문과 같으나 조건식과 블럭{}의 순서를 바꿔놓은 것이다. 

<br/>

```java
do {

} while (조건식);
```

<br/><br/>

사용되는 예제 

```java
int input = 0;
int answer = (int)(Math.random() * 100) + 1; // 1~100사이의 임의의 수를 저장
Scanner scanner = new Scanner(System.in);

do {
	System.out.println("1과 100사이의 정수를 입력하세요.>");
	input = scanner.nextInt();
	
	if(input > answer) {
		System.out.println("더 작은 수로 다시 시도해보세요.");
	} else if(input < answer) {
		System.out.println("더 큰 수로 다시 시도해보세요.");
	} while(input!=answer);
}

System.out.println("정답입니다.");

// 1과 100사이의 정수를 입력하세요.>50
// 더 작은 수로 다시 시도해보세요.
// 1과 100사이의 정수를 입력하세요.>25
// 더 작은 수로 다시 시도해보세요.
// 1과 100사이의 정수를 입력하세요.>12
// 더 큰 수로 다시 시도해보세요.
// 1과 100사이의 정수를 입력하세요.>21
// 정답입니다. 
```

<br/><br/><br/><br/><br/>


### continue문

continue문은 반복문 내에서만 사용될 수 있으며, 반복이 진행되는 도중에 continue문을 만나면 반복문의 끝으로 이동하여 다음 반복으로 넘어간다.

break과 다른 점

break는 블록을 벗어나지만,

continue는 다음 반복을 계속 수행한다. 

<br/>

예제 3의 배수만 출력하는 프로그램

```java
for(int i=0;i <= 10; i++) {
	if( i % 3 != 0) {
		continue;
	}
	System.out.println(i);
}

// 3 
// 6 
// 9
```

<br/><br/><br/><br/><br/>

### 이름 붙은 반복문

```java
public class Test {
    public static void main(String[] args){
        Loop1 : for(int i=2;i<=9;i++){
            for(int j=1;j<=9;j++){
                if(j==5){
                    break Loop1;
                    // break;
                    // continue Loop1;
                    //continue;
                }
                 System.out.println(i+"*"+j+"="+ (i*j));
            }
            System.out.println("hi");
        }
    }
}

// 2*1=2
// 2*2=4
// 2*3=6
// 2*4=8
```

<br/><br/><br/>

```java
public class Test {
    public static void main(String[] args){
        Loop1 : for(int i=2;i<=9;i++){
            for(int j=1;j<=9;j++){
                if(j==5){
                    //break Loop1;
                    break;
                    // continue Loop1;
                    //continue;
                }
                 System.out.println(i+"*"+j+"="+ (i*j));
            }
            System.out.println("hi");
        }
    }
}

/*
2*1=2
2*2=4
2*3=6
2*4=8
hi
3*1=3
3*2=6
3*3=9
3*4=12
hi

...

8*1=8
8*2=16
8*3=24
8*4=32
hi
9*1=9
9*2=18
9*3=27
9*4=36
hi
*/
```

<br/><br/><br/>

```java
public class Test {
    public static void main(String[] args){
        Loop1 : for(int i=2;i<=9;i++){
            for(int j=1;j<=9;j++){
                if(j==5){
                    //break Loop1;
                    //break;
                    continue Loop1;
                    //continue;
                }
                 System.out.println(i+"*"+j+"="+ (i*j));
            }
            System.out.println("hi");
        }
    }
}

/*
2*1=2
2*2=4
2*3=6
2*4=8
3*1=3
3*2=6
3*3=9
3*4=12

...

8*1=8
8*2=16
8*3=24
8*4=32
9*1=9
9*2=18
9*3=27
9*4=36
*/
```

<br/><br/><br/>

```java
public class Test {
    public static void main(String[] args){
        Loop1 : for(int i=2;i<=9;i++){
            for(int j=1;j<=9;j++){
                if(j==5){
                    //break Loop1;
                    //break;
                    // continue Loop1;
                    continue;
                }
                 System.out.println(i+"*"+j+"="+ (i*j));
            }
            System.out.println("hi");
        }
    }
}
/*
2*1=2
2*2=4
2*3=6
2*4=8
2*6=12
2*7=14
2*8=16
2*9=18
hi
3*1=3
3*2=6
3*3=9
3*4=12
3*6=18
3*7=21
3*8=24
3*9=27
hi

...

9*1=9
9*2=18
9*3=27
9*4=36
9*6=54
9*7=63
9*8=72
9*9=81
hi
*/
```
