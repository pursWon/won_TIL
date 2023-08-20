Firebase의 Storage
===============

FireStorage란?

Firebase용 Cloud Storage는 사진, 동영상 등의 사용자 제작 콘텐츠를 저장하고 제공해야 하는    

앱 개발자를 위해 만들어졌습니다.         

이 클라이언트 SDK를 사용하여 이미지, 오디오, 동영상 등의 사용자 제작 콘텐츠를 저장할 수 있습니다.     

서버에서 Firebase Admin SDK를 사용하여 버킷을 관리하고 다운로드 URL을 만들 수 있으며    

Google Cloud Storage API를 사용하여 파일에 액세스할 수 있습니다.      

## FireStorage 사용법 
 
Firebase의 Storage의 Rules로 가서 다음과 같이 수정     

</br>

![1](https://github.com/pursWon/won_TIL/assets/99719661/cc9f33d8-7688-4246-ae75-b51d8ae8a201)

</br>

Van de ven .jpeg 라는 파일을 다운받아보자.

</br>

![2](https://github.com/pursWon/won_TIL/assets/99719661/a2d1c2c0-5a4b-46a0-968f-04a406c82b22)

</br>

FirebaseStorage import 하기

</br>

![3](https://github.com/pursWon/won_TIL/assets/99719661/2b4e6d5f-f9f8-4352-8704-2b071df5b11a)

</br>

저장공간 상수를 만들어준다.

```swift

let storage = Storage.storage()

```

</br>

빨간 박스안의 링크를 복사한다. 복사한 후 com/ 뒤에는 파일 이름을 붙이면 된다.

</br>

![4](https://github.com/pursWon/won_TIL/assets/99719661/452cd4bc-81d4-4592-bdcb-09acb1c369ca)

</br>

아래와 같이 코드를 설정해준다.

</br>

```swift

@IBAction func imageDownloadButton(_ sender: UIButton) {
        storage.reference(forURL: "gs://fir-ex-41229.appspot.com/Van de ven .jpeg").downloadURL { url, error in
            guard error == nil else {
                print(error?.localizedDescription)
            return }
            
            guard let url = url else { return }
            
            DispatchQueue.global().async {
                if let data = try? Data(contentsOf: url) {
                    if let pictureImage = UIImage(data: data) {
                        DispatchQueue.main.async {
                            self.pictureImageView.image = pictureImage
                        }
                    }
                }
            }
        }
    }

```

반면에, 이미지 업로드는 다음과 같이 코드를 설정해주면 된다.

</br>

```swift

@IBAction func imageUploadButton(_ sender: UIButton) {
        guard let img = UIImage(named: "Van de ven") else { return }
        var data = Data()
        
        data = img.jpegData(compressionQuality: 0.8)! // 지정한 이미지를 포함하는 데이터 개체를 JPEG 형식으로 반환, 0.8은 데이터의 품질을 나타낸것 1에 가까울수록 품질이 높은 것
        let filePath = "Van de ven"
        let metaData = StorageMetadata() // Firebase 저장소에 있는 개체의 메타데이터를 나타내는 클래스, URL, 콘텐츠 유형 및 문제의 개체에 대한 FIRStorage 참조를 검색하는 데 사용
        metaData.contentType = "image/png" // 데이터 타입을 image or png
        
        storage.reference().child(filePath).putData(data, metadata: metaData) {
            (metaData,error) in if let error = error { // 실패
                print(error)
                
                return
            } else {
                print("성공")
            }
        }
    }

```


