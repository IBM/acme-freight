## Bluemix에서 OpenWhisk 액션을 위한 보안된 APIs 생성하기

### Bluemix에서 OpenWhisk 액션을 위한 API 생성하기

[툴체인 인스톨하기](TOOLCHAIN-README.md)를 마치면, 툴체인을 생성할 때 선택했던 bluemix 상의 region(지역) 및 space(공간)에 OpenWhisk 액션들이 배포됩니다. [Bluemix 상 OpenWhisk 대시보드](https://console.ng.bluemix.net/openwhisk/manage/actions)에서 해당 내용을 확인하실 수 있습니다. 폭풍우가 발생하는 상황의 시물레이션이 실행 될 때 마다, OpenWhisk 액션들이 실행되어, 필요한 조치에 대한 추천을 하게 됩니다. 

<img src="docs/actions.png" alt="OpenWhisk actions" width="600">

#### API와 엔드포인트 생성하기

API의 일부로 OpenWhisk액션을 노출시키기 위해서는, Bluemix OpenWhisk 인터페이스 상단 (또는 좌측 메뉴)에 위치한 API 링크를 클릭해야 합니다. 그리고서는 Create an OpenWhisk API 버튼을 클릭하십시오.

1. 생성하고자 하는 API 이름을 입력하세요. 저는 `Acme Freight OpenWhisk API`로 하겠습니다.

2. Create Operation 버튼을 클릭하여 여러분의 엔트포인트를 생성합니다. 

각각의 OpenWhisk액션에 상응하도록 엔드포인트 이름을 지정하십시오. Verb 입력란에 `POST` 를 선택하세요. 아래 예를 참조하십시오:

<img src="docs/endpoint-modal.png" alt="Create operation endpoints" width="500">

OpenWhisk액션마다 상응하는 엔드포인트를 만드시려면, 위의 단계를 반복하십시오. 

여러분이 만든 페이지는 아래의 이미지와 유사할 것입니다: 

<img src="docs/create-api.png" alt="API create" width="700">

화면 아래쪽으로 이동합니다.

- "Require ... via API key" 옵션을 선택합니다; 관련된 다른 값들 (Method, Location of API key and secrete 등)은 기본값을 그대로 사용합니다.
- "Method" 부분은 "API key only"로 선택되어 있는지 확인합니다.
- "Enable CORS..." 옵션도 선택되어 있는지 확인합니다.
- Save 버튼을 클릭합니다.

<img src="docs/save-api.png" alt="API save" width="700">

#### API 키 생성하기

엔드포인트에 엑세스하기 위한 API 키를 생성하려면, 아래 화면의 왼쪽에 위치한 "Sharing" 링크를 클릭합니다:

<img src="docs/sharing.png" alt="Sharing" width="700">

이 화면에서 "Create API Key" 버튼을 클릭합니다.

Create API Key 화면에서 아래 항목들을 실행합니다:

- API key에 이름을 지정합니다
- 여러분의 API key를 기록해 둡니다
- "Create"를 클릭합니다:

<img src="docs/create-api-key.png" alt="Create API Key" width="500">

마지막으로 필요한 것은 여러분이 생성한 APIs로 전체 경로 정보인데, 이는 Summary 페이지에서(아래 화면의 'Route'부분) 확인하실 수 있습니다. 다음 단계를 위해서 이를 저장합니다. 

<img src="docs/summary.png" alt="Summary" width="700">

### Configure the controller application to use your newly created secure API endpoints

이제 보안이 적용된 엔드포인트 (secured endpoint)를 생성하였으니, OpenWhisk액션을 호출할 Acme Freight 마이크로서비스 쪽을 변경할 차례입니다. 컨트롤러 애플리케이션에는 보안이 적용된 엔트포인트를 호출하는 코드가 이미 있습니다; 단순히 애플리케이션이 보안이 적용된 해당 API URL과 API 키를 사용하도록 설정하면 됩니다.

_Note: 컨트롤러가 사용하는 백엔드 서비스 정보를 업데이트할 때는 환경설정(environment configuration)을 사용하는 것이 가장 좋습니다. 컨트롤러 코드가 보안이 적용된 API를 엑세스하기 위해 API URL과 API 키가 제공되었는 지를 확인하고 호출시 사용합니다. [코드 보기](https://github.com/IBM/acme-freight-controller/blob/dev/server/utils.py#L76)_

[Bluemix DevOps toolchains](https://console.ng.bluemix.net/devops/toolchains) 으로 가서 Acme Freight로 생성한 툴체인을 클릭합니다. 그러면 아래와 같은 화면이 보이는데, `controller` 파이프라인을 위해서는 `Deliver` 밑의 사각형을 클릭하십시오:

<img src="docs/toolchains.png" alt="Toolchains" width="700">

 그런 다음, `Deploy` 단계의 파이프라인은 `Configure Stage`옵션을 클릭하십시오:

<img src="docs/configure-deploy.png" alt="Configure Deploy" width="300">

Under the `Environment Properties` 탭 아래, `OW_API_KEY`와 `OW_API_URL`라는 두 개의 `Text Property` 필드를 추가합니다. 대소문자가 구별된다는 것에 유의하세요. 다른 필드는 그대로 둡니다. 아래 화면을 참조하십시오:

<img src="docs/deploy-env.png" alt="Deploy environment" width="500">

save 버튼을 클릭하고 파이프라인으로 돌아가서 `Run Stage` 버튼을 클릭하십시오:

<img src="docs/run-stage.png" alt="Run stage" width="300">

몇 번의 클릭만으로 Acme Freight 애플리케이션은 보안이 적용된 OpenWhisk액션에 엑세스됩니다! OpenWhisk액션에 보안을 적용함에 따른 장점은 다음과 같습니다.:
- 안전한 rate-limit 세팅 (호출 빈도 제한)을 통해 당신의 OpenWhisk 액션을 향한 악성 스팸으로부터 애플리케이션을 보호하게 됩니다.
- Acme Freight가 아닌 다른 애플리케이션에서도 호출이 가능하도록, 여러분의 OpenWhisk 엔드포인트가 공개되는데, 접근이 필요한 애플리케이션 별, API 접근을 위한 키를 생성하면, 여러분의 API가 어떻게 활용되는지 추적 및 관리가 가능하며, 필요시 접근에 대한 권한을 해지할 수도 있습니다. 
- 분석 뷰(analytics view)를 활용하여 여러분의 APIs가 얼마나 자주 호출되는지와 실행되는데 얼마나 시간이 걸리는지 알수 있습니다. 모니터링을 통해 성능 지원의 이슈가 있는 APIs를 알아낼 수 있습니다.
