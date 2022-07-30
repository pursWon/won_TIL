7월 30일 공부
===

Struct, Class 코드 연습 문제 
---

(1) **아래의 프로퍼티를 갖는 학생(Student) 구조체와 강의(SchoolClass) 클래스를 만들어주세요.**

- 학생 : 이름(name), 학년(year)
- 강의: 강의명(title), 교실번호(classroom), 수업을 듣는 학생 목록(studentList)

```swift
struct Stdent {
    var name: String
    var year: Int
}

let 훈이: Stdent = Student(name: "훈이", year: 3)
print("\(훈이.name)는 \(훈이.year)학년입니다.")

let 맹구: Stdent = Stdent(name: "맹구", year: 5)
print("\(맹구.name)는 \(맹구.year)학년입니다.")

class schoolClass {
    var title: String
    var classroom: Int
    var studentList: String
    
    init(title1: String, classroom1: Int, studentList1: String) {
        title.self = title1
        classroom.self = classroom1
        studentList.self = studentList1
    }
    
}
```

(2) **jack, mike, sam, billy 라는 4명의 학생 객체를 만들어주세요.**

```swift
struct Student {
    var name: String
    var year: Int
}

let 훈이: Student = Student(name: "훈이", year: 3)
print("\(훈이.name)는 \(훈이.year)학년입니다.")

let 맹구: Student = Student(name: "맹구", year: 5)
print("\(맹구.name)는 \(맹구.year)학년입니다.")

let jack: Student = Student(name: "Jack", year: 3)
let mike: Student = Student(name: "Mike", year: 4)
let sam: Student = Student(name: "Sam", year: 2)
let billy: Student = Student(name: "Billy", year: 5)
```

(3)  **아래의 정보를 참고하여 강의 객체를 만들어주세요.**

- math : 302호, 듣는 학생목록 (jack, mike, sam)
- english : 406호, 듣는 학생목록 (jack, billy)

```swift 
class schoolClass {
    var title: String
    var classroom: Int
    var studentList: String

    init(title1: String, classroom1: Int, studentList1: String) {
        title.self = title1
        classroom.self = classroom1
        studentList.self = studentList1
    }

}

let math: schoolClass = schoolClass(title1: "math", classroom1: 302, studentList1: "\(jack.name), \(mike.name), \(sam.name)")
let english: schoolClass = schoolClass(title1: "english", classroom1: 406, studentList1: "\(jack.name), \(billy.name)")




