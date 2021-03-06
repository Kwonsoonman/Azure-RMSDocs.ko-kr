---
title: Azure Information Protection에 사용되는 용어
description: Microsoft Azure Information Protection과 관련된 단어, 구 또는 약어가 헷갈리시나요? Azure Information Protection에 관련이 있거나 이 서비스 컨텍스트에서 사용될 때 특정 의미를 지니는 용어 및 약어의 정의를 여기서 확인해 보세요.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/04/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 01c2e8d4dd476e0910a75fd5949362225743f322
ms.sourcegitcommit: 4cd90fcf94ac6e2543d8be10e6e29e8218d5fd9d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49651966"
---
# <a name="terminology-for-azure-information-protection"></a>Azure Information Protection에 사용되는 용어

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Microsoft Azure Information Protection과 관련된 단어, 구 또는 약어가 헷갈리시나요? Azure Information Protection에 관련이 있거나 이 서비스 컨텍스트에서 사용될 때 특정 의미를 지니는 용어 및 약어의 정의를 여기서 확인해 보세요.

|용어|정의|
|--------|--------------|
|AADRM|Azure Rights Management 서비스의 PowerShell 모듈 이름으로, 이전 이름이 (Windows) Azure Active Directory Rights Management였을 때 Azure Rights Management의 비공식 약어에서 파생된 서비스입니다.|
|활성화|조직이 문서 및 메일을 보호할 수 있도록 Azure Rights Management 서비스를 사용합니다. 이 동작은 Exchange Online 및 SharePoint Online에서 IRM 기능이 사용되도록 합니다.|
|Active Directory Rights Management Services|흔히 약어로 *AD RMS*라고 합니다.<br /><br />암호화 및 정책을 사용하여 권한 관리 보호를 제공함으로써 문서, 파일 및 메일을 보호하는 Windows Server 역할입니다.|
|AD RMS|*Active Directory Rights Management Services*를 참조하세요.|
AzureInformationProtection|Azure Information Protection 클라이언트에 대한 PowerShell 모듈의 이름입니다.
|Azure Information Protection|레이블을 사용하여 문서와 메일을 분류하고 보호하는 클라우드 기반 서비스입니다. Azure 권한 관리에서는 암호화, ID 및 권한 부여 정책을 사용하여 보호를 제공합니다.|
Azure Information Protection 클라이언트|사용자, 관리자 및 서비스가 Azure Information Protection 정책의 레이블 및 설정을 사용할 수 있도록 하는 Azure Information Protection의 클라이언트 쪽입니다.|
|Azure Information Protection 레이블|문서 및 메일에 분류 값을 적용하는 항목으로, 선택적으로 문서와 메일을 보호할 수 있습니다.|
|Azure Information Protection 정책|Azure Information Protection 레이블 및 정책 설정을 사용하는 클라이언트 및 서비스에 대해 관리자가 정의한 구성입니다.|
|Azure Information Protection 스캐너|Windows Server에서 실행되고 로컬 폴더, 네트워크 공유, SharePoint 서버 사이트 및 라이브러리에서 문서를 검색, 분류 및 보호할 수 있는 서비스입니다.|
|Azure Information Protection 뷰어|보호된 파일을 표시하기 위해 Windows 컴퓨터 및 모바일 장치에서 실행되는 앱입니다.|
|Azure Rights Management|흔히 약어로 *Azure RMS*라고 합니다.<br /><br />암호화 및 정책을 사용하여 문서, 파일 및 전자 메일을 보호하는 Azure Information Protection에서 사용되는 Azure 서비스입니다.  *Azure 권한 관리 서비스*라고도 합니다. 이전 이름은 다음과 같습니다.<br /><br />- *Microsoft Azure Active Directory Rights Management*: 흔히 약어로 Microsoft Azure AD Rights Management Service라고 합니다.<br /><br />- *RMS Online*: 원래 제안된 이름으로, 간혹 오류 메시지와 로그 파일 항목에 표시될 수 있습니다.|
|Azure RMS|*Azure 권한 관리*를 참조하세요.|
|기본 템플릿|중요한 정보가 포함되어 있는 문서와 메일 보호를 즉시 시작할 수 있도록 Azure Information Protection에 대한 구독을 구입할 때 자동으로 생성된 보호 템플릿입니다.|
|BYOK|*Bring Your Own Key*를 참조하세요.|
|Bring Your Own Key|흔히 약어로 *BYOK*라고 합니다.<br /><br />Azure Information Protection의 고유 테넌트 키를 생성 및 관리하려는 조직에서 선택하는 구성 및 토폴로지 옵션입니다.|
|콘텐츠 키|RMS 지원 응용 프로그램이 Rights Management를 사용하여 보호되는 각 문서 또는 이메일에 대해 만드는 고유 키로서 정보 공개 위험을 제한하는 데 도움이 됩니다.|
|사용|해당 콘텐츠가 Rights Management로 보호된 경우 문서나 메일을 열어 읽거나 사용합니다. 문서의 경우 사용에는 보호된 문서 편집 및 보호된 문서에 새 콘텐츠 추가가 포함됩니다. 메일 메시지의 경우 사용에는 보호된 메시지에 회신이 포함됩니다.|
|비활성화|조직이 더 이상 Azure Information Protection을 사용할 수 없도록 권한 관리 서비스가 사용되지 않게 합니다.|
|부서별 템플릿|사용자가 만들고 조직의 모든 사용자가 아닌 선택한 사용자만 볼 수 있도록 구성된 보호 템플릿입니다. *범위가 지정된 템플릿*이라고도 합니다.|
|지원 응용 프로그램|기본적으로 권한 관리를 지원하는 응용 프로그램입니다(Word 및 Excel과 같은 Office 응용 프로그램 포함). 또한 ISV(Independent Software Vendor) 및 개발자는 기본적으로 Rights Management를 지원하는 응용 프로그램을 작성할 수 있습니다.|
|엔터프라이즈 권한 관리|일반적으로 조직이 암호화 및 정책 권한 부여 도구를 조합하여 중요한 정보를 보호할 수 있게 해주는 제품과 솔루션을 설명하는 데 사용되는 업계 표준의 일반 용어입니다. Azure Information Protection은 ERM(엔터프라이즈 권한 관리) 솔루션의 한 가지 예입니다.|
|ERM|*엔터프라이즈 권한 관리*를 참조하세요.|
|일반 보호|모든 파일 형식을 암호화하고 권한 없는 사용자가 파일을 열지 못하도록 하는 보호 수준입니다. 파일이 열리고 나면 이제 파일의 암호가 해제되어 기본적으로 Rights Management를 지원하지 않는 응용 프로그램에서 파일을 사용할 수 있습니다.|
|HYOK|*Hold Your Own Key*를 참조하세요.|
|Hold Your Own Key|흔히 약어로 *HYOK*라고 합니다.<br /><br />일반적으로 규정 또는 준수 때문에 온-프레미스에서 고유한 키를 생성 및 저장하려는 조직을 위한 구성 및 토폴로지 옵션입니다.|
|키 개체|테넌트 키의 컨텍스트에서 암호화 작업에 대해 Azure Rights Management 서비스에서 필요로 하는 메타데이터를 포함하는 엔터티입니다.|
|label|*Azure Information Protection 레이블*을 참조하세요.|
|정보 보호|경우에 따라 약어로 *IP*라고 합니다.<br /><br />무단 액세스로부터 데이터와 파일을 보호하는 것을 지칭하는 업계 표준의 일반 용어로서, 메일 또는 문서 공유를 통해 데이터와 파일이 조직 경계를 벗어난 후에도 해당합니다. Microsoft Azure Information Protection은 IP(정보 보호) 솔루션의 한 가지 예입니다.|
|정보 권한 관리|흔히 약어로 *IRM*이라고 합니다.<br /><br />Office 서비스(예: Exchange Server, Word 및 SharePoint Online)와 함께 Microsoft Rights Management 서비스를 지원하는 기능을 설명하는 데 사용되는 용어입니다.|
|IRM|*정보 권한 관리*를 참조하세요.|
|Office 메시지 암호화|흔히 약어로 *OME*라고 합니다.<br /><br />새 Office 365 메시지 암호화 기능은 Azure Rights Management 서비스와의 네이티브 통합이 포함되어 고유한 키(BYOK) 시나리오에서 자동 내부 및 외부 사용자에게 동일한 이메일 보호, 템플릿 자동 새로 고침 및 지원을 제공합니다. 이전 OME 구현은 외부 받는 사람을 위해 설계되었으며, 메일 흐름 규칙이 필요했고, BYOK를 지원하지 않았습니다.|
|MSDRM|경우에 따라 RMS 클라이언트 1.0을 지칭하는 용어로 사용되며, RMS 클라이언트 1.0은 최신 클라이언트인 MSIPC로 바뀌었습니다. 이 이전 클라이언트는 RMS SDK 1.0으로 개발된 응용 프로그램과 Office 2010 및 Office 2007, Exchange 2010 및 Exchange 2013, SharePoint 2010 및 SharePoint 2007을 지원합니다.|
|MSIPC|경우에 따라 RMS 클라이언트 2.0을 지칭하는 용어로 사용되며, RMS 클라이언트 2.0은 이전 RMS 클라이언트인 MSDRM을 대체합니다. 이 나중 클라이언트는 RMS SDK 2.0으로 개발한 응용 프로그램을 지원하고 Office 2016 및 Office 2013, SharePoint 2013, RMS 공유 응용 프로그램과 Azure Information Protection 클라이언트를 지원합니다.|
|기본 보호|무단 사용자가 파일을 열지 못하도록 하고 더 엄격한 정책(예: 읽기 전용 및 인쇄 금지)도 강제 적용할 수 있는 모든 지원 응용 프로그램에서 사용 가능한 보호 수준입니다. 또한 이 보호 수준은 파일이 다른 사용자에게 전달되거나 다른 사용자가 액세스할 수 있는 공용 위치에 저장되는 경우에도 파일에 유지됩니다.|
|.pfile|권한 관리 서비스가 일반적으로 보호하는 모든 파일에 추가되는 파일 이름 확장명입니다.|
|사용 권한 수준|최종 사용자와 관리자가 역할 기반 구성 옵션을 보다 쉽게 선택할 수 있도록 하는 사용 권한의 논리적 그룹입니다. 예로 검토자 및 공동 작성자가 있습니다.|
|보호|데이터 보호를 위한 암호화, ID, 액세스 제어 정책 등을 통해 권한 관리 제어를 파일이나 전자 메일 메시지에 적용합니다.|
|보호 템플릿|*권한 정책 템플릿*, *Rights Management 템플릿*, *RMS 템플릿*이라고도 합니다.<br /><br />관리자가 관리하고 권한 있는 사용자에 대해 정의된 사용 권한, 만료 및 오프라인 액세스에 대한 액세스 제어가 포함되는 보호 설정 그룹입니다. |
|publish|무단 액세스 및 사용으로부터 파일을 보호하기 위해 파일에 보호 조치를 취하는 것입니다. 보호 템플릿 및 Azure Information Protection 정책과 함께 사용되어 이러한 항목을 클라이언트 및 서비스에서 사용할 수 있도록 만드는 용어로도 사용됩니다.|
|권한 관리 커넥터|Azure Rights Management 서비스로 데이터를 보호하기 위해 온-프레미스 서비스(예: Exchange Server 및 SharePoint)에 대해 배포할 수 있는 아웃바운드 프록시 릴레이입니다.|
|Rights Management 발급자|문서 또는 전자 메일을 보호하는 계정입니다.|
|Rights Management 소유자|Rights Management Full Control 사용 권한을 자동으로 부여하여 보호된 문서 또는 전자 메일에 대해 완전한 제어 권한을 가지고 만료 날짜 또는 오프 라인 설정으로부터 제외되는 계정입니다.|
|권한 관리 서비스|클라우드 버전의 Rights Management(Azure Rights Management) 및 온-프레미스 버전의 Rights Management(AD RMS)에 모두 적용되는 일반 용어입니다.|
|Rights Management 공유 응용 프로그램|현재 Azure Information Protection 클라이언트로 대체되며, Windows 및 모바일 장치용의 선택적 응용 프로그램으로서 내부 및 메일을 통해 파일이 안전하게 공유되도록 합니다.|
|RMS|*Rights Management Services*를 참조하세요.|
|RMS 커넥터|*Rights Management 커넥터*를 참조하세요.|
|개인용 RMS|조직이 Office 365 또는 Azure Active Directory 구독을 보유하고 있지 않은 경우 사용자가 Rights Management를 사용할 수 있도록 하는 무료 구독입니다.|
|RMS 공유 앱|*Rights Management 공유 응용 프로그램*을 참조하세요.|
|RMS 템플릿|*보호 템플릿*을 참조하세요.|
|보호 전용 모드|레이블을 적용할 Azure Information Protection 정책이 없는 경우 Azure Information Protection 클라이언트에 대한 작동 모드입니다. 이 모드에서는 분류 레이블이 표시되지 않지만 사용자가 Rights Management 보호를 계속 적용할 수 있습니다.|
|스캐너|*Azure Information Protection 스캐너*를 참조하세요.|
|슈퍼 사용자|조직에서 권한 관리 서비스로 보호하는 파일을 암호 해독하고 이러한 파일에 액세스할 수 있는 고도로 신뢰할 수 있는 관리자 그룹입니다. 일반적으로 이 액세스 수준은 법적 eDiscovery 및 감사 팀에 필요합니다.|
|테넌트 키|SLC(서버 사용 허가자 인증서) 키라고도 합니다.<br /><br />이 키는 조직에 대해 고유하며, 최종적으로 이 테넌트 키에 체이닝되는 모든 Rights Management 암호화 기능을 보호합니다.|
|보호 해제|데이터 보호를 위해 암호화, ID, 사용 권한 및 액세스 제어 정책이 사용된 파일이나 메일 메시지에서 보호 제어를 제거합니다.|
|사용 라이선스 |권한 관리 서비스로 보호되는 파일 및 메일 메시지를 여는 사용자에게 부여되는 문서별 인증서입니다. 이 인증서에는 문서의 정책에 정의된 추가적인 액세스 제한 사항뿐만 아니라 파일 또는 메일 메시지에 대한 사용자의 권한과 콘텐츠를 암호화하는 데 사용된 암호화 키도 들어 있습니다.|

