Frame과 Bound에 대하여
======

### Frame : Super View 좌표계에서 View의 위치와 크기를 나타낸다.

여기서 말하는 Super View란? 

→ View로 화면을 구성할 때, 계층 구조라는 것이 존재한다. 

동일 계층의 뷰도 있고, 한 칸 윗계층의 뷰도 존재한다. 

이 때, 한 칸 윗계층의 뷰가 Super View가 되는 것이다.

<img width="304" alt="스크린샷 2022-12-09 오전 8 56 14" src="https://user-images.githubusercontent.com/99719661/206656575-e12de999-d46f-4a03-9390-66f43587d8c7.png">

Table View의 Super View는 루트 View.

Content View의 Super View는 Table View.

즉, **나보다 한 칸위 계층의 뷰가 Super View**

frame이 나타내는 origin(x, y)의 좌표는 Super View의 원점을 (0.0)으로 놓고 원점으로부터 얼마나 떨어져있는가를 보는 것이다. 

- 원점 : View의 가장 윗쪽, 가장 왼쪽 부분

예를 들면, Table View가 가지는 frame의 origin 좌표는 루트 View의 원점이다.

루트 View의 원점에서 x축에서 50, y축에서 60만큼 떨어져 있다고 하면, Table View의 원점은 

(50, 60)이 되는 것이다. 

그러면 Table View의 하위 뷰인 Content View의 원점은 어떻게 측정할 수 있을까?

이는 **Table View 원점에서 얼마나 떨어져 있는가를 보면 된다**

만약 **Table View 원점**에서 x축으로 10, y축으로 30 떨어져있다고 하면 Content View의 원점은 (10, 30)이 된

다. 

이제 책 목록 앱을 만들 때 사용했던 frame 코드를 보자.

```swift
let header = UIView(frame: CGRect(x: 0, y: 0, width: 300, height: 60))
```

이는 section의 header에 문구를 넣기 위한 코드이다. 여기서 재밌는 건, x축으로 10,000만큼 이동시켜도 

해당 view는 변하지 않는다는 점이다. 왜냐하면, 해당 뷰가 최상위 view이므로 frame의 원점이 존재하지 않기 때문이다. 그리고 **width: 300, height: 60**으로 설정되어있는 것은 view의 가로, 세로가 아니라 view를 감싸고 있는 사각형의 가로 세로 길이이다. 

### Bounds : 자신의 좌표계에서 View의 위치와 크기를 나타낸다.

자신을 좌표계로 삼고 시작하기 때문에 (0, 0)으로 초기화된다. 

View를 감싸고 있는 직사각형의 크기가 아닌 View 자체가 Bound를 사용할 때에 크기가 된다.

정리

|  | frame | bounds |
| --- | --- | --- |
| origin (x, y) 기준점 | Super View의 좌표계 | 자신의 좌표계 |
| size (width, height) 기준점  | View 영역을 모두 감싸는 사각형 | View 영역 그 자체  |
