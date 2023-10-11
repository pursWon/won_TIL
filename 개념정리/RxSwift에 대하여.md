RxSwift에 대하여
=================

**RxSwift**는 비동기 프로그래밍을 관찰 가능한 순차적 형태와 함수 형태의 연산자를 통해 처리하게끔 도와준다.   

**RxSwift**는 반응형 프로그래밍으로 어떤 비동기 이벤트에 대하여 관찰 가능한 형태로 만들고 관찰하는 객체가 있을 경우,    

이 비동기 이벤트의 변화에 따른 전파를 받을 수 있다.   

관찰 가능한 순차적인 형태가 **Observable**   

이벤트의 변화를 관찰하여 전파 받는 객체가 **Observer**   

비동기 이벤트를 방출하는 Observable을 **Subscribe**를 해야 이벤트가 실행되어     

방출되는 item을 받을 수 있다.     

Subscribe라는 메서드의 원형은

</br>

```swift

public func subscribe(
    onNext: ((Element) -> Void)? = nil,
    onError: ((Swift.Error) -> Void)? = nil,
    onCompleted: (() -> Void)? = nil,
    onDisposed: (() -> Void)? = nil
) -> Disposable

```

</br>

모든 타입이 클로저 타입이고, onNext, onError, onCompleted라는 파라미터가 존재한다.

각 클로저의 역할은

**onNext** : 새로운 항목을 방출할 때마다 이 클로저가 호출이 된다.

Observable이 방출하는 항목을 클로저의 파라미터로 전달 받는다.

**onError** : observable은 기대하는 데이터가 생성되지 않았거나 다른 이유로 오류가 발생했을 때, 이 오류를 구독자인 Observer에게 알리기 위해 이 메서드를 호출한다.

**onCompleted** : Observable은 이벤트가 종료되어서 더 이상 호출되지 않을 때, 

이벤트가 완료 되었음을 구독자인 Observer에게 알리기 위해 이 메서드를 호출한다.
