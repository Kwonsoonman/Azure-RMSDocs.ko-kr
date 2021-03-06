---
title: 개념 - 정책 API 프로필 개체
description: 이 문서는 응용 프로그램 초기화 중에 생성된 Policy 프로필 개체의 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b229148c3028f4478f83cbbc928e19666c2f44b5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445430"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>Microsoft Information Protection SDK - 정책 API 프로필 개념

`mip::Profile`을 먼저 로드해야 정책 API 작업을 수행할 수 있습니다.

아래 두 예제에서는 메모리 내뿐만 아니라 상태 저장소에 로컬 저장소를 사용하여 profileSettings 개체를 만드는 방법을 보여 줍니다. 둘 다 `authDelegateImpl` 개체가 이미 생성되었다고 가정합니다.

## <a name="load-a-profile"></a>프로필 로드

이제 `ProfileObserver` 및 `AuthDelegateImpl`이 정의되었으므로 `mip::PolicyProfile`을 인스턴스화하는 데 사용하겠습니다. `mip::PolicyProfile` 개체를 만들려면 [`mip::PolicyProfile::Settings`](reference/class_mip_PolicyProfile_settings.md)가 필요합니다.

### <a name="profilesettings-parameters"></a>Profile::Settings 매개 변수

- `std::string path`: 로깅, 원격 분석 및 기타 영구 상태가 저장되는 파일 경로입니다.
- `bool useInMemoryStorage`: 모든 상태가 메모리(디스크가 아닌)에 저장되어야 하는지 여부를 정의합니다.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: `mip::AuthDelegate` 클래스의 공유 포인터입니다. 
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: `PolicyProfile::Observer` 구현에 대한 공유 포인터입니다.
- `mip::ApplicationInfo applicationInfo`: 개체입니다. SDK를 사용 중인 응용 프로그램에 관한 정보를 정의하는 데 사용됩니다.

아래 두 예제에서는 메모리 내뿐만 아니라 상태 저장소에 로컬 저장소를 사용하여 profileSettings 개체를 만드는 방법을 보여 줍니다. 둘 다 `authDelegateImpl` 개체가 이미 생성되었다고 가정합니다.

#### <a name="store-state-in-memory-only"></a>메모리에만 상태 저장

```cpp
Profile::Settings profileSettings("",
    true,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>디스크의 저장소 경로에서 프로필 설정 읽기/쓰기

```cpp
Profile::Settings profileSettings("./mip_app_data",
    false,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

다음으로, promise/future 패턴을 사용하여 `Profile`을 로드합니다.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<Profile>>>();
auto profileFuture = profilePromise->get_future();
Profile::LoadAsync(profileSettings, profilePromise);
```

프로필이 성공적으로 로드되면 `mip::Profile::Observer::OnLoadSuccess` 구현인 `ProfileObserver::OnLoadSuccess`에 알립니다. 결과 개체(이 예제에서는 `mip::Profile`) 및 컨텍스트는 관찰자 함수에 매개 변수로 전달됩니다.

*context*는 비동기 작업을 처리하기 위해 만든 `std::promise`에 대한 포인터입니다. 함수는 promise의 값을 첫 번째 매개 변수에 대해 전달된 Profile 개체로 설정합니다. main 함수가 `Future.get()`을 사용하는 경우 결과를 호출 스레드의 새 개체에 저장할 수 있습니다.

```cpp
//get the future value and store in profile. 
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>정리

관찰자 및 인증 대리자를 완전히 구현했으면 이제 프로필을 완전히 로드할 수 있습니다. 아래 코드 조각에서는 필요한 헤더가 이미 모두 포함되었다고 가정합니다.

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    Profile::Settings profileSettings("", false, authDelegateImpl, std::make_shared<ProfileObserver>(), mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<Profile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

최종 결과로, 프로필을 성공적으로 로드했으며 `profile`이라는 개체에 저장했습니다.

## <a name="next-steps"></a>다음 단계

이제 프로필이 추가되었으므로 다음 단계는 프로필에 엔진을 추가하는 것입니다.

[정책 엔진 개념](concept-profile-engine-policy-engine-cpp.md)