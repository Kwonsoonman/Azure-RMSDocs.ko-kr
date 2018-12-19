---
title: Azure AD에 앱을 등록 하는 방법 - AIP
description: RMS 사용 응용 프로그램에 대한 사용자 인증의 기본 사항에 대해 설명합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 42a1944dcb643c1647ee7299456307815f1023b4
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266633"
---
# <a name="how-to-register-and-rms-enable-your-app-with-azure-ad"></a>Azure AD에서 RMS를 등록하고 앱을 사용하도록 설정하는 방법

이 항목에서는 Azure 포털을 통해 앱을 등록하고 RMS를 사용하도록 설정하는 기본적인 방법과 Azure ADAL(Active Directory Authentication Library)을 통한 사용자 인증 방법을 안내합니다.

## <a name="what-is-user-authentication"></a>사용자 인증이란?
사용자 인증은 장치 앱과 RMS 인프라 간의 통신을 설정하기 위한 필수 단계입니다. 이 인증 프로세스에서는 현재 사용자 및 인증 요청에 관한 주요 정보가 필요한 표준 OAuth 2.0 프로토콜을 사용합니다.

## <a name="registration-via-azure-portal"></a>Azure 포털을 통해 등록
Azure 포털을 통해 앱의 등록을 구성하려면 이 가이드에 따라 [ADAL 인증을 위해 Azure RMS 구성](adal-auth.md)부터 수행합니다. 나중에 사용할 수 있도록 이 프로세스에서 **클라이언트 ID** 및 **리디렉션 URI**를 복사하여 저장해야 합니다.

## <a name="complete-your-information-protection-integration-agreement-ipia"></a>IPIA(정보 보호 통합 계약) 완료
응용 프로그램을 배포하려면 먼저 Microsoft Information Protection 팀의 IPIA를 완료해야 합니다. 자세한 내용은 [프로덕션 환경에 배포](deploying-your-application.md) 항목의 첫 번째 섹션을 참조하세요.

## <a name="implement-user-authentication-for-your-app"></a>앱에 대한 사용자 인증 구현
각 RMS API에는 사용자 인증을 사용하기 위해 구현해야 하는 콜백이 있습니다. 액세스 토큰을 제공하지 않거나, 액세스 토큰을 새로 고쳐야 하거나, 액세스 토큰이 만료된 경우 RMS SDK 4.2에서 콜백 구현을 사용합니다.

