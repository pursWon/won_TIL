prepare(for:, sender:) 메소드 
===

segue가 수행될 것임을 viewController에 알린다. 

```swift

func prepare(
for segue: UIStoryboardSegue, sender: Any?
)

````

해당 메소드의 매개변수   

(1) segue

segue에 관련된 뷰 컨트롤러에 대한 정보를 포함하는 segue 개체이다. 

(2) sender    

segue를 시작한 개체이다. 해당 매개변수를 사용하여 segue를 시작한 컨트롤에 따라 다른 작업을 수행할 수 있다.   

