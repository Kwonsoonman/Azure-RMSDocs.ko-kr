---
title: Azure Information Protection에 대한 문서 추적
description: Azure Information Protection에 대한 문서 추적을 구성하고 사용하는 관리자를 위한 지침 및 정보입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 181183d701cb5fa4891be0aa3e0ea3028682bea7
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150843"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>관리자 가이드: Azure Information Protection에 대한 문서 추적 구성 및 사용

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

[문서 추적 기능을 지원하는 구독](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)이 있는 경우 기본적으로 조직의 모든 사용자에 대해 문서 추적 사이트를 사용하도록 설정됩니다. 문서 추적은 보호된 문서에 액세스되는 경우에 대한 정보를 사용자 및 관리자에게 제공하며, 필요한 경우 추적된 문서를 해지할 수 있도록 합니다.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>PowerShell을 사용하여 문서 추적 사이트 관리

다음 섹션에는 PowerShell을 사용하여 문서 추적 사이트를 관리하는 방법을 설명합니다. PowerShell 모듈에 대한 설치 지침은 [AADRM PowerShell 모듈 설치](../install-powershell.md)를 참조하세요. 모듈을 이미 다운로드하여 설치한 경우 `(Get-Module aadrm –ListAvailable).Version`을 실행하여 버전 번호를 확인합니다.

각 cmdlet에 대한 자세한 내용은 제공된 링크를 사용하세요.

### <a name="privacy-controls-for-your-document-tracking-site"></a>문서 추적 사이트에 대한 개인 정보 관리

개인 정보 취급 방침 요구 사항으로 인해 조직의 모든 문서 추적 정보 표시가 금지된 경우 [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) cmdlet을 사용하여 문서 추적을 사용하지 않도록 설정할 수 있습니다. 

이 cmdlet은 조직의 모든 사용자가 보호된 문서를 추적하거나 문서에 대한 액세스 권한을 취소할 수 없도록 문서 추적 사이트에 대한 액세스를 사용하지 않도록 설정합니다. 언제든지 [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature)를 사용하여 문서 추적을 다시 사용하도록 설정할 수 있고 [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature)를 사용하여 문서 추적이 현재 사용하거나 사용하지 않도록 설정되어 있는지 확인할 수 있습니다. 이러한 cmdlet을 실행하려면 **2.3.0.0** 이상의 PowerShell용 AADRM 모듈 버전을 사용하고 있어야 합니다. 

문서 추적 사이트가 사용되도록 설정되면 기본적으로 보호된 문서에 액세스하려고 시도하는 사람의 메일 주소, 해당 문서에 액세스하려고 시도한 시간 및 해당 위치와 같은 정보를 표시합니다. 이 수준의 정보는 공유 문서가 사용되는 방식과 의심스러운 작업이 확인될 때 문서 공유를 해지할지 여부를 결정하는 데 유용할 수 있습니다. 그러나 개인 정보 보호를 위해 일부 또는 모든 사용자에 대해 이 사용자 정보를 사용하지 않도록 설정해야 할 수도 있습니다. 

다른 사용자에 의해 이 작업이 추적되지 않아야 하는 사용자가 있는 경우 Azure AD에 저장된 그룹에 추가하고 [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) cmdlet을 사용하여 이 그룹을 지정해야 합니다. 이 cmdlet을 실행할 때는 단일 그룹을 지정해야 합니다. 그러나 그룹에 중첩된 그룹을 포함할 수 있습니다. 

해당 그룹 구성원의 경우 사용자는 작업이 공유하는 문서와 관련된 경우 문서 추적 사이트의 모든 작업을 볼 수 없습니다. 또한 전자 메일 알림이 문서를 공유한 사용자에게 전송되지 않습니다.

이 구성을 사용하면 모든 사용자가 계속해서 문서 추적 사이트를 사용하고 보호한 문서에 대한 액세스 권한을 해지할 수 있습니다. 그러나 Set-AadrmDoNotTrackUserGroup cmdlet을 사용하면 지정한 사용자에 대한 활동이 표시되지 않습니다.

