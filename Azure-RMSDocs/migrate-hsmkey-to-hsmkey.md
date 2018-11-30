---
title: HSM 보호된 키-HSM 보호된 키 마이그레이션 - AIP
description: AD RMS에서 Azure Information Protection으로 마이그레이션 경로에 포함되며, AD RMS HSM으로 보호되고 Azure Key Vault의 HSM으로 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7ddaf0a54aa116a317cee8699caf437faae9676f
ms.sourcegitcommit: bcc9e0f9ae8512bf48d819533cf8ef3b667eb298
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52330335"
---
# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>2단계: HSM 보호된 키-HSM 보호된 키 마이그레이션

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


[AD RMS에서 Azure Information Protection으로 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS HSM으로 보호되고 Azure Key Vault의 HSM으로 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다. 

선택한 구성 시나리오가 아닌 경우 [4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection)로 돌아가서 다른 구성을 선택합니다.

> [!NOTE]
> 이러한 지침에서는 AD RMS 키가 모듈로 보호되어 있다고 가정합니다. 이는 가장 일반적인 경우입니다. 

다음은 Azure Information Protection에 HSM 키 및 AD RMS 구성을 가져오기 위한 두 부분으로 구성된 절차로, 이 작업을 수행하면 사용자가 관리하는(BYOK) Azure Information Protection 테넌트 키를 만들 수 있습니다.

Azure Information Protection 테넌트 키는 Azure Key Vault에 저장되고 관리되므로 이 마이그레이션 부분에서는 Azure Information Protection 외에도 Azure Key Vault에서 관리가 필요합니다. 조직에서 고객 외에 다른 관리자가 Azure Key Vault를 관리하는 경우 해당 관리자와 조정하고 협력하여 이러한 절차를 완료해야 합니다.

시작하기 전에 조직에 Azure Key Vault에 만든 주요 자격 증명 모음이 있으며 HSM 보호된 키를 지원하는지 확인합니다. Azure Information Protection 전용의 키 자격 증명 모음은 필수는 아니지만 갖고 있으면 좋습니다. Azure Information Protection 키만 이 주요 자격 증명 모음에 저장될 수 있도록 이 주요 자격 증명 모음은 Azure Rights Management 서비스에 액세스 권한을 허용하도록 구성됩니다.


> [!TIP]
> Azure Key Vault에 대한 구성 단계를 수행하려는데 이 Azure 서비스에 익숙하지 않은 경우 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 먼저 검토하면 도움이 됩니다. 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>1부: Azure 주요 자격 증명 모음에 키 전송

이 절차는 Azure 주요 자격 증명 모음의 관리자가 수행합니다.

1. 내보낸 각 SLC 키를 Azure Key Vault에 저장하려는 경우 [Azure Key Vault에 대해 BYOK(Bring Your Own Key) 구현](/azure/key-vault/key-vault-hsm-protected-keys#implementing-bring-your-own-key-byok-for-azure-key-vault)을 사용하여 Azure Key Vault 설명서의 지침을 따르세요. 다음과 같은 예외가 있습니다.

    - AD RMS 배포에서 생성된 동일한 키가 이미 있으므로 **테넌트 키 생성** 단계는 수행하지 마세요. 대신, Thales 설치의 AD RMS 서버에서 사용되는 키를 식별하고, 마이그레이션 중에 이 키를 사용해야 합니다. Thales 암호화된 키 파일 이름은 일반적으로 서버에서 로컬로 **key<*keyAppName*><*keyIdentifier*>** 입니다.

    키를 Azure 주요 자격 증명 모음으로 업로드할 때 키 속성이 표시되며 여기에 키 ID가 포함되어 있습니다. https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333과 유사하게 표시됩니다. 이 URL은 Azure Information Protection 관리자가 Azure Rights Management 서비스에 이 키를 테넌트 키로 사용하도록 지시하는 데 필요하므로 URL을 기록해 두세요.

2. 인터넷에 연결된 워크스테이션의 PowerShell 세션에서 [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) cmdlet을 사용하여 Azure Rights Management 서비스 주체가 Azure Information Protection 테넌트 키를 저장하는 Key Vault에 액세스하도록 권한을 부여합니다. 필요한 권한은 decrypt, encrypt, unwrapkey, wrapkey, verify 및 sign입니다.
    
    예를 들어 Azure Information Protection에 대해 만든 주요 자격 증명 모음의 이름이 contoso-byok-ky이고 리소스 그룹 이름이 contoso-byok-rg인 경우 다음 명령을 실행합니다.
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get


이제 Azure Information Protection의 Azure Rights Management에 대해 Azure Key Vault에 HSM 키를 준비했으므로 AD RMS 구성 데이터를 가져올 수 있습니다.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>2부: 구성 데이터를 Azure Information Protection으로 가져오기

이 절차는 Azure Information Protection의 관리자가 수행합니다.

1. 인터넷에 연결된 워크스테이션 및 PowerShell 세션에서 [Connnect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에 연결합니다.
    
    그런 다음 [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) cmdlet을 사용하여 트러스트된 각 게시 도메인(.xml) 파일을 업로드합니다. 예를 들어 AD RMS 클러스터를 암호화 모드 2로 업그레이드한 경우 추가 파일을 하나 이상 가져와야 합니다.
    
    이 cmdlet을 실행하려면 각 구성 데이터 파일에 대해 이전에 지정한 암호 및 이전 단계에서 식별된 키의 URL이 필요합니다.
    
    예를 들어 이전 단계의 키 URL 값 및 C:\contoso-tpd1.xml의 구성 데이터 파일을 사용하는 경우 암호를 저장하려면 다음을 먼저 실행합니다.
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
    지정한 암호를 입력하여 구성 데이터 파일을 내보냅니다. 그리고 다음 명령을 실행한 후 이 작업을 수행하려는 것을 확인합니다.
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword $TPD_Password –KeyVaultKeyUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```
    
    이 가져오기의 일부로, SLC 키를 가져오고 보관됨으로 자동 설정됩니다.

2.  각 파일을 업로드한 경우 [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)를 실행하여 AD RMS 클러스터에서 현재 활성 SLC 키와 일치하는 가져온 키를 지정할 수 있습니다. 이 키는 Azure Rights Management 서비스의 활성 테넌트 키가 됩니다.

3.  [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

Azure Key Vault에서 Azure Information Protection 테넌트 키가 사용하는 키를 나중에 확인해야 하는 경우 [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys) Azure RMS cmdlet을 사용합니다.

이제 [5단계. Azure Rights Management 서비스 활성화](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service)로 이동할 수 있습니다.


