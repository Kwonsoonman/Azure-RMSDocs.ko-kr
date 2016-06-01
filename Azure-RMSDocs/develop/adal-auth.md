---
# required metadata

title: RMS 사용 응용 프로그램에 대한 ADAL 인증 | Azure RMS
description: ADAL 인증을 위한 프로세스를 간략히 설명합니다.
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# RMS 사용 응용 프로그램에 대한 ADAL 인증

Azure ADAL을 사용하여 Azure RMS에서 앱을 인증하는 과정은 이제 RMS 클라이언트 2.1의 일부입니다.

Microsoft Online 로그인 도우미 대신 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하면 개발자와 고객이 다음을 수행할 수 있습니다.

- 다단계 인증 활용
- 컴퓨터에 대한 관리자 권한 없이 RMS 2.1 클라이언트 설치
- Windows 10용 응용 프로그램 인증

## 인증에 대한 두 가지 접근 방법

이 항목에서는 해당 코드 예제와 함께 인증의 두 가지 접근 방법을 설명합니다.

- **내부 인증** - RMS SDK를 통해 관리되는 OAuth 인증입니다. 인증이 필요한 경우 RMS 클라이언트에서 ADAL 인증 프롬프트를 표시하는 경우 이 방법을 사용합니다. 응용 프로그램을 구성하는 방법에 대한 자세한 내용은 "내부 인증" 섹션을 참조하세요.

> [!NOTE] 현재 응용 프로그램에서 로그인 도우미와 함께 AD RMS SDK 2.1을 사용하는 경우 내부 인증 방법을 응용 프로그램 마이그레이션 경로로 사용하는 것이 좋습니다.

- **외부 인증** - 응용 프로그램을 통해 관리되는 OAuth 인증입니다. 응용 프로그램에서 자체 OAuth 인증을 관리하려는 경우 이 방법을 사용합니다. 이 방법의 경우 인증이 필요할 때 RMS 클라이언트에서 응용 프로그램 정의 콜백을 실행합니다. 자세한 예제를 보려면 이 항목의 끝에 있는 "외부 인증" 섹션을 참조하세요.

> [!NOTE] 외부 인증이 사용자를 변경할 수 있는 기능을 의미하지는 않습니다. RMS 클라이언트는 항상 지정된 RMS 테넌트의 기본 사용자를 사용합니다.

### 내부 인증

다음이 필요합니다.

