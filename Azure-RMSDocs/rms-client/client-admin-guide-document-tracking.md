---
title: "Azure Information Protection에 대한 문서 추적"
description: "관리자가 Azure Information Protection에 문서 추적을 구성하고 사용하는 방법에 대한 지침 및 정보입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bbbc9a274ea815577109276bceb0b08617f03809
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>관리자 가이드: Azure Information Protection에 대한 문서 추적 구성 및 사용

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

[문서 추적을 지원하는 구독](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)이 있는 경우 기본적으로 조직의 모든 사용자에 대해 문서 추적 사이트를 사용하도록 설정됩니다. 문서 추적은 사용자와 관리자에게 보호된 문서에 액세스한 시간에 대한 정보를 제공하며, 필요한 경우 추적된 문서를 철회할 수 있습니다.

## <a name="privacy-controls-for-your-document-tracking-site"></a>문서 추적 사이트에 대한 개인 정보 관리

개인 정보 처리 방침 요구 사항으로 인해 조직에서 모든 문서 추적 정보를 표시하지 못하도록 금지하는 경우 [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) cmdlet을 사용하여 문서 추적을 사용하지 않도록 설정할 수 있습니다. 

이 cmdlet은 문서 추적 사이트에 대한 액세스를 사용하지 않도록 설정하여 조직의 모든 사용자가 보호된 문서를 추적하거나 이에 대한 액세스 권한을 취소할 수 없도록 합니다. 언제든지 [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature)를 사용하여 문서 추적을 사용하도록 다시 설정할 수 있으며, [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature)를 사용하여 문서 추적의 현재 사용 여부를 확인할 수 있습니다. 이러한 cmdlet을 실행하려면 **2.3.0.0** 이상의 PowerShell용 Azure Rights Management(AADRM) 모듈 버전이 있어야 합니다. 

문서 추적 사이트를 사용하도록 설정되면 기본적으로 보호된 문서에 액세스하려고 시도한 사람의 이메일 주소, 이러한 사람이 해당 문서에 액세스하려고 시도한 시간 및 위치와 같은 정보를 표시합니다. 이 수준의 정보는 공유 문서가 사용되는 방식 및 의심스러운 활동이 확인될 때 철회되어야 하는지 여부를 결정하는 데 유용할 수 있습니다. 그러나 개인 정보 보호를 위해 일부 또는 모든 사용자에 대해 이 사용자 정보를 사용하지 않도록 설정해야 할 수도 있습니다. 

다른 사용자가 이 활동을 추적하지 않아야 하는 사용자가 있는 경우, Azure AD에 저장된 그룹에 추가하고 [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) cmdlet을 사용하여 이 그룹을 지정합니다. 이 cmdlet을 실행하는 경우 단일 그룹을 지정해야 합니다. 그러나 그룹에는 중첩된 그룹이 포함될 수 있습니다. 

이러한 그룹의 구성원인 경우 사용자는 자신과 공유한 문서와 관련된 활동이 있을 때 문서 추적 사이트에서 어떠한 활동도 볼 수 없습니다. 또한 문서를 공유한 사용자에게 이메일 알림도 보내지 않습니다.

이 구성을 사용하면 모든 사용자가 문서 추적 사이트를 계속 사용하고 보호한 문서에 대한 액세스 권한을 철회할 수 있습니다. 그러나 Set-AadrmDoNotTrackUserGroup cmdlet을 사용하여 지정한 사용자의 활동은 표시되지 않습니다.

