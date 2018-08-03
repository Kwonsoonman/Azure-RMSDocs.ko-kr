---
title: Azure Information Protection 테넌트 키
description: Azure Information Protection 테넌트 키를 계획 및 관리하는 데 도움이 되는 정보를 제공합니다. Microsoft에서 테넌트 키(기본값)를 관리하는 대신, 조직에 적용되는 특정 규정을 준수하도록 자체 테넌트 키를 관리하려고 할 수 있습니다. 자체 테넌트 키를 관리하는 것을 BYOK(bring your own key)라고도 합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/26/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e38f2c84e450b11ea8d86aa8b1680e4754a5aae4
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39372654"
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Azure Information Protection 테넌트 키 계획 및 구현

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

이 문서의 정보는 Azure Information Protection 테넌트 키를 계획 및 관리하는 데 도움이 됩니다. 예를 들어 Microsoft에서 테넌트 키(기본값)를 관리하는 대신, 조직에 적용되는 특정 규정을 준수하도록 자체 테넌트 키를 관리하려고 할 수 있습니다. 자체 테넌트 키를 관리하는 것을 BYOK(bring your own key)라고도 합니다.

Azure Information Protection 테넌트 키란?

- Azure Information Protection 테넌트 키는 조직의 루트 키입니다. 다른 키는 사용자 키, 컴퓨터 키 및 문서 암호화 키와 같은 이 루트 키에서 파생될 수 있습니다. Azure Information Protection에서 조직에 대해 이 키를 사용할 때마다 Azure Information Protection의 테넌트 키와 암호화 방식으로 연결합니다.

- Azure Information Protection 테넌트 키는 AD RMS(Active Directory Rights Management Services)의 SLC(서버 사용 허가자 인증서) 키와 동등한 온라인 키입니다. 

**한 눈에 보기:** 다음 표를 참조하여 권장되는 테넌트 키 토폴로지를 빠르게 확인할 수 있습니다. 자세한 내용은 추가 설명서를 참조하세요.

|비즈니스 요구 사항|권장되는 테넌트 키 토폴로지|
|------------------------|-----------------------------------|
|Azure Information Protection을 특별한 하드웨어, 추가 소프트웨어 또는 Azure 구독 없이 신속하게 배포합니다.<br /><br />예: 테스트 환경 및 키 관리에 대한 규정 요구 사항이 조직에 없는 경우.|Microsoft에서 관리|
|모든 수명 주기 작업에 대한 제어, 추가 보안 및 준수 규정. <br /><br />예: 키는 HSM(하드웨어 보안 모듈)로 보호되어야 합니다.|BYOK [[1]](#footnote-1)|


필요한 경우 [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) cmdlet을 사용하여 배포 후 테넌트 키 토폴로지를 변경할 수 있습니다.


## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>테넌트 키 토폴로지 선택: Microsoft가 관리(기본값) 또는 고객이 직접 관리(BYOK)
조직에 가장 적합한 테넌트 키 토폴로지를 결정하세요. 기본적으로 Azure Information Protection은 고객의 테넌트 키를 생성하고 테넌트 키 수명 주기의 대부분의 측면을 관리합니다. 이 옵션은 관리 오버헤드가 가장 낮은 가장 간단한 옵션입니다. 대부분의 경우 고객은 테넌트 키를 가지고 있다는 사실조차 알 필요가 없습니다. Azure Information Protection에 등록하기만 하면 나머지 키 관리 프로세스는 Microsoft에서 처리합니다.

조직에 가장 적합한 테넌트 키 토폴로지를 결정하세요.

- **Microsoft에서 관리**: Microsoft가 조직의 테넌트 키를 자동으로 생성하며, 이 키는 Azure Information Protection에서 단독으로 사용됩니다. 기본적으로 Microsoft는 이 키를 테넌트에 사용하고 테넌트 키 수명 주기에 대한 대부분의 측면을 관리합니다. 
    
    이 옵션은 관리 오버헤드가 가장 낮은 가장 간단한 옵션입니다. 대부분의 경우 고객은 테넌트 키를 가지고 있다는 사실조차 알 필요가 없습니다. Azure Information Protection에 등록하기만 하면 나머지 키 관리 프로세스는 Microsoft에서 처리합니다.

- **고객이 직접 관리(BYOK)**: 테넌트 키를 완전히 제어하려면 Azure Information Protection과 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)를 사용하십시오. 이러한 테넌트 키 토폴로지의 경우 Key Vault에서 직접 키를 만들거나 온-프레미스에서 만듭니다. 온-프레미스에서 만들면 이 키를 Key Vault로 전송하거나 가져옵니다. 그런 다음 이 키를 사용하도록 Azure Information Protection을 구성하고 Azure Key Vault에서 관리합니다.
    

