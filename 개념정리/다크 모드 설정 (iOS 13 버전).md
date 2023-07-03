다크 모드 설정 (iOS 13 버전)
==============

## 1. 기본 Appearance 설정 

![스크린샷 2023-07-02 오전 10 43 40](https://github.com/pursWon/won_TIL/assets/99719661/23a295d5-1456-47c0-af72-6e37520cee5c)

Info.plist에서 Appearance를 설정한다.    

다크 모드로 보여주고 싶을 때는 Dark, 라이트 모드로 보여주고 싶을 땐, Light로 설정한다.    

앱 내에서 다크 모드를 On / Off 하기 위해서 UserDefaults를 이용

사용자가 다크 모드 버튼을 클릭하면 아래 코드가 실행되고 현재 ViewController의 Appearance를 확인한 후에

그와 반대의 값을 UserDefaluts에 저장한다. 그리고 ViewController를 reload한다.

```swift

@IBAction func lightButton(_ sender: UIButton) {
if self.overrideUserInterfaceStyle == .light {
    UserDefaults.standard.set("Dark", forKey: "Appearance")
} else {
    UserDefaults.standard.set("Light", forKey: "Appearance")
}
  self.viewWillAppear(true)
}

```

viewWillAppear()가 호출이 될 때, AppearanceCheck() 함수를 호출하여 해당 ViewController를 다크모드로 보여줄 지     

라이트 모드로 보여줄 지 판단한다.   

```swift

override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        appearanceCheck(self)
}
```

아래는 AppearanceCheck() 함수이다.

UserDefaults에 저장된 Appearance 값을 가져와서 그에 맞게 ViewController의     

overrideUserInterfaceStyle을 설정한다.   

```swift

func appearanceCheck(_ viewController: UIViewController) {
        guard let appearance = UserDefaults.standard.string(forKey: "Appearance") else { return }
        
        if appearance == "Light" {
            viewController.overrideUserInterfaceStyle = .light
            
            if #available(iOS 13.0, *) {
                UIApplication.shared.statusBarStyle = .darkContent
            } else {
                UIApplication.shared.statusBarStyle = .default
            }
        } else {
            print(appearance)
            viewController.overrideUserInterfaceStyle = .dark
            
            if #available(iOS 13.0, *) {
                UIApplication.shared.statusBarStyle = .lightContent
            } else {
                UIApplication.shared.statusBarStyle = .default
            }
        }
    }
```

여기서 중요한 건 statusBarStyle도 설정해줘여 상태 바의 글씨가 제대로 보인다.    

info.plist에서 View Controller - based status bar appearance 값을 No로 설정한다.

</br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/f858e7a3-6616-4497-805f-fc9e7cb9e5c0)

</br>

ViewController가 여러 개라면 해당 ViewController의 viewWillAppear() 안에    

AppearanceCheck(self)를 적어주면 사용자가 정의한 값에 따라 다크 모드가 적용이 될 것이다.    





