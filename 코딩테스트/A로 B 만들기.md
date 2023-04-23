A로 B 만들기
================

문자열 before와 after가 매개변수로 주어질 때, before의 순서를 바꾸어 after를 만들 수 있으면 1을, 만들 수 없으면 0을 return 하도록 solution 함수를 완성해보세요.

```swift 

import Foundation

func solution(_ before:String, _ after:String) -> Int {
    return before.map{ $0 }.sorted(by: <) == after.map{ $0 }.sorted(by: <) ? 1 : 0
}

```

if문을 사용했었지만 삼항연산자로 축약해보았다.
