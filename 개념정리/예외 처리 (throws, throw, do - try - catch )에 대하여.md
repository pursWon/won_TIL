예외 처리 (throws, throw, do - try - catch )에 대하여
===========

예외 처리가 필요한 이유? 

→ 옵셔널 타입은 오류가 발생했을 때 오류에 대한 정보를 외부로 전달할 방법이 없다. 

1. **오류의 종류를 정의**

```swift
enum Bicycle: Error {
    case wheel
}
```

자전거의 바퀴는 2개인데 개수가 맞지 않아서 에러가 생긴다고 생각해보자.

2. **오류가 나는 조건을 throw와 throws로 선언** 

오류가 발생할 수 있다는 조건을 표현 : throws를 “→” 앞에 표시한다(반환 전에 오류가 발생하면, 오류 객체를 반환한다는 의미이다.)

throw와 오류명 집어넣기 

```swift
func bicycleError(bicycleWheel: Int) throws -> Int {
    guard bicycleWheel == 2 else {
        throw Bicycle.wheel
    }
    
    return bicycleWheel
}
```

3. **do - try - catch 로 접근** 

마지막 catch에 <오류타입>을 작성하지 않으면 default문으로 됨

```swift
func getBicycleError(bicycleWheel: Int) -> Int {
    var wheelCount: Int = 0
    do {
        wheelCount = try bicycleError(bicycleWheel: bicycleWheel)
        print(wheelCount)
    } catch Bicycle.wheel {
        print("바퀴 개수는 2개여야 합니다. 해당 개수는 맞지 않습니다.")
    } catch {
        print("default error catch")
    }
    
    return wheelCount
}

let myBicycleWheel = getBicycleError(bicycleWheel: 10) // 2가 아니므로 오류 발생
print(myBicycleWheel)
```

2가 아니므로 오류가 발생하고 “바퀴 개수는 2개여야 합니다. 해당 개수는 맞지 않습니다.”를 프린트해준다.

전체 코드

```swift
import Foundation

enum Bicycle: Error {
    case wheel
}

func bicycleError(bicycleWheel: Int) throws -> Int {
    guard bicycleWheel == 2 else {
        throw Bicycle.wheel
    }
    
    return bicycleWheel
}

func getBicycleError(bicycleWheel: Int) -> Int {
    var wheelCount: Int = 0
    do {
    wheelCount = try bicycleError(bicycleWheel: bicycleWheel)
    } catch Bicycle.wheel {
        print("바퀴 개수는 2개여야 합니다. 해당 개수는 맞지 않습니다.")
    } catch {
        print("default error catch")
    }

    return wheelCount
}

let mine = getBicycleError(bicycleWheel: 10)
print(mine)
```





