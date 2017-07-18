# Acme Freight 둘러보기

이번 편에서는 https://acme-freight.mybluemix.net/ 에 있는 공유 실행 환경을 사용하거나 [툴체인](https://github.com/IBM/acme-freight/blob/master/TOOLCHAIN-README-ko.md)을 사용해 배포된 여러분 자신의 환경을 사용할 수도 있습니다.

이제 여러분을 공급망 관리 매니저라고 가정하겠습니다. 여러분은 여러 물류센터, 소매점과 여러 배송 업무를 소유한 세계적 규모의 유통 회사에서 근무하고 있습니다.  

1. 웹브라우저를 통해 해당 홈페이지로 이동합니다, https://acme-freight.mybluemix.net/ 또는 당신의 *webui* 앱의 url을 활용합니다.

  > webui의 소스 코드는 [여기](https://github.com/ibm/acme-freight-webui)에서 확인하실 수 있습니다.

1. 이 홈페이지는 포털 형태로 이번 설명편의 시작점이기도 합니다. 

1. **LOGIN TO ACME FREIGHT**를 클릭하십시오.

  > 만약 여러분이 실제로 이 회사의 직원이라면 애플리케이션에 로그인할 신임정보가 있겠지만, 이것은 예제이므로 아무런 신임정보가 필요하지 않습니다. 그래서 대신, 여러분이 이 버튼만 클릭하면 임의의 데이터세트로 구성된 독립된 환경을 자동 생성하도록 만들었습니다. 매번 버튼을 클릭하실 때마다 이 환경은 동일합니다. 다른 사용자의 액션에 영향을 받지 않고 마음껏 실행하실 수 있습니다. 

1. 대시보드에는 현재 진행 중인 배송건이 지도에 표시되어 공급망 매니저가 관련 정보를 한 눈에 파악할 수 있습니다.

  > 물류센터, 소매점, 배송 정보는 [the controller](https://github.com/ibm/acme-freight-controller)를 통해 [ERP 시뮬레이터](https://github.com/ibm/acme-freight-erp)에서 가져온 것입니다.

1. 물류센터를 고르면, 해당 물류센터에서 출고되는 배송건을 보여줍니다. 

1. 소매점을 고르면, 이 지역의 날씨와 입하되는 배송건을 보여줍니다.

  > 기상 정보는 [the recommendation service](https://github.com/ibm/acme-freight-recommendation)에 정의된 OpenWhisk액션을 호출하는 [controller](https://github.com/ibm/acme-freight-controller)를 통해 가져옵니다.

1. 배송을 선택하면, 현재 위치와 그 위치의 날씨를 확인할 수 있습니다.

1. 자세히보기 창을 닫으십시오.

1. 지도에 **Simulate Storm** 버튼이 있습니다. 우리가 날씨를 바꿀 수는 없지만, 시뮬레이션을 통해 해당 기상 정보가 추천 서비스에 입력되면 새로운 배송 추천안이 생성됩니다.

1. **Simulate Storm** 버튼을 누릅니다.

  > 버튼을 누르면 [the recommendation service](https://github.com/ibm/acme-freight-recommendation)는 폭풍우라는 이벤트에 맞는 배송 추천안을 생성하는 OpenWhisk 액션을 호출합니다.

1. 잠시 기다리면 경고창이 나타나며 지도가 업데이트 되어 폭풍우의 영향권에 해당되는 지역을 보여줍니다.

1. 지도에서 폭풍권에 속하는 지역을 선택합니다.

1. 폭풍우 정보를 보여주는 패널이 디스플레이됩니다. 기상 조건과 추가적인 배송 추천안을 확인할 수 있습니다.

1. 공급망 관리 매니저로서 여러분은 배송 추천안을 선택하거나 거절할 수 있습니다.

1. 한 개의 배송안을 승인하고, 다른 것은 거절합니다.

  > 승인과 거절된 2개의 추천 배송안은 [the recommendation service](https://github.com/ibm/acme-freight-recommendation)의 2가지 다른 OpenWhisk 액션입니다.

1. 자세히 보기 창에서 추천안이 사라집니다.
