---
title: "분류 및 레이블 지정에 대한 질문과 대답 | Azure Information Protection"
description: "Azure Information Protection의 현재 릴리스에 대한 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fb68fc152e7f1d323cce71e3873475c78f7bbc15
ms.openlocfilehash: ad94507f4aea48172ed3c3f74f6d12e3c67cc18e


---

# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Azure Information Protection에서 분류 및 레이블 지정에 대한 질문과 대답

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection에서 특별히 분류 및 레이블 지정에 대한 질문이 있나요?  여기에 해당 질문에 대한 대답이 있는지 확인하세요. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Azure Information Protection에서 분류 기능으로 수행할 수 있는 작업은 무엇인가요?

Azure Information Protection 클라이언트는 Office 문서 및 전자 메일을 보고 분류 레이블을 할당할 수 있는 Information Protection 표시줄을 Microsoft Office 응용 프로그램에 추가합니다.

중요한 데이터가 검색되면 기본적으로 수동으로 분류를 적용하는 것이 좋으며 자동으로 적용될 수도 있습니다. 이러한 레이블은 Rights Management 서비스를 사용하여 데이터를 자동으로 보호할 수도 있습니다. Office 문서와 전자 메일 외에도, 파일 탐색기에서 파일, 여러 개의 파일 또는 폴더를 마우스 오른쪽 단추로 클릭하여 다른 형식의 파일을 분류하고 보호할 수 있습니다. 또는 대량으로 더 빠르게 분류하고 보호할 수 있게 명령줄에서 PowerShell을 사용하여 이 작업을 수행할 수도 있습니다.

분류 레이블 및 동작은 Azure 포털에서 구성합니다. 기본 제공 정책을 사용하여 Azure Information Protection을 매우 빠르게 평가하거나 고유한 정책을 완전히 사용자 지정할 수 있습니다. 사용자에게 표시하는 분류 레이블의 색, 이름 및 순서를 변경할 수 있습니다. 도구 설명과 머리글, 바닥글, 워터마크 등의 분류 시각적 표시를 구성할 수도 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)를 통해 몇 분 만에 이러한 기능의 작동 방식을 확인해 보세요.

현재 릴리스에는 다음과 같은 제한 사항이 있습니다. 추가 기능 및 특징을 사용할 수 있게 되면 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection)(Enterprise Mobility 및 보안 블로그) 및 [Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)에서 공지 사항을 확인하세요.

- 레이블 이름 및 도구 설명은 하나의 언어로만 지원됩니다.

- 분류 및 레이블 지정을 위한 중앙 집중식 로깅은 없습니다.

- 자동 분류에 대한 조건은 구 또는 패턴이어야 합니다.

- 모바일 장치(iOS 및 Android) 및 Mac 컴퓨터용 Office 앱과 Office Web Apps(Office Online)는 아직 지원되지 않습니다.

- Exchange Online 또는 SharePoint Online과는 통합되지 않습니다.

- 파트너 및 개발자용 SDK를 사용할 수 없습니다.

위에 나열된 일부 제한 기능이 새 클라이언트의&2;월 릴리스에서는 사용할 수 있게 됩니다. 자세한 내용은 블로그 게시물 알림을 참조하세요.


## <a name="do-i-need-to-be-a-global-admin-to-try-azure-information-protection"></a>Azure Information Protection을 사용하려면 전역 관리자여야 하나요?

Azure Information Protection 정책을 구성하려면 Azure Active Directory의 전역 관리자로 Azure Portal에 로그인해야 합니다.

