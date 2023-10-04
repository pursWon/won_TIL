Button의 font 설정이 되지 않을 때
===============================

Button의 font를 설정하는 코드는 다음과 같다.

</br>

```swift

myButton.titleLabel?.font = UIFont(name: "SpoqaHanSansNeo-Bold", size: 14)

```

</br>

하지만 내가 지정한 font로 나타나지 않는 것을 확인할 때가 있는데, 그때에는 Storyboard를 확인해보면,    

</br>

![스크린샷 2023-10-04 오후 10 45 05](https://github.com/pursWon/won_TIL/assets/99719661/2f154b84-c8e9-4842-8ef6-670986ca8437)

</br>

해당되는 Button의 **Style**이 Plain이 아닌 Default로 설정되어 있는지 확인하자.   
