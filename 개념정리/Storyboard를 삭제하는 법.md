Storyboard를 삭제하는 법
========

코드로만 UI를 그릴 수 있다. 이를 위해서는 우선, 그동안 많이 사용했었던 Storyboard를 삭제를 해야하고 추가로 해야하는 준비 과정이
 
존재한다. 해당 과정은 다음과 같다. 
 
1. Storyboard를 삭제한다.

<img width="265" alt="스크린샷 2023-02-05 오전 2 44 08" src="https://user-images.githubusercontent.com/99719661/216781847-0084dcc4-3f65-4c11-82ad-8a7c7bd81c3b.png">
 
해당 메뉴에서 Storyboard를 삭제해주면 된다. (이미지는 삭제하고 난 후의 화면)

2. 위의 파란색 프로젝트를 클릭 → Targets의 파란색 프로젝트 → filter 창에 Main 검색 -> UIKit Main Storyboard File Base Name 제거

</br>

![스크린샷 2023-10-23 오전 9 24 01](https://github.com/pursWon/won_TIL/assets/99719661/2f88b94d-147a-4cf1-b615-5664ead388d2)

</br>

3. Info.plist에 들어가서 Application Scene Manifest 부분에 마우스를 갖다 대면 Item 0 버튼이 나오는데, 계속 확장해서 위와 같이 펼친다.      
Storyboard Name을 확장해서 키 부분을 삭제한다. 이때 삭제는 - 버튼으로 삭제하면 된다.

</br>
 
4. SceneDeleagate에 들어가서 willConnectTo 함수안에 해당 코드를 추가

</br>

```swift
guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)
        
        let viewController = ViewController()
        window?.rootViewController = viewController
        window?.makeKeyAndVisible()
```

</br>

5. Scene Life Cycle을 채택했을 때, iOS 13 이전의 기기에서도 작동하려면 다음과 같은 코드를 AppDelegate에 추가해주면 된다.

```swift
import UIKit

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        // 13이상인 경우에는 SceneDelegate에서 이미 초기화 되었으니까 바로 return
        if #available(iOS 13.0, *) {
            return true
        }
        
        return true
    }
```

</br>
 
6. view의 배경색을 바꿔서 잘 작동이 되는지 확인하기

</br>

```swift
override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .orange

    }
```

</br>
    
view의 배경색이 잘 나오면 과정이 잘 완료된 것임을 알 수 있다. 

