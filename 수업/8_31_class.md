8.31 수업 내용
===

```swift
import UIKit

class ViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {
    var manArray: [String] = ["Sargis 1", "Narek 1", "Edvard 1", "Karekin 1", "Krikor 1"]
    var womanArray: [String] = ["Elen 0", "Harutyun 0", "Poghos 0", "Hourig 0", "Rudolf 0"]
    
    @IBOutlet weak var contactTableView: UITableView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        contactTableView.dataSource = self
        contactTableView.delegate = self
        
        // 배열을 정렬하는 메서드
        manArray = manArray.sorted()
        womanArray = womanArray.sorted()
    }

    // 몇개의 section을 보여줄 지 갯수를 리턴하는 함수
    func numberOfSections(in tableView: UITableView) -> Int {
        return 2
    }
    
    // section의 header에 어떤 title을 보여줄지 문자열을 리턴하는 함수
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        if section == 0 {
            return "man"
        }
        
        return "woman"
    }
    
    // 몇 개의 row를 보여줄 지 갯수를 리턴하는 함수
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        if section == 0 {
            return manArray.count
        }
        
        return womanArray.count
    }
    
    // 어떻게 생긴 cell을 보여줄지 + 그 cell에 어떤 데이터를 보여줄지 설정하여 리턴하는 함수
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell: UITableViewCell = UITableViewCell(style: .default, reuseIdentifier: "contactCell")

        if indexPath.section == 0 {
            cell.textLabel?.text =  manArray[indexPath.row]
        } else {
            cell.textLabel?.text = womanArray[indexPath.row]
        }
        
        return cell
    }
}
