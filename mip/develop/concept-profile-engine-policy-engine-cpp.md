---
title: 개념 - 정책 API 엔진 개체
description: 이 문서는 애플리케이션 초기화 중에 생성된 정책 엔진 개체의 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07e0fc59e0ed5ec1fc66fe3179fce07dfcb687d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445277"
---
# <a name="microsoft-information-protection-sdk---policy-api-engine-concepts"></a>Microsoft Information Protection SDK - 정책 API 엔진 개념

`mip::PolicyEngine`은 프로필 로드를 제외하고 정책 API가 수행할 수 있는 모든 작업을 구현합니다. 

## <a name="implementation-add-a-policy-engine"></a>구현: 정책 엔진 추가

### <a name="implementation-create-policy-engine-settings"></a>구현: 정책 엔진 설정 만들기

프로필과 유사하게, 엔진에는 설정 개체인 `mip::PolicyEngine::Settings`도 필요합니다. 이 개체는 고유한 엔진 식별자, 디버깅 또는 원격 분석에 사용할 수 있는 사용자 지정 가능한 클라이언트 데이터 및 선택적으로 로캘을 저장합니다.

여기서는 *engineSettings*라는 `PolicyEngine::Settings` 개체를 만듭니다.

```cpp
PolicyEngine::Settings engineSettings("UniqueID", "");
```

첫 번째 매개 변수인 **id**는 엔진이 관련 사용자에 쉽게 연결할 수 있도록 하는 것이어야 하며, 사용자 계정 이름을 사용하는 것이 좋습니다.

### <a name="implementation-add-the-policy-engine"></a>구현: 정책 엔진 추가

엔진을 추가하기 위해 프로필을 로드하는 데 사용되는 future/promise 패턴으로 돌아가겠습니다. `mip::Profile`에 대한 promise를 만드는 대신 `mip::PolicyEngine`을 사용할 것입니다.

```cpp

  //auto profile will be std::shared_ptr<mip::Profile>
  auto profile = profileFuture.get();

  //Create the PolicyEngine::Settings object
  PolicyEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::PolicyEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::PolicyEngine>
  auto engine = engineFuture.get();
```

위 코드의 최종 결과는 인증된 사용자의 엔진을 프로필에 성공적으로 추가했음을 나타냅니다.

## <a name="implementation-list-sensitivity-labels"></a>구현: 민감도 레이블 나열

추가된 엔진을 사용하면, 이제 `engine->ListSensitivityLabels()`를 호출하여 인증된 사용자가 사용할 수 있는 모든 민감도 레이블을 나열할 수 있습니다.

`ListSensitivityLabels()`는 특정 사용자에 대한 레이블 목록 및 해당 레이블의 특성을 서비스에서 가져옵니다. 결과는 `std::shared_ptr<mip::Label>`의 벡터에 저장됩니다.

### <a name="implementation-listsensitivitylabels"></a>구현: ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

### <a name="implementation-print-the-labels"></a>구현: 레이블 인쇄

```cpp
//Iterate through all labels in the vector
for (const auto& label : labels) {
  //print the label name
  cout << label->GetName() << endl;
  //Iterate through all child labels
  for (const auto& child : label->GetChildren()) {
    //Print the label with some formatting
    cout << "->  " << child->GetName() << endl;
  }
}
```

이름을 인쇄하면 서비스에서 정책을 성공적으로 끌어왔으며 레이블을 가져올 수 있었음을 쉽게 보여 줄 수 있습니다. 레이블을 적용하려면 레이블 식별자가 필요합니다. 레이블 ID 결과가 다음 위치에 반환되도록 위의 조각 수정:

```cpp
for (const auto& label : labels) {
  //Print label name and GUID
  cout << label->GetName() << " : " << label->GetId() << endl;

  //Print child label name and GUID
  for (const auto& child : label->GetChildren()) {    
    cout << "->  " << child->GetName() <<  " : " << child->GetId() << endl;
  }
}
```

`GetSensitivityLabels()`에서 반환된 `mip::Label` 컬렉션을 사용하여 사용자가 사용할 수 있는 모든 레이블을 표시한 다음, 선택되면 ID를 사용하여 파일에 레이블을 적용할 수 있습니다.

