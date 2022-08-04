8월 4일 공부기록 
===

문자열의 여러가지 메소드 
---

**(1) 문자열 결합**

```swift
let friend: String = "안녕"
let hola: String = " 친구들 !"
let 인사말 = friend + hola
print(인사말)
```


**(2) 문자열의 길이 재기**

```swift
let europe: String = "에스토니아와 그리스는 유럽에 있습니다"
let countCharacter: Int = europe.count
print(countCharacter) // 공백까지 더하여 20이 나온다. 글자수 17 + 공백 3
```

**(3) 문자열이 비었는지 확인하기**

```swift
let africa: String = "South Africa"
if africa.isEmpty {
    print("비어있다")
} else {
    print("비어있지 않다")
}
```

**(4) 대소문자 변환**

```swift
let asia: String = "japan"

let ASIA: String = asia.uppercased()
print(ASIA)

let france: String = "FRANCE"
print("\(france.lowercased()) is famous for macarons.")
```

**(5) 섞인 문자열을 배열로 변환**

```swift
print("17udau881ygd".shuffled())
```

**(6) Index로 문자 가져오기**

Swift가 다른 언어들과는 달리 문자를 가져오기 어려운 이유? 

→ 유니코드의 독립적인 형태로 문자열을 처리하기 때문에 복잡한 인덱스를 사용하게 된다.

```swift
let psg: String = "Messi"

index 순서 -> 0: M, 1: e, 2: s, 3: s, 4: i
```