이 설정은 최종 사용자에게만 영향을 줍니다. Azure Information Protection에 대한 관리자는 해당 사용자가 Set-AadrmDoNotTrackUserGroup을 사용하여 지정된 경우에도 모든 사용자의 작업을 항상 추적할 수 있습니다. 관리자가 사용자에 대한 문서를 추적할 수 있는 방법에 대한 자세한 내용은 [사용자에 대해 문서 추적 및 취소](#tracking-and-revoking-documents-for-users) 섹션을 참조하세요.


### <a name="logging-information-from-the-document-tracking-site"></a>문서 추적 사이트의 로깅 정보

**2.13.0.0** 이상의 AADRM 모듈 버전을 사용하고 있는 경우 다음 cmdlet을 사용하여 문서 추적 사이트에서 로깅 정보를 다운로드할 수 있습니다.

- [Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)
    
    이 cmdlet은 문서를 보호한 지정된 사용자(Rights Management 발급자) 또는 보호된 문서에 액세스한 지정된 사용자의 보호된 문서에 대한 추적 정보를 반환합니다. 이 cmdlet을 사용하여 “지정된 사용자가 추적하거나 액세스한 보호된 문서는 무엇인가요?”라는 질문에 답할 수 있습니다.

- [Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)
    
    이 cmdlet은 지정된 사용자가 문서를 보호하거나(Rights Management 발급자) 문서의 Rights Management 소유자인 경우 또는 보호된 문서가 사용자에게 액세스 권한을 직접 부여하도록 구성된 경우 해당 사용자의 추적된 문서에 대한 보호 정보를 반환합니다. 이 cmdlet을 사용하여 “지정된 사용자의 문서가 어떻게 보호되었나요?”라는 질문에 답할 수 있습니다.
 
## <a name="destination-urls-used-by-the-document-tracking-site"></a>문서 추적 사이트에서 사용되는 대상 URL

다음 URL은 문서 추적에 사용되며, 모든 장치 및 Azure Information Protection 클라이언트를 실행하는 클라이언트와 인터넷 간의 모든 서비스에서 허용되어야 합니다. 예를 들어 보안이 강화된 Internet Explorer를 사용하는 경우 이러한 URL을 방화벽이나 신뢰할 수 있는 사이트에 추가합니다.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Bing 지도에서 사용자 위치를 표시하는 데 사용하는 virtualearth.net을 제외하고, 이러한 URL은 Azure 권한 관리 서비스에 대한 표준입니다.

## <a name="tracking-and-revoking-documents-for-users"></a>사용자에 대해 문서 추적 및 취소

사용자는 문서 추적 사이트에 로그인하면 Azure Information Protection 클라이언트를 사용하여 보호하거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 문서를 추적 및 취소할 수 있습니다. 테넌트에 대한 Azure AD 전역 관리자로 로그인하면 관리 아이콘을 클릭하여 관리자 모드로 전환할 수 있습니다. 다른 관리자 역할은 문서 추적 사이트에 대해 이 모드를 지원하지 않습니다. 

![문서 추적 사이트의 관리자 아이콘](../media/tracking-site-admin-icon.png)

관리자 모드에서는 조직의 사용자가 Azure Information Protection 클라이언트를 사용하여 추적하도록 선택하거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 문서를 볼 수 있습니다.

> [!NOTE] 
> 전역 관리자임에도 이 아이콘이 표시되지 않은 원인은 아직 스스로 문서를 공유하지 않았기 때문입니다. 이 경우에 다음 URL을 사용하여 문서 추적 사이트에 액세스합니다. https://portal.azurerms.com/#/admin

관리자 모드에서 수행하는 작업은 감사되어 사용 현황 로그 파일에 기록되며, 계속하려면 확인해야 합니다. 이 로깅에 대한 자세한 내용은 다음 섹션을 참조하세요.

관리자 모드에 있는 경우 사용자 또는 문서로 검색할 수 있습니다. 사용자로 검색하면 지정한 사용자가 Azure Information Protection 클라이언트를 사용하여 추적하도록 선택하거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 모든 문서가 표시됩니다. 

문서로 검색하면 Azure Information Protection 클라이언트를 사용하여 해당 문서를 추적하거나 Rights Management 공유 응용 프로그램을 사용하여 공유한 조직의 모든 사용자가 표시됩니다. 그러면 검색 결과를 드릴하여 사용자가 보호한 문서를 추적하고 필요한 경우 해당 문서를 해지할 수 있습니다. 

관리자 모드를 종료하려면 **관리자 모드 끝내기** 옆에 있는 **X**를 클릭합니다.

![문서 추적 사이트에서 관리자 모드 끝내기](../media/tracking-site-exit-admin-icon.png)

문서 추적 사이트를 사용하는 방법에 대한 자세한 내용은 사용자 가이드에서 [문서 추적 및 취소](client-track-revoke.md)를 참조하세요.

## <a name="usage-logging-for-the-document-tracking-site"></a>문서 추적 사이트에 대한 사용 현황 로깅

사용 현황 로그 파일의 두 필드 **AdminAction** 및 **ActingAsUser**가 문서 추적에 적용됩니다.

**AdminAction** - 관리자가 문서 추적 사이트를 관리자 모드로 사용하는 경우(예: 사용자 대신 문서를 취소하거나 언제 공유되었는지 확인하기 위해) 이 필드에 true 값이 포함됩니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다.

**ActingAsUser** - AdminAction 필드가 true이면 이 필드에 관리자가 검색된 사용자 또는 문서 소유자로 대신 작업하는 사용자 이름이 포함됩니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다. 

사용자와 관리자가 문서 추적 사이트를 어떻게 사용하고 있는지를 기록하는 요청 유형도 있습니다. 예를 들어 **RevokeAccess**는 사용자 또는 사용자를 대신하는 관리자가 문서 추적 사이트에서 문서를 취소한 경우의 요청 유형입니다. 이 요청 유형을 AdminAction 필드와 함께 사용하여 사용자가 고유한 문서를 취소했는지(AdminAction 필드가 비어 있음), 아니면 관리자가 사용자 대신 문서를 취소했는지(AdminAction이 true임) 확인할 수 있습니다.


사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management Service 사용 현황 로깅 및 분석](../log-analyze-usage.md)을 참조하세요.



## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트에 대한 문서 추적 사이트를 구성했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [사용자 지정](client-admin-guide-customizations.md)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)

