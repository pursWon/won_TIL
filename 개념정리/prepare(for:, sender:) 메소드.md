prepare(for:, sender:) 메소드 
===

segue가 수행될 것임을 viewController에 알린다. 

```swift

func prepare(
for segue: UIStoryboardSegue, sender: Any?
)

````

**해당 메소드의 매개변수**

(1) segue

segue에 관련된 뷰 컨트롤러에 대한 정보를 포함하는 segue 개체이다. 

(2) sender    

segue를 시작한 개체이다. 해당 매개변수를 사용하여 segue를 시작한 컨트롤에 따라 다른 작업을 수행할 수 있다.   

**사용 방법**

(1) 데이터를 다른 뷰 컨트롤러로 전송하기 위해서 먼저 스토리보드 내에 뷰 전환 기능을 구현할 것이다. 뷰 컨트롤러 상단의 노랑 동그라미를 control을 누른 채 드래그 한다.   

그리고 다른 뷰 컨트롤러에 drop하면 된다.    

(2) segue에는 다양한 옵션들이 존재한다. 이 때, 데이터 전송이 목적이라면 가장 기본인 Show를 선택한다.   

(3) 코드 편집기에서 segue를 사용하고 싶으면, identifier에서 해당 segue의 식별자를 지정해주면 된다.   

(4) 코드 내에서 특쟝 segue를 작동시키려면, 뷰 컨트롤러 전환 전에 데이터를 처리해야 한다. 이 때, 필요한 메소드가 바로 위의 prepare(for:, sender:) 메소드이다.   

(5) prepare(for:, sender:) 메소드 예시 

```swift

override func prepare(for segue: UIStoryboard, sender: Any?) {
    
    guard let secondViewController = segue.destination as? SecondViewController else { return }
    // 데이터를 전달할 수 있는 뷰 컨트롤러가 있는지 확인한다.
    
    secondViewController.labelString = self.labelString
    // 대상 뷰 컨트롤러가 있다면 데이터를 전송한다. 
}

```
해당 뷰 컨트롤러가 존재하는지 미리 확인하는 작업이 상단의 guard let 이다. 여기서 첫번째로 값을 지정받는 segue는 자체 프로퍼티인   

destination을 통해서 segue의 목적지 뷰 컨트롤러를 추출해 낼 수 있다.   

labelString은 첫번째, 두번째 뷰컨트롤러에 존재하는 String 변수이다. 이 곳에서 뷰 컨트롤러간에 데이터 교환이 일어나게 된다.   



