---
title: "Azure Information Protection 미리 보기 질문과 대답 | Azure Information Protection"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 7d5b58efb4b789ba4f3d897ae3a475cbd2c679e5


---

# Azure Information Protection 미리 보기 질문과 대답

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

Azure Information Protection의 미리 보기 릴리스에 대한 질문이 있나요?  여기에 해당 질문에 대한 대답이 있는지 확인하세요. 

일부 정보는 기본 설명서로 이동되고, 고객으로부터 받는 새로운 질문이 포함되므로 이 목록은 자주 업데이트됩니다. 

## Azure Information Protection의 미리 보기 릴리스로 수행할 수 있는 작업은 무엇이며 현재 제한 사항은 무엇인가요?

이 미리 보기 릴리스는 데이터에 할당된 분류 레이블을 보고 수정할 수 있는 Information Protection 표시줄을 Microsoft Office 응용 프로그램에 추가합니다. 분류는 수동으로 수행하거나, 자동으로 적용(권장 사항)할 수 있습니다. 지정한 분류의 경우 데이터는 Azure 권한 관리 템플릿을 사용하여 보호할 수 있습니다.  

분류 레이블 및 동작은 Azure 포털에서 구성합니다. 기본 제공 정책을 사용하여 Azure Information Protection을 매우 빠르게 평가하거나 고유한 정책을 완전히 사용자 지정할 수 있습니다. 사용자에게 표시하는 분류 레이블의 색, 이름 및 순서를 변경할 수 있습니다. 도구 설명과 머리글, 바닥글, 워터마크 등의 분류 시각적 표시를 구성할 수도 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)를 통해 몇 분 만에 이러한 기능의 작동 방식을 확인해 보세요.

미리 보기를 통해 새로운 **Premium P2 서비스 계획**과 자동 및 권장 레이블 지정과 같은 몇 가지 고급 기능(일반 공급 시 현재 계획에서는 사용하지 못할 수도 있음)을 사용해 볼 수 있습니다. 다양한 서비스 계획(Azure Information Protection Premium P1 및 Azure Information Protection Premium P2)에 대한 자세한 내용은 블로그 게시물 [Introducing Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/07/introducing-enterprise-mobility-security/)(Enterprise Mobility + 보안 소개)를 참조하세요.

이 미리 보기 릴리스에는 다음과 같은 제한 사항이 있습니다. 추가 기능 및 특징을 사용할 수 있게 되면 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)(Enterprise Mobility 및 보안 블로그) 및 [Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)에서 공지 사항을 확인하세요.

- 분류 및 레이블 지정을 위한 중앙 집중식 로깅은 없습니다.

- 레이블 이름 및 도구 설명은 영어로만 지원됩니다.

- 자동 분류에 대한 조건은 구 또는 패턴이어야 합니다.

- Windows 파일 탐색기에서 파일을 분류할 수 없습니다.

- 모바일 장치(iOS 및 Android) 및 Mac 컴퓨터용 Office 앱과 Office Web Apps(Office Online)는 아직 지원되지 않습니다.

- Exchange Online 또는 SharePoint Online과는 통합되지 않습니다.

- 파트너 및 개발자용 SDK를 사용할 수 없습니다.

## Azure Information Protection을 사용하려면 어떤 구독이 필요하나요?

