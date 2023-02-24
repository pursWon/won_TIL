isEmpty에 대하여
==========
<img width="838" alt="스크린샷 2023-02-24 오후 11 39 32" src="https://user-images.githubusercontent.com/99719661/221206169-61c268c3-5b45-4011-a1df-0eaba9bb7a22.png">



해석 : 문자열에 문자가 있는지 없는지 여부를 확인할 수 있는 Bool 타입의 값입니다.   

```swift

let apple: String = "apple"
let isEmptyChecked: Bool = apple.isEmpty
print(isEmptyChecked) // false

```

isEmpty는 String의 값에 Character가 있을 경우, 비어있지 않으므로 값이 없을 경우, false를 가진다.   

```swift

let pear: String = ""
let isEmptyChecked: Bool = pear.isEmpty
print(isEmptyChecked) // true

```

isEmpty는 String의 값에 Character가 없을 경우, 비어있으므로 true를 가진다.   


```swift

let numberArray: [Int] = [3, 9, 9, 10, 10, 12, 12, 34, 34, 42, 45]
let isEmptyChecked = numberArray.isEmpty ? true : false
print(isEmptyChecked) // false

```

위와 같이 Array에도 적용할 수 있다.

isEmpty일 경우, true를 리턴하게끔 해주고, 아닐 경우, false를 리턴하게끔 설정해주었다.

```swift

let numberArray: [Int] = [3, 9, 9, 10, 10, 12, 12, 34, 34, 42, 45]
let isEmptyChecked = numberArray.isEmpty ? 10 : 20
print(isEmptyChecked)

```

? 뒤에 있는 두 개의 값은 다른 타입으로도 대체할 수 있다.

isEmpty가 맞을 경우엔, 10이 나오고, 아닐 경우엔, 20이 나오게 된다.   