하지만 [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치할 때 데모 정책 설치 옵션을 선택하면 레이블 지정 기능을 확인하고 사용해 보기 위해 포털에 로그인하지 않아도 됩니다. 데모 정책에서는 Azure Information Protection에 대한 기본 정책을 로컬로 설치하므로 문서 및 메일에 레이블을 지정해 볼 수 있지만, Azure 포털에 로그인하지 않고서는 레이블을 변경하거나 새 레이블을 추가할 수 없습니다. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Azure Portal의 옵션은 P1인가요, P2인가요?

**Azure Information Protection Premium 1**(P1) 구독 및 **Azure Information Protection Premium 2**(P2) 구독에 포함되는 기능을 확인하려면 Azure Information Protection 사이트에서 [기능 목록](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)을 참조하세요. 그러나 일반적으로 자동 분류, HYOK(Hold Your Own Key) 등의 고급 기능은 Azure Information Protection Premium 2 구독에서만 제공됩니다.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Azure Information Protection에서는 온-프레미스 및 하이브리드 시나리오를 지원하나요?

Azure Information Protection은 클라우드 기반 솔루션입니다. 하이브리드 시나리오에 대한 Azure Information Protection 배포에 관심이 있는 경우 Information Protection 팀에 문의하거나, askipteam@microsoft.com으로 메일을 보내세요.

## <a name="how-do-computers-get-the-policy-information-from-azure-information-protection-and-how-often-is-it-refreshed"></a>컴퓨터는 어떻게 Azure Information Protection에서 정책 정보를 가져오며 정책 정보는 얼마나 자주 새로 고쳐지나요?

사용자가 Office 응용 프로그램을 열 때마다 Azure Information Protection 클라이언트는 최신 버전의 Azure Information Protection 정책이 있는지 확인합니다. 또한 Office 응용 프로그램은 24시간마다 확인합니다. 최신 버전이 있는 경우 클라이언트는 데이터를 보호하는 HTTPS 링크를 사용하여 최신 버전을 다운로드합니다. 

새 Azure Information Protection 정책을 게시할 때 Office 응용 프로그램의 여러 인스턴스가 로드되는 경우 모든 인스턴스를 닫아 최신 버전의 정책을 가져와야 합니다. 예를 들어 Word 문서 두 개가 열려 있는 경우 하나의 문서에서만 업데이트된 Azure Information Protection 정책을 테스트하려면 두 Word 문서를 모두 닫고 최신 정책을 사용할 문서를 다시 엽니다.

## <a name="where-can-files-be-stored-to-use-azure-information-protection"></a>Azure Information Protection을 사용하려면 파일을 어디에 저장하면 되나요? 

Azure Information Protection에서는 파일과 메일에 영구 레이블 및 보호를 적용하므로 파일 저장 위치는 중요하지 않습니다.

## <a name="can-i-classify-only-new-data-or-can-i-also-classify-existing-data"></a>새 데이터만 분류할 수 있나요? 아니면 기존 데이터도 분류할 수 있나요?

새 콘텐츠와 기존 콘텐츠에 대한 변경 내용 둘 다에 대해 Azure Information Protection 정책 작업은 문서가 저장되고 메일이 전송될 때 적용됩니다.

최신 버전의 클라이언트가 있는 경우 파일 탐색기의 기존 파일을 빠르게 분류하고 선택적으로 보호할 수도 있습니다. 

## <a name="can-i-use-azure-information-protection-for-classification-only-without-enforcing-encryption-and-restricting-usage-rights"></a>암호화 적용 및 사용 권한 제한 없이 분류 목적으로만 Azure Information Protection을 사용할 수 있나요?

예. 파일 형식이 이 작업을 지원하는 경우, 보호 없이 분류만 적용하는 Azure Information Protection 정책을 구성할 수 있습니다. 사실, 특별한 데이터 관리가 필요한 일부 문서나 메일만 보호하면 되는 배포 네트워크 대부분의 경우가 여기에 해당할 것으로 예상합니다.

## <a name="how-does-automatic-classification-work"></a>자동 분류는 어떻게 작동하나요?

Azure 포털에서 "신용 카드 번호" 또는 "주민등록번호"와 같은 미리 정의된 패턴을 사용할 수 있습니다. 또는 자동 분류에 대한 조건으로 사용자 지정 문자열 또는 패턴을 정의할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다. 

분류의 정확도는 조건을 기반으로 하는 분류 규칙을 구성하는 방법에 따라 달라집니다. 현재 조건에서는 텍스트 패턴 및 정규식이 지원됩니다. 테스트할 수 있는 제안된 몇 가지 예제와 함께 사용할 수 있는 각 옵션에 대한 설명은 [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](../deploy-use/configure-policy-classification.md)을 참조하세요. 문서가 저장되거나 메일이 전송되면 검색이 실행됩니다.

최상의 사용자 환경과 비즈니스 연속성 보장을 위해 완전한 자동 작업보다는 사용자 권장 작업으로 시작하는 것이 좋습니다. 이렇게 하면 사용자가 레이블 지정 또는 보호 작업을 수락하거나 이러한 제안을 재정의할 수 있습니다.   

## <a name="can-azure-information-protection-prompt-users-to-classify-files-themselves-rather-than-use-automatic-classification"></a>Azure Information Protection에서는 자동 분류를 사용하는 대신 사용자가 직접 파일을 분류하도록 메시지를 표시할 수 있나요? 

예. Azure 포털에서 **Select how this label is applied: automatically or recommended to user**(이 레이블 적용 방법 선택: 자동 또는 사용자에게 권장함) 옵션을 **Recommended**(권장)로 설정하여 자동 분류를 사용할지 사용자에게 권장할지를 구성할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다.  

## <a name="can-i-force-all-documents-to-be-classified"></a>모든 문서를 강제로 분류할 수 있나요?

예. 사용자가 보유한 모든 파일을 분류하도록 해야 할 경우 Azure Portal에서 **All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함) 정책 설정을 **On**(켜기)으로 구성합니다. 

