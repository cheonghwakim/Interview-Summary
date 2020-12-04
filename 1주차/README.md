# 1주차
 
* [Java와 C의 차이점](#Java와-C의-차이점)
* [객체지향 언어의 특징](#객체지향-언어의-특징)
  * [1. 캡슐화](#1-캡슐화Encapsulation)
  * [2. 정보은닉](#2-정보은닉Information-Hiding)
  * [3. 추상화](#3-추상화Abstraction)
  * [4. 상속성](#4-상속성Inheritance)
  * [5. 다형성](#5-다형성Polymorphism)
* [String, StringBuilder, StringBuffer 차이점](#String-StringBuilder-StringBuffer-차이점)
* [Overloading과 Overriding 차이점](#Overloading과-Overriding-차이점)
* [컬렉션 자료구조 종류와 특징](#컬렉션-자료구조-종류와-특징)
  * [1. Set](#1-Set)
  * [2. List](#2-List)
  * [3. Queue](#3-Queue)
  * [4. Map](#4-Map)
* [동기화와 비동기화](#동기화와-비동기화)

## Java와 C의 차이점

### Java의 특징

1. **운영체제에 독립적**이다.
- JVM에서 자바 바이트 코드를 OS에 맞게 해석하기 때문에 여러 운영 체제에서 같은 코드로 사용 가능하다. (C언어의 경우, OS 및 컴퓨터 아키텍쳐에 따라, 기존 코드를 재사용하기 어렵다.)

2. **객체지향 프로그래밍 언어**이다. [객체지향언어의 특징은 여기로](#객체지향-언어의-특징)

3. **가비지 컬렉션**, 메모리(RAM)가 자동 정리된다. 
- 더 이상 사용되지 않는 오브젝트를 가비지 컬렉션을 담당하는 프로세스가 자동으로 메모리에서 제거한다. 그래서 개발자는 개발에 집중할 수 있다.

4. 캡슐화, 다형성, 상속 등의 특징이 있다. [객체지향 언어의 특징은 여기로](#객체지향-언어의-특징)

5. 뛰어난 보안성과 멀티쓰레드를 지원한다.

### C의 특징

1. **시스템 프로그래밍이 가능**하다. 
- C는 현재 사용되고 있는 거의 모든 컴퓨터 시스템에서 사용할 수 있는 프로그래밍 언어이다. 현재 널리 사용되는 주요 운영체제의 커널은 대부분 C언어를 이용해 구현되어 있다. 시스템 프로그래밍에도 쓰이지만, 응용 프로그래밍에도 많이 사용된다.

2. 다양한 하드웨어로의 **이식성**이 좋다.

3. **처리 속도가 빠르다.**
- C는 컴파일 된 프로세스를 수행한다. 컴파일 과정이 오래 걸릴 뿐 수행시간은 빠르다. 반면 Java는 JVM 인터프리터에 의해 실행 시 매번 번역해야 하기 때문에 실행속도가 느리다.
- C로 짜여진 코드는 속도가 빠르고 바이너리 크리가 작기 때문에 빠른 속도를 필요로 하는 임베디드 혹은 모바일 계열, 시스템 프로그래밍 등에서 주로 사용된다.

- C코드는 [ Editor -> Source File --(컴파일)--> Object File --(링크)--> 실행 File -> 프로그램 실행 ] 순서로 진행
  - 컴파일 : 프로그래밍언어로 작성한 원시코드파일을 기계어로 번역하여 목적코드파일에 저장
  - 링크 : 목적코드 파일과 라이브러리 파일을 하나로 합처 실행파일 생성

  - cf. Java코드는 링크과정이 없음 컴파일러가 바로 바이트코드를 생성.


4. **절차지향 프로그래밍 언어**이다.
- 한줄 한줄 순차적으로 처리되기 때문에 흐름을 알기는 쉬우나 디버깅, 유지보수가 어렵다.

### Java와 C의 차이점

| C | Java |
|---|------|
| 절차지향 | 객체지향 |
| 유지보수, 디버깅 어려움 | 유지보수, 디버깅 용이함 |
| 실행/처리속도 빠름 | 상대적으로 느림 |
|프로그램 데이터 처리 방법인 알고리즘 중요 | 알고리즘 < 프로그램이 사용하고 있는 데이터 |



## 객체지향 언어의 특징

### 1. 캡슐화(Encapsulation)

**캡슐화는 데이터(속성)와 데이터를 처리하는 함수를 하나로 묶은 것**을 의미한다. Java에서 객체는 Method와 Field로 구성되고, 이 Method와 Field를 Class라는 캡슐에 구현한다.
- 캡슐화된 **객체의 세부 내용이 외부에 은폐(정보 은닉)**되어, 변경이 발생할 때 오류의 파급 효과가 적다.
- 캡슐화된 객체들은 **재사용이 가능**하다.
- 객체 간 메세지를 주고받을 때 각 객체의 세부 내용은 알 필요가 없으므로 **인터페이스가 단순해지고, 객체 간의 결합도가 낮아진다.**

### 2. 정보은닉(Information Hiding)

캡슐화에서 가장 중요한 개념으로, **다른 객체에게 자신의 정보를 숨기고 자신의 연산만을 통하여 접근을 허용**하는 것이다.
- 각 객체의 수정이 다른 객체에게 주는 영향을 최소화 하는 용도이다.
- 외부 객체가 특정 객체의 데이터와 함수를 직접 접근하여 사용하거나 변경하지 못하게 하여 유지보수와 소프트웨어 확장 시 오류를 최소화한다.

### 3. 추상화(Abstraction)

추상화는 불필요한 부분을 생략하고 **객체의 속성 중 가장 중요한 것에만 중점을 두어 개략화(모델화)**하는 것이다. 좀 더 쉽게 말하면, 복잡한 구조의 시스템을 생각이 가능한 수준의 덩어리로 만들어 관리 가능할 수준으로 만들어 나가는 것이 추상화이다.
- 완전한 시스템을 구축하기 이전에 그 시스템과 유사한 모델을 만들어 여러가지 요인을 테스트할 수 있다.
- 추상화를 통해 최소의 비용으로 실제 상황에 대처할 수 있고, 시스템의 구조 및 구성을 가시적으로 볼 수 있다.

### 4. 상속성(Inheritance)

상속성은 이미 정의된 **상위 클래스(부모 클래스)의 모든 속성과 연산을 하위 클래스가 물려 받는 것**이다.
- 상속성을 이용하면 하위 클래스는 상위 클래스의 모든 속성과 연산을 자기 클래스 내에서 다시 정의하지 않아도 즉시 사용할 수 있다.
- 하위 클래스는 상위 클래스로부터 상속받은 속성과 연산 외에 **새로운 속성과 연산을 추가하여 사용할 수 있다.**
- 상위 클래스의 속성과 연산을 하위 클래스가 물려받을 수 있기 때문에 객체와 클래스의 재사용, 즉 소프트웨어 재사용이 가능하다.


<p align="center">
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZvnWN%2FbtqxTLYsCHd%2FLLlllKZ4wkcfC8Hmcd1Kl0%2Fimg.png" height="250" width="700">
</p>

### 5. 다형성(Polymorphism)

다형성은 **같은 이름의 메소드 호출에 대하여 객체에 따라 다른 동작을 할 수 있도록 구현**되는 것이다. 상속받은 클래스의 Method를 재사용하는 것을 오버라이딩(Overriding)이라 하는데, 다형성을 할 때 [오버로딩과 오버라이딩](#Overloading과-Overriding-차이점)이 있다.
- 객체들은 모두 동일한 메소드명을 사용하며 같은 의미의 응답을 한다.

<p align="center">
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FI7rhG%2FbtqxVzCNjsm%2FlnUwxkofn8pZfGiXjQBE90%2Fimg.png" height="250" width="700">
</p>

## [String, StringBuilder, StringBuffer 차이점](https://github.com/cheonghwakim/CS-STUDY/tree/main/JAVA#String,-StirngBuffer,-StringBuilder%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

## Overloading과 Overriding 차이점

- Overloading : 두 메소드가 같은 이름을 갖고 있으나 **인자의 수나 자료형이 다른 경우**이다.
- 예시
``` java
public double computeArea(Circle c) {...}
public double computeArea(Circle c1, Circle c2) {...}
public double computeArea(Square s) {...}
```

- Overriding: **상위 클래스의 메소드와 이름, 인자가 같은 함수를 하위 클래스에 재정의** 하는 것이다.
- 예시
``` java
public abstract class Shape {
  public void printMe() { System.out.println("Shape"); }
  public abstract double computeArea();
}
public class Circle extends Shape {
  private double rad = 5;
  @Override // 개발자의 실수를 방지하기 위해 @Override(annotation) 쓰는 것을 권장
  public void printMe() { System.out.println("Circle"); }
  public double computeArea() { return rad * rad * 3.15; }
}
public class Ambiguous extends Shape {
  private double area = 10;
  public double computeArea() { return area; }
}
```
``` java
public class Main {
  public static void main(String[] args) {
    Shape[] shapes = new Shape[2];
    Circle circle = new Circle();
    Ambiguous ambiguous = new Ambiguous();

    shapes[0] = circle;
    shapes[1] = ambiguous;

    for(Shape s : shapes) {
      s.printMe();
      System.out.println(s.computeArea());
    }
  }
}
```
- 위의 코드에서 computeArea함수의 이름, 인자의 종류, 수가 같지만 안의 로직은 조금씩 다르다.


## Collection 자료구조 종류와 특징

**Collection은 데이터의 집합, 그룹을 의미한다.** JCF(Java Collections Framework)는 이러한 데이터, 자료구조인 컬렉션과 이를 구현하는 클래스를 정의하는 인터페이스를 제공한다. 아래의 사진은 Java 컬렉션 프레임워크의 상속 구조를 나타낸다.

<p align="center">
  <img src="https://blog.kakaocdn.net/dn/I1jdr/btqDACgkEMb/VwcO1xEQWKVDiH5NQFAyp1/img.png" height="450" width="550">
</p>

Collection 인터페이스는 또, **List, Set, Queue로 크게 3가지 인터페이스**로 분류된다. Map의 경우 Collection 인터페이스를 상속받고 있지 않지만 Collection으로 분류된다. 

### 1. Set

Set은 **원소 간에 순서가 없고, 중복 값을 허용하지 않는다.**
자바에서는 **HashSet, TreeSet, LinkedList**의 3가지 구현체가 있다.
- HashSet은 해쉬 테이블에 원소를 저장하여 성능 면에서 가장 우수하다.
- TreeSet은 [레드-블랙 트리](https://itstory.tk/entry/%EB%A0%88%EB%93%9C%EB%B8%94%EB%9E%99-%ED%8A%B8%EB%A6%ACRed-black-tree)에 원소를 저장해서, 값에 따라 순서가 결정되지만 HashSet보다는 성능이 느리다.
- **LinkedHashSet은 HashSet의 문제점인 순서의 불명확성의 단점을 제거한 구체이다.**

### 2. List

List는 배열처럼 **순서를 가지는 원소들의 모임으로 중복 값을 가질 수 있는 자료구조**이다.
종류는 **ArrayList, LinkedList, Vector**가 있다.

- ArrayList는 단방향 포인터 구조로 각 데이터에 대한 인덱스를 가지고 있어 조회 기능에 성능이 뛰어나다. 또, 저장되는 데이터의 개수에 따라 크기가 유동적으로 변하기 때문에 초기에 크기를 정해줘야 하는 배열보다 편리하다.
- LinkedList는 **양방향 포인터 구조로 데이터의 삽입, 삭제가 빈번할 경우** 데이터의 위치정보만 수정하면 되기 때문에 유용하다. 스택, 큐, 데큐 등을 만들기 위한 용도로 쓰인다.
- Vector는 과거에 대용량 처리를 위해 사용되었다. 내부에서 자동으로 동기화처리가 일어나 비교적 성능이 좋지않고 무거워서 잘 쓰이지 않는다.

  * 즉, 인덱스를 가지고 원소를 접근하는 연산은 ArrayList의 성능이 더 좋고, 중간에 원소의 삽입 삭제가 빈번히 일어나는 경우에는 LinkedList의 성능이 더 좋다. 
  
  * 배열을 리스트로 변경하기
  ``` java
  List<String> list = Arrays.asList(new String[5]);
  ```
### 3. Queue

Queue는 데이터를 처리하기 전에 잠시 저장하고 있는 **선입선출**의 자료구조이다. tail에서 원소를 추가하고, head에서 원소를 삭제한다. 

### 4. Map

Map 자체는 Collection 인터페이스와 별개이지만, json의 형식과 유사한 Key-Value 자료구조로 자주 쓰인다. Dictionary와 같은 자료 구조로, 중복된 키를 가질 수 없고 각 키는 오직 하나의 값에만 매핑될 수 있다. Map의 종류에는 **HashMap, TreeMap, LinkedHashMap** 등이 있다.
- HashMap은 중복과 순서가 허용되지 않으며 null 값이 올 수 있다. 
- TreeMap은 정렬된 순서대로 키(Key)와 값(Value)를 저장하여 검색이 빠르다.
- HashTable은 HashMap보다는 느리지만 동기화가 지원된다. null 값이 올 수 없다.

* HashMap은 해싱 테이블에 데이터를 저장하고 TreeMap은 탐색 트리에 저장한다. 
  * 키들을 **정렬된 순서로 방문할 필요가 없다면 HashMap이 약간 빠르다.**

### Collection 인터페이스의 특징

| 인터페이스 | 구현 클래스 | 특징 |
|------------|-----------|-------|
| Set | HashSet, TreeSet, LinkedHashSet, AbstractSet | 중복 데이터 불허, 입력시 순서 무시, 순차적인 접근 위해 Iterator 사용 |
| List | ArrayList, LinkedList, Vector, AbstractList | 데이터 중복 가능, 수집의 순서 있음, Vector는 동기화/ArrayList는 동기화 X |
| Queue | LinkedList, PriorityQueue | List와 유사 |
| Map | HashMap, Hashtable, TreeMap, AbstractMap, Attribute, IdentityHashMap, RenderingHints, WeakHashMap | 키(Key)-값(Value)의 쌍으로 이루어진 데이터의 집합, 순서는 유지되지 X, 키(Key)의 중복 허용 X & 값(Value)의 중복 허용 O, 많은 양의 데이터에서 원하는 특정 데이터에 접근(검색)할 때 사용 |


## 동기화와 비동기화

### 동기화

어느 메소드가 실행되는 동안 다른 메소드를 실행 불가능하게 블락하는 것이다.

- 서버와 클라이언트가 주고 받는 것이 동기에 이루어지는 형태이다.
- 시스템의 일치가 필요하다. (쉽지만 비쌈)
- 수신하고 다른 매체를 사용 불가능하기 때문에 대기시간 버퍼링이 발생한다.
- 시간적인 동기화가 필요한 곳에 많이 사용된다. (현금인출기)

### 비동기화

어느 메소드를 **실행하는 도중에도** 다시 메소드를 실행 가능하다. (ex. Ajax, thread..)

- 서버와 클라이언트가 주고 받는 것이 동시에 이루어지지 않는 형태이다.
- 시스템의 일치가 필요하지 않다. (비싸지만 쌈)
- 수신하는 동안 다른 작업을 수행 가능하며 버퍼링이 적다.
- 반응이 빠르기 때문에 여러 방면에서 사용 가능하다.

예시.
급하게 알아야 하는 답을 얻기 위해서 누군가에게 물어봐야 하는 상황.
1. 전화로 물어봐서 즉시 답을 얻는다. = 동기 요청처리
2. 이메일로 물어보고 메일송신완료. 하지만 답은 언제 올지 모른다. = 비동기 요청처리
