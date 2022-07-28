  클래스에 대하여 
  ===
  
  코드 및 리뷰 
  ---
  
  ```swift
  import Swift

//MARK: -정의

class 이름 { // 클래스는 구조체와 매우 유사하다.
    /* 구현부*/
}

//MARK: 프로퍼티 및 메소드

class Sample { // 클래스는 참조 타입이다.
    var mutableProperty: Int = 100 // 가변 프로퍼티
    let immutableProperty: Int = 100 // 불변 프로퍼티
    
    static var typeProperty: Int = 100 // 타입 프로퍼티
    
    // 인스턴스 메소드
    func instanceMethod() {
        print("instance method")
    }
    
    // 타입 메소드
    // 재정의 불가 타입 메소드 -> static
    static func typeMethod() {
        print("type method - static")
    }


// 재정의 기능 타입 메서드 - class
class func classMethod() {
    print("type method - class")
}

}

// MARK: 클래스 사용

var mutableReference: Sample = Sample()

mutableReference.mutableProperty = 200 // 클래스는 구조체와 다르게 var와 let을 이용한 인스턴스 모두가 안에 있는 mutableProperty를
// mutableReference.immutableProperty = 200 // 변경할 수 있다.

let immutableReference: Sample = Sample()

immutableReference.mutableProperty = 200  // 클래스에서는 let을 이용한 인스턴스 변경이 가능하나 구조체에서는 불가능하다.
// immutableReference.immutableProperty = 200 // 그렇지만 불변 프로퍼티는 변경이 불가능하다.

// immutableReference = mutableReference

// 타입 프로퍼티 및 메소드
Sample.typeProperty = 300 // 타입 프로퍼티를 사용한다는 것은 구조체와의 공통점이다.
Sample.typeMethod() // type method

//mutableReference.typeProperty = 400
//mutableReference.typeMethod()

//MARK: - 학생 클래스

class Student {
    var name: String = "unknown"
    var `class`: String = "Swift"
    
    class func selfIntroduce() {
        print("학생타입입니다")
    }
    
    func selfIntroducde() {
        print("저는 \(self.class)반 \(name)입니다")
    }
}

Student.selfIntroduce() // 학생 타입입니다
var yagom: Student = Student()
yagom.name = "unknown"
yagom.class = "Swift"
// yagom.selfIntroduce() // selfIntroduce는 static 멤버이므로 Student 인스턴스에서 사용할 수 없다.

let jina: Student = Student()
jina.name = "jina"
jina.class = "swift"
// jina.selfIntroduce() // selfIntroduce는 static 멤버이므로 Student 인스턴스에서 사용할 수 없다.
```
















              
              
              
              
              













