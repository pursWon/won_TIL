X 사이의 개수
===============

문자열 `myString`이 주어집니다. `myString`을 문자 "x"를 기준으로 나눴을 때 나눠진 문자열 각각의 길이를 

순서대로 저장한 배열을 return 하는 solution 함수를 완성해 주세요

```swift 

import Foundation

func solution(_ myString:String) -> [Int] {
    return myString.components(separatedBy: "x").map{ $0.count }
}

```
