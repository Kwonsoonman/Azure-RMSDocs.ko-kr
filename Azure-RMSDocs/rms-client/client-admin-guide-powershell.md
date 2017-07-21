---
title: "Azure Information Protection 클라이언트에서 PowerShell 사용"
description: "PowerShell을 사용하여 Azure Information Protection 클라이언트를 관리하는 관리자를 위한 지침 및 정보입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2f8ad221d1193f5a6f40cc773548b9342ffd6659
ms.sourcegitcommit: 0fd2e63822280ec96ab957e22868c63de9ef3d47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2017
---
# <a name="using-powershell-with-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에서 PowerShell 사용

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection 클라이언트를 설치하면 자동화에 대한 스크립트에 추가할 수 있는 명령을 실행하여 클라이언트를 관리할 수 있도록 PowerShell 명령이 자동으로 설치됩니다.

cmdlet은 PowerShell 모듈 **AzureInformationProtection**과 함께 설치됩니다. 이 모듈은 RMS 보호 도구와 함께 설치되는 RMSProtection 모듈을 대체합니다. Azure Information Protection 클라이언트를 설치할 때 RMSProtection 도구를 설치하면 RMSProtection 모듈이 자동으로 제거됩니다.

AzureInformationProtection 모듈에는 RMS 보호 도구의 모든 Rights Management cmdlet과 레이블을 지정하기 위해 AIP(Azure Information Protection) 서비스를 사용하는 3개의 새로운 cmdlet이 포함됩니다.

|레이블 지정 cmdlet|예제 사용법|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|공유 폴더에 대해 특정 레이블이 있는 모든 파일을 식별합니다.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|공유 폴더에 대해 파일 콘텐츠를 검사하고 지정한 조건에 따라 레이블이 지정되지 않은 파일에 자동으로 레이블을 지정합니다.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|공유 폴더에 대해 레이블이 없는 모든 파일에 지정된 레이블을 적용합니다.|

모든 cmdlet 목록 및 해당 도움말을 보려면 [AzureInformationProtection 모듈](/powershell/module/azureinformationprotection)을 참조하세요. PowerShell 세션 내에서 `Get-Help <cmdlet name> -online`를 입력하여 최신 도움말을 보고 영어 이외의 지원되는 언어를 확인하세요.  

이 모듈은 **\ProgramFiles (x86)\Microsoft Azure Information Protection**에 설치되고 이 폴더를 **PSModulePath** 시스템 변수에 추가합니다. 이 모듈의 .dll 이름은 **AIP.dll**입니다.

RMSProtection 모듈과 마찬가지로 AzureInformationProtection 모듈의 현재 릴리스에는 다음과 같은 제한이 있습니다.

- Outlook 개인 폴더(.pst 파일)의 보호를 해제할 수 있지만 현재는 이 PowerShell 모듈을 사용하여 이러한 파일 또는 기타 컨테이너 파일을 고유하게 보호할 수 없습니다.

- 보호된 Outlook 전자 메일 메시지(.rpmsg 파일)가 Outlook 개인 폴더(.pst)에 있을 때는 보호를 해제할 수 있으나 개인 폴더 밖에 있는 .rpmsg 파일의 보호는 해제할 수 없습니다.

이러한 cmdlet을 사용하기 전에 배포에 해당하는 추가 필수 구성 요소 및 지침을 참조하세요.

