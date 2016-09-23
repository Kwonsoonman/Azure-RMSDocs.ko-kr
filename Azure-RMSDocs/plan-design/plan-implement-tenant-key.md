---
title: "Azure 권한 관리 테넌트 키 계획 및 구현 | Azure RMS"
description: "Azure RMS용 RMS(Rights Management) 테넌트 키를 계획 및 관리하는 데 도움이 되는 정보를 제공합니다. 예를 들어 Microsoft에서 테넌트 키(기본값)를 관리하는 대신, 조직에 적용되는 특정 규정을 준수하도록 자체 테넌트 키를 관리하려고 할 수 있습니다. 자체 테넌트 키를 관리하는 것을 BYOK(bring your own key)라고도 합니다."
author: cabailey
manager: mbaldwin
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df79a02238c7cbadaae450ad8dabc03478de27e9
ms.openlocfilehash: 0e3e77073898e2ae9f84f555183fb6fcbc7d2d8a


---

# Azure 권한 관리 테넌트 키 계획 및 구현

>*적용 대상: Azure 권한 관리, Office 365*

이 문서의 정보는 Azure RMS용 권한 관리(RMS) 테넌트 키를 계획 및 관리하는 데 도움이 됩니다. 예를 들어 Microsoft에서 테넌트 키(기본값)를 관리하는 대신, 조직에 적용되는 특정 규정을 준수하도록 자체 테넌트 키를 관리하려고 할 수 있습니다.  자체 테넌트 키를 관리하는 것을 BYOK(bring your own key)라고도 합니다.

> [!NOTE]
> RMS 테넌트 키는 SLC(서버 사용 허가자 인증서) 키라고도 합니다. Azure RMS는 Azure RMS를 구독하는 각 조직에 대해 하나 이상의 키를 유지 관리합니다. 조직 내에서 키가 RMS에 사용될 때마다(예: 사용자 키, 컴퓨터 키, 문서 암호화 키), 이러한 키는 RMS 테넌트 키에 암호화 방식으로 체이닝됩니다.

**한 눈에 보기:** 다음 표를 참조하여 권장되는 테넌트 키 토폴로지를 빠르게 확인할 수 있습니다. 자세한 내용은 추가 설명서를 참조하세요.

Microsoft에서 관리하는 테넌트 키를 사용하여 Azure RMS를 배포하는 경우 나중에 BYOK로 변경할 수 있습니다. 그러나 현재는 Azure RMS 테넌트 키를 BYOK에서 Microsoft 관리 유형으로 변경할 수 없습니다.

|비즈니스 요구 사항|권장되는 테넌트 키 토폴로지|
|------------------------|-----------------------------------|
|특수한 하드웨어 필요 없이 신속하게 Azure RMS 배포|Microsoft에서 관리|
|Azure RMS가 있는 Exchange Online에서 전체 IRM 기능 필요|Microsoft에서 관리|
|사용자가 생성한 키를 HSM(하드웨어 보안 모듈)에서 보호|BYOK<br /><br />현재 이 구성을 사용하면 Exchange Online에서 IRM 기능이 축소됩니다. 자세한 내용은 [BYOK 가격 및 제한 사항](byok-price-restrictions.md)을 참조하세요.|

## 테넌트 키 토폴로지 선택: Microsoft가 관리(기본값) 또는 고객이 직접 관리(BYOK)
조직에 가장 적합한 테넌트 키 토폴로지를 결정하세요. 기본적으로 Azure RMS는 고객의 테넌트 키를 생성하고 테넌트 키 수명 주기의 대부분의 측면을 관리합니다. 이 옵션은 관리 오버헤드가 가장 낮은 가장 간단한 옵션입니다. 대부분의 경우 고객은 테넌트 키를 가지고 있다는 사실조차 알 필요가 없습니다. Azure RMS에 등록하기만 하면 나머지 키 관리 프로세스는 Microsoft에서 처리합니다.

