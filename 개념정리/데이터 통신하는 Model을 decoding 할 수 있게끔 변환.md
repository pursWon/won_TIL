데이터 통신하는 Model을 decoding 할 수 있게끔 변환
=========================================

```swift

import Foundation
import RealmSwift

class Book: Object, Decodable {
    var documents = List<Information>()
    
    private enum CodingKeys: String, CodingKey {
        case documents = "documents"
    }
		// CodingKeys 부분을 보면 "documents" 부분은 JSON Data의 
		// Key 값이고 case의 documents는 key 값을 대신해서 쓸 값이다.
    
    public required convenience init(from decoder: Decoder) throws {
        
        self.init()
        let container = try decoder.container(keyedBy: CodingKeys.self)
        let documentsDataDecode = try container.decodeIfPresent([Information].self, forKey: .documents) ?? [Information()]
        
        documents.append(objectsIn: documentsDataDecode)
				// JSON Data 부분에 List 형태의 데이터가 존재할 경우, 위의 코드와 같이
				// decode 해줘야 한다. 

				
    }
}

class Information: Object, Decodable {
    @objc dynamic var price: Int = 0
    @objc dynamic var title: String = ""
    @objc dynamic var thumbnail: String = ""
    // decoding을 해주기 위해선 @objc dynamic var를 사용해야 한다. 
    private enum CodingKeys: String, CodingKey {
        case price = "price"
        case title = "title"
        case thumbnail = "thumbnail"
    }
}

```





