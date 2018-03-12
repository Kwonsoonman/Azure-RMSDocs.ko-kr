---
title: "고객 관리 - AIP 테넌트 키 수명 주기 작업"
description: "Azure Information Protection용 테넌트 키를 직접 관리하는 경우(BYOK(Bring Your Own Key) 시나리오)와 관련된 수명 주기 작업에 대한 정보를 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 70d34253300e2bef442cdd7d8cf2c06ac8a9fd88
ms.sourcegitcommit: dd53f3dc2ea2456ab512e3a541d251924018444e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2018
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>고객 관리: 테넌트 키 수명 주기 작업

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection용 테넌트 키를 직접 관리하는 경우(BYOK(Bring Your Own Key) 시나리오) 다음 섹션에서 이 토폴로지와 관련된 수명 주기 작업에 대한 자세한 내용을 확인하세요.

## <a name="revoke-your-tenant-key"></a>테넌트 키 해지
Azure Key Vault에서 Azure Rights Management 서비스에서 더 이상 키에 액세스할 수 없도록 Azure Information Protection 테넌트 키를 포함하는 주요 자격 증명 모음에 대한 권한을 변경할 수 있습니다. 그러나 이렇게 하면 아무도 Azure Rights Management로 이전에 보호한 문서 및 메일을 열 수 없습니다.

Azure Information Protection에 대한 구독을 취소하면, Azure Information Protection에서 테넌트 키 사용이 중지되므로 별도의 조치가 필요하지 않습니다.

## <a name="rekey-your-tenant-key"></a>테넌트 키 다시 입력
키 다시 입력을 키 롤링이라고도 합니다. 이 작업을 수행하는 경우 Azure Information Protection이 문서 및 메일을 보호하기 위해 기존 테넌트 키 사용을 중지하고 다른 키를 사용하기 시작합니다. 정책 및 템플릿이 즉시 다시 서명되지만 이 전환은 Azure Information Protection을 사용하는 기존 클라이언트 및 서비스에 대해 점진적입니다. 일정 시간 동안에는 일부 새 콘텐츠가 계속해서 이전 테넌트 키로 보호됩니다.

키를 다시 생성하려면 테넌트 키 개체를 구성하고 사용할 대체 키를 지정해야 합니다. 그러면 이전에 사용한 키가 자동으로 Azure Information Protection에 대해 보관되는 것으로 표시됩니다. 이 구성을 통해 이 키를 사용하여 보호된 콘텐츠에 계속 액세스할 수 있습니다.

Azure Information Protection에 대해 키를 다시 생성해야 하는 경우는 다음과 같습니다.

- 회사가 둘 이상으로 분할된 경우. 테넌트 키를 다시 입력하면 새 회사에서는 직원이 게시하는 새 콘텐츠에 액세스할 수 없습니다. 이전 테넌트 키의 복사본이 있으면 이전 콘텐츠에는 액세스할 수 있습니다.

- 하나의 키 관리 토폴로지에서 다른 키 관리 토폴로지로 이동하려고 합니다. 

- 테넌트 키의 마스터 복사본(현재 소유 중인 복사본)이 노출되었다고 판단되는 경우.

관리하는 다른 키로 키를 다시 생성하려면 Azure Key Vault에 새 키를 생성하거나 Azure Key Vault에 이미 있는 다른 키를 사용하면 됩니다. 그런 다음 Azure Information Protection에 대해 BYOK를 구현하기 위해 수행했던 것과 동일한 절차를 수행합니다.

1. Azure Information Protection에 대해 이미 사용하고 있는 것과 다른 Key Vault에 새 키가 있는 경우에만 [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) cmdlet을 사용하여 Key Vault를 사용하도록 Azure Information Protection을 승인합니다.

2. 사용하려는 키를 Azure Information Protection이 아직 모르는 경우 [Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey) cmdlet을 실행합니다.

3. [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) cmdlet 실행을 통해 테넌트 키 개체를 구성합니다.

각 단계에 대한 자세한 내용은 다음을 참조하세요.

- 관리하는 다른 키로 키를 다시 생성하려면 [Azure Information Protection 테넌트 키에 BYOK 구현](../plan-design/plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key)을 참조하십시오.

- Microsoft에서 관리하는 키로 변경하여 키를 다시 생성하려면, Microsoft 관리 작업에 대한 [테넌트 키 다시 생성](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) 섹션을 참조하세요.