또는 [Azure 주요 자격 증명 모음](https://azure.microsoft.com/services/key-vault/)을 사용하여 테넌트 키를 완전히 제어할 수 있습니다. 이 시나리오에서는 테넌트 키를 만들고 프레미스에 마스터 복사본을 유지합니다. 이 시나리오를 흔히 BYOK(Bring Your Own Key)라고 합니다. 이 옵션을 사용할 경우 다음과 같은 상황이 발생합니다.

1.  고객이 IT 정책 및 보안 정책에 따라 고객의 프레미스에서 테넌트 키를 생성합니다.

2.  Azure 주요 자격 증명 모음을 사용하여 고객 소유의 HSM(하드웨어 보안 모듈)에서 Microsoft가 소유하고 관리하는 HSM으로 테넌트 키를 안전하게 전송합니다. 이 프로세스 전체에서 테넌트 키는 하드웨어 보호 경계를 벗어나지 않습니다.

3.  테넌트 키를 Microsoft로 전송할 때 테넌트 키는 Azure 주요 자격 증명 모음으로 보호됩니다.

선택 사항이기는 하지만 테넌트 키가 언제, 어떻게 사용되는지를 정확하게 확인하기 위해 Azure RMS의 근 실시간 사용 현황 로그를 사용하기를 원할 수도 있습니다.

> [!NOTE]
> 추가 보호 조치로 Azure 주요 자격 증명 모음에서는 북아메리카, EMEA(유럽, 중동 및 아시아) 및 아시아 같은 지역의 데이터 센터에 별도의 보안 도메인을 사용합니다. 그리고 Microsoft Azure Germany 및 Azure Government처럼 Azure의 여러 인스턴스에 대해서도 별도의 보안 도메인을 사용합니다. 고객의 고유 테넌트 키를 관리할 때 이 키는 고객의 RMS 테넌트가 등록된 지역 또는 인스턴스의 보안 도메인에 연결됩니다. 예를 들어 유럽 고객의 테넌트 키를 북아메리카 또는 아시아의 데이터 센터에서 사용할 수 없습니다.

## 테넌트 키 수명 주기
고객이 Microsoft가 고객의 테넌트 키를 관리해야 한다고 결정한 경우 Microsoft는 대부분의 키 수명 주기 작업을 처리합니다. 그러나 고객이 직접 테넌트 키를 관리하기로 결정한 경우 Azure 주요 자격 증명 모음의 키 수명 주기 작업의 많은 부분과 일부 추가 절차는 고객의 책임입니다.

다음 다이어그램은 이러한 두 옵션을 비교해서 보여줍니다. 첫 번째 다이어그램은 Microsoft가 테넌트 키를 관리하는 기본 구성을 사용할 경우 관리자 오버헤드가 얼마나 작은지 보여줍니다.

![Azure RMS 테넌트 키 수명 주기- Microsoft에서 관리, 기본값](../media/RMS_BYOK_cloud.png)

두 번째 다이어그램은 고객이 직접 테넌트 키를 관리할 경우 필요한 추가 단계를 보여줍니다.

![Azure RMS 테넌트 키 수명 주기 - 사용자가 직접 관리, BYOK](../media/RMS_BYOK_onprem4.png)

고객이 Microsoft에서 테넌트 키를 관리하도록 결정할 경우 키를 생성하기 위해 수행해야 할 추가 작업이 없으므로 [다음 단계](plan-implement-tenant-key.md#next-steps)로 바로 이동하세요.  

테넌트 키를 직접 관리하기로 결정한 경우 다음 섹션에서 자세한 내용을 확인하세요.

## Azure 권한 관리 테넌트 키 구현

직접 테넌트 키를 생성하고 관리하기로 결정한 경우(BYOK(Bring Your Own Key) 시나리오) 이 섹션의 정보 및 절차를 사용하세요.


> [!IMPORTANT]
> Microsoft에서 관리하는 테넌트 키를 사용하여 Azure RMS 사용을 시작했지만 이제는 BYOK 방식으로 전환하여 테넌트 키를 직접 관리하려는 경우, 보관된 키를 사용하여 이전에 보호했던 문서와 전자 메일에 계속 액세스할 수 있습니다. 그러나 Office 2010을 실행하는 사용자가 있는 경우에는 이러한 절차를 실행하기 전에 [Microsoft 지원에 문의](../get-started/information-support.md#to-contact-microsoft-support)하세요. 이러한 컴퓨터에서는 몇 가지 구성 단계를 추가로 수행해야 합니다.
> 
> 조직에 키 처리에 대한 특정 조직이 있는 경우에도 [Microsoft 지원에 문의](../get-started/information-support.md#to-contact-microsoft-support)하세요.

### BYOK 사전 요구 사항
BYOK(Bring Your Own Key) 사전 요구 사항 목록은 다음 표를 참조하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure RMS를 지원하는 구독|사용 가능한 구독에 대한 자세한 내용은 [Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.|
|개인용 또는 Exchange Online용으로 RMS를 사용하지 않도록 합니다. 또는 Exchange Online을 사용하는 경우 이 구성에서 BYOK를 사용할 때의 제한 사항을 이해하고 받아들여야 합니다.|BYOK와 관련된 현재 제한 사항에 대한 자세한 내용은 [BYOK 가격 및 제한 사항](byok-price-restrictions.md)을 참조하세요.<br /><br />**중요**: 현재 BYOK는 Exchange Online과 호환되지 않습니다.|
|주요 자격 증명 모음 BYOK에 대해 나열된 모든 필수 조건.|Azure 주요 자격 증명 모음 설명서에서 [BYOK에 대한 필수 조건](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok)을 참조하세요. <br /><br />**참고**: 소프트웨어 키-하드웨어 키를 사용하여 AD RMS에서 Azure RMS로 마이그레이션하는 경우 11.62 버전 이상의 Thales 펌웨어가 있어야 합니다.|
|Windows PowerShell용 Azure RMS 관리 모듈.|설치 지침은 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요. <br /><br />이전에 이 Windows PowerShell 모듈을 설치한 경우 다음 명령을 실행하여 버전 번호가 **2.5.0.0** 이상인지 확인합니다. `(Get-Module aadrm -ListAvailable).Version`|

Thales HSM 및 Azure 주요 자격 증명 모음과 함께 사용되는 방법에 대한 자세한 내용은 [Thales 웹 사이트](https://www.thales-esecurity.com/msrms/cloud)를 참조하세요.

고유한 테넌트 키를 생성하고 Azure 주요 자격 증명 모음으로 전송하려면 Azure 주요 자격 증명 모음 설명서에서 [Azure 주요 자격 증명 모음에 대해 HSM 보호된 키를 생성하고 전송하는 방법](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/)의 절차를 따르세요.

키를 주요 자격 증명 모음으로 전송하면 주요 자격 증명 모음에 자격 증명 모음의 이름, 키 컨테이너, 키의 이름 및 키 버전이 들어 있는 URL인 키 ID가 지정됩니다. 예를 들면 다음과 같습니다. **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333** 이 URL을 지정하여 Azure RMS에서 이 키를 사용하도록 알려야 합니다.

하지만 Azure RMS에서 키를 사용하기 전에 Azure RMS는 조직의 주요 자격 증명 모음의 키를 사용할 수 있는 권한을 받아야 합니다. 그렇게 하려면 Azure 주요 자격 증명 모음 관리자는 주요 자격 증명 모음 PowerShell cmdlet([Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx))을 사용하여 Azure RMS 서비스 주체(**Microsoft.Azure.RMS**)에 권한을 부여합니다. 예를 들면 다음과 같습니다.

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

이제 Azure RMS를 구성하여 조직의 Azure RMS 테넌트 키로 이 키를 사용할 준비가 되었습니다. Azure RMS cmdlet을 사용하여 먼저 Azure RMS에 연결하고 로그인합니다.

    Connect-AadrmService

그런 다음 [Use-AadrmKeyVaultKey cmdlet](https://msdn.microsoft.com/library/azure/mt759829.aspx)을 실행하여 키 URL을 지정합니다. 예를 들면 다음과 같습니다.

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

Azure RMS에 키 URL이 올바르게 설정되었는지 확인해야 하는 경우 Azure 주요 자격 증명 모음에서 [Get-AzureKeyVaultKey](https://msdn.microsoft.com/library/dn868053.aspx)를 실행하여 키 URL을 확인할 수 있습니다.


## 다음 단계

이제 테넌트 키를 계획하고 필요한 경우 생성했으므로 다음을 수행합니다.

1.  테넌트 키 사용을 시작합니다.

    -   아직 Rights Management를 활성화하지 않은 경우 조직에서 RMS 사용을 시작할 수 있도록 Rights Management를 활성화해야 합니다. 사용자는 즉시 테넌트 키(Microsoft에서 관리하거나 Azure 주요 자격 증명 모음에서 고객이 직접 관리함) 사용을 시작합니다.

        활성화에 대한 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.

    -   이미 Rights Management를 활성화한 후 직접 테넌트 키를 관리하기로 결정한 경우 사용자는 점진적으로 이전 테넌트 키에서 새 테넌트 키로 전환하며, 시차를 두고 진행되는 이 전환이 완료되기까지 몇 주가 걸릴 수 있습니다. 권한 있는 사용자는 이전 테넌트 키로 보호된 문서와 파일에 계속 액세스할 수 있습니다.

2.  Azure 권한 관리에서 수행하는 모든 트랜잭션을 기록하는 사용 현황 로깅을 사용하는 것이 좋습니다.

    직접 테넌트 키를 관리하기로 결정한 경우 로깅에는 테넌트 키 사용에 대한 정보가 포함됩니다. Excel에 표시된 다음과 같은 로그 파일의 코드 조각을 참조하세요. 여기서 **KeyVaultDecryptRequest** 및 **KeyVaultSignRequest** 요청 유형은 테넌트 키가 사용되고 있음을 보여줍니다.

    ![테넌트 키가 사용되는 위치의 로그 파일](../media/RMS_Logging.png)

    사용 현황 로깅에 대한 자세한 내용은 [Azure 권한 관리 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.

3.  테넌트 키를 유지 관리합니다.

    자세한 내용은 [Azure 권한 관리 테넌트 키에 대한 작업](../deploy-use/operations-tenant-key.md)을 참조하세요.




<!--HONumber=Sep16_HO3-->


