Font가 적용이 안될 때
===============

**font**에는 파일명을 그대로 적용하는 것이 아니라

진짜 파일명이 따로 있다.

진짜 파일명을 알 수 있는 방법은?

</br>

```swift 

UIFont.familyNames.sorted().forEach { familyName in
            print("*** \(familyName) ***")
            UIFont.fontNames(forFamilyName: familyName).forEach { fontName in
                print("\(fontName)")
            }
            print("---------------------")
        }
```

위와 같은 코드를 화면이 처음을 나타날 때 실행시키는.  

viewDidLoad() 함수에 적으면 화면이 켜짐과 동시에 글씨체 파일의

진짜 이름을 알 수 있다!  

![image](https://github.com/pursWon/won_TIL/assets/99719661/763737a2-4e62-4e3e-8a05-940b2082304c)

글씨체 파일 여러 개가 내장되어있는만큼. 

그 안에서 내가 찾고자 하는 파일명을 찾아서 확인하면 된다.   

내가 적용시키고자 하는 글씨체는 SCDream7이므로.  

진짜 파일명은 S-CoreDream-7ExtraBold임을 알 수 있다.    
