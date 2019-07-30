# Exceptions(예외)

* 예외를 발생시키기 위해 `throw` 키워드를 사용합니다.

~~~dart
if (astronauts = 0) {
  throw StateError('No astronauts.');
}
~~~

* 예외를 처리하기 위해 `try` 문을 `on` 또는 `catch` (혹은 둘 다) 키워드와 함께 사용합니다.

~~~dart
try {
  for (var object in flybyObjects) {
    var description = await File('$object.txt').readAsString();
    print(description);
  }
} on IOException catch (e) {
  print('Could not describe object: $e');
} finally {
  flybyObjects.clear();
}
~~~

