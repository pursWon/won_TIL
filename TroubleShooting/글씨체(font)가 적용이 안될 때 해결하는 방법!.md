글씨체(font)가 적용이 안될 때 해결하는 방법!
=============================================

내가 SCDream7.otf이라는 글씨체를    

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/9b3288aa-7b1d-4352-b13d-6f810552cab6)

글씨체를 Fonts 폴더에 넣은 후

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/c2a90105-cf06-484a-85ee-cafd2acb4fa6)


Fonts provided by application에 파일명 그대로 추가해준다.   

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/cca48fd4-4b9b-4038-88cf-62a005d42dd2)

</br>

그리고 내가 적용하고 싶은 Label의 글씨체로 설정해준다.

</br>

이제, 이러면 글씨체가 잘 적용되서 화면에 보여질 것이다.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/0c0a534f-a788-45d8-b435-329a7eb79a83)

내가 가져온 글씨체가 적용되지 않고 기본 글씨체가 적용이 되었다.

</br>

어떤 게 문제인지 찾아본 결과,

</br>

font에는 파일명을 그대로 적용하는 것이 아니라

</br>

진짜 파일명이 따로 있다는 것을 알게 되었다.

</br>

그러면 진짜 파일명을 알 수 있는 방법은 무엇이냐

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

</br>

위와 같은 코드를 화면이 처음을 나타날 때 실행시키는 

</br>

viewDidLoad() 함수에 적으면 화면이 켜짐과 동시에 글씨체 파일의 

</br>

진짜 이름을 알 수 있다!

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/bd20e038-730a-4d33-a278-99788f0c6ab2)

</br>

글씨체 파일 여러 개가 내장되어있는만큼

</br>

그 안에서 내가 찾고자 하는 파일명을 찾아서 확인하면 된다.

</br>

내가 적용시키고자 하는 글씨체는 SCDream7이므로

</br>

진짜 파일명은 S-CoreDream-7ExtraBold임을 알 수 있다. 

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/cdfdadb4-9d55-4f04-9c82-322f6307b934)

</br>

진짜 이름을 알아냈으므로 해당 파일명을 다시금 적용시켜보면

![image](https://github.com/pursWon/won_TIL/assets/99719661/a86be737-2a99-4b91-80b3-1352bf667efa)

</br>

잘 적용이 되어서 나온다는 것을 확인할 수 있었다.