- [Microsoft Azure에 대한 구독](https://azure.microsoft.com/en-us/)(무료 평가판이면 충분):
- Microsoft Azure 권한 관리에 대한 구독(무료 [개인용 RMS](https://technet.microsoft.com/en-us/library/dn592127.aspx) 계정이면 충분)

> [!NOTE] Microsoft Azure 권한 관리에 대한 구독이 있는지 여부에 대해서는 IT 관리자에게 문의하고 다음 단계를 수행하도록 요청하세요. 조직에 구독이 없는 경우 IT 관리자에게 만들어 달라고 요청해야 합니다. 또한 IT 관리자는 Microsoft 계정(예: Hotmail)이 아닌 회사 또는 학교 계정으로 가입되어 있어야 합니다.

Microsoft Azure에 등록한 후

- 관리자 권한이 있는 계정을 사용하여 조직에 대한 [Azure 관리 포털](https://manage.windowsazure.com)에 로그인합니다.

![Azure 로그인](../media/AzurePortalLogin.png)

- 포털의 왼쪽에 있는 **Active Directory** 응용 프로그램까지 이동합니다.

![Active Directory 선택](../media/AzureADPick.png)

- 디렉터리를 아직 만들지 않은 경우 포털의 왼쪽 아래 모서리에 있는 **새로 만들기** 단추를 선택합니다.

![새로 만들기 선택](../media/AzureNewBtn.png)

- **권한 관리** 탭을 선택하고 **권한 관리 상태**가 **활성**, **알 수 없음** 또는 **권한 없음**인지 확인합니다. 상태가 **비활성**인 경우 포털의 아래, 가운데에 있는 **활성화** 단추를 선택하고, 선택 사항을 확인합니다.

![활성화 선택](../media/RMTab.png)

- 이제 디렉터리와 응용 프로그램을 차례로 선택하여 새로운 *네이티브 응용 프로그램*을 만듭니다.

![응용 프로그램 선택](../media/CreateNativeApp.png)

- 이제 포털의 아래쪽, 가운데 부분에 있는 **추가** 단추를 선택합니다.

![추가 선택](../media/AddAppBtn.png)

- 프롬프트에서 **내 조직에서 개발 중인 응용 프로그램 추가**를 선택합니다.

![내 조직에서 개발 중인 응용 프로그램 추가 선택](../media/AddAnAppPick.png)

- **네이티브 클라이언트 응용 프로그램**과 **다음** 단추를 차례로 선택하여 응용 프로그램 이름을 지정합니다.

![앱 이름 지정](../media/TellUsInput.png)

- 리디렉션 URI를 추가하고 다음을 선택합니다. 리디렉션 URI는 유효한 URI여야 하며 디렉터리에 고유합니다. 예를 들어 `com.mycompany.myapplication://authorize`와 같은 항목을 사용할 수 있습니다.

![리디렉션 URI 추가](../media/RedirectURI.png)

- 디렉터리에서 응용 프로그램을 선택하고 **구성**을 선택합니다.

![구성 선택](../media/ConfigYourApp.png)

>[!NOTE] **클라이언트 ID** 및 **리디렉션 URI**를 복사하고 RMS 클라이언트를 구성할 때 사용할 수 있도록 저장합니다.

- 응용 프로그램 설정의 아래쪽으로 이동하고 **다른 응용 프로그램에 대한 권한**에서 **응용 프로그램 추가** 단추를 선택합니다.

![응용 프로그램 추가 선택](../media/PermissionsToOtherBtn.png)

- 이제 **다음으로 시작** 입력란에 GUID `00000012-0000-0000-c000-000000000000`을 추가하고 확인 단추를 선택합니다.

![GUID 추가](../media/AddGUID.png)

- **Microsoft Rights Management** 옆에 있는 더하기(+) 단추를 선택합니다.

![+ 단추 선택](../media/ChoosePlusBtn.png)

- 이제 대화 상자의 왼쪽 아래 모서리에 있는 확인 표시를 선택합니다.

![확인 표시 선택](../media/ChooseCheck.png)

- 이제 Azure RMS용 응용 프로그램에 대한 종속성을 추가할 준비가 되었습니다. 종속성을 추가하려면 **다른 응용 프로그램에 대한 사용 권한**에서 새로운 **Microsoft Rights Management Services** 항목을 선택하고 **위임된 권한:** 드롭 상자에서 **Create and access protected content for users(사용자의 보호된 콘텐츠 만들기 및 액세스)** 확인란을 선택합니다.

![사용 권한 설정](../media/AddDependency.png)

- 포털의 아래쪽 가운데에 있는 **저장** 아이콘을 선택하여 응용 프로그램의 변경 사항을 유지합니다.

![저장 선택](../media/SaveApplication.png)

- 이제 RMS SDK 2.1에서 제공하는 내부 ADAL 인증을 사용하도록 응용 프로그램을 구성할 준비가 되었습니다. RMS 클라이언트를 구성하려면 [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)를 호출하여 RMS 클라이언트를 구성한 직후에 [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/IpcSetGlobalProperty)에 대한 호출을 추가합니다. 예를 들어 다음 코드 조각을 사용합니다.


    IpcInitialize();

    IPC_AAD_APPLICATION_ID applicationId = { 0 };   applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);   applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";   applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";

    HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &amp;applicationId);

    if (FAILED(hr)) {    //Handle the error   }

### 외부 인증

- 다음 코드를 사용자 고유의 인증 토큰을 관리하는 방법의 예로 사용합니다.


    extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST&amp; Parameters, __out wstring wstrToken) throw();

    HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &amp;hKey)   {     IPC_OAUTH2_CALLBACK pfGetADALToken =         [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -&gt; HRESULT     {         wstring wstrToken;         HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);         return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;     };

      IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
      {
          sizeof(IPC_OAUTH2_CALLBACK_INFO),
          pfGetADALToken,
          pContextForAdal
      };

      IPC_CREDENTIAL credentialContext =
      {
          IPC_CREDENTIAL_TYPE_OAUTH2,
          NULL
      };
      credentialContext.pcOAuth2 = &amp;callbackCredentialContext;

      IPC_PROMPT_CTX promptContext =
      {
        sizeof(IPC_PROMPT_CTX),
        NULL,
        IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
        NULL,
        &amp;credentialContext
      };

      hKey = 0L;
      return IpcGetKey(pvLicense, 0, &amp;promptContext, NULL, &amp;hKey);
  }

### 관련 항목
- [데이터 형식](/rights-management/sdk/2.1/api/win/Data%20types)
- [환경 속성](/rights-management/sdk/2.1/api/win/Environment%20properties)
- [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/IpcCreateOAuth2Token)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/IpcGetKey)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)
- [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC\_CREDENTIAL)
- [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC\_NAME\_VALUE\_LIST)
- [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IPC\_OAUTH2\_CALLBACK\_INFO)
- [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC\_PROMPT\_CTX)
- [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IPC\_AAD\_APPLICATION\_ID)


<!--HONumber=May16_HO2-->