- Android - [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx) 및 [AuthenticationCompletionCallback](https://msdn.microsoft.com/library/dn758250.aspx) 인터페이스.
- iOS / OS X -  [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) 프로토콜.
-  Windows Phone / Window RT -  [IAuthenticationCallback](https://msdn.microsoft.com/library/microsoft.rightsmanagement.iauthenticationcallback.aspx) 인터페이스.
- Linux -  [IAuthenticationCallback](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html) 인터페이스.

### <a name="what-library-to-use-for-authentication"></a>인증에 사용할 라이브러리
인증 콜백을 구현하려면 적절한 라이브러리를 다운로드하고 해당 라이브러리를 사용하도록 개발 환경을 구성해야 합니다. GitHub에서 이러한 플랫폼에 대한 ADAL 라이브러리를 찾을 수 있습니다.

다음 리소스에는 각각 환경을 설정하고 라이브러리를 사용하는 지침이 포함되어 있습니다.

-   [Microsoft Azure Active Directory Authentication Library (ADAL) for iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)(iOS용 Microsoft Azure ADAL(Active Directory 인증 라이브러리))
-   [Microsoft Azure Active Directory Authentication Library (ADAL) for Mac](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)(Mac용 Microsoft Azure ADAL(Active Directory 인증 라이브러리))
-   [Microsoft Azure Active Directory Authentication Library (ADAL) for Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)(Android용 Microsoft Azure ADAL(Active Directory 인증 라이브러리))
-   [Microsoft Azure Active Directory Authentication Library (ADAL) for dotnet](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)(dotnet용 Microsoft Azure ADAL(Active Directory 인증 라이브러리))
-   Linux SDK의 경우 [Github](https://github.com/AzureAD/rms-sdk-for-cpp)를 통해 제공되는 SDK 원본과 함께 ADAL 라이브러리가 패키징되어 있습니다.

>[!NOTE]   다른 인증 라이브러리를 사용할 수도 있지만, ADAL 중 하나를 사용하는 것이 좋습니다.

### <a name="authentication-parameters"></a>인증 매개 변수

ADAL에서 사용자를 Azure RMS(또는 AD RMS)에 인증하려면 여러 가지 정보가 필요합니다. 이러한 정보는 Azure AD 앱에 일반적으로 필요한 표준 OAuth 2.0 매개 변수입니다. 앞에 나열된 해당 Github 리포지토리의 추가 정보 파일에서 ADAL 사용에 대한 최신 지침을 찾을 수 있습니다.

- **기관** – 인증 끝점(일반적으로 AAD 또는 ADFS)의 URL입니다.
- **리소스** - 액세스하려는 서비스 응용 프로그램(일반적으로 Azure RMS 또는 AD RMS)의 URL/URI입니다.
- **사용자 ID** – 앱에 액세스하려는 사용자의 UPN(일반적으로 메일 주소)입니다. 사용자를 아직 알 수 없는 경우 이 매개 변수는 비어 있을 수 있으며, 사용자 토큰을 캐시하거나 캐시에서 토큰을 요청하는 경우에도 사용됩니다. 또한 일반적으로 사용자 프롬프트에 대한 *힌트*로 사용됩니다.
- **클라이언트 ID** – 클라이언트 앱의 ID입니다. 유효한 Azure AD 응용 프로그램 ID여야 합니다.
Azure 포털을 통해 이전 등록 단계에서 가져옵니다.
- **리디렉션 URI** – 인증 라이브러리에 인증 코드의 URI 대상을 제공합니다. iOS 및 Android에는 특정한 형식이 필요합니다. 이러한 작업은 ADAL의 해당 GitHub 리포지토리에 있는 README 파일에 설명되어 있습니다. Azure 포털을 통해 이전 등록 단계에서 이 값을 가져옵니다.

>[!NOTE]
> **범위**는 현재 사용되지 않지만 사용될 수 있으므로 향후 사용을 위해 예약되었습니다.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

>[!NOTE]  앱이 이러한 지침을 따르지 않으면 Azure RMS 및 Azure AD 워크플로는 실패할 가능성이 크며 Microsoft.com에서 지원되지 않습니다. 또한 프로덕션 앱에서 잘못된 클라이언트 ID를 사용할 경우 RMLA(권한 관리 사용권 계약)를 위반할 수 있습니다.

### <a name="what-should-an-authentication-callback-implementation-look-like"></a>필요한 인증 콜백 구현 모양
**인증 코드 예제** - 이 SDK에는 인증 콜백 사용을 보여 주는 예제 코드가 있습니다. 편의상, 이러한 코드 예제는 여기뿐 아니라 연결된 다음 각 항목에도 표시되어 있습니다.

**Android 사용자 인증** - 자세한 내용은 [Android 코드 예제](android-code.md), 첫 번째 시나리오 "RMS 보호된 파일 사용"의 **2단계**를 참조하세요.


    class MsipcAuthenticationCallback implements AuthenticationRequestCallback
    {
    ...

    @Override
    public void getToken(Map<String, String> authenticationParametersMap,
                         final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
    {
        String authority = authenticationParametersMap.get("oauth2.authority");
        String resource = authenticationParametersMap.get("oauth2.resource");
        String userId = authenticationParametersMap.get("userId");
        mClientId = “12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”; // get your registered Azure AD application ID here
        mRedirectUri = “urn:ietf:wg:oauth:2.0:oob”;
        final String userHint = (userId == null)? "" : userId;
        AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
        if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
        {
            try
            {
                authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                App.getInstance().setAuthenticationContext(authenticationContext);
            }
            catch (NoSuchAlgorithmException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
            catch (NoSuchPaddingException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
       }
        App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                       "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                        {
                            @Override
                            public void onError(Exception exc)
                            {
                                …
                                if (exc instanceof AuthenticationCancelError)
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onCancel();
                                }
                                else
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onFailure();
                                }
                            }

                            @Override
                            public void onSuccess(AuthenticationResult result)
                            {
                                …
                                if (result == null || result.getAccessToken() == null
                                        || result.getAccessToken().isEmpty())
                                {
                                     …
                                }
                                else
                                {
                                    // request is successful
                                    …
                                    authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                }
                            }
                        });
                         }


**iOS/OS X 사용자 인증** - 자세한 내용은 [iOS/OS X 코드 예제](ios-os-x-code-examples.md), *첫 번째 시나리오 "RMS 보호된 파일 사용"의 2단계*를 참조하세요.


    // AuthenticationCallback holds the necessary information to retrieve an access token.
    @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

    @end

    @implementation MsipcAuthenticationCallback

    - (void)accessTokenWithAuthenticationParameters:
         (MSAuthenticationParameters *)authenticationParameters
                                completionBlock:
         (void(^)(NSString *accessToken, NSError *error))completionBlock
    {
    ADAuthenticationError *error;
    ADAuthenticationContext* context = [ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority error:&error];

    NSString *appClientId = @”12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”;

    // get your registered Azure AD application ID here

    NSURL *redirectURI = [NSURL URLWithString:@”ms-sample://com.microsoft.sampleapp”];

    // get your <app-scheme>://<bundle-id> here
    // Retrieve token using ADAL
    [context acquireTokenWithResource:authenticationParameters.resource
                             clientId:appClientId
                          redirectUri:redirectURI
                               userId:authenticationParameters.userId
                      completionBlock:^(ADAuthenticationResult *result)
                      {
                          if (result.status != AD_SUCCEEDED)
                          {
                              NSLog(@"Auth Failed");
                              completionBlock(nil, result.error);
                          }
                          else
                          {
                              completionBlock(result.accessToken, result.error);
                          }
                      }

        ];
    }



**Linux 사용자 인증** - 자세한 내용은 [Linux 코드 예제](linux-c-code-examples.md)를 참조하세요.



    // Class Header
    class AuthCallback : public IAuthenticationCallback {
    private:

      std::shared_ptr<rmsauth::FileCache> FileCachePtr;
      std::string clientId_;
      std::string redirectUrl_;

      public:

      AuthCallback(const std::string& clientId,
               const std::string& redirectUrl);
      virtual std::string GetToken(shared_ptr<AuthenticationParameters>& ap) override;
    };

    class ConsentCallback : public IConsentCallback {
      public:

      virtual ConsentList Consents(ConsentList& consents) override;
    };

    // Class Implementation
    AuthCallback::AuthCallback(const string& clientId, const string& redirectUrl)
    : clientId_(clientId), redirectUrl_(redirectUrl) {
      FileCachePtr = std::make_shared<FileCache>();
    }

    string AuthCallback::GetToken(shared_ptr<AuthenticationParameters>& ap)
    {
      string redirect =
      ap->Scope().empty() ? redirectUrl_ : ap->Scope();

      try
      {
        if (redirect.empty()) {
        throw rmscore::exceptions::RMSInvalidArgumentException(
              "redirect Url is empty");
      }

      if (clientId_.empty()) {
      throw rmscore::exceptions::RMSInvalidArgumentException("client Id is empty");
      }

      AuthenticationContext authContext(
        ap->Authority(), AuthorityValidationType::False, FileCachePtr);

      auto result = authContext.acquireToken(ap->Resource(),
                                           clientId_, redirect,
                                           PromptBehavior::Auto,
                                           ap->UserId());
      return result->accessToken();
      }

      catch (const rmsauth::Exception& ex)
      {
        // out logs
        throw;
      }
    }
