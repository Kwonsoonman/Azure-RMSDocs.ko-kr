---
title: 빠른 시작 - MIP(Microsoft Information Protection) SDK C++ 클라이언트 초기화
description: MIP(Microsoft Information Protection) SDK 클라이언트 응용 프로그램의 초기화 논리를 쓰는 방법을 보여 주는 빠른 시작입니다.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 578c5aa69faa986663ea6c164d94e5940580167d
ms.sourcegitcommit: 76e1b7c0255700813590be62d94b19338bf6c201
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48866139"
---
# <a name="quickstart-client-application-initialization-c"></a>빠른 시작: 클라이언트 응용 프로그램 초기화(C++)

이 빠른 시작은 런타임 시 MIP C++ SDK에 사용되는 클라이언트 초기화 패턴을 구현하는 방법을 보여 줍니다. 

> [!NOTE]
> 이 빠른 시작에 요약된 단계는 MIP 파일, 정책 또는 보호 API를 사용하는 모든 클라이언트 응용 프로그램에 필요합니다. 이 빠른 시작은 파일 API의 사용법을 보여 주지만, 정책 및 보호 API를 사용하여 클라이언트에 동일한 패턴을 적용할 수 있습니다. 이 빠른 시작 작업부터 시작하여 각 빠른 시작 작업이 이전 작업을 토대로 구축되므로 이후 빠른 시작 작업은 순차적으로 수행해야 합니다.

## <a name="prerequisites"></a>전제 조건

다음 작업을 아직 완료하지 않은 경우 먼저 수행합니다.

- [MIP(Microsoft Information Protection) SDK 설정 및 구성](setup-configure-mip.md)의 단계를 완료합니다. 이 “클라이언트 응용 프로그램 초기화” 빠른 시작을 위해서는 먼저 SDK 설정 및 구성을 적절히 진행해야 합니다.
- 필요할 경우 다음을 선택합니다.
  - [프로필 및 엔진 개체](concept-profile-engine-cpp.md)를 검토합니다. 프로필 및 엔진 개체는 MIP 파일/정책/보호 API를 사용하는 클라이언트에 필요한 유니버설 개념입니다. 
  - [인증 개념](concept-authentication-cpp.md)을 검토하여 SDK 및 클라이언트 응용 프로그램에서 인증 및 동의를 구현하는 방법을 알아봅니다.
  - [관찰자 개념](concept-async-observers.md)을 검토하여 관찰자와 구현 방식에 대해 자세히 알아봅니다. MIP SDK는 관찰자 패턴을 사용하여 비동기 이벤트 알림을 구현합니다.

## <a name="create-a-visual-studio-solution-and-project"></a>Visual Studio 솔루션 및 프로젝트 만들기

먼저 다른 빠른 시작의 구축 기반이 되는 초기 Visual Studio 솔루션 및 프로젝트를 만들고 구성합니다. 

