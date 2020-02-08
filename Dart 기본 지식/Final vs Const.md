# Final vs Const

## 공통점

* 선언과 정의를 동시에 했다면 다른 값으로 변경이 불가능하다.

## 차이점

### Final

* 런타임에서 결정되는 값을 설정할 수 있다.

### Const

* 컴파일 타임에서 상수를 정의할 수 있다.
* 런타임에서 정의되는 값은 설정할 수 없다.

* 생성자를 사용하여 선언하는 변수에는 `const` 를 사용할 수 있다.

~~~dart
const int myConst = 2 + 5 * 8; //가능, 컴파일 시 정의되기 때문.
const int myConst1 = DateTime.now(); //불가능, DateTime.now()는 런타임 시 정의되는 값이기 때문.
final myFinal = DateTime.now(); //가능, final은 런타임 시 결정되는 값을 설정할 수 있기 때문.
const color = Color(0xFFBE1555); //가능, 생성자를 사용하여 선언하는 변수이기 때문.
~~~

### 출처

* https://www.udemy.com/course/flutter-bootcamp-with-dart/learn/lecture/14485478#overview
* [https://medium.com/dartlang-korea/dart-final-%EA%B3%BC-const-bc8c6c024ef4](https://medium.com/dartlang-korea/dart-final-과-const-bc8c6c024ef4)