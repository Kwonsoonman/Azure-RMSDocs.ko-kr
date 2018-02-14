---
title: "Azure RMS 작동 방식 - Azure Information Protection"
description: "Azure RMS의 작동 방식, 사용되는 암호화 컨트롤 및 이 프로세스의 작동 방식에 대한 단계별 다이어그램을 분석합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: eb65f99d1a0fbc2c9aaee25a585561bd2511b723
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Azure RMS는 어떻게 작동합니까? 기본적인 이해

>*적용 대상: Azure Information Protection, Office 365*

Azure RMS가 작동하는 방식을 이해하는 데 있어 중요한 점은 Azure Information Protection의 이 데이터 보호 서비스에서 보호 프로세스의 일부로 데이터를 표시하거나 저장하지 않는다는 것입니다. 보호하는 정보는 Azure에 명시적으로 저장하거나 Azure에 저장하는 다른 클라우드 서비스를 사용하지 않는 한 Azure에 전송되거나 저장되지 않습니다. Azure RMS는 단순히 권한 있는 사용자 및 서비스 이외의 다른 사람이 문서의 데이터를 읽을 수 없게 만듭니다.

- 데이터는 응용 프로그램 수준에서 암호화되며, 해당 문서에 대해 권한 있는 사용을 정의하는 정책을 포함합니다.

- 합법적인 사용자가 보호된 문서를 사용하거나 권한 있는 서비스에서 이러한 문서를 처리하는 경우 문서의 데이터가 암호 해독되고 정책에 정의된 권한이 적용됩니다.

다음 그림에서는 이 프로세스가 높은 수준에서 작동하는 방식을 확인할 수 있습니다. 비밀 수식이 포함된 문서가 보호되고, 권한이 있는 사용자 또는 서비스에서 성공적으로 열립니다. 문서는 콘텐츠 키(이 그림의 녹색 키)로 보호됩니다. 이 키는 각 문서에 대해 고유하며, Azure Information Protection 테넌트 루트 키(이 그림의 빨간색 키)로 보호되는 파일 헤더에 배치됩니다. Microsoft에서 테넌트 키를 생성하고 관리하거나, 사용자 고유의 테넌트 키를 생성하고 관리할 수 있습니다.

Azure RMS에서 제한을 암호화, 암호 해독, 권한 부여 및 적용하는 보호 프로세스에서는 비밀 수식이 Azure로 전송되지 않습니다.

![Azure RMS에서 파일을 보호하는 방식](../media/AzRMS_SecretColaFormula_final.png)

상황에 대한 자세한 설명은 이 문서의 [Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 사용](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) 섹션을 참조하세요.

Azure RMS가 사용하는 알고리즘 및 키 길이에 대한 기술적인 세부 사항은 다음 섹션을 참조하세요.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Azure RMS에서 사용되는 암호화 컨트롤: 알고리즘 및 키 길이
이 기술의 작동 방식을 자세히 알 필요가 없는 경우에도 이 기술에서 사용하는 암호화 컨트롤에 대해 질문할 수 있습니다. 예를 들어 업계 표준의 보안 보호인지 확인하는 경우가 있습니다.


