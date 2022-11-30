Cocoapads
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
