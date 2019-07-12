# Mixins

- Mixins은 여러 클래스에서 코드를 재사용 하는 방법입니다.

- mixin 키워드는 dart 2.1에서 소개되었으며, 어떤 면에서는 추상 클래스와 유사하고 다른 면에서는 다릅니다.

- 추상 클래스처럼 mixin에서 추상적인 메소드를 선언할 수 있으며, 그것을 인스턴스화 할 수 없습니다.

- 그러나 추상 클래스와는 달리 mixin을 확장할 수 없습니다.

- Mixin 을 사용하려면  `with` 키워드 뒤에 하나 이상의 mixin을 사용합니다.

  ~~~dart
  class B {
    method() {
      print("B method");
    }
  }
  
  class A with B {}
  
  void main() {
    A a = A();
    a.method(); //실행결과는 'B method()'
  }
  ~~~

- mixin을 구현하려면, Object를 확장하고 생성자를 선언하지 않는 클래스를 만듭니다. mixin을 일반 클래스로 사용하지 않으려면 클래스 대신 `mixin` 키워드를 사용합니다.

  ~~~dart
  class Performer {
    void perform() {
      print('perform...');
    }
  }
  
  mixin Dancer {
    void perform() {
      print('dance dance');
    }
  }
  
  mixin Singer {
    void perform() {
      print('lalala');
    }
  }
  
  class Musician extends Performer withDancer, Singer {
    void showTime() {
      perform();
    }
  }
  
  void main() {
    Musician m = Musician();
    
    m.perform();	//실행결과는 'lalala'
  }
  ~~~

- 여러 개의 mixin을 사용할 때, 동일한 메소드를 포함하고 있다면 나중에 선언 된 mixin 클래스가 실행 됩니다.

- `on` 키워드는 mixin의 사용을 선언된 클래스를 확장하거나 구현하는 클래스로만 제한하는데 사용됩니다.

- `on` 키워드를 사용하려면 `mixin` 키워드를 사용해서 mixin을 선언해야 합니다

  ~~~dart
  class A {}
  mixin X on A {}
  class Y on A {}	//에러
  class P extends A with X {}
  class Q extends X {} //에러
  ~~~

  

* mixin은 다중 상속을 얻는 방법이 아닌 __상태와 동작을 추상화하고 재사용하기 위한 방법__입니다.