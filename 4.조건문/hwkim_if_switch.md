# 조건문과 반복문

### 조건문

**① if**

**② switch**

```sql
switch (조건식) {
	case 값1 :
			// 조건식의 결과가 값1과 같을 경우 수행될 문장들
			break;
	case 값2 : 
			// 조건식의 결과가 값1과 같을 경우 수행될 문장들
			break;
	default : 
			// 조건식의 결과와 일치하는 case문이 없을 때 수행될 문장들
}
```

조건식의 결과와 일치하는 case 문이 하나도 없는 경우에는 default문으로 이동한다.

그리고 만약 break문을 생략하면 case문 사이의 구분이 없어지므로 다른 break문을 만나거나 switch문 블럭{}의 끝을 만날 때까지 나오는 모든 문장들을 수행한다.

그러나 경우에 따라서는 다음과 같이 고의적으로 break문을 생략하는 경우도 있다. 

<br/><br/><br/>

```sql
switch (level){
	case 3 : 
		grantDelete();  // 삭제권한을 준다.
	case 2 :
		grantWrite();   // 쓰기권한을 준다.
	case 1 :
		grantRead();    // 읽기권한을 준다.
}
```

회원제로 운영되는 웹사이트에서 많이 사용될 만한 코드이다.

등급에 맞는 권한을 부여하는 방식이다.

