카카오 API 가져오는 방법 연습
=========

```swift 
import Foundation

struct Place: Decodable {
    var documents: [Documents]
}

struct Documents: Decodable {
    var place_name: String
    var address_name: String
}
```

가져오려는 **데이터 형식**에 맞게끔 **Model**을 만들어준다.   

해당 데이터의 모양에 맞는 틀을 만든다고 생각하면 된다.    

가져온 데이터는 테이블뷰를 통해서 보여줄 것이다.   

```swift

import UIKit

class ViewController: UIViewController {
    @IBOutlet weak var kakaoTableView: UITableView!
    
    var dataList: [Documents] = []
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        kakaoTableView.delegate = self
        kakaoTableView.dataSource = self
        
        getKakaoData()
    }
    
    func getKakaoData() {
        
        guard let url = URL(string: "https://dapi.kakao.com/v2/local/search/keyword.json?query=%EA%B3%A0%EA%B8%B0") else { return }
        // query를 붙인 url링크를 문자열 값으로 가져온다. 검색어는 "고기"로 지정해주었다. 
        
        var request = URLRequest(url: url)
        // URL을 요청한다.
        request.httpMethod = "GET"
        // 데이터를 받아올 것이므로 httpMethod는 GET으로 설정    
        request.setValue("KakaoAK d8b066a3dbb0e888b857f37b667d96d2", forHTTPHeaderField: "Authorization")
        // Headers 앱키와 Authorization를 적어준다.
        
        let dataTask = URLSession.shared.dataTask(with: request) { data, response, error in
            
            guard let data = data else { return }
            guard let response = response as? HTTPURLResponse else { return }
            guard error == nil else { return }
            
            switch response.statusCode {
            case 200:
            // 데이터 통신이 성공했을 경우 
                let data = try? JSONDecoder().decode(Place.self, from: data)
                // 만들어놓은 Model을 형변환 해준다. 
                if let data = data {
                // data가 있다면 (data는 Place 구조체를 Decoding한 값을 받음)
                    self.dataList = data.documents
                // dataList(Documents 구조체 빈 배열)는 data의 documents(Docunments의 배열)을 받음
                    DispatchQueue.main.async {
                        self.kakaoTableView.reloadData()
                    }
                }
            default:
                print("데이터 연결 실패")
            }
        }
        dataTask.resume()
        // dataTask를 실행시킨다. 
    }
}

extension ViewController: UITableViewDelegate, UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return dataList.count
        // dataList의 개수만큼 셀을 리턴시킴
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        guard let cell = tableView.dequeueReusableCell(withIdentifier: "kakaoCell") as? KakaoCell else {
            return UITableViewCell() }
        let document = dataList[indexPath.row]
        cell.nameLabel.text = document.place_name
        cell.addressLabel.text = document.address_name
        
        return cell
    }
    
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        return 90
    }
}
