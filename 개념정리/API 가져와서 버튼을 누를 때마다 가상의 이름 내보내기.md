API 가져와서 버튼을 누를 때마다 가상의 이름 내보내기
=========

12월 24일에 한 수업 내용이다. (API 관련)

**API 가져오는 법**

1. url 주소
2. 요청하는 객체 만들기
3. 데이터통신을 통해서 객체 만들기
4. 보내고 성공 여부에 따라서 분기

```swift 

import UIKit

class ViewController: UIViewController {
    
    @IBOutlet weak var nameLabel: UILabel!
    @IBOutlet weak var birthDateLabel: UILabel!
    @IBOutlet weak var randomGenearateButton: UIButton!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        getFakeNameData()
    }
    
    func getFakeNameData() {
        randomGenearateButton.isEnabled = false
        randomGenearateButton.backgroundColor = .gray
        
        // 1. URL 객체 만들기
        let url = URL(string: "https://api.namefake.com/")!
        
        // 2. request 객체 만들기
        var request = URLRequest(url: url)
        
        // 3번 데이터 통신 하기
        let dataTask = URLSession.shared.dataTask(with: request) { data, response, error in
            guard error == nil else {
                print("error: \(error?.localizedDescription)")
                return }
            
            guard let response = response as? HTTPURLResponse else {
                print("response: \(response?.description)")
                return
            }
            
            guard let data = data else {
                print("data error...")
                return
            }
            
            // 3-1. 응답이 성공적으로 들어왔는지 체크
            switch response.statusCode {
            case 200:
                print("성공")
                
                guard let fakeName = try? JSONDecoder().decode(FakeName.self, from: data) else {
                    print("decoding fail...")
                    return
                }
                
                // UI 관련 작업은 main만 할 수 있으므로, main에게 이 작업을 할당하는 과정
                DispatchQueue.main.async {
                    self.nameLabel.text = fakeName.name
                    self.birthDateLabel.text = fakeName.birth_data
                    self.randomGenearateButton.isEnabled = true
                    self.randomGenearateButton.backgroundColor = .orange
                }
                
            default:
                print("통신 실패 \(response.statusCode)")
            }
        }
        
        dataTask.resume()
    }
    
    @IBAction func button(_ sender: UIButton) {
        getFakeNameData()
    }
}

```












