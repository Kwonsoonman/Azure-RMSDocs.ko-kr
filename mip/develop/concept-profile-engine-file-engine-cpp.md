---
title: 개념 - 파일 API 엔진 개체
description: 이 문서는 응용 프로그램 초기화 중에 만들어지는 파일 엔진 개체의 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9ccea755c83b570aa17ff4d30d98783f4bef79e5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446603"
---
# <a name="microsoft-information-protection-sdk---file-api-engine-concepts"></a>Microsoft Information Protection SDK - 파일 API 엔진 개념

MIP SDK 파일 API의 `mip::FileEngine`은 지정된 ID를 대신하여 수행되는 모든 작업을 위한 인터페이스를 제공합니다. 응용 프로그램에 로그인하는 사용자별로 엔진이 하나씩 추가되고, 이 엔진이 수행하는 모든 작업은 해당 ID의 컨텍스트에서 수행됩니다.

`FileEngine`은 인증된 사용자의 레이블을 나열하고 사용자를 대신하여 파일 작업을 수행하는 파일 처리기를 만드는 등 두 가지 기본적인 역할을 담당합니다. 

- [`mip::FileEngine`](reference/class_mip_fileengine.md)
- `ListSensitivityLabels()`: 로드된 엔진의 레이블 목록을 가져옵니다.
- `CreateFileHandler()`: 특정 파일 또는 스트림의 `mip::FileHandler`를 만듭니다.

## <a name="add-a-file-engine"></a>파일 엔진 추가

[프로필 및 엔진 개체](concept-profile-engine-cpp.md)의 설명대로, 엔진은 `CREATED` 또는 `LOADED`의 두 상태를 가질 수 있습니다. 이 두 상태 중 하나가 아니면 엔진은 존재하지 않습니다. 상태를 작성하고 로드하려면 `FileProfile::LoadAsync`에 대해 단일 호출을 만들기만 하면 됩니다. 엔진이 이미 캐시된 상태로 존재하는 경우 상태는 `LOADED`입니다. 엔진이 존재하지 않는 경우 `CREATED` 및 `LOADED`입니다. `CREATED`는 응용 프로그램이 엔진을 로드하는 데 필요한 서비스의 모든 정보를 가지고 있음을 의미합니다. `LOADED`는 엔진을 활용하는 데 필요한 모든 데이터 구조가 메모리에 생성되었음을 의미합니다.

### <a name="create-file-engine-settings"></a>파일 엔진 설정 만들기

프로필과 유사하게, 엔진에는 설정 개체인 `mip::FileEngine::Settings`도 필요합니다. 이 개체는 고유한 엔진 식별자, 디버깅 또는 원격 분석에 사용할 수 있는 사용자 지정 가능한 클라이언트 데이터 및 선택적으로 로캘을 저장합니다.

여기서는 *engineSettings*라는 `FileEngine::Settings` 개체를 만듭니다. 

```cpp
FileEngine::Settings engineSettings("UniqueID", "");
```

첫 번째 매개 변수인 `id`는 엔진이 관련 사용자에 쉽게 연결할 수 있도록 하는 것이어야 합니다. 메일 주소, UPN, AAD 개체 GUID 등은 ID가 고유하며 서비스를 호출하지 않고 로컬 상태에서 로드될 수 있는지 확인합니다.

### <a name="add-the-file-engine"></a>파일 엔진 추가

엔진을 추가하기 위해 프로필을 로드하는 데 사용되는 promise/future 패턴으로 돌아가겠습니다. `mip::FileProfile`에 대해 promise를 생성하는 대신 `mip::FileEngine`을 사용하여 생성합니다.

```cpp
  //auto profile will be std::shared_ptr<mip::FileProfile>
  auto profile = profileFuture.get();

  //Create the FileEngine::Settings object
  FileEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::FileEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::FileEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::FileEngine>
  auto engine = engineFuture.get();
```

위 코드의 최종 결과는 인증된 사용자의 엔진이 프로필에 추가되는 것입니다.

## <a name="list-sensitivity-labels"></a>민감도 레이블 나열

추가된 엔진을 사용하면, 이제 `engine->ListSensitivityLabels()`를 호출하여 인증된 사용자가 사용할 수 있는 모든 민감도 레이블을 나열할 수 있습니다.

`ListSensitivityLabels()`는 특정 사용자에 대한 레이블 목록 및 해당 레이블의 특성을 서비스에서 가져옵니다. 결과는 `std::shared_ptr<mip::Label>`의 벡터에 저장됩니다.

[여기]()에서 `mip::Label`에 대한 자세한 내용을 확인할 수 있습니다.

### <a name="listsensitivitylabels"></a>ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

또는 다음과 같이 단순화합니다.

```cpp
auto labels = engine->ListSensitivityLabels();
```

### <a name="print-the-labels-and-ids"></a>레이블 및 ID 인쇄

이름을 인쇄하면 서비스에서 정책을 성공적으로 끌어왔으며 레이블을 가져올 수 있었음을 쉽게 보여 줄 수 있습니다. 레이블을 적용하려면 레이블 식별자가 필요합니다. 아래 코드는 모든 레이블을 반복하여 각 부모 및 자식 레이블의 `name` 및 `id`를 표시합니다.

```cpp
//Iterate through all labels in the vector
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

## <a name="next-steps"></a>다음 단계

이제 프로필이 로드되었고, 엔진이 추가되었으며, 레이블이 있으므로 파일의 레이블을 읽거나 쓰거나 제거하기 위한 처리기를 추가할 수 있습니다. [MIP SDK의 파일 처리기](concept-handler-file-cpp.md)를 참조하세요.

