---
title: 소프트웨어 보호된 키-HSM 보호된 키 마이그레이션 - AIP
description: AD RMS에서 Azure Information Protection으로 마이그레이션 경로에 포함되며, AD RMS 키가 소프트웨어로 보호되고 Azure Key Vault의 HSM으로 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.service: information-protection
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bacfe4f0bdc7c400e58bc3f054d3539b6883a9fd
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808054"
---
# <a name="step-2-software-protected-key-to-hsm-protected-key-migration"></a>2단계: 소프트웨어 보호된 키-HSM 보호된 키 마이그레이션

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


[AD RMS에서 Azure Information Protection으로 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS 키가 소프트웨어로 보호되고 Azure Key Vault의 HSM으로 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다. 

선택한 구성 시나리오가 아닌 경우 [4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection)로 돌아가서 다른 구성을 선택합니다.

다음은 Azure Information Protection에 AD RMS 구성을 가져오기 위한 네 부분으로 구성된 절차로, 이 작업을 수행하면 Azure Key Vault에서 사용자가 관리하는(BYOK) Azure Information Protection 테넌트 키를 만들 수 있습니다.

먼저 AD RMS 구성 데이터에서 SLC(서버 사용 허가자 인증서) 키를 추출하여 온-프레미스 Thales HSM에 전송하고, HSM 키를 패키지하고 Azure Key Vault로 전송한 다음 Azure Information Protection의 Azure Rights Management에서 주요 자격 증명 모음에 액세스할 수 있도록 권한을 부여한 다음 구성 데이터를 가져와야 합니다.

Azure Information Protection 테넌트 키는 Azure Key Vault에 저장되고 관리되므로 이 마이그레이션 부분에서는 Azure Information Protection 외에도 Azure Key Vault에서 관리가 필요합니다. 조직에서 고객 외에 다른 관리자가 Azure Key Vault를 관리하는 경우 해당 관리자와 조정하고 협력하여 이러한 절차를 완료해야 합니다.

시작하기 전에 조직에 Azure Key Vault에 만든 주요 자격 증명 모음이 있으며 HSM 보호된 키를 지원하는지 확인합니다. Azure Information Protection 전용의 키 자격 증명 모음은 필수는 아니지만 갖고 있으면 좋습니다. 이 키 자격 증명 모음은 Azure Information Protection의 Azure Rights Management 서비스에서 액세스하도록 구성되어, Azure Information Protection 키만 이 키 자격 증명 모음에 저장될 수 있게 합니다.


> [!TIP]
> Azure Key Vault에 대한 구성 단계를 수행하려는데 이 Azure 서비스에 익숙하지 않은 경우 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 먼저 검토하면 도움이 됩니다. 


## <a name="part-1-extract-your-slc-key-from-the-configuration-data-and-import-the-key-to-your-on-premises-hsm"></a>1부: 구성 데이터에서 SLC 키를 추출하고 온-프레미스 HSM으로 키 가져오기

1.  Azure Key Vault 관리자: 내보낸 각 SLC 키를 Azure Key Vault에 저장하려는 경우 Azure Key Vault 설명서에서 [Azure Key Vault에 대해 BYOK(Bring Your Own Key) 구현](/azure/key-vault/key-vault-hsm-protected-keys#implementing-bring-your-own-key-byok-for-azurekey-vault) 섹션의 다음 단계를 사용하세요.

    -   **키를 생성하여 Azure 주요 자격 증명 모음 HSM으로 전송**: [1단계: 인터넷에 연결된 워크스테이션 준비](/azure/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: [2단계: 연결이 끊어진 워크스테이션 준비](/azure/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    내보낸 구성 데이터(.xml) 파일에 테넌트 키가 이미 있으므로, 테넌트 키를 생성하는 단계는 수행하지 않도록 합니다. 대신 도구를 실행하여 파일에서 이 키를 추출한 후 온-프레미스 HSM으로 가져옵니다. 도구를 실행하면 파일 두 개가 만들어집니다.

    - Azure Information Protection 테넌트로 가져올 준비가 되는, 키가 없는 새 구성 데이터 파일

    - 온-프레미스 HSM으로 가져올 준비가 되는, 키가 있는 PEM 파일(키 컨테이너)

2. Azure Information Protection 관리자 또는 Azure Key Vault 관리자: 연결이 끊어진 워크스테이션에서 [Azure RMS 마이그레이션 도구 키트](https://go.microsoft.com/fwlink/?LinkId=524619)의 TpdUtil 도구를 실행합니다. 예를 들어 ContosoTPD.xml이라는 구성 데이터 파일을 복사할 E 드라이브에 도구가 설치되어 있는 경우:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    둘 이상의 RMS 구성 데이터 파일이 있는 경우 나머지 파일에 대해 이 도구를 실행합니다.

    설명, 사용법 및 예제가 포함되어 있는 이 도구에 대한 도움말을 보려면 매개 변수 없이 TpdUtil.exe를 실행합니다.

    이 명령에 대한 추가 정보:

    - **/tpd**: 내보낸 AD RMS 구성 데이터 파일의 이름과 전체 경로를 지정합니다. 전체 매개 변수 이름은 **TpdFilePath**입니다.

    - **/otpd**: 키가 없는 구성 데이터 파일의 출력 파일 이름을 지정합니다. 전체 매개 변수 이름은 **OutPfxFile**입니다. 이 매개 변수를 지정하지 않으면 출력 파일은 접미사가 **_keyless**인 원래 파일 이름이 기본값이 되며 현재 폴더에 저장됩니다.

    - **/opem**: 추출된 키가 포함된 PEM 파일의 출력 파일 이름을 지정합니다. 전체 매개 변수 이름은 **OutPemFile**입니다. 이 매개 변수를 지정하지 않으면 출력 파일은 접미사가 **_key**인 원래 파일 이름이 기본값이 되며 현재 폴더에 저장됩니다.

    - 이 명령을 실행할 때 암호를 지정하지 않은 경우(**TpdPassword** 전체 매개 변수 이름 또는 **pwd** 간단한 매개 변수 이름을 사용하여) 암호를 지정하라는 메시지가 표시됩니다.

3. 연결이 끊어진 동일한 워크스테이션에서 Thales 설명서에 따라 Thales HSM을 연결하고 구성합니다. 이제 ContosoTPD.pem에 대한 고유한 파일 이름을 대체해야 하는 다음 명령을 사용하여 연결된 Thales HSM에 키를 가져올 수 있습니다.

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >파일이 두 개 이상인 경우 마이그레이션 후 콘텐츠를 보호하기 위해 Azure RMS에서 사용하려는 HSM 키에 해당하는 파일을 선택합니다.

    다음과 비슷한 출력 디스플레이가 생성됩니다.

    **키 생성 매개 변수:**

    **작업 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 수행할 작업 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 가져오기**

    **응용 프로그램 &nbsp;&nbsp;&nbsp;&nbsp;응용 프로그램&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 기본**

    **확인 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 구성 키의 보안 확인&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 예**

    **유형 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 키 유형 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; RSA 키가 포함된 PEM 파일 &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 키 식별자 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 키 이름 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **키를 가져왔습니다.**

    **키 경로: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

이 출력은 키에 저장되는 암호화된 복사본과 함께 온-프레미스 Thales HSM 장치에 개인 키(이 예에서는 "key_simple_contosobyok")가 마이그레이션되었음을 확인합니다. 

SLC 키를 추출하고 온-프레미스 HSM으로 가져왔으므로 HSM 보호된 키를 패키지하고 Azure 주요 자격 증명 모음으로 전송할 준비가 되었습니다.

> [!IMPORTANT]
> 이 단계를 완료하면 이러한 PEM 파일을 연결이 끊어진 워크스테이션에서 안전하게 지워서 권한이 없는 사용자가 액세스할 수 없도록 합니다. 예를 들어 "cipher /w: E"를 실행하여 E: 드라이브에서 모든 파일을 안전하게 삭제합니다.

## <a name="part-2-package-and-transfer-your-hsm-key-to-azure-key-vault"></a>2부: HSM 키를 패키지한 후 Azure 주요 자격 증명 모음으로 전송

Azure Key Vault 관리자: 내보낸 각 SLC 키를 Azure Key Vault에 저장하려는 경우 Azure Key Vault 설명서에서 [Azure Key Vault에 대해 BYOK(Bring Your Own Key) 구현](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azurekey-vault) 섹션의 다음 단계를 사용하세요.

- [4단계: 키 전송 준비](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

- [5단계: Azure Key Vault에 키 전송](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azurekey-vault)

키가 이미 있으므로 키 쌍을 생성하는 단계를 수행하지 마세요. 대신 명령을 실행하여 온-프레미스 HSM에서 이 키를 전송합니다(이 예에서는 KeyIdentifier 매개 변수에 "contosobyok" 사용).

Azure 주요 자격 증명 모음으로 키를 전송하기 전에 권한이 낮춰진 키 복사본을 만들고(4.1단계) 키를 암호화할 때(4.3단계) KeyTransferRemote.exe 유틸리티가 **Result: SUCCESS**를 반환하는지 확인합니다.

키를 Azure 주요 자격 증명 모음으로 업로드할 때 키 속성이 표시되며 여기에 키 ID가 포함되어 있습니다. **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**과 유사하게 표시됩니다. 이 URL은 Azure Information Protection 관리자가 Azure Information Protection의 Azure Rights Management 서비스에 이 키를 테넌트 키로 사용하도록 지시하는 데 필요하므로 URL을 기록해 두세요.

그러면 [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) cmdlet을 사용하여 Key Vault에 액세스할 Azure Rights Management 서비스 주체에 권한을 부여할 수 있습니다. 필요한 권한은 decrypt, encrypt, unwrapkey, wrapkey, verify 및 sign입니다.

예를 들어 Azure Information Protection에 대해 만든 Key Vault의 이름이 contosorms-byok-kv이고 리소스 그룹 이름이 contosorms-byok-rg인 경우 다음 명령을 실행합니다.
    
    Set-AzureRmKeyVaultAccessPolicy -VaultName "contosorms-byok-kv" -ResourceGroupName "contosorms-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

이제 HSM 키를 Azure Key Vault로 전송했으므로 AD RMS 구성 데이터를 가져올 수 있습니다.

## <a name="part-3-import-the-configuration-data-to-azure-information-protection"></a>3부: 구성 데이터를 Azure Information Protection으로 가져오기

1. Azure Information Protection 관리자: 인터넷에 연결된 워크스테이션 및 PowerShell 세션에서 TpdUtil 도구를 실행한 후 SLC 키가 제거된 새 구성 데이터 파일(.xml)을 복사합니다.

2. [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) cmdlet을 사용하여 첫 번째 .xml 파일을 업로드합니다. 예를 들어 AD RMS 클러스터를 암호화 모드 2로 업그레이드한 경우 추가 파일을 하나 이상 가져와야 합니다.

    이 cmdlet을 실행하려면 구성 데이터 파일에 대해 이전에 지정한 암호 및 이전 단계에서 식별된 키의 URL이 필요합니다.

    예를 들어 이전 단계의 키 URL 값 및 C:\contoso_keyless.xml의 구성 데이터 파일을 사용하는 경우 암호를 저장하려면 다음을 먼저 실행합니다.
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
   지정한 암호를 입력하여 구성 데이터 파일을 내보냅니다. 그리고 다음 명령을 실행한 후 이 작업을 수행하려는 것을 확인합니다.

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword $TPD_Password –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```

    이 가져오기의 일부로, SLC 키를 가져오고 보관됨으로 자동 설정됩니다.

3. 각 파일을 업로드한 경우 [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)를 실행하여 AD RMS 클러스터에서 현재 활성 SLC 키와 일치하는 가져온 키를 지정할 수 있습니다.

4. [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

Azure Key Vault에서 Azure Information Protection 테넌트 키가 사용하는 키를 나중에 확인해야 하는 경우 [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys) Azure RMS cmdlet을 사용합니다.


이제 [5단계. Azure Rights Management 서비스 활성화](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service)로 이동할 수 있습니다.


