7.20 공부 기록
===

##### 함수의 4가지 기본 사용법
---

## (1) 전달 O, 반환 O
---
```swift
func rock(name: String) -> String {
    return name
}

let festival = rock(name: "MUSE")
print(festival)
```

## (2) 전달 O, 반환 X
---
```swift
func rock2(band: String, sing: String) -> Void {
    print("\(band)는 \(sing) 이상의 명곡들을 가지고 있다.")
}

rock2(band: "muse", sing: "100곡")
```

## (3) 전달 X, 반환 O
---
```swift
func rock3() -> String {
  return "hoobastank"
}

print(rock3())
```

## (4) 전달 X, 반환 X
---
```swift
func rock4() -> Void {
    print("Oasis는 엄청 유명한 영국의 밴드지.")
}
rock4()
```