## <a name="can-i-remove-classification-from-a-file"></a>파일에서 분류를 제거할 수 있나요?

예. 이 내용은 사용자 가이드 [파일 및 전자 메일에서 분류 레이블 및 보호 제거](../rms-client/client-remove-label-protection.md)에 설명되어 있습니다. 

## <a name="can-i-prompt-users-to-justify-why-they-are-changing-the-classification-level"></a>사용자에게 분류 수준을 변경하는 이유를 묻는 메시지를 표시할 수 있나요?

예. 사용자에게 분류를 변경하는 이유를 묻는 메시지를 표시하려면 Azure 포털에서 **Users must provide justification to set a lower classification label, remove a label, or remove protection**(더 낮은 분류 레이블을 설정하거나, 레이블 또는 보호를 제거할 때 사용자가 근거를 제공해야 함)을 **On**(켜기)으로 설정합니다. 사용자가 이렇게 할 때 해당 작업 및 변경 이유는 사용자의 로컬 Windows 이벤트 로그 **응용 프로그램 및 서비스 로그** > **Microsoft Azure Information Protection**에 기록됩니다.

## <a name="how-can-i-automatically-protect-the-content-after-its-been-classified"></a>콘텐츠가 분류된 후 자동으로 콘텐츠를 보호할 수 있나요?

Azure Portal에서 지정한 분류 수준에 따라 자동으로 콘텐츠를 보호하는 Rights Management 템플릿을 선택할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다. 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)을 참조하세요.

## <a name="can-a-file-have-more-than-one-classification"></a>파일에 분류가 여러 개 있을 수 있나요?

사용자는 각 문서 또는 메일에 대해 한 번에 레이블 하나만 선택할 수 있으며, 그 결과 분류가 하나만 생깁니다. 그러나 사용자가 하위 레이블을 선택하면 실제로 두 레이블(기본 레이블 및 보조 레이블)이 동시에 적용됩니다. 하위 레이블을 사용함으로써 추가 수준의 제어에 대해 파일에 부모\자식 관계를 나타내는 두 분류가 있을 수 있습니다.

예를 들어 레이블 **Secret**은 **Legal**과 **Finance** 같은 하위 레이블을 포함할 수 있습니다. 서로 다른 분류 시각적 표시와 서로 다른 Rights Management 템플릿을 이러한 하위 레이블에 적용할 수 있습니다. 사용자는 **Secret** 레이블 하나만 선택할 수 없으며 **Legal** 같은 하위 레이블 중 하나를 선택해야 합니다. 결과적으로 표시되는 레이블은 **Secret \ Legal**입니다. 해당 파일의 메타데이터에는 **Secret**에 대한 사용자 지정 텍스트 속성 하나, **Legal**에 대한 사용자 지정 텍스트 속성 하나, 두 값을 모두 포함하는 다른 사용자 지정 텍스트 속성(**Secret Legal**)이 포함됩니다. 

하위 레이블을 사용할 때에는 기본 레이블에 시각적 표시, 보호 및 상태를 구성하지 마세요. 하위 수준을 사용할 때에는 하위 레이블에만 이러한 설정을 구성합니다. 기본 레이블과 하위 레이블에 이러한 설정을 구성하는 경우 하위 레이블의 설정이 우선합니다.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>메일에 레이블이 지정되면 첨부 파일에 자동으로 동일한 레이블이 지정되나요?

