## Flutter Navigator

## 참고자료

- [https://jinhan38.com/147](https://jinhan38.com/147)
- [화면 이동 Navigator - Push, Pop 정리](https://seosh817.tistory.com/211)



## Route, Navigator

- Route : Screen, Page 등과 같은 위젯
- Navigator : Route 위짓을 관리하는 위젯



## Push, Pop

- Push : 다른 페이지로 이동
- Pop : 이전 페이지로 이동

Push 와 Pop 은 Navigator 의 메서드입니다.<br/>



### Push

push 는 다른 페이지로 이동하는 동작입니다. 따라서 어디로 이동할지 알 수 있어야 하기에 Route 가 필요하며, 그 정보를 담기 위한 Context 가 필요합니다. MaterialRoute 클래스를 이용해서 builder(Context) 함수를 오버라이딩하며, 오버라이딩하는 메서드에서는 Screen 객체가 생성되어 리턴되는 방식으로 작성합니다. 간단한 예제 코드는 아래와 같습니다.

```dart
Navigator.push(context, MaterialPageRoute(
  builder: (context) {
    return RouteSecondScreen();
  },
));
```

<br/>



### Pop

pop 은 context 만 넘겨주면 됩니다.

```dart
Navigator.pop(context);
```

<br/>



## pushReplacement, pushAndRemoveUntil, popUntil

- pushReplacement : 현재 페이지를 다른 페이지로 대체하는 Navigator 내의 메서드
- pushAndRemoveUntil : 특정 화면으로 이동하고 기존에 있는 화면을 모두 제거하는 Navigator 내의 메서드
- popUntil : 첫번째 라우트까지 이동하고 그 외의 화면들은 종료하는 Navigator 내의 메서드

<br/>



### pushReplacement

```dart
Navigator.pushReplacement(
  context,
  MaterialPageRoute(
    builder: (context) {
      return RouteSecondScreen();
    },
  ),
);
```



### pushAndRemoveUntil

```dart
Navigator.pushAndRemoveUntil(
  context,
  MaterialPageRoute(
    builder: (context) {
      return const HomeScreen();
    },
  ),
  (route) => false,
);
```



### popUntil

```dart
Navigator.popUntil(
  context,
  (route) {
    return route.isFirst;
  },
)
```

<br/>





## removeRoute

remoteRoute 함수는 Route(스크린)을 지우는 역할을 합니다.





