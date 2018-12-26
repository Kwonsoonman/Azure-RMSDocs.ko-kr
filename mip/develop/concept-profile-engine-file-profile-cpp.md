---
title: 개념 - 파일 API 프로필 개체
description: 이 문서는 애플리케이션 초기화 중에 생성된 File 프로필 개체의 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 33ec266068d15e827267b7d518344aebd0f8f072
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445906"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>Microsoft Information Protection SDK - 파일 API 프로필 개념

프로필은 MIP SDK의 모든 작업에 대한 루트 클래스입니다. 파일 API 기능을 사용하기 전에 `FileProfile`을 만들어야 하며, 이후의 모든 작업은 프로필 또는 프로필에 ‘추가’된 다른 개체에 의해 수행됩니다.

프로필을 인스턴스화하기 전에 충족해야 하는 몇 가지 코드 필수 조건이 있습니다.

- `AuthDelegateImpl`은 `mip::AuthDelegate`를 확장하도록 구현되었습니다.
- `ConsentDelegateImpl`은 `mip::ConsentDelegate`를 확장하도록 구현되었습니다.
- 애플리케이션이 [Azure Active Directory에 등록](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md)되었으며 클라이언트 ID가 애플리케이션 또는 구성 파일에 하드 코드되었습니다. 
- `mip::FileProfile::Observer`를 상속하는 클래스가 적절하게 구현되었습니다.

## <a name="load-a-profile"></a>프로필 로드

`ProfileObserver`, `ConsentDelegateImpl` 및 `AuthDelegateImpl`이 정의되었으므로 이제 `mip::FileProfile`을 인스턴스화할 수 있습니다. `mip::FileProfile` 개체를 만들려면 `FileProfile`에 대한 모든 설정 정보를 저장할 [`mip::FileProfile::Settings`](reference/class_mip_fileprofile_settings.md)가 필요합니다.

### <a name="fileprofilesettings-parameters"></a>FileProfile::Settings 매개 변수

`FileProfile::Settings` 생성자는 아래에 나열된 다섯 개의 매개 변수를 허용합니다.

- `std::string path`: 로깅, 원격 분석 및 기타 영구 상태가 저장되는 파일 경로입니다.
- `bool useInMemoryStorage`: 모든 상태가 메모리(디스크가 아닌)에 저장되어야 하는지 여부를 정의합니다.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: `mip::AuthDelegate` 클래스의 공유 포인터입니다. 
- `std::shared_ptr<mip::ConsentDelegate>`: 
- `std::shared_ptr<mip::FileProfile::Observer> observer`: `FileProfile::Observer` 구현에 대한 공유 포인터입니다.
- `mip::ApplicationInfo applicationInfo`: 개체입니다. SDK를 사용 중인 애플리케이션에 관한 정보를 정의하는 데 사용됩니다.

다음 예제에서는 메모리 내뿐만 아니라 상태 저장소에 로컬 저장소를 사용하여 `profileSettings` 개체를 만드는 방법을 보여 줍니다. 둘 다 `authDelegateImpl` 개체가 이미 생성되었다고 가정합니다.

#### <a name="store-state-in-memory-only"></a>메모리에만 상태 저장

```cpp
FileProfile::Settings profileSettings(
    "",                                          //path to store settings
    true,                                        //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>디스크의 저장소 경로에서 프로필 설정 읽기/쓰기

다음 코드 조각은 모든 앱 상태 데이터를 `./mip_app_data`에 저장하도록 `FileProfile`에 지시합니다.

```cpp
FileProfile::Settings profileSettings(
    "./mip_app_data",                            //path to store settings
    false,                                       //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="load-the-profile"></a>프로필 로드

위의 접근 방법 중 하나를 사용하여 이제 promise/future 패턴을 통해 `FileProfile`을 로드합니다.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<FileProfile>>>();
auto profileFuture = profilePromise->get_future();
FileProfile::LoadAsync(profileSettings, profilePromise);
```

프로필을 로드했으며 해당 작업이 성공했으면 `mip::FileProfile::Observer::OnLoadSuccess` 구현인 `ProfileObserver::OnLoadSuccess`가 호출됩니다. 결과 개체 또는 예외 포인터와 컨텍스트는 함수에 매개 변수로 전달됩니다. context는 비동기 작업을 처리하기 위해 만든 `std::promise`에 대한 포인터입니다. 함수는 promise의 값을 첫 번째 매개 변수에 대해 전달된 FileProfile 개체로 설정합니다. main 함수가 `Future.get()`을 사용하는 경우 결과를 새 개체에 저장할 수 있습니다.

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

    FileProfile::Settings profileSettings("",
            false,
            authDelegateImpl,
            std::make_shared<ConsentDelegateImpl>(),
            std::make_shared<ProfileObserver>(),
            mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
    auto profileFuture = profilePromise->get_future();
    FileProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

최종 결과로, 프로필을 성공적으로 로드했으며 `profile`이라는 개체에 저장했습니다.

## <a name="next-steps"></a>다음 단계

이제 프로필이 추가되었으므로 다음 단계는 프로필에 엔진을 추가하는 것입니다. 

- [파일 엔진 개념](concept-profile-engine-file-engine-cpp.md)