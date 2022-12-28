Naver 지도 API 가져와보기 (API 연습)
========

(1) 네이버 클라우드 플랫폼 콘솔 페이지로 접속한다.

링크 :  [https://console.ncloud.com/dashboard](https://console.ncloud.com/dashboard)

(2) AI, NAVER API → Application → Application 등록

Application에 이름을 입력하고 Mobile Dynamic Map에 체크한다.

(3) 서비스 환경 등록에 Bundle Identifier를 추가 버튼을 눌러서 추가해준다.


(예시 이미지)

(4) 라이브러리를 설치하기에 앞서 필요한 프로그램들을 설치해준다. 

cocoapod이 설치되어 있지 않으면 다음 명령어를 입력

```xml
sudo gem install cocoapods
```

homebrew가 설치되어 있지 않으면 다음 명령어를 입력 

```xml
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

git-lfs가 설치되어 있지 않으면 다음 명령어를 입력

```xml
brew install git-lfs
```

프로젝트 파일 경로로 이동 (내 프로젝트 이름 :  NaverApiPractice2)

```xml
cd NaverApiPractice2
```

아래 명령어로 cocoapods를 초기화 

```xml
pod init 
```

git-lfs로 초기화도 해줘야한다.

```xml
git-lfs install 
```

Podfile에 아래 코드를 추가한다. 

pod ‘NMapsMap’

pod install로 라이브러리를 설치해준다. 

```xml
pod install --repo-update
```

(5) 클라이언트 ID를 설정해준다. 

pod install 을 하면 xcworkspace 파일이 생성된다.

프로젝트명.xcworkspace 로 프로젝트를 연다.

Info.plist 를 열고 Information Property List 에 마우스를 클릭하면 + 버튼이 보인다.



Key 칸에는 NMFClientld 를 입력




Value 칸에는 Client ID를 입력 

(6) 지도 표시 

ViewController.swift 파일 상단에 아래 코드를 추가해 NMapsMap 를 임포트 시킨다. 

```swift
import NMapsMap
```

ViewDidLoad 함수에 아래 코드를 추가해 네이버 지도를 화면에 표시한다.

```swift
let mapView = NMFMapView(frame: view.frame)
view.addSubview(mapView)
```

총 코드 

```swift 

import NMapsMap
import CoreLocation

class ViewController: UIViewController, CLLocationManagerDelegate, NMFMapViewCameraDelegate {
    
    var locationManager = CLLocationManager()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let mapView = NMFMapView(frame: view.frame)
        view.addSubview(mapView)
        
        locationManager.delegate = self
        self.locationManager.requestWhenInUseAuthorization()
        locationManager.desiredAccuracy = kCLLocationAccuracyBest
        locationManager.requestWhenInUseAuthorization()
        
        if CLLocationManager.locationServicesEnabled() {
            print("위치 서비스 On 상태")
            locationManager.startUpdatingLocation()
            print(locationManager.location?.coordinate)
            let cameraPosition = mapView.cameraPosition
            print(cameraPosition)
            
            let cameraUpdate = NMFCameraUpdate(scrollTo: NMGLatLng(lat: 37.5666102, lng: 126.9783881))
            mapView.moveCamera(cameraUpdate)
            print(cameraUpdate)
            
            let coord = NMGLatLng(lat: 37.577013, lng: 126.9783740)
            print("위도: \(coord.lat), 경도: \(coord.lng)")
            
        } else {
            print("위치 서비스 Off 상태")
        }
    }
}

```

**위도**와 **경도**를 추가할 수 있게끔 되었다.



