CollectionView를 Storyboard 없이 그리기
===================

1. Storyboard 삭제

(1) Xcode 옆의 관리창에서 Storyboard 아이콘 삭제 



(2) 위의 파란색 프로젝트 아이콘을 클릭 -> Targets의 파란색 프로젝트 아이콘 클릭 -> Info -> Main Storyboard File Base Name 

(Value에는 "Main") 삭제



(3) Info.plist에 들어가서 Application Scene Manifest 부분에 마우스를 갖다 대면 Item 0 버튼이 나오는데, 계속 확장해서 펼친다.

Storyboard Name을 확장해서 키 부분을 삭제한다. 이 때, 삭제는 - 버튼을 눌러서 삭제하면 된다.



(4) Scene Delegate에 들어가서 willConnectTo 함수안에 해당 코드를 추가

```swift 
guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(windowScene: windowScene)
        
        let viewController = ViewController()
        window?.rootViewController = viewController
        window?.makeKeyAndVisible()
```
