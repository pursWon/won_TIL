Mutating이 무엇인가
========

```swift 
import Foundation

struct studyMutating {
    var number: Int = 30
    
    mutating func changeNumber() {
    number = 40
    }
}
```

구조체 메서드를 구조체 내부에서 변경할 때 mutating 키워드를 사용해야 합니다.   

mutating 키워드를 붙여서 사용해야, 메서드가 종료될 때,   

원본 구조체 인스턴스를 인스턴스 프로퍼티가 변경된 구조체 인스턴스로 대체할 수 있습니다.   
