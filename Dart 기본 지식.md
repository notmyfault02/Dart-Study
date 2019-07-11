# Dart 기본 지식

---

## 모든 Dart App은 `main()` 함수를 가집니다

~~~dart
void main() {
  print('Hello World');
}
~~~

---

## 변수

* 대부분의 Dart 변수는 명시적으로 타입을 선언할 필요가 없습니다
* 변수에 값이 들어가면 자동으로 타입을 추론합니다

~~~dart
// String 타입
var name = '김영래'; 

// Int 타입
var age = 27;

// List<String> 타입
var companies = ['Apple', 'Orange', 'Grape', 'Banana']; 

// List<Object> 타입
var array = ['apple', 12, 44.5]; 

// Map<List<String>, String> 타입
var image = {
  'tags': ['Human'],
  'url': 'human.jpg'
}; 
~~~

---

## 흐름 제어문

* __If__ 문과 __for__ 문, __while__ 문 등이 있습니다

~~~dart
// if - else 문
if(condition) {
  // true
} else {
  // false
}

// for 문
for (var object in image) {
  print(object);
}

for (int month = 1; month <= 12; month++) {
  print(month);
}

// while 문
while (age < 30) {
  age += 1;
}

~~~

---

## 함수

* Dart에서는 함수의 인자와 반환 값에 타입을 선언하는 것을 권장합니다

~~~dart
int fibonacci(int n) {
  if (n==0 || n==1) return n;
  return fibonacci(n-1) + fibonacci(n-2);
}

var result = fibonacci(20);
~~~

---

## 주석

* Dart의 주석은 보통 `//` 를 사용해 선언합니다

~~~dart
// 주석
/* 여러 글 주석 */
~~~

---

## import

* `import` 를 이용해 다른 라이브러리에서 정의한 __API__에 접근할 수 있습니다

~~~dart
// Dart의 코어 라이브러리를 Import 하고 싶은 경우
import 'dart:math';

// 외부 패키지에서 라이브러리를 Import 하고 싶은 경우
import 'package:test/test.dart';

//파일을 Import 하고 싶은 경우
import 'path/to/my_other_file.dart';
~~~

---

## Classes

* 객체지향 언어가 그러하듯 Dart에서도 Class를 지원합니다.
* 여러 class를 하나로 묶어서 하나의 어플리케이션을 구성한다고 생각하면 편합니다

~~~dart
class Person {
  // Person 클래스가 가지는 속성
  String name;
  
  Person(this.name) {
    // 생성자 함수를 선언하는 기본값
  }
  
  // 이름만 초기화하는 함수
  Person.reset(String name) : this(null);
  
  void describe() {
    // 따옴표 안에 변수의 값을 넣고 싶을 때는 변수 앞에 `$` 를 붙여줍니다
    print('Person: $name');
  }
}
~~~

* 클래스를 선언할 때는

~~~dart
var young = Person('영래');
young.describe(); // '영래' 라는 결과가 나옵니다
~~~

---

## 상속

* Dart에서는 `extends` 키워드를 사용해 상속을 구현할 수 있습니다

~~~dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
    	title: 'Welcom to Flutter',
    	home: Scaffold(
      	appBar: AppBar(
        	title: Text('Welcome to Flutter'),
        ),
      	body: Center(
        	child: Text('Hello World'),
        ),
      ),
    );
  }
}
~~~

* 이 경우 `MyApp` 은 __Flutter__의 `StatelessWidget` 을 상속받아서 구현한 것입니다
* `StatelessWidget` 이 가지고 있던 `Widget` 을 __override__ 하고 있습니다.