아니요. 첨부 파일이 있는 메일 메시지에 레이블을 지정하면 해당 첨부 파일은 동일한 레이블을 상속하지 않습니다. 첨부 파일은 레이블 없이 유지되거나 별도로 적용된 레이블을 보유합니다. 그러나 메일의 레이블에 보호를 적용하는 경우 해당 보호는 첨부 파일에 적용됩니다.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>전자 메일에 대한 Azure Information Protection 분류와 Exchange 메시지 분류는 어떻게 다른가요?

Exchange 메시지 분류는 전자 메일을 분류할 수 있는 이전 기능으로, Azure Information Protection 분류와는 독립적으로 구현됩니다. 그러나 사용자가 Outlook Web App을 사용하여 전자 메일을 분류할 때와 일부 모바일 메일 응용 프로그램을 사용할 때 Azure Information Protection 분류와 해당하는 레이블 표시가 자동으로 추가되도록 두 솔루션을 통합할 수 있습니다. 이 경우 Exchange에서 분류를 추가하면 Azure Information Protection 클라이언트에서 이 분류에 해당하는 레이블 설정을 적용합니다.

Outlook Web App에서는 Azure Information Protection 및 보호가 아직 기본적으로 지원되지는 않지만, 이와 동일한 기술을 사용하면 데스크톱 Outlook 클라이언트 외에 이 전자 메일 클라이언트에서도 레이블을 사용할 수 있습니다.

이 솔루션을 활용하려면 다음을 수행합니다. 

