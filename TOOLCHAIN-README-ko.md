## 나만의 Acme Freight를 DevOps 툴체인으로 Bluemix에 배포하세요

*다른 언어로 보기: [English](TOOLCHAIN-README.md).*

버튼 클릭 한 번으로 여러분은 Acme Freight 인스턴스에 필요한 모든 마이크로서비스와 서버리스 액션을 배포할 수 있습니다. 더불어, 여러분이 Github에 푸쉬하는 변경사항들을 자동으로 배포하도록 사전 설정된 개발 파이프라인 툴체인도 제공됩니다. 이를 통해, Bluemix의 DevOps 환경을 경험하게 되실 것이며, 동시에 Acme Freight 애플리케이션의 기능도 확장할 수 있습니다.

Acme Freight의 실행 중인 인스턴스를 확인하려면 이 곳에 엑세스하십시오: 
[http://acme-freight.mybluemix.net](http://acme-freight.mybluemix.net)

  [![Deploy To Bluemix](./.bluemix/create_toolchain_button.png)](https://console.ng.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2FIBM%2Facme-freight.git&cm_mmc=github-readme--native-_-acme-_-create-toolchain&cm_mmca1=000019RT&cm_mmca2=10004796)

시작하려면, Create Toolchain 버튼을 클릭합니다. Bluemix에 로그인합니다. - 아직 계정이 없으시다면, 30일 무료 체험판에 가입합니다. 로그인하면 툴체인을 생성하기 위한 개별 설정을 하기 위한 창이 제공됩니다. 아래 단계를 따라합니다:

1. 맨 위에 있는 여러분의 툴체인 이름부터 `acme-freight-toolchain-XXX`같은 식으로 변경합니다. URL 경로는 앱 이름으로 결정된다는 점에 유의하여, 고유한 이름을 고릅니다.
1. `GitHub` 탭에서 "Track Deployment of Code Changes" 을 선택하면 모든 GitHub 저장소의 코드 변경을 추적합니다.
1. `Delivery Pipeline` 탭을 클릭하고
    * 애플리케이션 이름을 개별 설정합니다. 가령 ERP 앱은 Acme-Freight-ERP라고 입력하는 식으로요.
    * OpenWhisk Authorization 키를 검색합니다: https://console.ng.bluemix.net/openwhisk/cli (권한 키 정보는 `네임스페이스 및 권한 키`섹션의 "--auth" 다음에 위치합니다)
    * 해당 OpenWhisk Authorization 키를 해당 필드에 복사하여 붙입니다.
1. `Create`을 클릭합니다


15분 정도면, 마이크로서비스의 배포가 끝나고 여러분은 자신만의 Acme Freight 인스턴스를 엑세스할 수 있습니다. [Bluemix 대시보드](https://console.ng.bluemix.net/dashboard/apps/)로 이동하여 애플리케이션의 상태를 확인하고 엑세스합니다. 

앱을 확장하거나 변경하려면, 여러분에게 포크된 GitHub 저장소에 변경 사항을 푸쉬합니다. 배포된 툴체인 파이프라인이 알아서 나머지 처리를 완료합니다.
