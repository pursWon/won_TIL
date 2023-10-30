A 강조하기
============

문자열 myString이 주어집니다.    

myString에서 알파벳 "a"가 등장하면 전부 "A"로 변환하고,    

"A"가 아닌 모든 대문자 알파벳은 소문자 알파벳으로 변환하여 return 하는 solution 함수를 완성하세요.   

</br>

**입출력 예시**

|myString|result|
|----|---|
|"abstract algebra"|"AbstrAct AlgebrA"|
|"PrOgRaMmErS"|"progrAmmers"|

</br>



나의 풀이 

```swift

import Foundation

func solution(_ myString:String) -> String {
    var array = myString.map { String($0) }
    
    for i in 0..<array.count {
        if array[i] == "a" || array[i] == "A" {
            array[i] = "a".uppercased()
        } else {
            array[i] = array[i].lowercased()
        }
    }
    
    return array.reduce("", +)
}

```
