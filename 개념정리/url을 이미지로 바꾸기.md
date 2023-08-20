url을 이미지로 바꾸기
======================

url을 Data로 변경   

Data를 image로 변경

```swift

  DispatchQueue.global().async {
                if let data = try? Data(contentsOf: url) {
                    if let pictureImage = UIImage(data: data) {
                        DispatchQueue.main.async {
                            self.pictureImageView.image = pictureImage
           }
       }
    }
 }
```

KingFisher 라이브러리를 사용하면 수월하게 처리할 수 있다.

```swift

if let imageURL = URL(string: imageURL) {
    imageView.kf.setImage(with: url)
}

```



