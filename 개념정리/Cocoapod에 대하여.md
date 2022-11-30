Cocoapad
===

명령어 2가지만 입력하면 된다. 

**sudo gem install cocoapads**

**pop setup --verbose**

설치가 완료되었는지 확인하려면, 

**pod --version**

# Podfile

코코아팟의 역할은?

→ 우리가 원하는 라이브러리를 자동으로 설치해줌

그러면 **Podfile**의 역할은?

→ 우리가 설치하고픈 라이브러리를 코코아팟에게 알려주는 역할

# Podfile.lock

코코아팟이 Podfile을 통해 우리가 원하는 라이브러리를 다운받고 나면 해당 코코아팟의 버전을 

명시해주는 곳이 **Podfile.lock** 이다. 

**Podfile.lock**은 왜 필요할까?

프로젝트에서 사용하는 라이브러리의 버전을 명시하니까, 협업 시에 동일한 버전을 공유할 수 있다. 

# Pods

다운받고 설치한 팟이 실제로 저장되는 공간을 의미한다.

**pod install** 

→ pod을 프로젝트에 세팅하기 위하여 맨 처음에 사용되는 명령어

Podfile의 Pod를 수정, 추가, 삭제할 때도 사용한다. 

pop update 라이브러리 이름 

→ pod update뒤에 라이브러리 이름을 써주면 코코아팟은 해당 팟의 업데이트된 버전이 있는지 찾아서 최신 버전으로 업데이트 시켜준다.

# Cocoapod의 사용방법 

**1단계**

```markdown
sudo gem install cocoapods
```

**2단계**

```markdown
cd 해당되는 프로젝트 폴더의 경로 
```

**3단계**

```markdown
pod init // pod 파일을 생성해준다. 
```

**4단계**

```markdown
open -e podifle // pod 파일을 열어준다. 
```

**5단계**

podfile을 열어서 Tabman 라이브러리를 사용할 것이므로 다음과 같이 입력한다.
<img width="676" alt="스크린샷 2022-11-30 오후 5 49 08" src="https://user-images.githubusercontent.com/99719661/204784835-c7d3b67c-92e6-4ee4-af06-19305d846373.png">

https://cocoapods.org/pods/Tabman   
podfile에 입력할 때에는 해당 링크에서 cocoapods에 무엇이라고 써야하는지 참고하면 된다.    

**6단계**

```markdown
pod install
```

pod install을 쳤을 때 생기는 오류문구 → ****[!]Oh no, an error occurred.****


맥북 에어m1에서 생기는 오류라고 한다.    

**해결법 :** 

```markdown
1) sudo arch -x86_64 gem install ffi
2) arch -x86_64 pod install
```

터미널에 이 두 문장을 모두 입력하고 pod install을 다시 실행시키면 해결이 된다.      

**7단계** 

위의 단계들이 잘 실행이 됐다면 프로젝트 경로에 프로젝트.xcworkspace 파일이 생겼을 것이다.      

xcworkspace는 프로젝트의 집합체 같은 파일이라고 보면된다.      

앞으로는 프로젝트를 실행할 때 xcworkspace 파일로 실행시키면 된다.  

**8단계**

<img width="962" alt="스크린샷 2022-11-27 오전 12 52 01" src="https://user-images.githubusercontent.com/99719661/204785160-01c3b3c1-3f0f-45e7-9a7e-85345be77a42.png">

xcworkspace에서 Tabman 라이브러리가 잘 import 된 것을 확인할 수 있다.    