1. Visual Studio 2017을 열고 **파일** 메뉴, **새로 만들기**, **프로젝트**를 선택합니다. **새 프로젝트** 대화 상자에서 다음을 수행합니다.
   - 왼쪽 창의 **설치됨**, **기타 언어**에서 **Visual C++** 를 선택합니다.
   - 가운데 창에서 **Windows 콘솔 응용 프로그램**을 선택합니다.
   - 아래쪽 창에서 프로젝트 **이름**, **위치** 및 포함된 **솔루션 이름**을 적절하게 업데이트합니다.
   - 완료되면 오른쪽 아래의 **확인** 단추를 클릭합니다.

     [![Visual Studio 솔루션 만들기](media/quick-app-initialization-cpp/create-vs-solution.png)](media/quick-app-initialization-cpp/create-vs-solution.png#lightbox)

2. MIP SDK 파일 API의 Nuget 패키지를 다음과 같이 프로젝트에 추가합니다.
   - **솔루션 탐색기**에서 프로젝트 노드(위쪽/솔루션 노드 바로 아래에 있음)를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...** 를 선택합니다.
   - **NuGet 패키지 관리자** 탭이 편집기 그룹 탭 영역에서 열리면 다음을 수행합니다.
     - **찾아보기**를 선택합니다.
     - 검색 상자에 “Microsoft.InformationProtection”을 입력합니다.
     - “Microsoft.InformationProtection.File” 패키지를 선택합니다.
     - “설치”를 클릭하고 **미리 보기 변경** 확인 대화 상자가 표시되면 “확인”을 클릭합니다.
   
     [![Visual Studio에서 NuGet 패키지 추가](media/quick-app-initialization-cpp/add-nuget-package.png)](media/quick-app-initialization-cpp/add-nuget-package.png#lightbox)
 
## <a name="implement-an-observer-class-to-monitor-the-file-profile-and-engine-objects"></a>파일 프로필 및 엔진 개체를 모니터링하기 위한 Observer 클래스 구현

이제 SDK의 `mip::FileProfile::Observer` 클래스를 확장하여 파일 프로필 Observer 클래스에 대한 기본 구현을 만듭니다. Observer는 인스턴스화된 후, 나중에 파일 프로필 개체의 로드와 엔진 개체의 프로필 추가를 모니터링하는 데 사용됩니다.

1. 헤더/.h 및 구현/.cpp 파일을 둘 다 생성하는 새 클래스를 프로젝트에 추가합니다.

   - **솔루션 탐색기**에서 프로젝트 노드를 다시 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 후 **클래스**를 선택합니다.
   - **클래스 추가** 대화 상자에서 다음을 수행합니다.
     - **클래스 이름** 필드에 “profile_observer”를 입력합니다. **.h 파일** 및 **.cpp 파일** 필드가 입력한 이름을 기준으로 자동으로 채워집니다.
     - 완료되면 **확인** 단추를 클릭합니다.

     [![Visual Studio에서 클래스 추가](media/quick-app-initialization-cpp/add-class.png)](media/quick-app-initialization-cpp/add-class.png#lightbox)

2. 클래스에 대해 .h 및 .cpp 파일을 생성하면 두 파일이 편집기 그룹 탭에서 열립니다. 이제 각 파일을 업데이트하여 새 Observer 클래스를 구현합니다.

   - 생성된 `profile_observer` 클래스를 선택/삭제하여 “profile_observer.h”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 기존 전처리기 지시문 뒤에 다음 소스를 복사한 후 붙여넣습니다.

     ```cpp
     #include <memory>
     #include "mip/file/file_profile.h"

     class ProfileObserver final : public mip::FileProfile::Observer {
     public:
          ProfileObserver() { }
          void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
          void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
          void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context) override;
          void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
     };
     ```

   - 생성된 `profile_observer` 클래스 구현을 선택/삭제하여 “profile_observer.cpp”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 기존 전처리기 지시문 뒤에 다음 소스를 복사한 후 붙여넣습니다.

     ```cpp
     #include <future>

     using std::promise;
     using std::shared_ptr;
     using std::static_pointer_cast;
     using mip::FileEngine;
     using mip::FileProfile;

     void ProfileObserver::OnLoadSuccess(const shared_ptr<FileProfile>& profile, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_value(profile);
     }

     void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_exception(error);
     }

     void ProfileObserver::OnAddEngineSuccess(const shared_ptr<FileEngine>& engine, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_value(engine);
     }

     void ProfileObserver::OnAddEngineFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_exception(error);
     }
     ```

3. 경우에 따라 F6 키(**솔루션 빌드**)를 통해 솔루션의 테스트 컴파일/연결을 실행하여 성공적으로 빌드되는지 확인합니다.

## <a name="implement-an-authentication-delegate"></a>인증 대리자 구현

MIP SDK는 클라이언트 응용 프로그램과 인증 작업을 공유하는 메커니즘을 제공하는 클래스 확장성을 사용하여 인증을 구현합니다. 클라이언트는 적합한 OAuth2 액세스 토큰을 획득한 후 런타임에 MIP SDK에 제공해야 합니다. 

이제 SDK의 `mip::AuthDelegate` 클래스를 확장하고 `mip::AuthDelegate::AcquireOAuth2Token()` 순수 가상 함수를 재정의/구현하여 인증 대리자를 구현합니다. 인증 대리자는 인스턴스화된 후 나중에 파일 프로필 및 파일 엔진 개체에서 사용됩니다.

1. 이전 섹션의 1단계에서 사용한 것과 동일한 Visual Studio “클래스 추가” 기능을 사용하여 프로젝트에 다른 클래스를 추가합니다. 이번에는 **클래스 이름** 필드에 “auth_delegate”를 입력합니다. 

2. 이제 각 파일을 업데이트하여 새 인증 대리자 클래스를 구현합니다.

   - 생성된 모든 `auth_delegate` 클래스 코드를 다음 소스로 바꾸어 “auth_delegate.h”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**.

     ```cpp
     #include <string>
     #include "mip/common_types.h"

     class AuthDelegateImpl final : public mip::AuthDelegate {
     public:
          AuthDelegateImpl() = delete;        // Prevents default constructor
          
          AuthDelegateImpl(
            const std::string& appId)         // AppID for registered AAD app
            : mAppId(appId) {};

          bool AcquireOAuth2Token(            // Called by MIP SDK to get a token
            const mip::Identity& identity,    // Identity of the account to be authenticated, if known
            const OAuth2Challenge& challenge, // Authority (AAD tenant issuing token), and resource (API being accessed; "aud" claim).
            OAuth2Token& token) override;     // Token handed back to MIP SDK
     private:
          std::string mAppId;
          std::string mToken;
          std::string mAuthority;
          std::string mResource;
     };
     ```

   - 생성된 모든 `auth_delegate` 클래스 구현을 다음 소스로 바꾸어 “auth_delegate.cpp”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 

     > [!IMPORTANT]
     > 다음 토큰 획득 코드는 프로덕션 용도에 적합하지 않습니다. 프로덕션에서는 다음을 사용하여 토큰을 동적으로 확보하는 코드로 대체해야 합니다.
     > - Azure AD 앱 등록에 지정된 앱 ID 및 회신/리디렉션 URI(**회신/리디렉션 URI는**  앱 등록과 일치해야 함)
     > - `challenge` 인수에서 SDK가 제공한 권한 및 리소스 URL(리소스 URL은 앱 등록의 API/권한과 **반드시** 일치해야 함)
     > - 유효한 앱/사용자 자격 증명. 여기서 계정은 SDK에서 제공한 `identity` 인수와 일치합니다. OAuth2 “네이티브” 클라이언트는 사용자 자격 증명을 요구하며 “인증 코드” 흐름을 사용합니다. OAuth2 “기밀 클라이언트”는 “클라이언트 자격 증명” 흐름에서 고유한 보안 자격 증명을 사용하거나(예: 서비스), “인증 코드” 흐름을 사용하여 사용자 자격 증명을 요구할 수 있습니다(예: 웹앱). 
     >
     > OAuth2 토큰 획득은 복잡한 프로토콜이며 일반적으로 라이브러리를 사용하여 수행됩니다. TokenAcquireOAuth2Token()은 필요에 따라 MIP SDK**에 의해서만** 호출됩니다.

     ```cpp
     #include <iostream>
     using std::cout;
     using std::cin;
     using std::string;

     bool AuthDelegateImpl::AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) 
     {
          // Acquire a token manually, reuse previous token if same authority/resource. In production, replace with token acquisition code.
          string authority = challenge.GetAuthority();
          string resource = challenge.GetResource();
          if (mToken == "" || (authority != mAuthority || resource != mResource))
          {
              cout << "\nRun the PowerShell script to generate an access token using the following values, then copy/paste it below:\n";
              cout << "Set $authority to: " + authority + "\n";
              cout << "Set $resourceUrl to: " + resource + "\n";
              cout << "Sign in with user account: " + identity.GetEmail() + "\n";
              cout << "Enter access token: ";
              cin >> mToken;
              mAuthority = authority;
              mResource = resource;
              system("pause");
          }

          // Pass access token back to MIP SDK
          token.SetAccessToken(mToken);

          // True = successful token acquisition; False = failure
          return true;
     }
     ``` 
3. 경우에 따라 F6 키(**솔루션 빌드**)를 통해 솔루션의 테스트 컴파일/연결을 실행하여 성공적으로 빌드되는지 확인합니다.

## <a name="implement-a-consent-delegate"></a>동의 대리자 구현

이제 SDK의 `mip::ConsentDelegate` 클래스를 확장하고 `mip::AuthDelegate::GetUserConsent()` 순수 가상 함수를 재정의/구현하여 동의 대리자를 구현합니다. 동의 대리자는 인스턴스화된 후 나중에 파일 프로필 및 파일 엔진 개체에서 사용됩니다.

1. 이전에 사용한 것과 동일한 Visual Studio “클래스 추가” 기능을 사용하여 프로젝트에 다른 클래스를 추가합니다. 이번에는 **클래스 이름** 필드에 “consent_delegate”를 입력합니다. 

2. 이제 각 파일을 업데이트하여 새 동의 대리자 클래스를 구현합니다.

   - 생성된 모든 `consent_delegate` 클래스 코드를 다음 소스로 바꾸어 “consent_delegate.h”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**.

     ```cpp
     #include "mip/common_types.h"
     #include <string>

     class ConsentDelegateImpl final : public mip::ConsentDelegate {
     public:
          ConsentDelegateImpl() = default;
          virtual mip::Consent GetUserConsent(const std::string& url) override;
     };
     ```

   - 생성된 모든 `consent_delegate` 클래스 구현을 다음 소스로 바꾸어 “consent_delegate.cpp”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 

     ```cpp
     #include <iostream>
     using mip::Consent;
     using std::string;

     Consent ConsentDelegateImpl::GetUserConsent(const string& url) 
     {
          // Accept the consent to connect to the url
          std::cout << "SDK will connect to: " << url << std::endl;
          return Consent::AcceptAlways;
     }
     ``` 
3. 경우에 따라 F6 키(**솔루션 빌드**)를 통해 솔루션의 테스트 컴파일/연결을 실행하여 성공적으로 빌드되는지 확인합니다.

## <a name="construct-a-file-profile-and-engine"></a>파일 프로필 및 엔진 생성

앞서 언급한 것처럼 MIP API를 사용하는 SDK 클라이언트에는 프로필 및 엔진 개체가 필요합니다. 프로필 및 엔진 개체를 인스턴스화하는 코드를 추가하여 이 빠른 시작의 코딩 부분을 완료하세요. 

1. **솔루션 탐색기**의 프로젝트에서 `main()` 메서드의 구현이 포함된 .cpp 파일을 엽니다. 파일 이름은 프로젝트를 만드는 동안 지정한 프로젝트 이름과 같습니다.

2. 생성된 `main()` 구현을 제거합니다. 프로젝트를 만드는 동안 Visual Studio에서 생성된 전처리기 지시문(#pragma, #include)을 제거하지**마세요**. 전처리기 지시문 뒤에 다음 코드를 추가합니다.

   ```cpp
   #include "auth_delegate.h"
   #include "consent_delegate.h"
   #include "profile_observer.h"

   using std::promise;
   using std::future;
   using std::make_shared;
   using std::shared_ptr;
   using std::string;
   using std::cout;
   using mip::ApplicationInfo; 
   using mip::FileProfile;
   using mip::FileEngine;

   int main()
   {
     // Construct/initialize objects required by the application's profile object
     ApplicationInfo appInfo{"<application-id>",                    // ApplicationInfo object (App ID, friendly name)
                 "<friendly-name>" };
     auto profileObserver = make_shared<ProfileObserver>();         // Observer object                  
     auto authDelegateImpl = make_shared<AuthDelegateImpl>(         // Authentication delegate object (App ID)
                 "<application-id>");
     auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object
 
     // Construct/initialize profile object
     FileProfile::Settings profileSettings("",    // Path for logging/telemetry/state
       true,                                      // true = use in-memory state storage (vs disk)
       authDelegateImpl,                            
       consentDelegateImpl,                     
       profileObserver,                         
       appInfo);                                    

     // Set up promise/future connection for async profile operations; load profile asynchronously
     auto profilePromise = make_shared<promise<shared_ptr<FileProfile>>>();
     auto profileFuture = profilePromise->get_future();
     mip::FileProfile::LoadAsync(profileSettings, profilePromise);
     auto profile = profileFuture.get();

     // Construct/initialize engine object
     FileEngine::Settings engineSettings(
       mip::Identity("<engine-account>"),         // Engine identity (account used for authentication)
       "<engine-state>",                          // User-defined engine state      
       "en-US");                                  // Locale (default = en-US)

     // Set up promise/future connection for async engine operations; add engine to profile asynchronously
     auto enginePromise = make_shared<promise<shared_ptr<FileEngine>>>();
     auto engineFuture = enginePromise->get_future();
     profile->AddEngineAsync(engineSettings, enginePromise);
     std::shared_ptr<FileEngine> engine; 
     try
     {
       engine = engineFuture.get();             
     }
     catch (const std::exception& e)
     {
       cout << "An exception occurred... is the access token incorrect/expired?\n\n"
        << e.what() << "'\n";
       system("pause");
       return 1;
     }

      return 0;
     }

   ``` 

3. 방금 붙여넣은 소스 코드의 자리 표시자 값을 다음 값으로 바꿉니다.

   | 자리 표시자 | 값 | 예제 |
   |:----------- |:----- |:--------|
   | \<application-id\> | “MIP SDK 설정 및 구성”에 등록된 응용 프로그램에 할당된 Azure AD 응용 프로그램 ID입니다 (2개 인스턴스).  | 0edbblll-8773-44de-b87c-b8c6276d41eb |
   | \<friendly-name\> | 응용 프로그램의 사용자 정의 이름입니다. | AppInitialization |
   | \<engine-account\> | 엔진의 ID에 사용되는 계정입니다. 토큰을 확보하는 동안 사용자 계정으로 인증하는 경우 이 값과 일치해야 합니다. | user1@tenant.onmicrosoft.com |
   | \<engine-state\> | 엔진과 연결될 사용자 정의 상태입니다. | MyAppState |


4. 이제 응용 프로그램의 최종 빌드를 수행하고 오류를 해결합니다. 코드가 성공적으로 빌드되지만, 다음 빠른 시작을 완료할 때까지 올바르게 실행되지 않습니다. 응용 프로그램을 실행하는 경우 다음과 유사한 출력이 표시됩니다. 다음 빠른 시작을 완료할 때까지 제공할 액세스 토큰은 없습니다.

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Be sure to sign in with user account:
   Enter access token:
   ```

## <a name="next-steps"></a>다음 단계

이제 초기화 코드가 완료되었으므로 MIP 파일 API를 경험해볼 수 있는 다음 빠른 시작을 수행할 준비가 되었습니다.

> [!div class="nextstepaction"]
> [민감도 레이블 나열](quick-file-list-labels-cpp.md)