## <a name="backup-and-recover-your-tenant-key"></a>테넌트 키 백업/복구
사용자가 테넌트 키를 관리 중이므로 Azure Information Protection을 사용하는 키를 백업해야 하는 책임이 있습니다. 

Thales HSM의 온-프레미스에서 테넌트 키를 생성한 경우: 키를 백업하려면 토큰화된 키 파일, 권역 파일 및 관리자 카드를 백업합니다. Azure Key Vault에 키를 전송할 때 서비스는 서비스 노드의 오류로부터 보호하기 위해 토큰화된 키 파일을 저장합니다. 이 파일은 특정 Azure 지역 또는 인스턴스에 대해 보안 권역에 바인딩되어 있습니다. 그러나 이 토큰화된 키 파일이 전체 백업은 아닙니다. 예를 들어 Thales HSM 외부에서 사용할 키의 일반 텍스트 복사본이 필요한 경우 Azure Key Vault는 복구 불가능한 복사본만 보존하므로 해당 복사본을 검색할 수 없습니다.

Azure Key Vault에는 다운로드하여 파일에 저장하여 키를 백업하는 데 사용할 수 있는 [백업 cmdlet](/powershell/module/azurerm.keyvault/Backup-AzureKeyVaultKey)이 있습니다. 다운로드된 콘텐츠는 암호화되어 있으므로 Azure Key Vault 외부에서 사용할 수 없습니다. 

## <a name="export-your-tenant-key"></a>테넌트 키 내보내기
BYOK 사용 시에는 Azure Key Vault 또는 Azure Information Protection에서 테넌트 키를 내보낼 수 없습니다. Azure 주요 자격 증명 모음의 복사본은 복구할 수 없습니다. 

## <a name="respond-to-a-breach"></a>위반 사항에 대응
아무리 강력한 보안 시스템이라도 위반 대응 프로세스가 없다면 완벽하다고 할 수 없습니다. 테넌트 키는 노출되거나 도용될 수 있습니다. 테넌트 키를 효율적으로 보호한다고 하더라도 현재 생성 기술 또는 현재 키 길이/알고리즘에 취약점이 있을 수도 있습니다.

Microsoft에서는 전담 팀이 제품 및 서비스의 보안 문제에 대응하고 있습니다. 이 팀은 신뢰할 만한 문제 보고서가 확인되는 즉시 해당 범위, 근본 원인 및 완화 방법을 조사합니다. 이 문제가 사용자의 자산에 영향을 주는 경우 Microsoft는 구독 시 사용자가 제공한 주소를 사용해 메일로 Azure Information Protection 테넌트 관리자에게 문제를 알립니다.

보안 위반이 발생한 경우 사용자나 Microsoft에서 수행할 수 있는 최선의 작업은 위반 범위에 따라 다르며, Microsoft는 사용자와 협의하여 이 프로세스를 진행합니다. 다음 표에는 몇 가지 일반적인 상황과 가능한 대응 방법이 나와 있습니다. 정확한 대응 방법은 조사 중에 확인되는 모든 정보에 따라 달라집니다.

|문제 설명|가능한 대응 방법|
|------------------------|-------------------|
|테넌트 키가 유출되었습니다.|테넌트 키를 다시 입력합니다. [테넌트 키 다시 입력](#rekey-your-tenant-key)을 참조하세요.|
|권한이 없는 개인이나 맬웨어가 테넌트 키 사용 권한을 확보했으나 키 자체가 유출되지는 않았습니다.|이 경우에는 테넌트 키를 다시 입력해도 도움이 되지 않으며 근본 원인을 분석해야 합니다. 프로세스 또는 소프트웨어 버그로 인해 권한이 없는 개인이 액세스 권한을 얻은 경우에는 해당 상황을 해결해야 합니다.|
|현재 생성 HSM 기술에서 취약점이 발견되었습니다.|Microsoft에서 HSM을 업데이트해야 합니다. 취약점으로 인해 키가 노출되었다고 생각되면 Microsoft는 모든 고객에게 테넌트 키를 갱신할 것을 지시합니다.|
|RSA 알고리즘이나 키 길이에 취약점이 있거나 전산상 무차별 암호 대입 공격(brute force attack)이 가능합니다.|Microsoft에서 복원 가능한 더 긴 키 길이와 새 알고리즘을 지원하도록 Azure Key Vault 또는 Azure Information Protection을 업데이트하고 모든 고객에게 테넌트 키를 다시 생성하도록 지시해야 합니다.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

