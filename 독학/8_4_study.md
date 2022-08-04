8월 4일 공부기록 
===

문자열의 여러가지 메소드 
---

(1) 문자열 결합
--

```swift
let friend: String = "안녕"
let hola: String = " 친구들 !"
let 인사말 = friend + hola
print(인사말)
```


(2) 문자열의 길이 재기
--

```swift
let europe: String = "에스토니아와 그리스는 유럽에 있습니다"
let countCharacter: Int = europe.count
print(countCharacter) // 공백까지 더하여 20이 나온다. 글자수 17 + 공백 3
```

(3) 문자열이 비었는지 확인하기
--

```swift
let africa: String = "South Africa"
if africa.isEmpty {
    print("비어있다")
} else {
    print("비어있지 않다")
}
```

(4) 대소문자 변환
--

```swift
let asia: String = "japan"

let ASIA: String = asia.uppercased()
print(ASIA)

let france: String = "FRANCE"
print("\(france.lowercased()) is famous for macarons.")
```

(5) 섞인 문자열을 배열로 변환
--

```swift
print("17udau881ygd".shuffled())
```

(6) Index로 문자 가져오기
--

Swift가 다른 언어들과는 달리 문자를 가져오기 어려운 이유? 

→ 유니코드의 독립적인 형태로 문자열을 처리하기 때문에 복잡한 인덱스를 사용하게 된다.

```swift
let psg: String = "Messi"
```
index 순서 -> 0: M, 1: e, 2: s, 3: s, 4: i

**1. 첫번째 문자 가져오기**

```swift
let firstCharacter = psg[psg.startIndex] // M
```

**2. 두번째 문자 가져오기**

```swift
let secondCharacter = psg[psg.index(after: psg.startIndex)] // e
```

**3. 끝에 문자 가져오기**

```swift
let endCharacter = psg[psg.index(before: psg.endIndex)] // i
```

**4. 세번째 문자 가져오기**

```swift
let thirdCharacter = psg[psg.index(psg.startIndex, offsetBy: 2)] // s
```
-> offsetBy에 적혀있는 숫자는 index 2에 위치한 숫자를 가져온다.

**5. 네번째 문자부터 다섯번째 문자까지 가져오기**

```swift
let range1 = psg[psg.index(psg.startIndex, offsetBy: 3)...psg.index(psg.startIndex, offsetBy: 4)]
print(range1) // si
```
-> startIndex를 이용하여 index 3부터 4에 있는 문자를 가져온다.

**6. endIndex를 이용하여 문자를 모두 가져오기** 

```swift
let range2 = psg[psg.index(psg.endIndex, offsetBy: -5)...psg.index(psg.endIndex, offsetBy: -1)]
print(range2) // Messi
```
-> endIndex를 기준으로 마지막 문자의 index는 -1이므로 역순으로 정렬하면 첫번째 문자가 -5가 된다.

































