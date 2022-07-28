7월 27일 수업 내용
===

enum
---
열거형.  

케이스들을 나열해 놓은것을 하나의 묶음으로 관리하는 타입.  

열거형은 동등한 위치에 있다.   

같은 선상에 있는 케이스들을 모아놓는다.   

enum 에 원시값 타입으로 지정해 줄 수 있는 타입은 무엇이 있을까? (숙제).  

enum은 switch문과 조합이 잘 맞는다.   

switch문에 들어갈 케이스는 enum의 갯수만큼이 최대라서,   

이외의 변수가 없기에 default문을 추가할 필요가 없다.   

```swift
import Foundation

enum Direction: Int { // 동서남북
    case east = 10
    case west
    case south
    case north
    
}
```

```swift
// 선언
var direction: Direction = .north

// rawValue = 원시값
print(direction.rawValue)

print("\(direction): \(direction.rawValue)")

switch direction {
case .east:
    print("동쪽 : \(direction.rawValue)")
case .west:
    print("서쪽 : \(direction.rawValue) ")
case .south:
    print("남쪽 : \(direction.rawValue) ")
case .north:
    print("북쪽 : \(direction.rawValue) ")
}
```

Optional(옵셔널)
---
값이 존재할수도 안할수도 있다.   

타입 enum으로 구현되어 있다.   

```swift
enum Optional {
    case none // 값이 존재하지 않는다.
    case sum // 무언가 값이 있는 상태.
}

var optionalValue : Int? = Int("aa")

// Int?(옵셔널 int 타입), Int(그냥 int 타입)

// optioanlValue의 옵셔널을 벗겨봤는데 값이 존재하면 value 라는 상수에 담아주고, 그 value가 12와 같은지 비교한다.
// 위의 두 조건이 모두 참일 경우, if문을 실행하고 하나라도 거짓일 경우 else 문을 실행한다.
if let value = optionalValue, value == 12 { // optioanl(12)
    print("\(value)와 12는 같습니다") // optioanl(12)
} else {
    print("다릅니다")
}

//
// ??
print(optionalValue ?? 57)

// guard문은 함수안에서만 사용할 수 있다.
// guard문에 있는 조건이 거짓일 경우, guard 아래에 있는 코드는 실행되지 않는다.

func optionalTest() {
    print("함수 시작")
    
    if let value = optionalValue {
        // optionalValue 안에 어떤 값이 존재하는 경우
        print("\(value)라는 값이 존재합니다.")
    }
    print("1")
    print("2")
    print("3")
    
    print("함수 끝")
}

optionalTest()
```

guard (가드)
---

```swift
func guardTest() {
    print("함수 시작")
    
    guard let value = optionalValue else { return }
    // optionalValue 안에 어떤 값이 존재하는 경우
    print("\(value)라는 값이 존재합니다.")
    
    print("1")
    print("2")
    print("3")
    
    print("함수 끝")
}

guardTest()
```

구조체
---

사람에 대해 정의하는 구조체.  

```swift
/*
 이름(name), 나이(age), 성별(gender)
 */

struct Person {
    var name: String
    let age: Int
    let gender: String
}

let 철수: Person = Person(name: "김철수", age: 18, gender: "남자")
var 복제인간철수 = 철수

복제인간철수.name = "이철수"
철수.name
```

클래스
---

```swift
// 클래스는 초기값을 지정해주어야 한다. (= 초기화를 해주어야 한다.)
// 참조한다 = 값이 지정되어있는 메모리 공간의 주소값을 갖고 있다.

class PersonClass {
    var name: String
    let age: Int
    let gender: String
    
    init(name1: String, age1: Int, gender1: String) { // 이니셜라이저
        self.name = name1
        self.age = age1
        self.gender = gender1
    }
}

let 영희: PersonClass = PersonClass(name1: "김영희", age1: 20, gender1: "여자")
영희.age
let 복제인간영희 = 영희


복제인간영희.name = "최영희"
영희.name
```

/*
 컴퓨터라는 구조체와 클래스로 둘 다 만들 것이다.
 운영체제 (os)
 화면크기 (windowSize)
 램 크기 (ram)
 무게 (weight)
 */


구조체와 클래스의 차이점
---
```swift
struct sComputer {
    let os: String
    let windowSize: String
    var ram: Int
    let weight: Double
}

let 맥북: sComputer = sComputer(os: "Mac", windowSize: "10 x 15", ram: 16, weight: 2.3)
var 복제맥북 = 맥북

복제맥북.ram = 32

class cComputer {
    
    
    let os: String
    var windowSize: String
    let ram: Int
    let weight: Double
    
    init(os1: String, windowSize1: String, ram1: Int, weight1: Double) {
        self.os = os1
        self.windowSize = windowSize1
        self.ram = ram1
        self.weight = weight1
    }
}

let 그램: cComputer = cComputer(os1: "Window", windowSize1: "16", ram1: 32, weight1: 1.9)
var 복제그램 = 그램

복제그램.windowSize = "17"

print(그램.windowSize)
```
