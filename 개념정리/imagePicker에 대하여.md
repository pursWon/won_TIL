imagePicker에 대하여
=========

### MyBookRecord에 imagePicker 추가하기

구현하고자 하는 기능 : addViewController에서 책 이미지를 눌러서 사진을 고를 수 있는 창을 띄운다음 이미지를 눌러서 기본 이미지에 누른 해당 이미지를 보여주게끔 하기

![Simulator Screen Shot - iPhone 11 - 2022-12-17 at 20 09 17](https://user-images.githubusercontent.com/99719661/208240032-85ce86ee-f994-4a17-b61d-078616079836.png)

일단 책 이미지를 버튼처럼 눌렀을 때 창이 띄워지게끔 해야 한다.     

해당 메서드를 사용하도록 하자.   

<img width="609" alt="스크린샷 2022-12-17 오후 8 12 24" src="https://user-images.githubusercontent.com/99719661/208240071-43780f5a-ab68-4476-b00c-bc17069ed387.png">

요약 : **단일 또는 다중 탭을 해석하는 개별 제스처 인식기입니다.**.   

viewDidLoad()에 다음과 같이 코드를 추가해준다.       

```swift

let tapGesture = UITapGestureRecognizer(target: self, action: #selector(touchPhoto))
        defaultImage.addGestureRecognizer(tapGesture)
        defaultImage.isUserInteractionEnabled = true
```

touchPhoto 함수는 extension 클래스에서 설정해준다.     

기본 이미지를 눌렀을 때 창을 띄우게끔 하려면 눌렀을 때 행해지는 액션 → 함수.  

해당 제스처를 기본 이미지 outlet에 추가해주고     

사용자와의 상호작용을 true로 설정해주어야 한다.    

```swift

extension AddViewController: UIImagePickerControllerDelegate {
    @objc func touchPhoto() {
    let picker = UIImagePickerController()
        picker.sourceType = .photoLibrary
        picker.allowsEditing = true
        picker.delegate = self
        
        self.present(picker, animated: true)
    }
    
    func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
        picker.dismiss(animated: true) { () in
            let img = info[UIImagePickerController.InfoKey.editedImage] as? UIImage
            self.defaultImage.image = img
        }
    }
}

```

extension 클래스를 설정해주고 **UIImagePickerControllerDelegate**를 붙여준다.    

touchPhoto 함수를 설정해줘야 기본 이미지를 눌렀을 때 행해지는 액션을 볼 수 있을 것이다.    

그리고 **imagePickerController** 함수는 이미지가 선택되었을 때 행해지는 액션을 설정하기 위한 함수이다.    

(이미지가 선택되지 않았을 때 행해지는 액션의 함수도 존재하지만 여기서는 사용하지 않았다.)

## 결과

https://user-images.githubusercontent.com/99719661/208240164-a1fdfafb-4b4c-49ee-afb1-eb9eafc51de2.mp4















