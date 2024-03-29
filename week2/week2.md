# 자바 데이터 타입, 변수 그리고 배열

### 💻목표

> 자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법을 익힌다.

<br>

## Primitive 타입과 Reference 타입

코딩을 하면서 `int`, `long`등 여러가지 데이터 타입을 사용하여 변수/상수들을 선언해 본적이 있을 것이다.  
간편하게 하나로만 사용하면 되지 왜 여러개로 나눈 것일까?  
이는 **효율적인 메모리 사용**을 위해서이다.

만약 데이터 타입이 하나만 존재한다고 가정해보자.  
우리는 굉장히 큰 수까지 사용하기 때문에 64bit 단위로 수를 나타낼 것이다.  
이러한 상황에서 1부터 100까지만 사용하기만 한다면..?  
7개의 bit로만 커버가 가능하나 우리는 64bit 단위로만 사용이 가능하므로 57개의 bit는 낭비된다.  
이런 단점을 보완하기 위해 여러가지 종류의 데이터 타입을 만들어 적재적소에 사용하는 것이다.

Java에서도 기본적으로 내장되어 있는 **기본형 타입**과, 그 외 나머지들은 **참조형 타입**으로 나뉜다.

* 기본형
  * 범위가 존재하고 기본값이 존재하여 `null`을 사용하지 않음
  * Stack 메모리에 저장
  * 전역으로 선언된 변수는 컴파일러가 알아서 초기화(기본값)  
    지역 변수에서는 직접 초기화하지 않는다면 컴파일 에러
* 참조형
  * 기본형을 제외한 타입들은 모두 참조형
  * 실제 값을 가지고 있는 것이 아닌 Heap 공간에 할당된 위치를 가지고 있음
  * `null`이 존재

<br>

## Primitive 타입 종류와 값의 범위 그리고 기본값

Java에서는 8개의 원시형 데이터 타입을 제공한다.

| Data Type | Bit  |              Range              | Default Value |
| :-------: | :--: | :-----------------------------: | :-----------: |
|   byte    |  8   |           -128 ~ 127            |       0       |
|   short   |  16  |        -32,768 ~ 32,767         |       0       |
|    int    |  32  |        -2^31^~ 2^31^- 1         |       0       |
|   long    |  64  |       -2^63^ ~ 2^63^ - 1        |      0L       |
|   float   |  32  |  3.4 * 10^-38^ ~ 3.4 * 10^38^   |     0.0f      |
|  double   |  64  | 1.7 * 10^-308^ ~ 1.7 * 10^308^  |     0.0d      |
|   char    |  16  | '\u0000'(0) ~ '\uffff' (65,535) |   '\u0000'    |
|  boolean  |  1   |           true/false            |     false     |

<br>

## 변수 선언 및 초기화 하는 방법

변수 선언의 경우, 해당 변수의 타입과 이름을 작성하면 해당 타입의 크기만큼 메모리가 할당된다.  
또 선언시 바로 해당 변수를 초기화 할 수 있다.

```java
int number;   // 선언
number = 123; // 초기화

int age = 20; // 선언 및 초기화

User user1 = new User("jongnan", 20); // User 객체 타입 선언 및 초기화
```

만약, 선언만 하고 해당 값을 사용한다면 어떻게 될까?  
바로 에러가 뜨는 것을 확인 할 수 있다.  
그렇기 때문에 변수를 사용하기 위해서는 초기화는 **필수**이다.

<br>

## 리터럴

`literal`이란 단어를 살펴보자.  
리터럴은 `정확한`,`융통성 없는`,`문자 그대로 정확한` 뜻을 가지고 있다.  
프로그래밍에서도 이와 똑같은 특성을 보인다.  
즉, **변하지 않는(고정된) 데이터**를 의미한다.

이렇게 말로만 설명하면 "뭐지..?"라는 생각을 할 수 있다.  

```java
int num = 10;
```

위와 같은 코드가 존재할 때, `num`이란 `int`형 타입의 변수에 `10`이란 고정된 값을 할당하였다.  
여기서 `10`이 리터럴이란 것이다.  
위의 예 말고도 `true`, `'Jongnan'`, `10.22`등 여러가 가지 타입의 리터럴이 존재한다.

