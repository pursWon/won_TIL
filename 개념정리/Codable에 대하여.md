Codable에 대하여
==========

**Codable의 정의 :**

</br>

JSON 데이터를 간편하고 쉽게 Encoding / Decoding 할 수 있게 해준다.   

서버와 데이터를 주고 받을 때, 주로 JSON으로 주고 받게 되는데,        

라이브러리(SwiftyJSON)와 직접 다루는 것보다 더 쉽게 다룰 수 있게 된다.    

Codable은 Encodable과 Decodable을 준수하는 프로토콜이다. 

Struct, Class, Enum은 모두 Codable을 채택할 수 있다.    

## (1) Encoding 

내가 원하는 Struct, Class, Enum의 인스턴스를 JSON 형태의 Data로 만들어주는 것이다.    

Codable을 이용해 JSON으로 Encoding 하고 싶을 경우, 반드시 Codable을 이라는 Protocol을 준수하고 있어야 한다.   

```swift

import Foundation

struct Name: Codable {
    let name: String
}

let myName: Name = Name(name: "홍원기")

let data = try? JSONEncoder().encode(myName)

```

Codable을 이용하면 이렇게 encoding을 쉽게 할 수 있다.   

## (2) Decoding 

JSON 형태의 Data를 struct, class, enum등의 인스턴스에 자동으로 파싱.    

decode 함수 원형부터 살펴보자면,   

```swift 

open func decode<T>(_ type: T.Type, from data: Data) throws -> T where T : Decodable 

```

Encode와 마찬가지로 Generic T는 Decodable을 준수하며,   

Decoing중에 실패할 수 있으므로, 반드시 try와 함께 써줘야 한다.   

구조체를 하나 만들고, JSON Data의 Key 값과 동일한 이름의 구조체 변수에 value에 값을 파싱하면 된다. 

그리고 파싱된 구조체를 리턴시킨다.   

```JSON
{
  "file": "https://coffee.alexflipnote.dev/_R3YTAbmFwk_coffee.png"
}
```

예를 들면, 이러한 JSON Data가 있다고 하면, JSON Data의 Key 값은 Decodable을 따르는 타입의 멤버 이름과 

1대1 매칭이 되어야만 문제 없이 사용이 가능하다.    

```swift

struct Coffee: Decodable {
    var file: String
}

```

그래서 이런식으로 구조체를 만들어줘야 한다.

만약에, Key 값이 구조체의 멤버 이름과 맞지 않으면 Decoding Fail로 간주되어, nil로 떨어지게 된다.    














