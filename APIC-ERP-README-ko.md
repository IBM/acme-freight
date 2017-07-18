## ERP LoopBack 앱을 로컬에서 개발하기

### 이 과정의 준비 사항

#### Node.js
Node.js는 브라우저가 아닌 환경에서 JavaScript를 실행하는 플랫폼입니다. ERP 레이어는 Node.js 환경에서 APIs를 빠르게 개발하는 LoopBack 프레임워크 기반의 애플리케이션입니다.

Node.js 설치를 아직 안하셨다면,  여러분의 플랫폼에 맞는 인스톨러를 NodeJS.org에서 검색해 보세요.

#### API Connect
Node.js에 있는 Node Package Manager를 사용해 API Connect을 설치하겠습니다. 터미널에 아래와 같이 입력합니다:

`npm install --global apiconnect`

이제 여러분의 컴퓨터에 API Connect Node.js 가 설치되는데, 이제는 컴퓨터 내의 어떤 디렉토리에서든지 API Connect을 활용할 수 있게 됩니다.

### 로컬 머신에 ERP 코드 가져오기

여러분 컴퓨터의 로컬에서 코드를 운영하는 가장 쉬운 방법 두 가지는 git을 사용하여 저장소를 로컬에 복제하거나 또는 단순히 zip 파일을 다운로드 받는 것입니다. 여러분이 만약 저장소를 복제한다면, 업데이트가 있을 때 변경본을 쉽게 가지고 올 수 있습니다. 만약 코드만 다운로드 받는다면, 그 기능은 사용할 수 없습니다.

코드를 복제하려면, 터미널에서 이 명령을 실행하십시오:
`git clone https://github.com/IBM/acme-freight-erp.git`

코드를 다운로드하려면, 전체 저장소의 zip 아카이브 파일을 받을 수 있는 이 링크를 클릭하십시오:
https://github.com/IBM/acme-freight-erp/archive/dev.zip

만약 추가적으로 코드를 수정하여 마스터 프로젝트에 여러분의 수정사항을 반영하고 싶으시다면, Github 계정으로 저장소를 포크(fork)하신 후 그 포크를 복제하십시오.

### 로컬머신에서 ERP 코드를 실행하십시오

로컬머신에 소스 코드 환경이 갖춰어 졌다면 (이전 단계), 터미널에서 해당 디렉토리로 이동합니다. 우선 실행에 필요한 종속 패키지들(dependencies)을 모두 다운로드합니다. 아래와 같이 타이핑하십시오:

`npm install`

하위 패키지들을 모두 다운로드 받은 후에는 애플리케이션을 실행하실 수 있습니다. 아래와 같이 타이핑하십시오:

`npm start`

여기서 애플리케이션은 인메모리 데이터베이스로 실행됩니다. 앱을 중단하면 그간의 모든 변화가 소실됩니다. 이제 영구적 저장소(persistent storage)를 구성해봅니다.


### 영구적 인메모리 데이터베이스 사용하기

아래와 같이 file server/datasources.local.json 를 생성합니다:
```
{
 "db": {
   "name": "db",
   "connector": "memory",
   "file": "in-memory-database.json"
 }
}
```
애플리케이션을 시작합니다: `npm start`
이제 데이터는 in-memory-database.json에 영구적으로 저장됩니다.

## 이제 만든 APIs를 테스트해 봅니다

### APIC 툴킷을 실행하십시오
API Connect의 툴킷을 사용하면 비주얼한 환경에서 APIs를 생성, 테스트, 배포할 수 있습니다. 시작하려면, 여러분의 애플리케이션 디렉토리에서 apic edit을 실행하십시오. 처음 실행 시 로그인 창이 나타날 수 있습니다. 기존 Bluemix 계정이 있다면 해당 정보로 로그인하시고, 없으실 경우 Bluemix 계정을 만드십시오.
```
apic edit
```

### 애플리케이션 실행하기
이제  APIs가 모두 생성되었으니 여러분의 APIs에 엑세스하기 위해 로컬에서 애플리케이션을 실행할 수 있습니다. 왼쪽 아래에 위치한 `Play` 버튼을 클릭하면 애플리케이션이 실행됩니다. 몇 초 안에 애플리케이션과 마이크로게이트웨이가 실행될 것입니다. 애플리케이션이 실제 APIs 환경을 제공한다면, 마이크로게이트웨이는 rate limiting과 같은 API 운영 정책을 시행하고 보안 레이어를 제공합니다.

### 나의 APIs 알아보기
다음으로, 오른쪽 상단에 위치한 Explore 버튼을 클릭하면 Swagger기반 뷰(Open API Spec)로 가용한 APIs를 보여줍니다. 화면 왼쪽에는 여러분이 이전 단계에서 생성한 모델의 운영상황을 확인할 수 있습니다.

화면 아래쪽 `Demo.newDemo` operation 으로 이동한 후, `Try it`을 클릭합니다. 그런 다음 `Call Operation`을 클릭합니다. CORS 에러창이 나타는 경우, 링크를 클릭하여 CORS 에러를 무시고, 예외조항을 추가한 후 탭을 닫습니다. 그런 다음, 다시 `Call Operation`을 클릭합니다.

사용자 정보와 토큰이 담긴 결과를 확인할 수 있습니다. 새로운 세션을 통해 Acme Freight 샘플이 접근될 때 마다, 토큰이 생성되며 이 정보는 다른 엔트포인트에 접근할 때 필요합니다.

API Connect 툴킷을 사용하면, 보안과 CRUD를 위한 복잡한 APIs를 생성하는 것 뿐 아니라, 로컬 머신에서 바로 테스트를 해 볼 수 있습니다. Acme Freight 애플리케이션을 확장하실 계획이 있다면, API Connect 기반의 ERP LoopBack 애플리케이션에서 시작하시면 됩니다.  
