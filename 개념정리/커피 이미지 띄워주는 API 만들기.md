커피 이미지 띄워주는 API 만들기
=====

```swift

import UIKit

struct Coffee: Decodable {
    let file: String
} // Decodable : 외부 형식을 가져와서 디코딩할 수 있는 기능입니다.
// 상수 이름은 API에 있는 이름과 같아야 합니다.

class ViewController: UIViewController {

    @IBOutlet weak var coffeeImageView: UIImageView!
    let url = "https://coffee.alexflipnote.dev/random.json" // 이미지가 담겨있는 링크를 상수(url)에 담아줌
    // url 주소
    override func viewDidLoad() {
        super.viewDidLoad()
        
    }
    
    func getCoffeeData(url: String) { // 커피를 얻는 함수를 만듬
        guard let url = URL(string: url) else { return }
        
        let request = URLRequest(url: url) // URL을 요청하는 객체 생성
        
        let dataTask = URLSession.shared.dataTask(with: request) { data, response, error in
            // 데이터 통신을 통해서 객체 만들기
            guard let data = data else { return } // 데이터가 없을 때를 대비하여 guard문을 사용
            guard let response = response as? HTTPURLResponse else { return }
            // response는 HTTPURLResponse로 다운캐스팅한다. 밑에서 statusCode를 사용해야 하므로..
            guard error == nil else { return }
            // error가 없을 때에 guard문을 통과해야 하므로 guard let문을 사용하지 않는다.
            // guard let 문을 사용할 경우
            // guard let error = error가 되므로 error가 있어야 guard 문을 통과하는 형식이 되는데
            // error가 존재해야 밑의 코드가 실행이 되는 이상한 형태가 되버리기 때문이다.
            switch response.statusCode {
            // 성공 여부에 따라 분기 처리
            case 200:
            print("성공")
                
                let coffee = try? JSONDecoder().decode(Coffee.self, from: data)
                // JSONDecoder() -> JSON 개체에서 데이터 유형의 인스턴스를 디코딩하는 개체입니다.
                if let coffee = coffee {
                // decoding한 객체를 if let 문을 통하여 안전하게 let에 담아주기
                // let image = UIImage(data: data)
                let imageURL = URL(string: coffee.file)!
                // 디코딩을 마친 이미지 URL을 상수에 담아줌
                let imageData = try? Data(contentsOf: imageURL)
                    // Data를 이미지화 시켜주는 작업이다.
                    DispatchQueue.main.async { // UI를 그려주는 일이므로 Dispatchqueue를 통해서 대신 처리해준다.
                        if let data = imageData {
                            self.coffeeImageView.image = UIImage(data: data)
                        }
                    }
                } else {
                    print("파싱 싪패")
                }
            default:
            print("실패", "\(error?.localizedDescription)")
            // error에 관한 텍스트를 띄워주려면 localizedDescription를 사용 \
            }
        }
        
        dataTask.resume() // 해당 객체를 resume를 통해 다시 실행되게끔 해야 API가 정상적으로 실행됨
    }

    @IBAction func coffeeButton(_ sender: UIButton) {
        getCoffeeData(url: url) // 버튼을 눌러서 함수를 실행시키게끔 해줌
    }
}