### <a name="more-information-about-byok"></a>BYOK에 대한 추가 정보
자체 키를 만들려면 다음과 같은 옵션이 있습니다.

- **온-프레미스에서 만들고 Key Vault로 전송하거나 가져오는 키**:
    
    - 온-프레미스에서 만들고 Key Vault에 HSM 보호 키로 전송하는 HSM 보호 키입니다.
    
    - 온-프레미스에서 만들고 변환한 다음 Key Vault에 HSM 보호 키로 전송하는 소프트웨어 보호 키입니다. 이 옵션은 [AD RMS(Active Directory Rights Management Services)에서 마이그레이션할](migrate-from-ad-rms-to-azure-rms.md) 때만 지원됩니다.
    
    - 온-프레미스에서 만들고 Key Vault에 소프트웨어 보호 키로 가져오는 소프트웨어 보호 키. 이 옵션에는 .PFX 인증서 파일이 필요합니다.
    
- **Key Vault에서 만드는 키**:
    
    - Key Vault에서 만드는 HSM 보호 키.
    
    - Key Vault에서 만드는 소프트웨어 보호 키.

이러한 BYOK 옵션 중 가장 일반적인 옵션은 온-프레미스에서 만들고 Key Vault에 HSM 보호 키로 전송하는 HSM 보호 키입니다. 이 옵션은 관리 오버헤드가 가장 크지만 조직이 특정 규정을 준수해야 하는 경우 필요할 수 있습니다. Azure Key Vault에 사용되는 HSM은 FIPS 140-2 수준 2 유효성이 검사됩니다.

이 옵션을 사용할 경우 다음과 같은 상황이 발생합니다.

1. 고객이 IT 정책 및 보안 정책에 따라 고객의 프레미스에서 테넌트 키를 생성합니다. 이 키는 마스터 복사본입니다. 온-프레미스로 유지되며 사용자에게 백업 책임이 있습니다.

2. 이 키의 복사본을 만들고 복사본을 HSM에서 Azure Key Vault로 안전하게 전송합니다. 이 프로세스 전체에서 이 키의 마스터 복사본은 하드웨어 보호 경계를 벗어나지 않습니다.

3. 키의 복사본은 Azure Key Vault에 의해 보호됩니다.

> [!NOTE]

> 추가 보호 조치로 Azure Key Vault에서는 북아메리카, EMEA(유럽, 중동 및 아시아) 및 아시아 같은 지역의 데이터 센터에 별도의 보안 도메인을 사용합니다. Azure Key Vault는 Microsoft Azure 독일 및 Azure Government처럼 다른 Azure 인스턴스도 사용합니다. 

선택 사항이기는 하지만 테넌트 키가 언제, 어떻게 사용되는지를 정확하게 확인하기 위해 Azure Information Protection의 근 실시간 사용 현황 로그를 사용하기를 원할 수도 있습니다.

### <a name="when-you-have-decided-your-tenant-key-topology"></a>테넌트 키 토폴로지를 결정한 경우

Microsoft가 테넌트 키를 관리하도록 결정한 경우: 