|암호화 컨트롤|Azure RMS에서 사용|
|-|-|
|알고리즘: AES<br /><br />키 길이: 128비트 및 256비트 [[1]](#footnote-1)|문서 보호|
|알고리즘: RSA<br /><br />키 길이: 2,048비트 [[2]](#footnote-2)|키 보호|
|SHA-256|인증서 서명|

###### <a name="footnote-1"></a>각주 1 

파일에 .ppdf 파일 이름 확장명이 있거나 보호된 텍스트 또는 이미지 파일(예: .ptxt 또는 .pjpg)인 경우, Azure Information Protection 클라이언트 및 Rights Management 공유 응용 프로그램에서 일반 보호 및 기본 보호에 대해 256비트를 사용합니다.

###### <a name="footnote-2"></a>각주 2

2,048비트는 Azure Rights Management 서비스가 활성화될 때의 키 길이입니다. 1,024비트는 다음과 같은 선택적 시나리오에서 지원됩니다.

- AD RMS 클러스터가 암호화 모드 1에서 실행되는 경우 온-프레미스에서 마이그레이션하는 동안

- AD RMS 클러스터가 Exchange Online을 사용하는 경우 온-프레미스에서 마이그레이션한 후

- 마이그레이션 전에 온-프레미스에서 만든 보관된 키의 경우. 이전에 AD RMS로 보호된 콘텐츠는 Azure Rights Management 서비스 마이그레이션 후에도 계속 열 수 있습니다.

- 고객이 Azure Key Vault를 사용하여 자신의 키(BYOK)를 가져오도록 선택하는 경우. Azure Information Protection에서 1,024비트 및 2,048비트의 키 길이를 지원합니다. 강화된 보안을 위해 2,048비트의 키 길이를 사용하는 것이 좋습니다.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>Azure RMS 암호화 키를 저장 및 보호하는 방법

Azure RMS는 Azure RMS로 보호되는 각 문서 또는 이메일에 대한 단일 AES 키("콘텐츠 키")를 만들고, 이 키는 문서에 포함되며 문서의 모든 버전에서 유지됩니다. 

콘텐츠 키는 문서에서 정책의 일부인 조직의 RSA 키("Azure Information Protection 테넌트 키")로 보호되며, 문서 작성자가 정책에 서명합니다. 이 테넌트 키는 조직의 Azure Rights Management 서비스로 보호되는 모든 문서 및 이메일에 공통적으로 적용되며, 조직에서 고객이 관리하는 테넌트 키(BYOK 또는 "Bring Your Own Key")를 사용하는 경우에만 Azure Information Protection 관리자가 변경할 수 있습니다. 

이 테넌트 키는 Microsoft의 온라인 서비스, 엄격히 통제되는 환경 및 면밀한 모니터링에서 보호됩니다. 고객이 관리하는 테넌트 키(BYOK)를 사용하는 경우,키를 추출하거나, 내보내거나, 모든 환경에서 공유하는 기능이 없어도 이 보안은 각 Azure 지역에서 고급 HSM(하드웨어 보안 모듈) 배열을 사용하여 강화됩니다. 테넌트 키 및 BYOK에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요.

Windows 장치로 전송되는 라이선스 및 인증서는 클라이언트의 장치 개인 키로 보호되며, 이 키는 장치의 사용자가 Azure RMS를 처음 사용할 때 만들어집니다. 따라서 이 개인 키는 클라이언트에서 사용자의 암호로부터 파생된 키를 사용하여 이러한 비밀을 보호하는 DPAPI로 보호됩니다. 모바일 장치에서 키는 한 번만 사용됩니다. 따라서 이러한 키는 클라이언트에 저장되지 않으므로 장치에서 보호할 필요가 없습니다. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 사용
Azure RMS가 작동하는 방식을 자세히 이해하기 위해 [Azure Rights Management 서비스가 활성화](../deploy-use/activate-service.md)된 후 및 사용자가 자신의 Windows 컴퓨터에서 Rights Management Services를 처음 사용하고(**사용자 환경 초기화** 또는 부트 스트랩으로 알려진 프로세스), **콘텐츠(문서 또는 이메일)를 보호**한 다음, 다른 사람이 보호한 콘텐츠를 **사용**하는 경우의 일반적인 흐름을 단계별로 살펴보겠습니다.

사용자 환경이 초기화되면 해당 사용자가 해당 컴퓨터에서 문서를 보호하거나 보호된 문서를 사용할 수 있습니다.

> [!NOTE]
> 이 사용자가 다른 Windows 컴퓨터로 이동하거나 다른 사용자가 동일한 이 Windows 컴퓨터를 사용하는 경우 초기화 프로세스가 반복됩니다.

### <a name="initializing-the-user-environment"></a>사용자 환경 초기화
사용자가 Windows 컴퓨터에서 콘텐츠를 보호하거나 보호된 콘텐츠를 사용하려면, 먼저 장치에서 사용자 환경을 준비해야 합니다. 이는 일회성 프로세스이며, 사용자가 보호된 콘텐츠를 보호하거나 사용하려고 할 때 사용자 개입 없이 자동으로 수행됩니다.

![RMS 클라이언트 활성화 흐름 - 1단계 클라이언트 인증](../media/AzRMS.png)

**1단계의 상황**: 컴퓨터의 RMS 클라이언트에서 먼저 Azure Rights Management 서비스에 연결하고, Azure Active Directory 계정을 사용하여 사용자를 인증합니다.

사용자 계정이 Azure Active Directory와 페더레이션되면, 이 인증은 자동으로 수행되며 사용자에게 자격 증명을 묻는 메시지가 표시되지 않습니다.

![RMS 클라이언트 활성화 - 2단계 클라이언트에 인증서 다운로드](../media/AzRMS_useractivation2.png)

**2단계의 상황**: 사용자가 인증되면 보호된 콘텐츠를 사용하고 오프라인으로 콘텐츠를 보호하기 위해 연결이 조직의 Azure Information Protection 테넌트로 자동으로 리디렉션됩니다. 이 테넌트는 사용자가 Azure Rights Management 서비스에 인증할 수 있는 인증서를 발급합니다.

사용자의 인증서 복사본은 Azure에 저장되므로 사용자가 다른 장치로 이동하는 경우 동일한 키를 사용하여 인증서가 만들어집니다.

### <a name="content-protection"></a>콘텐츠 보호
사용자가 문서를 보호하면 RMS 클라이언트에서 보호되지 않은 문서에 대해 다음 작업을 수행합니다.

![RMS 문서 보호 - 1단계 문서 암호화](../media/AzRMS_documentprotection1.png)

**1단계의 상황**: RMS 클라이언트에서 임의 키(콘텐츠 키)를 만들고, AES 대칭 암호화 알고리즘을 사용하여 이 키로 문서를 암호화합니다.

![RMS 문서 보호 - 2단계 정책 만들기](../media/AzRMS_documentprotection2.png)

**2단계의 상황**: 다음으로 RMS 클라이언트에서 사용자 또는 그룹에 대한 [사용 권한](../deploy-use/configure-usage-rights.md) 및 기타 제한 사항(예: 만료 날짜)이 포함된 문서에 대한 정책을 포함하는 인증서를 만듭니다. 이러한 설정은 관리자가 이전에 구성했거나 콘텐츠가 보호되는 시점에 지정한 템플릿("임시 정책"이라고도 함)에서 정의할 수 있습니다.   

선택한 사용자 및 그룹을 식별하는 데 사용되는 기본 Azure AD 특성은 사용자 또는 그룹의 모든 이메일 주소를 저장하는 Azure AD ProxyAddresses 특성입니다. 그러나 사용자 계정에 AD ProxyAddresses 특성의 값이 없으면 사용자의 UserPrincipalName 값이 대신 사용됩니다.

그런 다음, RMS 클라이언트는 사용자 환경을 초기화할 때 얻은 조직의 키를 사용하고, 이 키를 사용하여 정책 및 대칭 콘텐츠 키를 암호화합니다. 또한 RMS 클라이언트는 사용자 환경을 초기화할 때 얻은 사용자의 인증서로 정책에 서명합니다.

![RMS 문서 보호 - 3단계 문서에 정책 포함](../media/AzRMS_documentprotection3.png)

**3단계의 상황**: 마지막으로 RM 클라이언트에서 이전에 암호화된 문서 본문이 있는 파일에 정책을 포함하여 보호된 문서를 구성합니다.

이 문서는 어디에든 저장할 수 있고, 어떤 방법으로든 공유할 수 있으며, 정책은 항상 암호화된 문서와 함께 유지됩니다.

### <a name="content-consumption"></a>콘텐츠 사용
사용자가 보호된 문서를 사용하려면 Azure Rights Management 서비스에 대한 액세스를 요청하여 RMS 클라이언트를 시작합니다.

![RMS 문서 사용 - 1단계 사용자에 의한 인증 및 권한 목록 가져오기](../media/AzRMS_documentconsumption1.png)

**1단계의 상황**: 인증된 사용자는 문서 정책과 사용자의 인증서를 Azure Rights Management 서비스에 보냅니다. 서비스는 정책을 해독하고, 평가하고, 사용자가 문서에 대해 갖는 권한 목록을 작성합니다(있는 경우). 사용자를 식별하기 위해 Azure AD ProxyAddresses 특성이 사용자의 계정 및 사용자가 속한 그룹에 사용됩니다. 성능상의 이유로 그룹 구성원 자격이 [캐시됩니다](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). 사용자 계정에 Azure AD ProxyAddresses 특성 값이 없는 경우 Azure AD UserPrincipalName의 값이 대신 사용됩니다.

![RMS 문서 사용 - 2단계 클라이언트에 사용 라이선스 반환](../media/AzRMS_documentconsumption2.png)

**2단계의 상황**: 다음으로 서비스에서 해독된 정책으로부터 AES 콘텐츠 키를 추출합니다. 이 키는 요청을 통해 얻은 사용자의 공개 RSA 키로 암호화됩니다.

그런 다음, 다시 암호화된 콘텐츠 키가 사용자 권한 목록과 함께 암호화된 사용 라이선스에 포함된 후 RMS 클라이언트에 반환됩니다.

![RMS 문서 사용 - 3단계 문서의 암호 해독 및 권한 적용](../media/AzRMS_documentconsumption3.png)

**3단계의 상황**: 마지막으로 RMS 클라이언트에서 암호화된 사용 라이선스를 가져오고 자체의 사용자 개인 키로 해독합니다. 이렇게 하면 RMS 클라이언트에서 필요에 따라 문서의 본문을 해독하고 화면에 렌더링할 수 있습니다.

또한 클라이언트는 권한 목록을 해독하고 응용 프로그램에 전달하여 응용 프로그램의 사용자 인터페이스에 해당 권한을 적용합니다.

> [!NOTE]
> 조직 외부의 사용자가 보호한 콘텐츠를 사용하는 경우 사용 흐름은 동일합니다. 이 시나리오의 변경 내용은 사용자가 인증되는 방법입니다. 자세한 내용은 [보호되는 문서를 회사 외부의 누군가와 공유할 때 해당 사용자를 어떻게 인증하나요?](../get-started/faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)를 참조하세요.


### <a name="variations"></a>변형
앞의 연습에서는 표준 시나리오를 다루었지만, 이제 몇 가지 변형이 있습니다.

-   **모바일 장치**: 모바일 장치에서 Azure Rights Management 서비스를 사용하여 파일을 보호하거나 사용하는 경우 프로세스 흐름이 훨씬 더 간단합니다. 대신 각 트랜잭션(콘텐츠 보호 또는 사용)이 독립적이기 때문에 모바일 장치는 먼저 사용자 초기화 프로세스를 거치지 않습니다. Windows 컴퓨터와 마찬가지로 모바일 장치는 Azure Rights Management 서비스에 연결하여 인증합니다. 콘텐츠를 보호하기 위해 모바일 장치는 정책을 제출하고, Azure Rights Management 서비스는 문서를 보호하기 위한 게시 라이선스 및 대칭 키를 모바일 장치에 보냅니다. 콘텐츠를 사용하기 위해 모바일 장치가 Azure Rights Management 서비스에 연결되어 인증되면, 문서 정책을 Azure Rights Management 서비스에 보내고 문서를 사용하기 위한 사용 라이선스를 요청합니다. 이에 대한 응답으로 Azure Rights Management 서비스는 필요한 키와 제한 사항을 모바일 장치로 보냅니다. 두 프로세스 모두에서 TLS를 사용하여 키 교환 및 기타 통신을 보호합니다.

-   **RMS 커넥터**: Azure Rights Management 서비스를 RMS 커넥터와 함께 사용하는 경우 프로세스 흐름은 동일하게 유지됩니다. 유일한 차이점은 커넥터가 온-프레미스 서비스(예: Exchange Server 및 SharePoint Server)와 Azure Rights Management 서비스 간의 릴레이 역할을 한다는 것입니다. 커넥터 자체는 사용자 환경 초기화 또는 암호화/암호 해독과 같은 작업을 수행하지 않습니다. 커넥터는 일반적으로 AD RMS 서버로 이동하는 통신을 중계하여 양쪽에서 사용되는 프로토콜 간의 변환을 처리합니다. 이 시나리오에서는 온-프레미스 서비스와 함께 Azure Rights Management 서비스를 사용할 수 있습니다.

-   **일반 보호(.pfile)**: Azure Rights Management 서비스에서 일반적으로 파일을 보호하는 경우, RMS 클라이언트가 모든 권한을 부여하는 정책을 만드는 것을 제외하고는 콘텐츠 보호에 대한 흐름이 기본적으로 동일합니다. 파일이 사용되면 대상 응용 프로그램에 전달되기 전에 해독됩니다. 이 시나리오에서는 RMS를 기본적으로 지원하지 않는 경우에도 모든 파일을 보호할 수 있습니다.

-   **보호된 PDF(.ppdf)**: Azure Rights Management 서비스에서 Office 파일을 기본적으로 보호하는 경우, 해당 파일의 복사본을 만들고 동일한 방식으로 보호합니다. 유일한 차이점은 파일 복사가 PPDF 파일 형식이며, Azure Information Protection 클라이언트 뷰어 및 RMS 공유 응용 프로그램에서 보기 전용으로 여는 방법을 알고 있다는 것입니다. 이 시나리오에서는 모바일 장치에 보호된 Office 파일을 기본적으로 지원하는 앱이 없더라도 모바일 장치의 받는 사람이 항상 읽을 수 있다는 사실을 알고 있으므로 이메일을 통해 보호된 첨부 파일을 보낼 수 있습니다.

## <a name="next-steps"></a>다음 단계

Azure Rights Management 서비스에 대해 자세히 알아보려면, [응용 프로그램에서 Azure Rights Management 서비스를 지원하는 방법](applications-support.md)과 같은 다른 문서의 **이해 및 탐색** 섹션을 사용하여 기존 응용 프로그램이 Azure Rights Management와 통합되어 정보 보호 솔루션을 제공하는 방법을 확인합니다. 

[Azure Information Protection에 사용되는 용어](../get-started/terminology.md)를 검토하여 Azure Rights Management 서비스를 구성하고 사용할 때 나올 수 있는 용어를 파악하고, 배포를 시작하기 전에 [Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)도 확인합니다. 직접 참여하여 사용해 보려면 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 사용합니다.

조직에 대한 데이터 보호 배포를 시작할 준비가 되면 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 배포 단계 및 방법 지침에 대한 링크를 확인합니다.

> [!TIP]
> 추가 정보 및 도움말을 보려면 [Azure Information Protection에 대한 정보 및 지원](../get-started/information-support.md)의 리소스 및 링크를 사용하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]