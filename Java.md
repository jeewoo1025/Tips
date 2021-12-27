## 거듭제곱 구하기 Math.pow()
Java에서 특정값의 제곱을 구하려면 java.lang.Math 클래스의 pow()메소드를 사용하면 된다. Math.pow() 메소드는 입력값과 출력값은 모두 double형이며 `Math.pow(대상숫자, 지수)`를 넣어주면 된다.
```java
double result = Math.pow(5,2);  // 5의 제곱
System.out.println("5의 제곱은 :"+result);
```
<br>

## 올림 Math.ceil()
입력 입자 값보다 크거나 같은 가장 작은 정수 값을 double형으로 반환한다. 
```java
System.out.println(Math.ceil(10.675));  // 11.0
System.out.println(Math.ceil(-9.12));   // -9.0
```
<br>

## 내림 Math.floor()
입력 인자 값보다 작거나 같은 가장 큰 정수 값을 double형으로 반환한다
```java
System.out.println(Math.ceil(10.675));  // 10.0
System.out.println(Math.ceil(-9.12));   // -10.0
```
<br>

## String.format(String format, Object args)
문자열 형식을 설정하는 메소드로 정수, 문자열, 실수형 형식이 다르다.
```java
int num = 23;
float num2 = 123.45678;

// 정수 
System.out.println(String.format("%5d_", num));  //    23_, 오른쪽 정렬
System.out.println(String.format("%-5d_", num));  // 23   _, 왼쪽 정렬

// 실수
System.out.println(String.format("%.3f_", num2));  // 123.457_, 소수점 아래 3자로 나타냄
System.out.println(String.format("%15.2f_", num2)); //          123.46_, 글자 길이 15, 소수점 아래 2자로 나타냄
```
<br>

## Windows 10에 Java 설치하기
1. [오라클](https://www.oracle.com/java/technologies/downloads/#java8) 홈페이지에서 Java exe 파일 다운로드
2. exe 파일 실행하기
3. 시스템 환경 변수 변경 (JAVA_HOME - jdk 경로, Path - %JAVA_HOME%\bin)
4. cmd 창에서 `java -version` 실행 (버전확인하기) <br>
▶ 링크 : https://fluorite94.tistory.com/384
<br>