* 정수 리터럴

  > 기본 숫자(1, 2, 100 등의 10진수)만 존재하는 리터럴 사용시 int형으로 판단한다.  
  > 만약, `L` 혹은 `l`(영어, 1과 혼동이 있을 수 있음, 권장 X)을 사용한다면 long형 리터럴이 된다.  
  > 2진수는 `0b`를, 8진수는 `0`을, 16진수는 `0x`를 앞에 붙혀 리터럴을 사용할 수 있다.  
  > byte, short 타입의 변수에 가능한 숫자 범위의 리터럴을 사용시에는 에러가 발생하지 않는다.

* 부동 소수점 리터럴

  > float형일 경우 숫자 마지막에 `F` 혹은 `f`를 붙히고 double일 경우에는 `D` 혹은 `d`를 붙힌다.  
  > 두가지 모두 `E`와 `e`를 사용하여 나타낼 수도 있다.
  >
  > ```java
  > double a = 111.1d;
  > double b = 1.111e2; //a와 b는 111.1이란 동일한 값을 나타냄
  > ```

* 문자 및 문자열 리터럴

  > `''`(작은 따옴표)의 경우 문자 리터럴이 그리고 `""`(큰 따옴표)의 경우 문자열 리터럴을 나타낸다.
  > 유니코드 형식으로도 문자와 문자열을 나타낼 수 있다.  
  > 또한, 자바에서 `\`(역 슬래쉬)를 사용하여 특정 시퀀스를 나타낼 수 도 있다.(`\t`(탭), `\n`(줄 바꿈)...)

* 숫자 + 밑줄 리터럴

  > Java SE 7 이후 버전에서는 숫자와 `_`(Under bar)를 사용하여 특정 단위를 구분지을 수 있다.
  >
  > ```java
  > int birth = 99_12_25;
  > ```
  >
  > `_`는 반드시 숫자 사이에만 존재할 수 있다.

<br>

## 변수의 스코프와 라이프 타임

### # 스코프

변수의 스코프란, 해당 변수가 영향을 끼칠 수 있는 영역을 의미한다.  
즉, 변수를 할당하거나 사용하기 위해서는 해당 변수 스코프 안에서만 가능하다는 것이다.

Java는 C/C++와 동일하게 **Lexical Scope**를 따르고 있다.  
렉시컬 스코프는 변수 혹은 메소드를 어디에 **선언**을 하였는가에 따라 스코프가 달라지는 것이다.  
그렇기 때문에 Java에서는 여러가지 종류의 변수들이 존재한다.

* #### 인스턴스 변수(Non-Static) / 클래스 변수(Static)

  잠깐! `static` 필드란?

  > 스태틱 필드를 선언하게 되면, 해당 변수/메소드는 클래스가 로딩되는 순간 한번만 인스턴스화 된다.  
  > 그렇기 때문에 해당 객체를 생성하지 않아도 변수 혹은 메소드를 바로 사용할 수 있다.

  인스턴스 변수와 클래스 변수 모두 클래스 영역에 선언된 변수로 클래스 내부에서 접근이 가능하다.

  ```java
  public class Human {
    static String type = "표유류";  // 클래스 변수
    String name;                  // 인스턴스 변수
    int age;                      // 인스턴스 변수
  }
  ```

  두 변수의 차이는 `static` 필드의 특징을 가지느냐 아니냐이다.  
  즉, `type`(클래스 변수)의 경우 클래스가 로딩되는 순간 한번만 인스턴스화가 되기 때문에 여러 `Human` 객체에서 접근해도 같은 값을 표시한다.  
  반대로 인스턴스 변수는 객체가 생성될 때마다 따로 공간이 생기게 된다.  

* #### 지역 변수

  지역(`{}` 중괄호)을 기준(스코프)으로 하는 변수로 일반 변수를 선언하는 것과 똑같다.

  ```java
  public class Human {
    static String type = "표유류";
    String name;
    int age;
    
    boolean isAdult() {
      int korBase = 20;       // 지역 변수
      return age >= korBase;
    }
  }
  ```

  그렇다면, 아래와 같이 인스턴스/클래스 변수와 지역 변수의 이름이 같다면 어떤 상황이 벌어질까?

  ```java
  public class Main {
    static int a = 1;
    void method() {
      int a = 5;
      System.out.println(a);
    }
  }
  ```

  답은 `5`가 나오게 된다.  
  즉, **지역 변수가 인스턴스/클래스 변수보다 우선순위를 가진다.**

  또한 다른 지역에 있는 변수는 접근이 불가능하다.

  ```java
  public class Main {
   // method_A 지역
    void method_A() {
      int a = 5;
    }
    // method_B 지역
    void method_B() {
      System.out.println(a); // 접근 불가(에러 발생)
    }
  }
  ```

* #### 매개 변수

  지역 변수와 똑같이 해당 지역 내에서만 사용이 가능하며, 인스턴스/클래스 변수보다 높은 우선 순위를 가진다.

### # 라이프타임

스코프가 변수가 영향을 미칠 수 있는 **영역**이라면, 라이프 사이클은 변수가 영향을 미칠 수 있는 **시점**이다.  
즉, 어느 위치에 어떻게 선언 되었느냐에 따라 어느 시점에 이 변수를 호출할 수 있는가가 달라진다.

* #### 인스턴스 변수

  인스턴스가 생성될 때부터 메모리에 존재할 때 까지(GC에 의해 수거 되기 전까지) 접근 가능하다.

* #### 클래스 변수

  클래스가 로딩될 때 부터 프로그램이 종료 될 때까지 접근 가능하다.

* #### 지역 변수

  선언이 되고 초기화 될 때부터 지역이 끝날 때까지(`}`) 접근이 가능하다.

<br>

## 타입 변환, 캐스팅 그리고 타입 프로모션

타입 변환(캐스팅)은 어떠한 데이터 타입으로 지정된 변수를 다른 타입으로 변경하는 것을 말한다.

여기서 궁금한 점이 하나 생긴다.  
범위가 작은 타입에서 큰 타입으로의 변환은 괜찮을 거라 생각하지만, 그 반대는 어떻게 될까..?  
이 때는 Java 컴파일러가 이를 파악하여 오류를 발생시킨다.

Java에서는 타입 변환은 다음과 같이 크게 두 가지 종류로 나뉜다.

* #### 묵시적(자동 변환, Promotion)

  대입 혹은 산술 시에 컴파일러가 자동으로 타입을 변환 해주는 것을 말한다.(`boolean` 제외)

  ```java
  int num = 100;
  double doubleNum = num;        // 100.0
  double sum = num + doubleNum;  // 200.0
  ```

  위와 같이 `int`형의 변수를 `double`형의 변수에 대입하거나 산술 시에 에러 없이 가능하고 출력 시에 형 변환이 일어난 것을 볼 수 있다.  
  신기하게도 3번째 줄과 같이 `int`형과 `double`형의 덧셈도 가능하다는 것이다.  
  이는 Java 컴파일러에서 `int`형을 `double`형으로 형 변환을 하는데 이를 **Promotion**이라고 한다. 

  이렇게 Java 컴파일러에 의해 데이터 손실이 없는 한에서 자동으로 타입 변환이 일어난다.

  > 자동 타입 변환 가능 표
  >
  > ```java
  > byte → short → int → long → float → double
  >                 ↑
  >                char(범위는 short와 같으나 char는 음수가 존재하지 않으므로 int형부터 가능)
  > ```

* #### 명시적(강제 변환, Casting)

  사용자가 타입 캐스트 연산자( `()` )를 통해 직접 형 변환 하는 것(Casting)을 말한다.

  ```java
  int a = 3;
  int b = 5;
  double div1 = a / b;         // 0.0
  double div2 = (double)a / b; // 0.6
  ```

  여기서 주의 할 점은 `div1`과 `div2` 의 차이에 있다.

  `div1`은 `0.0` 이 나오는 것을 확인할 수 있는데 이는 `a`, `b`가 `int`형이기 때문이다.  
  Java에서는 결과값은 피연산자의 타입과 일치해야 되기 때문에 `a / b`는 `int`형이 되어 소수점 아래는 짤리게 된다.  
  그 이후, Java 컴파일러에 의해 자동 형 변환이 일어나기 때문에 `0.0`이 나오게 된다.

  `div2`와 같이 `a`를 타입 캐스트 연산자로 `double`형으로 **Casting** 한 뒤에 연산을 하게 되면 Promotion에 의해 결과값이 `double`형으로 나오게 되므로 `0.6`이 나올 수 있는 것이다.

<br>

## 타입 추론, var

Java 10부터 초기화 된 값을 보고 타입을 추론할 수 있는 `var` 라는 키워드가 생겼다.  
해당 변수가 어떤 타입인지 컴파일러가 추론해야 하기 때문에 선언과 동시에 초기화는 필수적이다.

```java
// java 10 이전
String str = "hi!";

