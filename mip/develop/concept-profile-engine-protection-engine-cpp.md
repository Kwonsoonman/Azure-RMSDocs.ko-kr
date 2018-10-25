---
title: 개념 - 보호 API 엔진 개체
description: 이 문서는 응용 프로그램 초기화 중에 생성된 보호 엔진 개체의 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: da0c50de6a818fcd8beda0483696ba433ce22149
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453319"
---
# <a name="microsoft-information-protection-sdk---protection-api-engine-concepts"></a>Microsoft Information Protection SDK - 보호 API 엔진 개념

## <a name="implementation-add-a-protection-engine"></a>구현: 보호 엔진 추가

파일 API에서 `mip::ProtectionProfile` 클래스는 모든 SDK 작업의 루트 클래스입니다. 프로필을 이미 만들었으므로 이제 프로필에 엔진을 추가할 수 있습니다.

아래 예제는 단일의 인증된 사용자에 대해 단일 엔진을 사용하는 방법을 보여 줍니다.

### <a name="implementation-create-protection-engine-settings"></a>구현: 보호 엔진 설정 만들기

프로필과 유사하게, 엔진에는 설정 개체인 `mip::ProtectionEngine::Settings`도 필요합니다. 이 개체는 고유한 엔진 식별자, 디버깅 또는 원격 분석에 사용할 수 있는 사용자 지정 가능한 클라이언트 데이터 및 선택적으로 로캘을 저장합니다.

여기서는 *engineSettings*라는 `ProtectionEngine::Settings` 개체를 만듭니다. 

```cpp
ProtectionEngine::Settings engineSettings("UniqueID", "");
```

**참고**: 이 방법을 사용하여 보호 설정 개체를 만드는 경우 CloudEndpointBaseUrl도 https://api.aadrm.com으로 수동 설정해야 합니다.

첫 번째 매개 변수인 **id**는 엔진이 관련 사용자에 쉽게 연결할 수 있게 하는 것**이거나** `mip::Identity` 개체인 것이 가장 좋습니다. `mip::Identity`로 설정을 초기화하려면 다음을 수행합니다.

```cpp
ProtectionEngine::Settings engineSettings(mip::Identity("Bob@Contoso.com", "");
```

일반적으로는 하드 코드가 아닌 ID에 변수를 전달합니다.

### <a name="implementation-add-the-protection-engine"></a>구현: 보호 엔진 추가

엔진을 추가하기 위해 프로필을 로드하는 데 사용되는 future/promise 패턴으로 돌아가겠습니다. `mip::ProtectionProfile`에 대한 promise를 만드는 대신 `mip::ProtectionEngine`을 사용할 것입니다.

```cpp

  //auto profile will be std::shared_ptr<mip::ProtectionProfile>
  auto profile = profileFuture.get();

  //Create the ProtectionEngine::Settings object
  ProtectionEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::ProtectionEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::ProtectionEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::ProtectionEngine>
  auto engine = engineFuture.get();
```

위 코드의 최종 결과는 인증된 사용자의 엔진을 프로필에 성공적으로 추가했음을 나타냅니다.

## <a name="implementation-list-templates"></a>구현: 템플릿 나열

추가된 엔진을 사용하면, 이제 `engine->GetTemplatesAsync()`를 호출하여 인증된 사용자가 사용할 수 있는 모든 민감도 템플릿을 나열할 수 있습니다. 

`GetTemplatesAsync()`는 템플릿 식별자 목록을 가져옵니다. 결과는 `std::shared_ptr<std::string>`의 벡터에 저장됩니다.

### <a name="implementation-listsensitivitytemplates"></a>구현: ListSensitivityTemplates()

```cpp
auto loadPromise = std::make_shared<std::promise<shared_ptr<vector<string>>>>();
std::future<std::shared_ptr<std::vector<std::string>>> loadFuture = loadPromise->get_future();
mEngine->GetTemplatesAsync(engineObserver, loadPromise);
auto templates = loadFuture.get();
```

### <a name="implementation-print-the-template-ids"></a>구현: 템플릿 ID 인쇄

```cpp
//Iterate through all template IDs in the vector
for (const auto& temp : *templates) {
  cout << "Template:" << "\n\tId: " << temp << endl;
}
```

이름을 인쇄하면 서비스에서 정책을 성공적으로 끌어왔으며 템플릿을 가져올 수 있었음을 쉽게 보여 줄 수 있습니다. 템플릿을 적용하려면 템플릿 식별자가 필요합니다.

레이블에 템플릿을 매핑하는 작업은 `ComputeActions()`의 결과를 검사하여 정책 API를 통해서만 수행할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이제 프로필이 로드되었고, 엔진이 추가되었으며, 템플릿이 있으므로 파일의 템플릿을 읽거나 쓰거나 제거하기 위한 처리기를 추가할 수 있습니다. [보호 처리기 개념](concept-handler-protection-cpp.md)을 참조하세요.