미리 보기 릴리스의 경우 Azure 권한 관리를 포함하는 모든 구독을 사용할 수 있습니다. Azure Information Protection은 모든 지역에서 사용할 수 있습니다. 사용 가능한 구독에 대한 자세한 내용과 무료 평가판 링크는 [Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.

Azure 포털에서 Azure Information Protection 정책을 구성하려면 Azure 구독이 있어야 합니다. 조직에서 아직 Azure를 구독하지 않은 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. [Azure 시작](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따르세요.

구독 요구 사항에 대한 모든 변경 내용은 [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)에 공지됩니다.

## Azure Information Protection 미리 보기를 사용하려면 전역 관리자여야 하나요?

미리 보기 릴리스의 경우에 한해, Azure에 의해 인증된 모든 사용자는 Azure 포털에서 테넌트의 Azure Information Protection 정책을 확인하고 구성할 수 있습니다.

[Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치할 때 데모 정책 설치 옵션을 선택하면 미리 보기를 사용하기 위해 포털에 로그인할 필요조차 없습니다. 데모 정책에서는 Azure Information Protection에 대한 기본 정책을 로컬로 설치하므로 문서 및 메일에 레이블을 지정해 볼 수 있지만, Azure 포털에 로그인하지 않고서는 레이블을 변경하거나 새 레이블을 추가할 수 없습니다. 

분류하고 레이블을 지정하는 문서와 메일을 보호하려는 경우 아직 Azure 권한 관리를 활성화하지 않았다면 활성화 프로세스에서 특별한 관리자 권한이 필요하게 됩니다. 자세한 내용은 [Azure RMS를 구성하려면 전역 관리자여야 하나요? 또는, 다른 관리자에게 위임할 수 있나요?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators)를 참조하세요.


## Azure Information Protection에서는 온-프레미스 및 하이브리드 시나리오를 지원하나요?

Azure Information Protection은 클라우드 기반 솔루션입니다. 하이브리드 시나리오에 관심이 있는 경우 Information Protection 팀에 문의하거나, askipteam@microsoft.com으로 메일을 보내세요.

## Azure Information Protection에서는 어떤 클라이언트 플랫폼과 응용 프로그램이 지원되나요?

이 내용은 현재 [Azure Information Protection에 대한 요구 사항](requirements-azure-infoprotect.md)에 설명되어 있으며 업데이트될 예정입니다.


## 컴퓨터는 어떻게 Azure Information Protection에서 정책 정보를 가져오며 정책 정보는 얼마나 자주 새로 고쳐지나요?

사용자가 Office 응용 프로그램을 열 때마다 Azure Information Protection 클라이언트는 최신 버전의 Azure Information Protection 정책이 있는지 확인합니다. 최신 버전이 있는 경우 클라이언트는 데이터를 보호하는 HTTPS 링크를 사용하여 최신 버전을 다운로드합니다. 

새 Azure Information Protection 정책을 게시할 때 Office 응용 프로그램의 여러 인스턴스가 로드되는 경우 모든 인스턴스를 닫아 최신 버전의 정책을 가져와야 합니다. 예를 들어 Word 문서 두 개가 열려 있는 경우 하나의 문서에서만 업데이트된 Azure Information Protection 정책을 테스트하려면 두 Word 문서를 모두 닫고 최신 정책을 사용할 문서를 다시 엽니다.

## Azure Information Protection을 사용하려면 파일을 어디에 저장하면 되나요? 

Azure Information Protection에서는 파일과 메일에 영구 레이블 및 보호를 적용하므로 파일 저장 위치는 중요하지 않습니다.

## 새 데이터만 분류할 수 있나요? 아니면 기존 데이터도 분류할 수 있나요?

새 콘텐츠와 기존 콘텐츠에 대한 변경 내용 둘 다에 대해 Azure Information Protection 정책 작업은 문서가 저장되고 메일이 전송될 때 적용됩니다. 

분류하려는 파일을 저장했으면 Office 응용 프로그램에 해당 파일을 열었다가 저장하기만 하면 됩니다. 

현재 분류를 대량으로 검색하고 적용할 수는 없으며, Office 응용 프로그램에서 각 문서를 열고 저장해야 합니다. 

## 암호화 적용 및 사용 권한 제한 없이 분류 목적으로만 Azure Information Protection을 사용할 수 있나요?

예. 레이블을 적용만 하는 Azure Information Protection 정책을 구성할 수 있습니다. 사실, 특별한 데이터 관리가 필요한 일부 문서나 메일만 보호하면 되는 배포 네트워크 대부분의 경우가 여기에 해당할 것으로 예상합니다.

## 자동 분류는 어떻게 작동하나요?

Azure 포털에서 "신용 카드 번호" 또는 "주민등록번호"와 같은 미리 정의된 패턴을 사용할 수 있습니다. 또는 자동 분류에 대한 조건으로 사용자 지정 문자열 또는 패턴을 정의할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다. 

분류의 정확도는 조건을 기반으로 하는 분류 규칙을 구성하는 방법에 따라 달라집니다. 현재 조건에서는 텍스트 패턴 및 정규식이 지원됩니다. 테스트할 수 있는 제안된 몇 가지 예제와 함께 미리 보기에서 사용할 수 있는 각 옵션에 대한 설명은 [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](configure-policy-classification.md)을 참조하세요. 문서가 저장되거나 메일이 전송되면 검색이 실행됩니다.

최상의 사용자 환경과 비즈니스 연속성 보장을 위해 완전한 자동 작업보다는 사용자 권장 작업으로 시작하는 것이 좋습니다. 이렇게 하면 사용자가 레이블 지정 또는 보호 작업을 수락하거나 이러한 제안을 재정의할 수 있습니다.   

## Azure Information Protection에서는 자동 분류를 사용하는 대신 사용자가 직접 파일을 분류하도록 메시지를 표시할 수 있나요? 

예. Azure 포털에서 **Select how this label is applied: automatically or recommended to user**(이 레이블 적용 방법 선택: 자동 또는 사용자에게 권장함) 옵션을 **Recommended**(권장)로 설정하여 자동 분류를 사용할지 사용자에게 권장할지를 구성할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다.  

## 모든 문서를 강제로 분류할 수 있나요?

예. 사용자가 보유한 모든 파일을 분류하도록 해야 할 경우 Azure 포털에서 **All documents and emails must have a label**(모든 문서와 메일에 레이블이 있어야 함)을 **On**(켜기)으로 설정합니다. 

## 파일에서 분류를 제거할 수 있나요?

예. 파일에서 분류를 제거하려면 Office 응용 프로그램에서 파일을 열고 Information Protection 표시줄에서 **Edit label**(레이블 편집) 아이콘을 클릭하고 **Remove label**(레이블 제거) 아이콘을 클릭한 다음 **OK**(확인)를 클릭하여 작업을 확인합니다. 


## 사용자에게 분류 수준을 변경하는 이유를 묻는 메시지를 표시할 수 있나요?

예. 사용자에게 분류를 변경하는 이유를 묻는 메시지를 표시하려면 Azure 포털에서 **Users must provide justification when lowering the sensitivity level**(민감도를 낮출 때 사용자가 근거를 제공해야 함)을 **On**(켜기)으로 설정합니다. 사용자가 이렇게 할 때 해당 작업 및 변경 이유는 사용자의 로컬 Windows 이벤트 로그 **응용 프로그램** > **Microsoft Azure Information Protection**에 기록됩니다.

## 콘텐츠가 분류된 후 자동으로 콘텐츠를 보호할 수 있나요?

Azure 포털에서 지정한 분류 수준에 따라 자동으로 콘텐츠를 보호하는 Azure 권한 관리 템플릿을 선택할 수 있습니다.

[Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)에서 이러한 예제를 확인할 수 있습니다. 자세한 내용은 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.

## 파일 하나를 두 가지 분류로 분류할 수 있나요?

필요한 경우 특정 민감도 레이블의 하위 범주를 더 잘 설명하는 하위 레이블을 만들 수 있습니다. 예를 들어 주 레이블 **Secret**(비밀)은 **Secret – Legal**(비밀 – 법적) 및 **Secret – Finance**(비밀 – 재무)와 같은 하위 레이블을 포함할 수 있습니다. 그런 다음 서로 다른 분류 시각적 표시와 서로 다른 권한 관리 템플릿을 서로 다른 하위 레이블에 적용할 수 있습니다.

현재 두 수준 모두에 시각적 표시, 보호 및 조건을 설정할 수는 있지만, 하위 수준을 사용할 때는 이러한 설정을 하위 수준에 대해서만 구성하세요. 부모 레이블과 하위 수준에 같은 설정을 구성하면 하위 수준의 설정이 우선합니다.

## DLP 솔루션 및 다른 응용 프로그램을 Azure Information Protection과 통합하려면 어떻게 하나요?

Azure Information Protection에서는 일반 텍스트 레이블을 포함하는 영구 메타데이터를 분류에 사용하므로 DLP 솔루션 및 다른 응용 프로그램에서 이 정보를 읽을 수 있습니다. 파일에서 이 메타데이터는 사용자 지정 속성에 저장되고, 메일에서 이 정보는 메일 헤더에 있습니다.

## 문서 추적 및 취소는 Azure Information Protection에 대해 어떻게 작동하나요?

Azure Information Protection을 사용하여 분류하고 보호하는 파일에 대한 문서 추적은 현재 Azure 권한 관리에 대해서와 동일하게 작동합니다. 자세한 내용은 [RMS 공유 응용 프로그램을 사용하는 경우 문서 추적 및 취소](../rms-client/sharing-app-track-revoke.md)를 참조하세요.

## 구성한 정책을 Azure Information Protection에서는 어떻게 적용하나요?

Azure 권한 관리 템플릿을 사용하여 문서가 보호되는 경우 먼저 사용자가 인증되어 해당 사용자에게 문서에 대한 권한이 있는지를 확인한 다음 응용 프로그램에서 사용 권한 정책을 적용합니다. 

## Azure Information Protection에서는 Azure Active Directory를 어떻게 사용하나요?

Azure Information Protection에서는 사용자 인증에 Azure Active Directory를 사용합니다.

## Azure Information Protection을 사용하여 콘텐츠를 분류하고 보호할 수 있는 사용자를 제어할 수 있나요?

Azure Information Protection 클라이언트 배포를 제어하여 데이터를 분류하고 보호하는 사용자를 제한할 수 있습니다. 

Azure Information Protection에 의해 분류된 파일과 메일은 Azure Information Protection 클라이언트의 설치 여부와 관계없이 모든 사용자가 이용하거나 편집할 수 있습니다. 

## 이 미리 보기에 대한 문제를 보고하거나 의견을 보낼 수 있나요?

이 미리 보기 릴리스를 사용하다가 문제를 발견한 경우 Office 응용 프로그램의 **홈** 탭에 있는 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다. **Microsoft Azure Information Protection** 대화 상자에서 **Send feedback**(의견 보내기)을 클릭합니다. 그러면 Information Protection 팀에 메일이 전송되고 자동으로 PC에서 로그 파일이 첨부되어 문제 진단에 도움을 줍니다. 

질문이나 의견이 있으면 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)를 사용하세요. 

## 내 문의 내용이 여기 없다면 어떻게 하나요?

먼저, Enterprise Mobility 및 보안 블로그에서 내 문의 내용이 [Azure Information Protection preview announcement](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/12/azure-information-protection-public-preview-available-now/)(Azure Information Protection 미리 보기 공지)에 없는지 확인합니다.

그런 다음 [Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)를 방문하여 다른 사용자가 같은 문의 내용을 남겼는지 확인합니다. 같은 문의 내용이 없으면 그곳에 문의 내용을 게시합니다.







<!--HONumber=Jul16_HO5-->


