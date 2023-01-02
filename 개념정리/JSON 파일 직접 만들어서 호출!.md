JSON 파일 직접 만들어서 호출
===========

<img width="730" alt="스크린샷 2023-01-03 오전 3 22 02" src="https://user-images.githubusercontent.com/99719661/210269413-f67c18ef-00dd-438d-b8a4-2dbd2b184e23.png">

String File을 이용해서 **JSON** 형식의 파일을 만들어야 한다. **파일명**과 **확장자 파일명**을 정해야 한다. 파일명은 People, 확장자 파일명은 json.

```json
{
    "people" : [
    {
    "first_name" : "Wongi",
    "last_name" : "Hong",
    "age" : 29
    },
    {
    "first_name" : "Moon",
    "last_name" : "TaeHyeon",
    "age" : 29
    },
    {
    "first_name" : "Kim",
    "last_name" : "SeHyeon",
    "age" : 29
    }
    ]
}
```

사람에 관한 정보에 대한 JSON 파일을 만들었다.

이제 JSON 파일을 불러오는 코드를 쓰자. 

```swift
func load() -> Data? {
    let fileName: String = "People"
    // 불러올 파일 이름
    let extensionType: String = "json"
    // 불러올 확장자 이름
    
    guard let fileLocation = Bundle.main.url(forResource: fileName, withExtension: extensionType) else
    { return nil }
    // 파일 위치
    
    do {
    let data = try Data(contentsOf: fileLocation)
    // 해당 위치의 파일을 데이터로 초기화하기
    return data
    } catch {
        return nil
    // 잘못된 위치나 불가능한 파일 처리
    }
}
```

JSON 데이터를 받을 모델을 만들자.

```swift
struct PeopleList: Decodable {
let people: [People]
    
    struct People: Decodable {
    let first_name: String
    let last_name: String
    let age: Int
    }
}
```

설정해 놓았던 데이터를 받는다.

```swift
let jsonData = load()
```

해당 데이터를 String으로 변환해서 프린트를 해보았다.

```swift
let data = String(data: jsonData!, encoding: .utf8)
print(data!)
```

<img width="606" alt="스크린샷 2023-01-03 오전 3 38 02" src="https://user-images.githubusercontent.com/99719661/210269458-d9adf9e2-15f0-4a09-93bd-1bb9832b2bc0.png">

데이터를 잘 받은 것을 알 수 있었다.

받은 해당 데이터를 Decoding을 해준다. 그리고 레이블에 프린트를 해준다.

```swift
guard let peopleList = try? JSONDecoder().decode(PeopleList.self, from: jsonData) else { return }
peopleLabel.text = "이름 : \(peopleList.people[2].first_name) \(peopleList.people[2].last_name)"
```

![Simulator Screen Shot - iPhone 12 mini - 2023-01-03 at 03 41 37](https://user-images.githubusercontent.com/99719661/210269527-94c9f921-e1d9-488f-ad72-8e8b83618988.png)


제대로 출력이 됐다는 것을 알 수 있다.
