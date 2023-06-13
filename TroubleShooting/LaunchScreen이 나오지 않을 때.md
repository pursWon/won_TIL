LaunchScreen이 나오지 않을 때
=======================

**포트폴리오로 만든 앱에 설정한 LaunchScreen**

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/1999e176-9589-4d9a-9a14-ca37d3a1f9e8)

발생한 문제  

</br>

LaunchScreen을 실행시키기 위한 설정을 인터넷에서 서치하여 모두 

</br>

설정했다고 생각했지만 막상 실행을 해보니, LaunchScreen이 나오지 않았다.

</br>

해결법 

</br>

앱의 SceneDelegate로 들어간다. 


</br>
SceneDelegate에는 window가 선언되어 있다. 


</br>


window를 사용하여 rootViewController를 변경할 수 있다. 


</br>


여기서 rootViewController는 무엇일까?

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/f382126c-0643-4042-9739-9d0d69b1778c)

말 그대로 window를 위한 View Controller이다.

</br></br>

![image](https://github.com/pursWon/won_TIL/assets/99719661/09160759-b426-4bc6-aba8-8ea376edbcb2)


rootViewController는 window의 content view를 제공한다.     





rootViewController에 viewController를 할당하면 viewController의 view가     





window의 content view로 설치되게 된다.     





요약하면, 내가 보여주고 싶은 view를 rootViewController에 설치함에 따라.   





window에 보여주게 된다는 것이다.    





그렇다면 SceneDelegate의 willConnectTo 함수에 가서 window의 rootViewController에     





LaunchScreen을 설치하면 첫 화면으로 보여줄 수 있지 않을까?   

</br>

```swift 
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        window?.rootViewController = UIStoryboard(name: "LaunchScreen", bundle: nil).instantiateInitialViewController()
        self.window?.makeKeyAndVisible()
        
        DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
            self.window?.rootViewController = UIStoryboard(name: "Main", bundle: nil).instantiateInitialViewController()
        }
    }
```
</br>

파일 이름이 LaunchSceen이므로 해당 이름을 rootViewController로          





설정해준 후, 초기화 시켜준다.   





그러면 처음 화면으로 LaunchScreen이 나타날 것이고             







그리고 나서, DispatatchQueue의 main 스레드에서 일정 시간 이후에 Main 화면이 나타나야 하므로        







asyncAfter를 사용하여 1초 이후에 Main 화면이 나타나게끔 설정하였다.      




추가로, 특정 코드를 일정한 시간 뒤에 실행시키고자 하면           





DispatchQueue.main.asyncAfter를 사용한다.   

</br></br>


![image](https://github.com/pursWon/won_TIL/assets/99719661/cafdd344-c19c-4417-a766-d7ac459d79b9)

for문에서 0부터 4까지 출력하고  



3초 뒤에 "3초 뒤에 출력"이라는 String 값을 출력한다.       






