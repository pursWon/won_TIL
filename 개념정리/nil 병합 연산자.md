nil 병합 연산자
==========

nil coalescing operator : ??을 써서 아주 간단하게 언래핑

if let이나 guard let을 써야해서 코드가 길어질 수 있지만 nil 병합 연산자는 한줄로 쓸 수 있다는 장점이 존재

```swift
import Foundation

let box: String? = "Present"

if let openBox = box {
print(openBox)
    
} else {
print("Nothing")
    
}
```

이렇게 if let절로 안전하게 box를 언랩핑해서 openBox에 담아줄 수 있지만, nil 병합 연산자 방법을 사용하면

```swift
import Foundation

let box: String? = "Present"

let openBox = box ?? "Nothing"
print(openBox)
```

위의 코드와 같이 옵셔널 String 타입 box를 선언하고 해당 옵셔널을 해제하는 과정을

 **let openBox = box ?? "Nothing"** 한 줄로 표현했습니다. optional 값을 해제했을 때 값이 존재하면 해당 값을 openBox에 담아주고 값이 존재하지 않으면 ?? 뒤에 있는 **Nothing**을 담아주도록 한다.

 **nil 병합 연산자** : 옵셔널 변수 ?? nil일 경우 행동


옵셔널 값이 nil이 아니라면, 해당 옵셔널 값을 일반 값으로 가공시켜줍니다. (언래핑)

따라서, 사용하기가 매우 편리하고, 안전성도 보장됩니다.
