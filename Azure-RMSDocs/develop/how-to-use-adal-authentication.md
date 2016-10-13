---
title: "RMS 사용 응용 프로그램에 대한 ADAL 인증 | Azure RMS"
description: "ADAL 인증을 위한 프로세스를 간략히 설명합니다."
keywords: "인증, RMS, ADAL"
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: 3ed49cf7dddb72783ecd3bf1e89454d805552743


---

# 방법: ADAL 인증 사용

Azure ADAL(Active Directory 인증 라이브러리)을 사용하여 Azure RMS에 앱을 인증합니다.

Microsoft Online 로그인 도우미 대신 ADAL 인증을 사용하도록 응용 프로그램을 업데이트하면 개발자와 고객이 다음을 수행할 수 있습니다.

- 다단계 인증 활용
- 컴퓨터에 대한 관리자 권한 없이 RMS 2.1 클라이언트 설치
- Windows 10용 응용 프로그램 인증

## 인증에 대한 두 가지 접근 방법

이 항목에서는 해당 코드 예제와 함께 인증의 두 가지 접근 방법을 설명합니다.

- **내부 인증** - RMS SDK를 통해 관리되는 OAuth 인증입니다.

  인증이 필요한 경우 RMS 클라이언트에서 ADAL 인증 프롬프트를 표시하는 경우 이 방법을 사용합니다. 응용 프로그램을 구성하는 방법에 대한 자세한 내용은 "내부 인증" 섹션을 참조하세요.

  > [!Note] 
  > 현재 응용 프로그램에서 로그인 도우미와 함께 AD RMS SDK 2.1을 사용하는 경우 내부 인증 방법을 응용 프로그램 마이그레이션 경로로 사용하는 것이 좋습니다.

- **외부 인증** - 응용 프로그램을 통해 관리되는 OAuth 인증입니다.

  응용 프로그램에서 자체 OAuth 인증을 관리하려는 경우 이 방법을 사용합니다. 이 방법의 경우 인증이 필요할 때 RMS 클라이언트에서 응용 프로그램 정의 콜백을 실행합니다. 자세한 예제를 보려면 이 항목의 끝에 있는 "외부 인증" 섹션을 참조하세요.

  > [!Note] 
  > 외부 인증이 사용자를 변경할 수 있는 기능을 의미하지는 않습니다. RMS 클라이언트는 항상 지정된 RMS 테넌트의 기본 사용자를 사용합니다.

## 내부 인증

1. [ADAL 인증을 위해 Azure RMS 구성](adal-auth.md)의 Azure 구성 단계를 따른 후 다음 앱 초기화 단계로 돌아갑니다.
2. 이제 RMS SDK 2.1에서 제공하는 내부 ADAL 인증을 사용하도록 응용 프로그램을 구성할 준비가 되었습니다.

RMS 클라이언트를 구성하려면 [IpcInitialize](/information-protection/sdk/2.1/api/win/functions#msipc_ipcinitialize)를 호출하여 RMS 클라이언트를 구성한 직후에 [IpcSetGlobalProperty](/information-protection/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)에 대한 호출을 추가합니다. 예를 들어 다음 코드 조각을 사용합니다.

      C++
      IpcInitialize();

      IPC_AAD_APPLICATION_ID applicationId = { 0 };
      applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);
      applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";
      applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";
      HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &applicationId);
      if (FAILED(hr)) {
        //Handle the error
      }

## 외부 인증

다음 코드를 사용자 고유의 인증 토큰을 관리하는 방법의 예로 사용합니다.
C++ extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST& Parameters, __out wstring wstrToken) throw();

      HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &hKey)
      {
          IPC_OAUTH2_CALLBACK pfGetADALToken =
          [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -> HRESULT
          {
              wstring wstrToken;
              HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);
              return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;
          };

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
          credentialContext.pcOAuth2 = &callbackCredentialContext;

          IPC_PROMPT_CTX promptContext =
          {
              sizeof(IPC_PROMPT_CTX),
              NULL,
              IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
              NULL,
              &credentialContext
          };

          hKey = 0L;
          return IpcGetKey(pvLicense, 0, &promptContext, NULL, &hKey);
      }

## 관련 항목

* [데이터 형식](/information-protection/sdk/2.1/api/win/data%20types)
* [환경 속성](/information-protection/sdk/2.1/api/win/environment%20properties#msipc_environment_properties)
* [IpcCreateOAuth2Token](/information-protection/sdk/2.1/api/win/functions#msipc_ipccreateoauth2token)
* [IpcGetKey](/information-protection/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcInitialize](/information-protection/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [IPC_CREDENTIAL](/information-protection/sdk/2.1/api/win/IPC_CREDENTIAL)
* [IPC_NAME_VALUE_LIST](/information-protection/sdk/2.1/api/win/IPC_NAME_VALUE_LIST)
* [IPC_OAUTH2_CALLBACK_INFO](/information-protection/sdk/2.1/api/win/ipc_oauth2_callback_info#msipc_ipc_oath2_callback_info)
* [IPC_PROMPT_CTX](/information-protection/sdk/2.1/api/win/IPC_PROMPT_CTX)
* [IPC_AAD_APPLICATION_ID](/information-protection/sdk/2.1/api/win/ipc_aad_application_id#msipc_ipc_aad_application_id)



<!--HONumber=Sep16_HO5-->


