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
