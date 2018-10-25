---
title: 개념 - MIP SDK의 정책 API 관찰자.
description: MIP SDK는 거의 완전히 비동기로 설계되었습니다. 이 문서는 정책 API 관찰자가 구현되고 비동기에 사용되는 방법을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 50bc3bfd9bcba8e90a386a6e0444f65389bcfa76
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445804"
---
# <a name="microsoft-information-protection-sdk---policy-api-observers"></a>Microsoft Information Protection SDK - 정책 API 관찰자

정책 API SDK에는 하나의 관찰자 클래스가 있습니다. 관찰자 멤버는 가상이며 비동기 작업의 콜백을 처리하도록 재정의해야 합니다.

- [`mip::PolicyProfile::Observer`](reference/class_mip_policyprofile_observer.md)

비동기 작업이 완료되면 결과에 해당하는 `OnXxx()` 멤버 함수가 호출됩니다. `mip::Profile::Observer`의 경우 `OnLoadSuccess()`, `OnLoadFailure()` 및 `OnAddEngineSuccess()`를 예로 들 수 있습니다.

아래 예제에서는 SDK 샘플에서도 사용되는 promise/future 패턴을 보여 주며, 원하는 콜백 동작을 구현하기 위해 확장할 수 있습니다. 

## <a name="profile-observer-implementation"></a>프로필 관찰자 구현

다음 예제에서는 `mip::Profile::Observer`에서 파생된 `ProfileObserver` 클래스를 만들었습니다. 멤버 함수는 샘플 전체에서 사용되는 future/promise 패턴을 사용하도록 재정의되었습니다.

**참고**: 아래 샘플은 부분적으로만 구현되었으며 `mip::ProfileEngine` 관련 관찰자에 대한 재정의를 포함하지 않습니다.

### <a name="profileobserverh"></a>profile_observer.h

헤더에서 `mip::Profile::Observer`에서 파생하여 `ProfileObserver`를 정의한 다음, 각 멤버 함수를 재정의합니다.

```cpp
class ProfileObserver final : public mip::Profile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement remaining members
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

구현 자체에서 각 관찰자 멤버 함수에 대해 수행할 작업을 정의합니다.

각 멤버는 두 개의 매개 변수를 허용합니다. 첫 번째는 함수에서 처리하는 클래스에 대한 공유 포인터입니다. `ProfileObserver::OnLoadSuccess`는 `mip::Profile`을 받을 것으로 예상합니다. `ProfileObserver::OnAddEngineSuccess`는 `mip::ProfileEngine`을 예상합니다.

두 번째는 *context*에 대한 공유 포인터입니다. 이 구현에서 컨텍스트는 `shared_ptr<void>`로 전달된 `std::promise`에 대한 참조입니다. 함수의 첫째 줄에서 이 컨텍스트를 `std::promise`로 캐스트한 다음, `promise`라는 개체에 저장합니다.

마지막으로, `promise->set_value()`를 설정하고 `mip::Profile` 개체를 전달하여 future를 준비합니다.

```cpp
#include "profile_observer.h"
#include <future>

//Called when Profile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when Profile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement remaining observer members
```

비동기 작업을 수행할 때 관찰자 구현은 설정 생성자 또는 비동기 함수 자체에 전달됩니다. 

