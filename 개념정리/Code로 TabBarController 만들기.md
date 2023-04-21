Code로 TabBarController 만들기
=============================
StoryBoard는 사용하지 않는다.

<br/>

1. **SceneDelegage 파일로 들어가기**

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)

}
```

<br/><br/><br/>

2. **TabBarController 안에 넣을 VC 생성**

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)

				let mainViewController = MainViewController()
        let subViewController = UIViewController()
}
```

<br/><br/><br/>

3. **TabBarController 생성** 

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)

				let mainViewController = MainViewController()
        let subViewController = UIViewController()

				let tabBarController: UITabBarController = UITabBarController()
        tabBarController.setViewControllers([mainViewController, subViewController], animated: true)
}
```

TabBarController를 만든 뒤 setViewControllers() 메서드를 사용하여     

TabBar 안에 들어갈 viewController들을 넣어줍니다.   

<br/><br/><br/>


4. **TabBar Item 설정**

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)

				let mainViewController = MainViewController()
        let subViewController = UIViewController()

				let tabBarController: UITabBarController = UITabBarController()
        tabBarController.setViewControllers([mainViewController, subViewController], animated: true)

				if let items = tabBarController.tabBar.items {
            items[0].image = UIImage(systemName: "folder")
            items[0].selectedImage = UIImage(systemName: "folder.fill")
            items[0].title = "Home"
            
            items[1].image = UIImage(systemName: "circle")
            items[1].selectedImage = UIImage(systemName: "circle.fill")
            items[1].title = "Sub"
        }
}
```

TabBar 아이템들은 Optioanl 타입이므로 if let 구문을 사용해서 안전하게 binding 해야한다.

- TabBar 아이템이 선택되었을 때 이미지를 selectedImage에, 선택되지 않았을 때 이미지를 image에 지정한다.
- TabBar 아이템의 타이틀도 title에 설정한다.

<br/><br/><br/>


5. **rootViewController 설정**

```swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let _ = (scene as? UIWindowScene) else { return }
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)
        
        let mainViewController = MainViewController()
        let subViewController = UIViewController()
        
        let tabBarController: UITabBarController = UITabBarController()
        tabBarController.setViewControllers([mainViewController, subViewController], animated: true)
        
        if let items = tabBarController.tabBar.items {
            items[0].image = UIImage(systemName: "folder")
            items[0].selectedImage = UIImage(systemName: "folder.fill")
            items[0].title = "Home"
            
            items[1].image = UIImage(systemName: "circle")
            items[1].selectedImage = UIImage(systemName: "circle.fill")
            items[1].title = "Sub"
        }
        
        window?.rootViewController = tabBarController
        window?.makeKeyAndVisible()
    }
```

TabBar 설정이 완료되면 window.rootViewController에 생성한 tabBarController를 지정한다.    

밑의 makeKeyAndVisible() 함수도 반드시 적어줘야한다. window를 보여주는 메서드이므로..   
