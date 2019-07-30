# Async(비동기)

* 비동기식 처리는 일이 종료되지 않은 상태여도 대기하지 않고 다음 일을 실행하는 처리 방식입니다.

* **callback 지옥**에서 벗어나고 코드의 가독성을 높이기 위해 `async` 와 `await` 를 사용합니다.

> callback 지옥은 JavaScript를 이용한 비동기 프로그래밍시 발생하는 문제로, 함수의 매개 변수로 넘겨지는 콜백 함수가 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상입니다.
>
> Dart에서도 JS와 마찬가지로 callback 지옥이 발생할 수 있습니다.

~~~dart
const oneSecond = Duration(seconds: 1);

Future<void> printWithDelay(String message) async {
  await Future.delayed(oneSecond);
  print(message);
}
~~~

~~~dart
//async와 await를 사용하지 않은 동일한 코드
Future<void> printWithDelay(String message) {
  return Future.delayed(oneSecond).then((_) {
    print(message);
  });
}
~~~

* `async` 와 `await` 는 비동기 코드를 읽기 쉽게 도와줍니다.

~~~dart
Future<void> createDescriptions(Iterable<String> objects) async {
  for (var object in objects) {
    try {
      var file = File('$object.txt');
      if (await file.exists()) {
        var modified = await file.lastModified();
       	print(
        		'File for $object already exists. It was modified on $modified.');
        continue;
      }
      await file.create();
      await file.writeAsString('Start describing $object in this file.');
    } on IOException catch (e) {
      print('Cannot create description for $object: $e');
    }
  }
}
~~~

* `async*` 키워드는 `Stream` 을 읽기 쉽고 좋게 만듭니다.

~~~dart
Stream<String> report(SpaceCraft craft, Iterable<String> objects) async* {
  for (var object in objects) {
    await Future.delayed(onSecond);
    yield '${craft.name} flies by $object';
  }
}
~~~