- AD RMS에서 마이그레이션하는 경우가 아니라면 키를 생성하기 위해 추가적인 조치가 필요하지 않으므로 [다음 단계](plan-implement-tenant-key.md#next-steps)로 바로 이동할 수 있습니다.


- 현재 AD RMS가 있고 Azure Information Protection으로 마이그레이션하려면 AD RMS에서 Azure Information Protection으로 마이그레이션이라는 지침을 참조하세요. 

테넌트 키를 직접 관리하기로 결정한 경우 다음 섹션에서 자세한 내용을 확인하세요.

## <a name="implementing-byok-for-your-azure-information-protection-tenant-key"></a>Azure Information Protection 테넌트 키에 대한 BYOK 구현

직접 테넌트 키를 생성하고 관리하기로 결정한 경우(BYOK(Bring Your Own Key) 시나리오) 이 섹션의 정보 및 절차를 사용하세요.

> [!NOTE]
> Microsoft에서 관리하는 테넌트 키를 사용하여 Azure Information Protection 사용을 시작했지만 이제는 BYOK 방식으로 전환하여 테넌트 키를 직접 관리하려는 경우, 보관된 키를 사용하여 이전에 보호했던 문서와 메일에 계속 액세스할 수 있습니다. 

### <a name="prerequisites-for-byok"></a>BYOK 사전 요구 사항
BYOK(Bring Your Own Key) 사전 요구 사항 목록은 다음 표를 참조하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure Information Protection 테넌트는 Azure 구독이 있어야 합니다. 구독이 없는 경우 [무료 계정](https://azure.microsoft.com/pricing/free-trial/)을 등록할 수 있습니다. <br /><br /> HSM 보호 키를 사용하려면 Azure Key Vault 프리미엄 서비스 계층이 있어야 합니다.|Azure Active Directory 구성 및 Azure Rights Management 사용자 지정 템플릿 구성에 대한 액세스 권한을 제공하는 무료 Azure 구독(**Azure Active Directory에 액세스**)은 Azure Key Vault를 사용하기에 충분하지 않습니다. BYOK에 대해 사용할 수 있는 Azure 구독이 있는지 확인하려면 [Azure Resource Manager](https://msdn.microsoft.com/library/azure/mt786812\(v=azure.300\).aspx) PowerShell cmdlet을 사용하세요. <br /><br /> 1. **Run as administrator**(관리자로 실행) 옵션으로 Azure PowerShell 세션을 시작하고 다음 명령을 사용하여 Azure Information Protection 테넌트의 전역 관리자로 로그인합니다. `Login-AzureRmAccount`<br /><br />2. 다음을 입력하고 구독 이름 및 ID, Azure Information Protection 테넌트 ID에 대해 표시된 값과 상태가 활성화되어 있는지 확인합니다. `Get-AzureRmSubscription`<br /><br />값이 표시되지 않고 프롬프트로 돌아가는 경우 BYOK를 사용할 수 있는 Azure 구독이 없습니다. <br /><br />**참고**: BYOK 필수 조건 외에도, 소프트웨어 키-하드웨어 키를 사용하여 AD RMS에서 Azure Information Protection으로 마이그레이션하는 경우 11.62 버전 이상의 Thales 펌웨어가 있어야 합니다.|
|온-프레미스에서 생성한 HSM 보호 키를 사용하려면: <br /><br />- Key Vault BYOK에 대해 나열된 모든 필수 조건 |Azure Key Vault 설명서에서 [BYOK에 대한 필수 조건](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok)을 참조하세요. <br /><br /> **참고**: BYOK 필수 조건 외에도, 소프트웨어 키-하드웨어 키를 사용하여 AD RMS에서 Azure Information Protection으로 마이그레이션하는 경우 11.62 버전 이상의 Thales 펌웨어가 있어야 합니다.|
|테넌트 키를 포함할 키 자격 증명 모음이 Key Vault의 가상 네트워크 서비스 끝점(현재 미리 보기에 있음)을 사용하는 경우: <br /><br />- 신뢰할 수 있는 Microsoft 서비스가 이 방화벽을 우회하도록 하는 옵션을 선택합니다.|자세한 내용은 [Announcing Virtual Network Service Endpoints for Key Vault(preview)](https://blogs.technet.microsoft.com/kv/2018/06/25/announcing-virtual-network-service-endpoints-for-key-vault-preview/)(Key Vault의 네트워크 서비스 끝점(미리 보기) 발표)를 참조하세요.|
|Windows PowerShell용 Azure Rights Management 관리 모듈.|설치 지침은 [AADRM PowerShell 모듈 설치](../deploy-use/install-powershell.md)를 참조하세요. <br /><br />이전에 이 Windows PowerShell 모듈을 설치한 경우 다음 명령을 실행하여 버전 번호가 **2.9.0.0** 이상인지 확인합니다. `(Get-Module aadrm -ListAvailable).Version`|

Thales HSM 및 Azure 주요 자격 증명 모음과 함께 사용되는 방법에 대한 자세한 내용은 [Thales 웹 사이트](https://www.thales-esecurity.com/msrms/cloud)를 참조하세요.

### <a name="choosing-your-key-vault-location"></a>키 자격 증명 모음 위치 선택

Azure Information에 대한 테넌트 키로 사용할 키를 포함하는 키 자격 증명 모음을 만드는 경우 위치를 지정해야 합니다. 이 위치는 Azure 지역 또는 Azure 인스턴스입니다.

먼저 규정 준수를 위해 선택하고 네트워크 대기 시간을 최소화하도록 선택하십시오.

- 규정 준수를 위해 BYOK 키 토폴로지를 선택한 경우 해당 규정 준수 요구 사항에 따라 Azure Information Protection 테넌트 키를 저장하는 Azure 지역 또는 Azure 인스턴스가 필요할 수 있습니다.

- 보호를 위한 모든 암호화 호출이 Azure Information Protection 테넌트 키에 연결되기 때문에 이러한 호출이 발생하는 네트워크 대기 시간을 최소화해야 합니다. 이렇게 하려면 Azure Information Protection 테넌트와 동일한 Azure 지역이나 인스턴스에 키 자격 증명 모음을 만듭니다.

Azure Information Protection 테넌트의 위치를 식별하려면 [Get-AadrmConfiguration](/powershell/module/aadrm/get-aadrmconfiguration) PowerShell cmdlet을 사용하고 URL에서 해당 지역을 식별하십시오. 예를 들면 다음과 같습니다.

    LicensingIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

지역은 **rms.na.aadrm.com**으로 식별할 수 있으며 이 예의 경우 북아메리카입니다.

다음 테이블을 사용하여 네트워크 대기 시간을 최소하기 위해 권장되는 Azure 영역 또는 인스턴스를 확인하십시오.

|Azure 지역 또는 인스턴스|키 자격 증명 모음에 권장되는 위치|
|---------------|--------------------|
|rms.**na**.aadrm.com|**미국 중북부** 또는 **미국 동부**|
|rms.**eu**.aadrm.com|**북유럽** 또는 **유럽 서부**|
|rms.**ap**.aadrm.com|**동아시아** 또는 **동남 아시아**|
|rms.**sa**.aadrm.com|**미국 서부** 또는 **미국 동부**|
|rms.**govus**.aadrm.com|**미국 중부** 또는 **미국 동부 2**|


### <a name="instructions-for-byok"></a>BYOK에 대한 지침

Azure Key Vault 설명서를 사용하여 Azure Information Protection에 사용할 키 자격 증명 모음 및 키를 만드십시오. 예를 들어 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 참조하세요.

키 길이는 2048비트(권장) 또는 1024비트여야 합니다. 다른 키 길이는 Azure Information Protection에서 지원되지 않습니다.

온-프레미스에서 HSM 보호 키를 만들어서 키 자격 증명 모음에 HSM 보호 키로 전송하려면 [Azure Key Vault용으로 HSM 보호 키를 생성하여 전송하는 방법](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/)의 절차를 따르십시오.

Key Vault에 저장된 키에는 키 ID가 있습니다. 키 ID는 키 자격 증명 모음의 이름, 키 컨테이너, 키 이름 및 키 버전이 포함된 URL입니다. 예: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. 이 키를 사용하려면 Key Vault URL을 지정하여 Azure Information Protection을 구성해야 합니다.

Azure Information Protection에서 키를 사용할 수 있으려면 조직의 키 자격 증명 모음에서 Azure Rights Management 서비스에 키를 사용할 수 있도록 권한을 부여해야 합니다. 그렇게 하려면 Azure Key Vault 관리자는 Key Vault PowerShell cmdlet([Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy))을 사용하고 GUID 00000012-0000-0000-c000-000000000000을 사용하여 Azure Rights Management 서비스 주체에 권한을 부여합니다. 예를 들면 다음과 같습니다.

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get

이제 Azure Information Protection을 구성하여 조직의 Azure Information Protection 테넌트 키로 이 키를 사용할 준비가 되었습니다. Azure RMS cmdlet을 사용하여 Azure Rights Management 서비스에 연결한 다음 로그인합니다.

    Connect-AadrmService

그런 다음 [Use-AadrmKeyVaultKey cmdlet](/powershell/module/aadrm/use-aadrmkeyvaultkey)을 실행하여 키 URL을 지정합니다. 예를 들면 다음과 같습니다.

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

> [!IMPORTANT]
> 이 예에서는 "aaaabbbbcccc111122223333"이 사용할 키 버전입니다. 버전을 지정하지 않으면 경고 없이 키의 현재 버전이 사용되고 작업할 명령이 표시됩니다. 그러나 Key Vault의 키가 나중에 업데이트(갱신)되는 경우, Use-AadrmKeyVaultKey 명령을 다시 실행하더라도 Azure Rights Management 서비스에서 테넌트에 대해 작동을 중지합니다.
>
>이 명령을 실행할 때 키 이름과 함께 키 버전을 지정하세요. Azure Key Vault cmd([Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey))를 사용하여 현재 키의 버전 번호를 가져올 수 있습니다. 예를 들어 `Get-AzureKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`를 구성할 수 있습니다.

Azure Information Protection에 대해 키 URL이 제대로 설정되어 있는지 확인하려면 Azure Key Vault에서 [Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey)를 실행하여 키 URL을 확인할 수 있습니다.

마지막으로 Azure Rights Management 서비스가 이미 활성화된 경우 [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)를 실행하여 Azure Information Protection에 이 키를 Azure Rights Management 서비스에 대한 활성 테넌트 키로 사용하도록 알립니다. 이 단계를 수행하지 않으면 Azure Information Protection은 테넌트에 대해 자동으로 생성된 기본 Microsoft 관리 키를 계속 사용합니다.


## <a name="next-steps"></a>다음 단계

이제 테넌트 키를 계획하고 필요한 경우 생성하고 구성했으므로 다음을 수행하십시오.

1.  테넌트 키 사용을 시작합니다.
    
    - 아직 Rights Management 서비스를 활성화하지 않은 경우 조직에서 Azure Information Protection 사용을 시작할 수 있도록 Rights Management 서비스를 활성화해야 합니다. 사용자는 즉시 테넌트 키(Microsoft에서 관리하거나 Azure Key Vault에서 고객이 직접 관리함) 사용을 시작합니다.
    
        활성화에 대한 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.
        
    - 이미 Rights Management 서비스를 활성화한 후 직접 테넌트 키를 관리하기로 결정한 경우 사용자는 점진적으로 이전 테넌트 키에서 새 테넌트 키로 전환하며, 시차를 두고 진행되는 이 전환이 완료되기까지 몇 주가 걸릴 수 있습니다. 권한 있는 사용자는 이전 테넌트 키로 보호된 문서와 파일에 계속 액세스할 수 있습니다.
        
2. Azure Rights Management 서비스에서 수행하는 모든 트랜잭션을 기록하는 사용 현황 로깅을 사용하는 것이 좋습니다.
    
    직접 테넌트 키를 관리하기로 결정한 경우 로깅에는 테넌트 키 사용에 대한 정보가 포함됩니다. Excel에 표시된 다음과 같은 로그 파일의 코드 조각을 참조하세요. 여기서 **KeyVaultDecryptRequest** 및 **KeyVaultSignRequest** 요청 유형은 테넌트 키가 사용되고 있음을 보여줍니다.
    
    ![테넌트 키가 사용되는 위치의 로그 파일](../media/RMS_Logging.png)
    
    사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management Service 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.
    
3.  테넌트 키 관리.
    
    테넌트 키의 수명 주기 작업에 대한 자세한 내용은 [Azure Information Protection 테넌트 키에 대한 작업](../deploy-use/operations-tenant-key.md)을 참조하세요.