이 설정은 최종 사용자에게만 영향을 줍니다. Azure Information Protection에 대한 관리자는 Set-AadrmDoNotTrackUserGroup을 사용하여 사용자를 지정한 경우에도 언제든지 모든 사용자의 활동을 추적할 수 있습니다. 관리자가 사용자에 대한 문서를 추적하는 방법에 대한 자세한 내용은 [사용자에 대한 문서 추적 및 철회](#tracking-and-revoking-documents-for-users) 섹션을 참조하세요.

이 옵션이 더 이상 필요하지 않으면 [Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup)을 사용할 수 있습니다. 또는 사용자를 선택적으로 제거하려는 경우 그룹에서 제거하지만 [그룹 캐싱](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection)을 알고 있어야 합니다. [Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup)을 사용하여 이 옵션이 현재 사용 중인지 여부를 확인할 수 있습니다. 이 그룹 구성에 대한 cmdlet을 실행하려면 **2.10.0.0** 이상의 PowerShell용 Azure Rights Management(AADRM) 모듈 버전이 있어야 합니다.

이러한 cmdlet 각각에 대한 자세한 내용은 제공된 링크를 사용하세요. PowerShell 모듈 설치에 대한 지침은 [Azure Rights Management용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요. 이전에 모듈을 다운로드하여 설치한 경우 `(Get-Module aadrm –ListAvailable).Version`을 실행하여 버전 번호를 확인합니다.


## <a name="destination-urls-used-by-the-document-tracking-site"></a>문서 추적 사이트에서 사용되는 대상 URL

다음 URL은 문서 추적에 사용되며, Azure Information Protection 클라이언트를 실행하는 클라이언트와 인터넷 사이의 모든 장치 및 서비스에서 허용되어야 합니다. 예를 들어 향상된 보안이 강화된 Internet Explorer를 사용하는 경우 이러한 URL을 방화벽 또는 신뢰할 수 있는 사이트에 추가합니다.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

이러한 URL은 Bing 지도에서 사용자 위치를 표시하는 데 사용되는 virtualearth.net URL을 제외하고는 Azure Rights Management 서비스에 대한 표준입니다.

## <a name="tracking-and-revoking-documents-for-users"></a>사용자에 대한 문서 추적 및 철회

사용자가 문서 추적 사이트에 로그인하면 Azure Information Protection 클라이언트를 사용하여 보호하거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 문서를 추적 및 철회할 수 있습니다. Azure Information Protection(전역 관리자)에 대한 관리자로 로그인하면 관리자 아이콘을 클릭하여 관리자 모드로 전환할 수 있습니다. 이 모드에서는 조직의 사용자가 Azure Information Protection 클라이언트를 사용하여 추적하도록 선택한 문서 또는 Rights Management 공유 응용 프로그램을 사용하여 공유한 문서를 볼 수 있습니다.

![문서 추적 사이트의 관리자 아이콘](../media/tracking-site-admin-icon.png)

> [!NOTE] 
> 전역 관리자임에도 불구하고 이 아이콘이 표시되지 않으면 아직 문서를 공유하지 않았기 때문입니다. 이 경우 https://portal.azurerms.com/#/admin URL을 사용하여 문서 추적 사이트에 액세스하세요.

관리자 모드에서 수행하는 작업은 감사되고, 사용 현황 로그 파일에 기록되며, 계속하려면 확인해야 합니다. 이 로깅에 대한 자세한 내용은 다음 섹션을 참조하세요.

관리자 모드에 있으면 사용자 또는 문서별로 검색할 수 있습니다. 사용자별로 검색하는 경우 지정된 사용자가 Azure Information Protection 클라이언트를 사용하여 추적하도록 선택했거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 모든 문서가 표시됩니다. 

문서별로 검색하는 경우 Azure Information Protection 클라이언트를 사용하여 해당 문서를 추적하거나 Rights Management 공유 응용 프로그램을 사용하여 해당 문서를 공유한 조직의 모든 사용자가 표시됩니다. 그러면 검색 결과를 조사하여 사용자가 보호한 문서를 추적하고, 필요한 경우 이러한 문서를 철회할 수 있습니다. 

관리자 모드를 종료하려면 **관리자 모드 끝내기** 옆에 있는 **X**를 클릭합니다.

![문서 추적 사이트에서 관리자 모드 끝내기](../media/tracking-site-exit-admin-icon.png)

문서 추적 사이트 사용 방법에 대한 지침은 사용자 가이드의 [문서 추적 및 철회](client-track-revoke.md)를 참조하세요.

## <a name="usage-logging-for-the-document-tracking-site"></a>문서 추적 사이트에 대한 사용 현황 로깅

사용 현황 로그 파일의 두 필드, **AdminAction** 및 **ActingAsUser**는 문서 추적에 적용할 수 있습니다.

**AdminAction** - 관리자가 관리자 모드에서 문서 추적 사이트를 사용하는 경우(예 : 사용자를 대신하여 문서를 철회하거나 공유 시기를 확인하는 경우) 이 필드의 값은 true입니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다.

**ActingAsUser** - AdminAction 필드가 true인 경우 이 필드에는 검색된 사용자 또는 문서 소유자 대신 관리자가 수행하는 사용자 이름이 포함됩니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다. 

또한 사용자와 관리자가 문서 추적 사이트를 사용하는 방식을 기록하는 요청 유형도 있습니다. 예를 들어 **RevokeAccess**는 사용자를 대신하여 사용자 또는 관리자가 문서 추적 사이트에서 문서를 철회했을 때의 요청 형식입니다. 이 요청 형식을 AdminAction 필드와 함께 사용하여 사용자가 자신의 문서를 철회했는지(AdminAction 필드가 비어 있음), 아니면 관리자가 사용자를 대신하여 문서를 철회했는지(AdminAction이 true임)를 결정합니다.


사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management 서비스의 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.



## <a name="next-steps"></a>다음 단계
이제 Azure Information Protection 클라이언트에 대한 문서 추적 사이트를 구성했으므로 이 클라이언트를 지원하는 데 필요한 추가 정보에 대해 다음을 참조하세요.

- [사용자 지정](client-admin-guide-customizations.md)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [지원되는 파일 형식](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
