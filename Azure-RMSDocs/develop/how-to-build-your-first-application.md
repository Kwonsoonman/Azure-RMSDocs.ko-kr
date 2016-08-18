---
title: "IPCHelloWorld - 예제 응용 프로그램 | Azure RMS"
description: "이 항목에는 예제 권한 사용 응용 프로그램을 만드는 지침이 포함되어 있습니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 581451A2-9558-4D0D-9D01-BEAB282C5A83
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac6afddc2b39d6209ef1b89d8d84011942cdba5a
ms.openlocfilehash: e75ec6c04afd171552697f79deb33ad2cfe2c4e1


---
** 이 SDK 콘텐츠는 현재 버전이 아닙니다. 잠시 MSDN에서 [현재 버전](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx)의 설명서를 확인해 주세요. **
# IPCHelloWorld - 예제 응용 프로그램

이 항목에는 예제 권한 사용 응용 프로그램을 만드는 지침이 포함되어 있습니다.

이 간단한 응용 프로그램인 IPCHelloWorld는 권한 사용 응용 프로그램의 기본 개념 및 코드를 이해하는 데 도움이 됩니다.

Microsoft Connect에서 샘플 응용 프로그램인 [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)을 다운로드합니다. 사이트에서 다운로드할 수 있는 나머지 항목은 사용자 편의를 위해 여기에 통합되었습니다.

**참고** IPCHelloWorld 프로젝트는 권한 관리 서비스 SDK 2.1용으로 이미 구성되어 있습니다. RMS SDK 2.1을 사용하도록 새 프로젝트를 구성하는 방법에 대한 자세한 내용은 [Visual Studio 구성](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)을 참조하세요.

 
다음 섹션에서는 필요한 주요 응용 프로그램 단계와 정보를 설명합니다.

## MSIPC.dll 로드

RMS SDK 2.1 함수를 호출하려면 먼저 [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) 함수를 호출하여 MSIPC.dll을 로드해야 합니다.



    hr = IpcInitialize();

    if (FAILED(hr))
    {
      wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
      goto exit;
    }



## 템플릿 열거

RMS 템플릿은 데이터를 보호하는 데 사용되는 정책을 정의합니다. 즉, 데이터에 액세스할 수 있는 사용자와 해당 권한을 정의합니다. RMS 템플릿은 RMS 서버에 설치됩니다.

다음 코드 조각은 기본 RMS 서버에서 사용 가능한 RMS 템플릿을 열거합니다.



    hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

    if (FAILED(hr))
    {
      DisplayError(L"IpcGetTemplateList failed", hr);
      goto exit;
    }



이 호출은 기본 서버에 설치된 RMS 템플릿을 검색하고 그 결과를 *pcTil* 변수가 가리키는 [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) 구조에 로드한 다음 템플릿을 표시합니다.



    if (0 == pcTil->cTi)
    {
      wprintf(L"* No templates configured for your RMS server * \n\n");
      wprintf(L"\\------------------------------------------------------\n\n");
      goto exit;
    }

    for (DWORD dw = 0; dw < pcTil->cTi; dw++)
    {
      wprintf(L"Template #%d:\n", dw);
      wprintf(L"    Name:         %s\n", pcTil->aTi[dw].wszName);
      wprintf(L"    Issued by:    %s\n", pcTil->aTi[dw].wszIssuerDisplayName);
      wprintf(L"    Description:  %s\n", pcTil->aTi[dw].wszDescription);
      wprintf(L"\n");
    }



## 라이선스 직렬화

데이터를 보호하려면 먼저 라이선스를 직렬화하고 콘텐츠 키를 가져와야 합니다. 콘텐츠 키는 중요한 데이터를 암호화하는 데 사용됩니다. 직렬화된 라이선스는 일반적으로 암호화된 데이터에 연결되며 보호된 데이터의 소비자가 사용합니다. 소비자는 직렬화된 라이선스로 [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)를 호출하여 콘텐츠 암호를 해독하고 콘텐츠와 관련된 정책을 가져오기 위한 콘텐츠 키를 얻어야 합니다.

간단하게, [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)에서 반환된 첫 번째 RMS 템플릿을 사용하여 라이선스를 직렬화합니다.

일반적으로 사용자 인터페이스 대화 상자를 사용하여 사용자가 원하는 템플릿을 선택할 수 있도록 합니다.



    hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
    0, NULL, &hContentKey, &pSerializedLicense);

    if (FAILED(hr))
    {
      DisplayError(L"IpcSerializeLicense failed", hr);
      goto exit;
    }



이렇게 하면 콘텐츠 키 *hContentKey*와 보호된 데이터에 연결해야 하는 직렬화된 라이선스 *pSerializedLicense*를 보유하게 됩니다.

## 데이터 보호

이제 [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) 함수를 사용하여 중요한 데이터를 암호화할 준비가 되었습니다. 먼저 **IpcEncrypt** 함수에 암호화된 데이터의 예상 크기를 물어야 합니다.



    cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    NULL, 0, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }



여기서는 *wszText*에 보호할 일반 텍스트가 포함되어 있습니다. [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) 함수가 암호화된 데이터의 크기를 *cbEncrypted* 매개 변수에 반환합니다.

이제 암호화된 데이터에 대한 메모리를 할당합니다.



    pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

    if (NULL == pbEncrypted) {
      wprintf(L"Out of memory\n");
      goto exit;
    }


마지막으로, 실제 암호화를 수행할 수 있습니다.



    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    pbEncrypted, cbEncrypted, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }


이 단계를 마치면 암호화된 데이터 *pbEncrypted*와 소비자가 데이터 암호를 해독하는 데 사용할 직렬화된 라이선스 *pSerializedLicense*를 보유하게 됩니다.

## 오류 처리

이 예제 응용 프로그램 전체에서 **DisplayError** 함수는 오류 처리에 사용됩니다.



    void DisplayError(LPCWSTR wszErrorInfo, HRESULT hrError)
    {
        LPCWSTR wszErrorMessageText = NULL;

        if (SUCCEEDED(IpcGetErrorMessageText(hrError, 0, &wszErrorMessageText))) {
          wprintf(L"%s: 0x%08X (%s)\n", wszErrorInfo, hrError, wszErrorMessageText);
        }
        else {
          wprintf(L"%s: 0x%08X\n", wszErrorInfo, hrError);
        }
    }   


**DisplayError** 함수는 [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) 함수를 사용하여 해당 오류 코드에서 오류 메시지를 가져오고 표준 출력에 출력합니다.

## 정리

완료하기 전에 할당된 리소스도 모두 해제해야 합니다.



    if (NULL != pbEncrypted) {
      LocalFree((HLOCAL)pbEncrypted);
    }

    if (NULL != pSerializedLicense) {
      IpcFreeMemory((LPVOID)pSerializedLicense);
    }

    if (NULL != hContentKey) {
      IpcCloseHandle((IPC_HANDLE)hContentKey);
    }

    if (NULL != pcTil) {
      IpcFreeMemory((LPVOID)pcTil);
    }


## 관련 항목

* [개발자 노트](developer-notes.md)
* [Visual Studio 구성](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
* [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
* [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
* [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
 

 



<!--HONumber=Jun16_HO4-->


