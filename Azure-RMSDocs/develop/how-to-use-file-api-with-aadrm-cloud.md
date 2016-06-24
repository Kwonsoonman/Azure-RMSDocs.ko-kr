---
# required metadata

title: "방법: 서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정 | Azure RMS"
description: 이 항목에서는 Azure 권한 관리를 사용하도록 서비스 응용 프로그램을 설정하는 단계를 간략하게 설명합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 방법: 서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정

이 항목에서는 Azure 권한 관리를 사용하도록 서비스 응용 프로그램을 설정하는 단계를 간략하게 설명합니다. 자세한 내용은 [Azure 권한 관리 시작](https://technet.microsoft.com/en-us/library/jj585016.aspx)을 참조하세요.

**중요**  
Azure RMS와 함께 권한 관리 서비스 SDK 2.1 서비스 응용 프로그램을 사용하려면 사용자 고유의 테넌트를 만들어야 합니다. 자세한 내용은 [Azure RMS requirements: Cloud subscriptions that support Azure RMS](/rights-management/get-started/requirements-subscriptions.md)(Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독) 항목을 참조하세요.

## 필수 구성 요소

-   RMS SDK 2.1을 설치 및 구성해야 합니다. 자세한 내용은 [RMS SDK 2.1 시작](getting-started-with-ad-rms-2-0.md)을 참조하세요.
-   대칭 키 옵션을 사용하거나 다른 방법으로 [ACS를 통해 서비스 ID를 만들고](https://msdn.microsoft.com/en-us/library/gg185924.aspx) 해당 프로세스에서 얻은 키 정보를 기록해야 합니다.

## Azure 권한 관리 서비스 연결

-   [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)를 호출합니다.
-   [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)를 설정합니다.

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **참고** 자세한 내용은 [API 보안 모드 설정](setting-the-api-security-mode-api-mode.md)을 참조하세요.

     
-   다음 단계는 **pcCredential**([**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)) 멤버에 Azure 권한 관리 서비스의 연결 정보를 채워 [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) 구조체 인스턴스를 만들기 위한 설정입니다.
-   [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) 구조체 인스턴스를 만드는 경우 대칭 키 서비스 ID 생성(이 항목의 앞부분에 나열된 필수 조건 참조)의 정보를 사용하여 **wszServicePrincipal**, **wszBposTenantId** 및 **cbKey** 매개 변수를 설정합니다.

**참고** 검색 서비스의 기존 조건으로 인해 북미 지역에 거주하지 않는 경우 다른 지역의 대칭 키 자격 증명은 수락되지 않으므로 테넌트 URL을 직접 지정해야 합니다. 이 작업은 [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) 또는 [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)의 [**IPC\_CONNECTION\_INFO**](/rights-management/sdk/2.1/api/win/ipc_connection_info#msipc_ipc_connection_info) 매개 변수를 통해 수행됩니다.

## 대칭 키를 생성하고 필요한 정보 수집

### 대칭 키 생성 지침

-   [Microsoft Online 로그인 도우미](http://go.microsoft.com/fwlink/p/?LinkID=286152)를 설치합니다.
-   [Azure AD Powershell 모듈](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi)을 설치합니다.

**참고** Powershell cmdlet을 사용하려면 테넌트 관리자여야 합니다.

-   Powershell을 시작하고 다음 명령을 실행하여 키        `Import-Module MSOnline`
            `Connect-MsolService`(관리자 자격 증명 입력)        `New-MsolServicePrincipal`(표시 이름 입력)를 생성합니다.
-   대칭 키를 생성한 후 키 자체와 **AppPrincipalId**를 포함하여 키에 대한 정보를 출력합니다.


    The following symmetric key was created as one was not supplied ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

    DisplayName : RMSTestApp ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963} ObjectId : 0ee53770-ec86-409e-8939-6d8239880518 AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### **TenantBposId** 및 **Url**확인 지침

-   [Azure RMS powershell 모듈](https://technet.microsoft.com/en-us/library/jj585012.aspx)을 설치합니다.
-   Powershell을 시작하고 다음 명령을 실행하여 테넌트의 RMS 구성을 가져옵니다.

    `Import-Module aadrm`

    `Connect-AadrmService` (관리자 자격 증명 입력)

    `Get-AadrmConfiguration`


-   [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) 인스턴스를 만들고 몇 개의 멤버를 설정합니다.

    // Create a key structure.
    IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

    // Set each member with information from service creation.
    symKey.wszBase64Key = "your service principal key"; symKey.wszAppPrincipalId = "your app principal identifier"; symKey.wszBposTenantId = "your tenent identifier";


자세한 내용은 [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key)를 참조하세요.

-   [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) 인스턴스를 포함하는 [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential) 구조체 인스턴스를 만듭니다.

**참고** *connectionInfo* 멤버는 이전 `Get-AadrmConfiguration` 호출의 URL로 설정되며 여기서 해당 필드 이름으로 설명됩니다.

    // Create a credential structure.
    IPC_CREDENTIAL cred = {0};

    IPC_CONNECTION_INFO connectionInfo = {0};
    connectionInfo.wszIntranetUrl = LicensingIntranetDistributionPointUrl;
    connectionInfo.wszExtranetUrl = LicensingExtranetDistributionPointUrl;

    // Set each member.
    cred.dwType = IPC_CREDENTIAL_TYPE_SYMMETRIC_KEY;
    cred.pcCertContext = (PCCERT_CONTEXT)&symKey;

    // Create your prompt control.
    IPC_PROMPT_CTX promptCtx = {0};

    // Set each member.
    promptCtx.cbSize = sizeof(IPC_PROMPT_CTX);
    promptCtx.hwndParent = NULL;
    promptCtx.dwflags = IPC_PROMPT_FLAG_SILENT;
    promptCtx.hCancelEvent = NULL;
    promptCtx.pcCredential = &cred;

### 템플릿 식별 후 암호화

-   암호화에 사용할 템플릿을 선택합니다.
    동일한 [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) 인스턴스를 전달하여 [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)를 호출합니다.


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   이 항목의 앞부분에서 설명한 템플릿을 사용하고 동일한 [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) 인스턴스를 전달하여 [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)을 호출합니다.

[**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile) 사용 예:

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

[**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile) 사용 예:

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

이제 응용 프로그램이 Azure 권한 관리를 사용할 수 있도록 설정하는 데 필요한 단계를 완료했습니다.

## 관련 항목

* [Azure 권한 관리 시작](https://technet.microsoft.com/en-us/library/jj585016.aspx)
* [RMS SDK 2.1 시작](getting-started-with-ad-rms-2-0.md)
* [ACS를 통해 서비스 ID 만들기](https://msdn.microsoft.com/en-us/library/gg185924.aspx)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)
* [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)
* [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key)
* [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcCreateLicenseFromTemplateID**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromtemplateid)
 

 


<!--HONumber=Jun16_HO2-->