// java 10 이후
var str = "hello!!";
```

초기화 외에도 주의할 점이 있는데 이는 Java 7에서 나온 `<>` 연산자이다.  
다이아몬드 연산자의 경우, 선언된 타입을 보고 타입을 추론하기 때문에 `var`와 같이 사용될 수 없다.  
이 외에도 여러 상황에서 에러가 발생할 수 있다.

```java
var lists = new ArrayList<>();           // Error : type 추론 실패
var empty = null;                        // Error : null 허용 X
public var num = 10;                     // Error : 로컬 변수만 허용
var str = (String s) -> s.length() > 5;  // Error : 람다식 불가
var arr = {1,2,3,4};                     // Error : 배열 리터럴 불가
```

<br>

## 1차 및 2차 배열 선언하기

### # 1차 배열

> 배열은 데이터들을 담는 간단한 자료구조중 하나로 연속적인 메모리를 가지고 있으며, Random 접근이 가능하다.

* #### 선언

  ```java
  // 모든 타입 가능 및 다음과 같이 선언
  int[] intArr;
  long []longArr;
  String strArr[];
  ```

  배열은 다음과 같이 3가지 방법을 사용하여 선언이 가능하다.  
  위 상태에서는 초기화가 되어있지 않기 때문에 메모리를 차지하지 않는다.

* #### 초기화

  ```java
  int[] intArr;
  intArr = new int[5];
  ```

  위와 같이 초기화가 가능하고 5개의 int형 데이터를 넣을 수 있는 공간을 초기화하였다.  
  배열의 값들은 기본값으로 셋팅되어 있다.(`int` → 0)

* #### 선언 + 초기화

  ```java
  int[] intArr = new int[5];  // 1)
  int[] intArr2 = {1,2,3,4,5};// 2)
  ```

  선언과 초기화를 동시에 할 수 있고,  `2)`와 같이 배열 리터럴을 사용하여 기본값을 셋팅할 수 도 있다.

### # 2차 배열

> 2차원 배열은 1차원 배열의 데이터 형태가 배열로 배열 안에 또다른 배열이 존재하는 것이다.

* #### 선언

  ```java
  int[][] intArr;    // 1) 
  long [][]longArr;  // 2) Error
  String strArr[][]; // 3) Error
  ```

  1차원 배열과는 다르게  `1)` 방식으로만 선언이 가능하다.

* #### 초기화

  ```java
  int[][] intArr;
  intArr = new int[3][3];
  ```

  1차원 배열과 똑같은 방식으로 초기화가 가능하며, 위에서는 3개의 공간 안에 또다른 3개의 공간을 생성했다.(3*3)

* #### 선언 + 초기화

  ```java
  int[][] intArr = new int[3][3];
  int[][] intArr2 = {{1,2,3},{4,5,6},{7,8,9}};
  ```

  1차원 배열과 동일하게 선언과 초기화를 동시에 할 수 있으며, 배열 리터럴 또한 사용이 가능하다.

<br>

---

### Reference

* [자바의 데이터 타입(Primitive type, Reference type)](https://gbsb.tistory.com/6)
* [ORACLE - The Java™ Tutorials - Primitive Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
* [Scope and Lifetime of a Variable in Java](https://www.learningjournal.guru/article/programming-in-java/scope-and-lifetime-of-a-variable/)
* [TCP School - 타입 변환](http://www.tcpschool.com/java/java_datatype_typeConversion)
* [Java Basics - Promotion and Casting(영상)](https://www.youtube.com/watch?v=FNPEKwQUJwU&ab_channel=MargretPosch)
* [[Java] 타입 추론](https://velog.io/@bk_log/Java-%ED%83%80%EC%9E%85-%EC%B6%94%EB%A1%A0)
* [Baeldung - Java 10 LocalVariable Type-Inference](https://www.baeldung.com/java-10-local-variable-type-inference)
* [[Java] 자바 1차원 배열 생성(선언 및 초기화)](https://keichee.tistory.com/349)
* [[Java] 자바 2차원 배열 생성(선언 및 초기화)](https://keichee.tistory.com/423)