1. [New-MessageClassification](https://technet.microsoft.com/library/bb124400) Exchange PowerShell cmdlet을 사용하여 Azure Information Protection 정책의 레이블 이름에 매핑되는 Name 속성을 포함하는 메시지 분류를 만듭니다. 

2. 각 레이블에 대해 Exchange 전송 규칙을 만든 다음 구성된 분류가 메시지 속성에 포함될 때 해당 규칙을 적용하고 메시지 속성을 수정하여 메시지 헤더를 설정합니다. 

    메시지 헤더에서는 Azure Information Protection 레이블을 사용하여 분류한 Office 파일의 속성을 검사하면 지정할 정보를 확인할 수 있습니다. **MSIP_Label_<GUID>_Enabled** 형식의 파일 속성을 찾은 다음 메시지 헤더로 이 문자열을 지정하고 헤더 값으로 **True**를 지정합니다. 예를 들어 메시지 헤더는 **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**와 같은 문자열일 수 있습니다.


이렇게 하면 사용자가 권한 관리 보호를 지원하는 모바일 장치 클라이언트 또는 Outlook Web Access 앱을 사용할 때 다음과 같은 과정이 진행됩니다. 

- 사용자가 Exchange 메시지 분류를 선택하고 전자 메일을 보냅니다.

- Exchange 규칙이 Exchange 분류를 검색한 다음 그에 따라 메시지 헤더를 수정하여 Azure Information Protection 분류를 추가합니다.

- Azure Information Protection 클라이언트를 실행 중인 받는 사람이 Outlook에서 전자 메일을 볼 때 할당된 Azure Information Protection 레이블과 그에 해당하는 전자 메일 머리글, 바닥글 또는 워터마크가 표시됩니다. 

Azure Information Protection 레이블이 권한 관리 보호를 적용하는 경우에는 메시지 보안을 수정하는 옵션을 선택하여 규칙 구성에 권한 관리 보호를 추가하고, 권한 보호를 적용한 후에 RMS 템플릿 또는 전달 금지 옵션을 선택합니다.

역방향 매핑을 수행하는 전송 규칙을 구성할 수도 있습니다. Azure Information Protection 레이블이 검색되면 해당 Exchange 메시지 분류를 설정합니다. 이렇게 하려면 다음을 수행합니다.

- 각 Azure Information Protection 레이블에 대해 **msip_labels** 헤더에 레이블의 이름(예: **Confidential**)이 포함될 때 적용되는 전송 규칙을 만들고 이 레이블에 매핑되는 메시지 분류를 적용합니다.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>DLP 솔루션 및 다른 응용 프로그램을 Azure Information Protection과 통합하려면 어떻게 하나요?

Azure Information Protection에서는 일반 텍스트 레이블을 포함하는 영구 메타데이터를 분류에 사용하므로 DLP 솔루션 및 다른 응용 프로그램에서 이 정보를 읽을 수 있습니다. 파일에서 이 메타데이터는 사용자 지정 속성에 저장되고, 메일에서 이 정보는 메일 헤더에 있습니다.

## <a name="how-does-document-tracking-and-revocation-work-for-azure-information-protection"></a>문서 추적 및 취소는 Azure Information Protection에 대해 어떻게 작동하나요?

Azure Information Protection을 사용하여 분류하고 보호하는 파일에 대한 문서 추적 기능은 Azure Rights Management 클라이언트의 최신 릴리스(버전 1.3.155.2 이상)에서 작동됩니다. 

자세한 내용은 [Azure Information Protection 사용 시 보호된 문서 추적 및 액세스 권한 해지](../rms-client/client-track-revoke.md)를 참조하세요.

## <a name="can-i-control-which-users-can-use-azure-information-protection-to-classify-and-protect-content"></a>Azure Information Protection을 사용하여 콘텐츠를 분류하고 보호할 수 있는 사용자를 제어할 수 있나요?

Azure Information Protection 클라이언트 배포를 제어하여 데이터를 분류하고 보호하는 사용자를 제한할 수 있습니다. [범위 지정 정책](../deploy-use\configure-policy-scope.md)을 구성할 때는 지정된 사용자에게만 새 레이블을 추가합니다. 

Azure Information Protection에 의해 분류된 파일과 메일은 Azure Information Protection 클라이언트의 설치 여부와 관계없이 모든 사용자가 이용하거나 편집할 수 있습니다. 

## <a name="how-do-i-sign-in-as-a-different-user"></a>다른 사용자로 로그인하려면 어떻게 하나요?

프로덕션 환경에서는 Azure Information Protection 클라이언트를 사용 중에 일반적으로 다른 사용자로 로그인할 필요가 없습니다. 그러나 여러 테넌트가 있는 경우에는 그렇게 해야 할 수 있습니다. 예를 들어 조직에서 사용하는 Office 365 또는 Azure 테넌트 외에 테스트 테넌트가 있을 수 있습니다.

**Microsoft Azure Information Protection** 대화 상자를 사용하여 현재 로그인한 계정을 확인할 수 있습니다. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 의견**을 클릭합니다. 계정 이름은 **클라이언트 상태** 섹션에 표시됩니다.

특히 관리자 계정을 사용하고 있는 경우 표시된 로그인 계정의 도메인 이름을 확인해야 합니다. 예를 들어 두 개의 다른 테넌트에 "admin" 계정이 있는 경우 로그인한 계정 이름은 올바르지만 도메인은 잘못되었음을 모르기 쉽습니다. 이로 인해 Azure Information Protection 정책을 다운로드하지 못하거나 예상한 레이블 또는 동작이 표시되지 않을 수 있습니다.

다른 사용자로 로그인하려면 현재 레지스트리를 편집해야 합니다.

1. 레지스트리 편집기를 사용하여 **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**로 이동하고 **TokenCache** 값을 삭제합니다.

2. 열려 있는 Office 응용 프로그램을 다시 시작하고 다른 사용자 계정으로 로그인합니다. Office 응용 프로그램에서 Azure Information Protection 서비스에 로그인하라는 메시지가 표시되지 않는 경우 **Microsoft Azure Information Protection** 대화 상자로 돌아와 업데이트된 **클라이언트 상태** 섹션에서 **로그인**을 클릭합니다.

추가 필수 구성 요소:

- Azure 권한 관리 서비스에 대한 환경을 다시 초기화(부트스트래핑이라고도 함)하려는 경우 [RMS 분석기 도구](https://www.microsoft.com/en-us/download/details.aspx?id=46437)의 **재설정** 옵션을 사용할 수 있습니다.

- 현재 다운로드한 Azure Information Protection 정책을 삭제하려면 %localappdata%\Microsoft\MSIP 폴더에서 **Policy.msip** 파일을 삭제하면 됩니다.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Azure Information Protection에 대한 문제를 보고하거나 의견을 보낼 수 있나요?

기술 지원에 대해서는 표준 지원 채널을 사용하거나 [Microsoft 지원에 문의](information-support.md#to-contact-microsoft-support)하세요.

향상된 기능 및 새 기능에 대한 제안과 같은 피드백을 보내려면 Office 응용 프로그램의 **홈** 탭에 있는 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. **Microsoft Azure Information Protection** 대화 상자에서 **Send feedback**(의견 보내기)을 클릭합니다. 그러면 Information Protection 팀에 메일이 전송되고 자동으로 PC에서 로그 파일이 첨부됩니다. 

또한 엔지니어링 팀과 의견을 나눌 수 있게 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다. 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