- [Azure Information Protection 서비스 및 Azure Rights Management 서비스](#azure-information-protection-service-and-azure-rights-management-service)

    - 분류만 또는 Rights Management 보호가 적용된 분류를 사용하는 경우에 적용 가능: Azure Information Protection를 포함하는 구독이 있습니다(예: Enterprise Mobility + Security).
    - Azure Rights Management 서비스와 보호만을 사용하는 경우에 적용 가능: Azure Rights Management 서비스를 포함하는 구독이 있습니다(예: Office 365 E3 및 Office 365 E5).

- [Active Directory Rights Management Services](#active-directory-rights-management-services)

    - Azure Rights Management의 온-프레미스 버전인 AD RMS(Active Directory Rights Management Services)와 함께 보호만을 사용하는 경우 적용 가능


## <a name="azure-information-protection-service-and-azure-rights-management-service"></a>Azure Information Protection 서비스 및 Azure Rights Management 서비스

조직에서 Azure Information Protection 및 Azure Rights Management 데이터 보호 서비스를 사용하는 경우나 Azure Rights Management 서비스만 사용하는 경우 먼저 이 섹션을 읽은 다음 PowerShell 명령 사용을 시작하세요.


### <a name="prerequisites"></a>필수 구성 요소

AzureInformationProtection 모듈을 설치하기 위한 필수 구성 요소 외에, Azure Information Protection 서비스 및 Azure Rights Management 데이터 보호 서비스에 대한 추가적인 필수 구성 요소가 있습니다.

1. Azure Rights Management 서비스가 활성화되어야 합니다.

2. 자기 계정을 사용하는 다른 사람의 파일에서 보호 제거 
    
    - 조직에 대해 슈퍼 사용자 기능을 사용하도록 설정해야 하고 계정은 Azure Rights Management에 대해 슈퍼 사용자로 구성되어야 합니다.

3. 사용자 개입 없이 파일을 직접 보호 또는 보호 해제하려면: 
    
    - 서비스 주체 계정을 만들고, Set-RMSServerAuthentication을 실행하고, 이 서비스 주체를 Azure Rights Management에 대한 슈퍼 사용자로 만드는 것을 고려합니다.

4. 북미 이외의 지역: 
    
    - 서비스에 인증할 레지스트리를 편집합니다.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>필수 구성 요소 1: Azure Rights Management 서비스가 활성화되어야 함

레이블을 사용하여 데이터 보호를 적용하는 경우와 Azure Rights Management에 직접 연결하여 데이터 보호를 적용하는 경우 모두 이 필수 조건이 적용됩니다.

Azure Information Protection 테넌트가 활성화되지 않은 경우 [Azure Rights Management 활성화](../deploy-use/activate-service.md)에 대한 지침을 참조하세요.

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>필수 구성 요소 2: 여러분의 계정을 사용하는 다른 사람을 위해 파일에서 보호 제거

다른 사용자를 위해 파일에서 보호를 제거하기 위한 일반적인 시나리오에는 데이터 검색 또는 데이터 복구가 포함됩니다. 레이블을 사용하여 보호를 적용하는 경우 보호를 적용하지 않는 새 레이블을 설정하거나 레이블을 제거하여 보호를 제거할 수 있습니다. 하지만 Azure Rights Management 서비스에 직접 연결하여 보호를 제거할 가능성이 높습니다.

파일에서 보호를 제거할 수 있는 Rights Management 사용 권한이 있거나 슈퍼 사용자여야 합니다. 데이터 검색 또는 데이터 복구의 경우 일반적으로 슈퍼 사용자 기능이 사용됩니다. 이 기능을 사용하도록 설정하고 사용자 계정을 슈퍼 사용자로 구성하려면 [Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)을 참조하세요.

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>필수 구성 요소 3: 사용자 개입 없이 파일 보호 또는 보호 해제

현재 비대화형으로 레이블을 적용할 수 없으나 비대화형으로 Azure Rights Management 서비스에 직접 연결하여 파일을 보호하거나 보호를 해제할 수 있습니다.

Azure Rights Management 서비스에 비대화형으로 연결할 때는 서비스 사용자 계정을 사용해야 하며 이 작업은 `Set-RMSServerAuthentication` cmdlet을 사용하여 수행합니다. 각 Windows PowerShell 세션에 대해 이 작업을 수행하여 Azure Rights Management 서비스에 직접 연결하는 cmdlet을 실행해야 합니다. 이 cmdlet을 실행하기 전에 다음과 같은 세 가지 식별자가 있는지 확인합니다.

- BposTenantId

- AppPrincipalId

- 대칭 키

다음 섹션에서는 이러한 식별자를 가져오는 방법을 설명합니다.

##### <a name="to-get-the-bpostenantid"></a>BposTenantId를 가져오려면

Azure RMS Windows PowerShell 모듈에서 Get-AadrmConfiguration cmdlet을 실행합니다.

1. 이 모듈이 컴퓨터에 설치되지 않은 경우 [Azure Rights Management용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

2. **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작합니다.

3. `Connect-AadrmService` cmdlet을 사용하여 Azure Rights Management 서비스에 연결합니다.
    
        Connect-AadrmService
    
    메시지가 표시되면 Azure Information Protection 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).
    
4. `Get-AadrmConfiguration`을 실행하고 BPOSId 값의 복사본을 만듭니다.
    
    다음은 Get-AadrmConfiguration의 출력 예제입니다.
    
            BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
        
            RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
        
            LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
        
            CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

5. 서비스에서 연결을 끊습니다.
    
        Disconnect-AadrmService

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>AppPrincipalId 및 대칭 키를 가져오려면

Azure Active Directory에 대한 MSOnline PowerShell 모듈에서 `New-MsolServicePrincipal` cmdlet을 실행하여 새 서비스 주체를 만들고 다음 지침을 사용합니다. 

> [!IMPORTANT]
> 이 서비스 주체를 만드는 데 새로운 Azure AD PowerShell cmdlet인 New-AzureADServicePrincipal을 사용하지 마세요. Azure Rights Management 서비스에서는 New-AzureADServicePrincipal을 지원하지 않습니다. 

1. MSOnline 모듈이 컴퓨터에 아직 설치되지 않았으면 `Install-Module MSOnline`을 실행합니다.

2. **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작합니다.

3. **Connect-MsolService** cmdlet을 사용하여 Azure AD에 연결합니다.
    
        Connect-MsolService
    
    메시지가 표시되면 Azure AD 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).

4. New-MsolServicePrincipal cmdlet을 실행하여 새 서비스 사용자를 만듭니다.
    
        New-MsolServicePrincipal
    
    이 서비스 사용자의 표시 이름을 입력하라는 메시지가 표시되면 입력합니다. 이 이름은 나중에 파일을 보호하거나 보호를 해제할 수 있도록 Azure Rights Management 서비스에 연결할 때 사용할 계정으로 식별하는 데 도움이 됩니다.
    
    New-MsolServicePrincipal 출력 예제:
    
        Supply values for the following parameters:
        
        DisplayName: AzureRMSProtectionServicePrincipal
        The following symmetric key was created as one was not supplied
        zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=
        
        Display Name: AzureRMSProtectionServicePrincipal
        ServicePrincipalNames: (b5e3f7g1-b5c2-4c96-a594-a0807f65bba4)
        ObjectId: 23720996-593c-4122-bfc7-1abb5a0b5109
        AppPrincialId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4
        TrustedForDelegation: False
        AccountEnabled: True
        Addresses: ()
        KeyType: Symmetric
        KeyId: 8ef61651-ca11-48ea-a350-25834a1ba17c
        StartDate: 3/7/2014 4:43:59 AM
        EndDate: 3/7/2014 4:43:59 AM
        Usage: Verify

5. 이 출력에서 대칭 키 및 AppPrincialId를 적어둡니다.

    나중에는 대칭 키를 완전히 검색할 수 없으며, 이 키를 모르면 다음에 Azure Rights Management 서비스에서 인증을 받아야 할 경우 서비스 사용자를 새로 만들어야 하므로 대칭 키 사본을 만드는 것이 중요합니다.

이러한 지침 및 예제를 보면 Set-RMSServerAuthentication을 실행하는 데 다음과 같은 세 가지 식별자가 필요합니다.

- 테넌트 ID: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- 대칭 키: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

예제 명령은 다음과 같습니다.

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

이전 명령에서와 같이 단일 명령을 사용해서 여러 값을 제공하거나, Set-RMSServerAuthentication만 입력하고 요구가 있을 때마다 값을 하나씩 제공할 수 있습니다. 명령이 완료되면 클라이언트가 현재 “서버 모드"에서 작동하는 것을 나타내는 "**The RmsServerAuthentication is set to ON**"(RmsServerAuthentication이 ON으로 설정됨)이 표시됩니다. 이 메시지는 사용자가 제공한 값을 사용하여 인증에 성공한 것을 확인하지 않고 서버 모드로의 전환에 성공한 것을 확인합니다.

이 서비스 사용자를 슈퍼 사용자로 만드는 것을 고려: 이 서비스 사용자가 항상 다른 사용자를 위해 파일 보호를 해제할 수 있도록 하려면 슈퍼 사용자로 구성할 수 있습니다. 표준 사용자 계정을 슈퍼 사용자로 구성할 때와 같은 방식으로 동일한 Azure RMS cmdlet, [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md)를 사용하되, AppPrincipalId 값을 갖는 **-ServicePrincipalId** 매개 변수를 지정합니다.

슈퍼 사용자에 대한 자세한 내용은 [Azure Rights Management 및 검색 서비스 또는 데이터 검색을 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)을 참조하세요.

> [!NOTE]
> 자체 계정을 사용하여 Azure Rights Management 서비스에서 인증을 받으려면 파일을 보호하거나 보호를 해제하거나, 템플릿을 가져오기 전에 Set-RMSServerAuthentication을 실행할 필요가 없습니다.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>필수 구성 요소 4: 북미 이외의 지역

Azure North America 지역 외에서 인증을 받으려면 레지스트리를 다음과 같이 편집해야 합니다. Azure Information Protection 테넌트가 북미 지역에 있으면 이 단계를 수행하지 마세요.

1. Get-AadrmConfiguration cmdlet을 다시 실행하고 **CertificationExtranetDistributionPointUrl** 및 **LicensingExtranetDistributionPointUrl** 값을 적어둡니다.

2. AzureInformationProtection cmdlet을 실행할 각 컴퓨터에서 레지스트리 편집기를 열고 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC`로 이동합니다.

3. **ServiceLocation** 키가 표시되지 않으면 만듭니다. 그러면 레지스트리 경로에 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation**이 표시됩니다.

4. **ServiceLocation** 키가 없으면 **EnterpriseCertification** 및 **EnterprisePublishing** 이름의 키 2개를 만듭니다. 
    
    이러한 REG_SZ 키를 만들 때 "(기본값)"인 Name을 변경하지 말고, 편집하여 값 데이터를 설정합니다.

    - **EnterpriseCertification**으로 CertificationExtranetDistributionPointUrl 값을 붙여 넣습니다.
    
    - **EnterprisePublishing**으로 LicensingExtranetDistributionPointUrl 값을 붙여 넣습니다.

5. 레지스트리 편집기를 닫습니다. 컴퓨터를 다시 시작할 필요는 없습니다. 그러나 사용자 고유의 사용자 계정이 아닌 서비스 사용자 계정을 사용하는 경우 이 레지스트리 편집을 수행한 후 Set-RMSServerAuthentication 명령을 실행해야 합니다.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Azure Information protection 및 Azure Rights Management 서비스에 대한 cmdlet 사용 예제 시나리오

레이블을 사용하여 파일을 분류하고 보고하는 것이 좀 더 효율적입니다. 단독으로 또는 함께 실행할 수 있는 [Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus) 및 [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel)의 두 cmdlet만 필요하기 때문입니다. 자세한 내용 및 예제를 보려면 이 cmdlet에 대한 도움말을 사용하세요.

그러나 Azure Rights Management 서비스에 직접 연결하여 파일을 보호하거나 보호를 해제하려면 다음에 설명된 것처럼 일반적으로 일련의 cmdlet을 실행해야 합니다.

먼저, 자체 계정을 사용하는 대신, 서비스 사용자 계정을 사용해서 Azure Rights Management 서비스에서 인증을 받아야 할 경우 Powershell 세션에서 다음을 입력합니다.

    Set-RMSServerAuthentication

3개의 식별자를 입력하라는 메시지가 표시되면 [필수 구성 요소 3: 사용자 개입 없이 파일을 보호하거나 보호 해제](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction)에 설명된 대로 입력합니다.

파일을 보호하려면 먼저 Rights Management 템플릿을 컴퓨터에 다운로드한 후 사용할 템플릿과 해당 ID 번호를 식별해야 합니다. 그런 후에는 출력에서 템플릿 ID를 복사할 수 있습니다.

    Get-RMSTemplate
    
출력은 다음과 비슷할 수 있습니다.

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

Set-RMSServerAuthentication 명령을 실행하지 않은 경우 자체 사용자 계정을 사용하여 Azure Rights Management 서비스에서 인증을 받게 됩니다. 도메인에 연결된 컴퓨터에서 작업하는 경우 현재 자격 증명이 항상 자동으로 사용됩니다. 작업 그룹 컴퓨터에 있으면 Azure에 로그인하라는 메시지가 표시된 후 이러한 자격 증명이 후속 명령을 위해 캐시됩니다. 이 시나리오에서는 나중에 다른 사용자로 로그인해야 하는 경우 `Clear-RMSAuthentication` cmdlet을 사용합니다.

이제 템플릿 ID를 알게 되었으므로 `Protect-RMSFile` cmdlet에서 이 ID를 사용하여 단일 파일 또는 폴더의 모든 파일을 보호할 수 있습니다. 예를 들어 단일 파일만 보호하고 원본을 덮어쓰려면 "Contoso, Ltd - Confidential" 템플릿을 사용하여 다음을 수행합니다.

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

출력은 다음과 비슷할 수 있습니다.

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx

폴더의 모든 파일을 보호하려면 드라이브 문자/경로 또는 UNC 경로와 함께 **-Folder** 매개 변수를 사용합니다. 예를 들면 다음과 같습니다.

    Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

출력은 다음과 비슷할 수 있습니다.

    InputFile                          EncryptedFile
    ---------                          -------------
    \Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
    \Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
    \Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
    \Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx

보호를 적용한 후에 파일 이름 확장명이 변경되지 않으면 나중에 항상 `Get-RMSFileStatus` cmdlet을 사용하여 파일이 보호되고 있는지 여부를 확인할 수 있습니다. 예를 들면 다음과 같습니다.

    Get-RMSFileStatus -File \Server1\Documents\Test1.docx

출력은 다음과 비슷할 수 있습니다.

    FileName                              Status
    --------                              ------
    \Server1\Documents\Test1.docx         Protected

파일의 보호를 해제하려면 파일이 보호되었을 때 소유자 또는 압축 풀기 권한이 있거나 cmdlet을 슈퍼 사용자 권한으로 실행하고 있어야 합니다. 그런 후 Unprotect cmdlet을 사용합니다. 예를 들면 다음과 같습니다.

    Unprotect-RMSFile C:\test.docx -InPlace

출력은 다음과 비슷할 수 있습니다.

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Rights Management 템플릿이 변경되면 `Get-RMSTemplate -force`를 사용하여 다시 다운로드해야 합니다. 

## <a name="active-directory-rights-management-services"></a>Active Directory Rights Management Services

조직에서 Active Directory Rights Management Services만 사용할 경우 PowerShell 명령을 사용하여 파일을 보호하거나 보호를 해제하려면 먼저 이 섹션을 읽어보세요.


### <a name="prerequisites"></a>전제 조건

AzureInformationProtection 모듈을 설치하기 위한 필수 구성 요소 외에도 사용자 계정에는 ServerCertification.asmx에 액세스하기 위한 읽기 및 실행 권한이 있어야 합니다.

1. AD RMS 서버로 로그온합니다.

2. **시작**을 클릭한 다음 **컴퓨터**를 클릭합니다.

3. 파일 탐색기에서 %systemdrive%\Initpub\wwwroot\_wmsc\Certification으로 이동합니다.

4. **ServerCertification.asmx**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

5. **ServerCertification.asmx 속성** 대화 상자에서 **보안** 탭을 클릭합니다. 

6. **계속** 단추 또는 **편집** 단추를 클릭합니다. 

7. **ServerCertification.asmx에 대한 권한** 대화 상자에서 **추가**를 클릭합니다. 

8. 계정 이름을 추가합니다. 다른 AD RMS 관리자도 이러한 cmdlet을 사용하여 파일을 보호 및 보호 해제하는 경우 해당 관리자 이름도 추가합니다.

9. **허용** 열에 **읽기 및 실행** 및 **읽기** 확인란이 선택되어 있는지 확인합니다.

10.**확인**을 두 번 차례로 클릭합니다.

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Active Directory Rights Management Services에 대한 cmdlet 사용의 예제 시나리오

이러한 cmdlet에 대한 일반적인 시나리오는 권한 정책 템플릿을 사용하여 폴더의 모든 파일을 보호하거나 파일 보호를 해제하는 것입니다. 

먼저, AD RMS 배포가 2개 이상 있는 경우 AD RMS 서버의 이름이 필요합니다. 따라서 Get-RMSServer cmdlet을 사용하여 사용 가능한 서버 목록을 표시합니다.

    Get-RMSServer

출력은 다음과 비슷할 수 있습니다.

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

파일을 보호하려면 먼저 RMS 템플릿 목록을 가져온 후 사용할 템플릿과 해당 ID 번호를 식별해야 합니다. AD RMS 배포가 여러 개 있는 경우에만 RMS 서버도 지정해야 합니다. 

그런 후에는 출력에서 템플릿 ID를 복사할 수 있습니다.

    Get-RMSTemplate -RMSServer RmsContoso

출력은 다음과 비슷할 수 있습니다.

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

이제 템플릿 ID를 알게 되었으므로 Protect-RMSFile cmdlet에서 이 ID를 사용하여 단일 파일 또는 폴더의 모든 파일을 보호할 수 있습니다. 예를 들어 단일 파일만 보호하고 원본을 바꾸려면 "Contoso, Ltd - Confidential" 템플릿을 사용하여 다음을 수행합니다.

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

출력은 다음과 비슷할 수 있습니다.

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx   

폴더의 모든 파일을 보호하려면 드라이브 문자/경로 또는 UNC 경로와 함께 -Folder 매개 변수를 사용합니다. 예를 들면 다음과 같습니다.

    Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

출력은 다음과 비슷할 수 있습니다.

    InputFile                          EncryptedFile
    ---------                          -------------
    \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
    \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
    \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
    \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

RMS 보호를 적용한 후에 파일 이름 확장명이 변경되지 않으면 나중에 항상 Get-RMSFileStatus cmdlet을 사용하여 파일이 보호되고 있는지 여부를 확인할 수 있습니다. 예를 들면 다음과 같습니다. 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

출력은 다음과 비슷할 수 있습니다.

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

파일의 보호를 해제하려면 파일이 보호되었을 때 소유자 또는 추출 권한이 있거나 AD RMS에 대한 슈퍼 사용자여야 합니다. 그런 후 Unprotect cmdlet을 사용합니다. 예를 들면 다음과 같습니다.

    Unprotect-RMSFile C:\test.docx -InPlace

출력은 다음과 비슷할 수 있습니다.

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Azure Information Protection에 대해 비대화형으로 파일에 레이블을 지정하는 방법

Azure Information Protection 클라이언트 버전 1.8.41.0(현재 미리 보기)부터 **Set-AIPAuthentication** cmdlet을 사용하여 비대화형으로 레이블링 cmdlet을 실행할 수 있습니다.

기본적으로 레이블 지정에 대한 cmdlet을 실행하는 경우 명령이 대화형 PowerShell 세션의 자체적인 사용자 컨텍스트에서 실행됩니다. 무인으로 실행하려면 이 용도에 맞는 Azure AD 사용자 계정을 새로 만듭니다. 그런 다음 해당 사용자의 컨텍스트에서 Set-AIPAuthentication cmdlet을 설정하여 Azure AD의 액세스 토큰으로 자격 증명을 설정 및 저장합니다. 그런 후 이 사용자 계정이 Azure Rights Management 서비스에 대해 인증되고 부트스트랩됩니다. 이 계정은 레이블이 사용하는 Azure Information Protection 정책 및 모든 Rights Management 템플릿을 다운로드합니다.

이 cmdlet을 처음 실행하면 Azure Information Protection에 로그인하라는 메시지가 표시됩니다. 무인 사용자에 대해 만든 사용자 계정 이름 및 암호를 지정합니다. 그러면 이 계정은 인증 토큰이 만료될 때까지 레이블링 cmdlet을 비대화형으로 실행할 수 있습니다. 토큰이 만료되면 이 cmdlet을 다시 실행하여 새 토큰을 획득합니다.

매개 변수 없이 이 cmdlet을 실행하는 경우 계정은 90일 동안 또는 암호가 만료될 때까지 유효한 액세스 토큰을 획득합니다.  

액세스 토큰이 만료되는 시기를 제어하려면 매개 변수를 지정하여 이 cmdlet을 실행합니다. 이렇게 하면 액세스 토큰을 1년 또는 2년용 구성하거나 절대 만료되지 않도록 구성할 수 있습니다. 이 구성을 사용하려면 Azure Active Directory에 2개의 응용 프로그램인 **웹앱/API** 응용 프로그램 및 **네이티브 응용 프로그램**이 등록되어야 합니다. 이 cmdlet용 매개 변수는 이러한 응용 프로그램의 값을 사용합니다.

이 cmdlet을 실행한 후에는 만든 사용자 계정의 컨텍스트에서 레이블링 cmdlet을 실행할 수 있습니다. 둘 이상의 계정을 사용하려는 경우 각 계정은 Azure AD에 자체 응용 프로그램이 등록되어야 하므로 각 계정에 대해 이 cmdlet을 실행해야 합니다.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>Set-AIPAuthentication에 대해 Azure AD 응용 프로그램을 만들고 구성하려면

1. 새 브라우저 창에서 [Azure Portal](https://portal.azure.com/)에 로그인합니다.

2. Azure Information Protection을 사용할 Azure AD 테넌트에 대해 **Azure Active Directory** > **앱 등록**으로 이동합니다. 

3. **새 응용 프로그램 등록**을 선택하여 웹앱/API 응용 프로그램을 만듭니다. **만들기** 레이블에서 다음 값을 지정하고 **만들기**를 클릭합니다.
    
    - 이름: **AIPOnBehalfOf**
    
    - 응용 프로그램 유형: **웹앱/API**
    
    - 로그온 URL: **http://localhost**
    
4. 방금 만든 응용 프로그램 **AIPOnBehalfOf**를 선택하고 **설정** 블레이드에서 **속성**을 선택합니다. **속성** 블레이드에서 **응용 프로그램 ID**에 대한 값을 복사하고 이 블레이드를 닫습니다. 
    
    이 값은 Set-AIPAuthentication cmdlet을 실행할 때 `WebAppId` 매개 변수에 사용됩니다.

5. **설정** 블레이드에서 **키**를 선택합니다. 설명을 지정하고 기간(1년, 2년 또는 만료되지 않음)을 선택하여 새 키를 추가합니다. 그런 다음 **저장**을 선택하고 표시되는 **값**에 대한 문자열을 복사합니다. 이 문자열은 다시 표시되지 않으며 검색도 불가능하므로 반드시 저장해야 합니다.
    
    이 값은 Set-AIPAuthentication cmdlet을 실행할 때 `WebAppKey` 매개 변수에 사용됩니다.

6. **앱 등록** 블레이드로 돌아가 **새 응용 프로그램 등록**을 선택하여 네이티브 응용 프로그램을 만듭니다. **만들기** 레이블에서 다음 값을 지정하고 **만들기**를 클릭합니다.
    
    - 이름: **AIPClient**
    
    - 응용 프로그램 유형: **네이티브**
    
    - 로그온 URL: **http://localhost**

7. 방금 만든 응용 프로그램 **AIPClient**를 선택하고 **설정** 블레이드에서 **속성**을 선택합니다. **속성** 블레이드에서 **응용 프로그램 ID**에 대한 값을 복사하고 이 블레이드를 닫습니다.
    
    이 값은 Set-AIPAuthentication cmdlet을 실행할 때 `NativeAppId` 매개 변수에 사용됩니다.

8. **설정** 블레이드에서 **필요한 권한**을 선택합니다. 

9. **필요한 권한** 블레이드에서 **추가**를 클릭하고 **API 선택**을 클릭합니다. 검색 상자에 **AIPOnBehalfOf**를 입력합니다. 목록 상자에서 이 값을 선택한 다음 **선택**을 클릭합니다.

10. **액세스 사용** 블레이드에서 **AIPOnBehalfOf**를 선택하고 **선택**을 클릭한 후 **완료**를 클릭합니다.
    
    이제 두 앱의 구성을 완료했으며 매개 변수를 사용하여 [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)을 실행하는 데 필요한 값이 구성되었습니다.


## <a name="next-steps"></a>다음 단계
PowerShell 세션에 있는 경우에 cmdlet 도움말을 보려면 `Get-Help <cmdlet name> cmdlet`을 입력하고 -online 매개 변수를 사용하 여 가장 최신 정보를 읽어보세요. 예를 들면 다음과 같습니다. 

    Get-Help Get-RMSTemplate -online

Azure Information Protection 클라이언트를 지원하는 데 필요할 수 있는 추가 정보는 다음을 참조하세요.

- [Customizations](client-admin-guide-customizations.md)(사용자 지정)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
