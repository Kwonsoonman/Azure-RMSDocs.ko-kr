---
title: "Azure RMS 작동 방식 | Azure Information Protection"
description: "Azure RMS의 작동 방식과 Azure RMS에서 사용하는 암호화 컨트롤에 대해 자세히 설명하고 이 프로세스의 작동 방식을 보여 주는 단계별 다이어그램을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0e66bfa436bf811b34cf3cfe1b2d68a6a4e137c2
ms.openlocfilehash: dd6c9250102e104ba49b0c08f14d9959cd1228cb


---


# <a name="how-does-azure-rms-work-under-the-hood"></a>Azure RMS는 어떤 방식으로 작동합니까? 기본적인 이해

>*적용 대상: Azure Information Protection, Office 365*

Azure RMS가 작동하는 방식을 이해할 때 중요한 한 가지 사항은 권한 관리 서비스(및 Microsoft)가 데이터를 정보 보호 프로세스의 일부로 보거나 저장하지 않는다는 것입니다. 보호하는 정보는 Azure에 명시적으로 저장하거나 Azure에 정보를 저장하는 다른 클라우드 서비스를 사용하지 않는 한, Azure로 전송되거나 Azure에 저장되지 않습니다. Azure RMS는 단순히 문서의 데이터를 허가된 사용자 및 서비스 이외의 사람이 읽을 수 없게 합니다.

-   데이터는 응용 프로그램 수준에서 암호화되며 해당 문서의 허가된 사용을 정의하는 정책을 포함합니다.

-   합법적인 사용자가 보호된 문서를 사용되거나 허가된 서비스가 이러한 문서를 처리할 경우 문서의 데이터 암호가 해독되고 정책에 정의된 권한이 적용됩니다.

다음 그림에서는 이 프로세스가 작동하는 방식을 높은 수준에서 확인할 수 있습니다. 비밀 수식이 들어 있는 문서는 보호되며 허가된 사용자나 서비스에서 열 수 있습니다. 이 문서는 콘텐츠 키(이 그림의 녹색 키)로 보호됩니다. 이 키는 각 문서에 대해 고유하며 Azure Information Protection 테넌트 루트 키(이 그림의 빨간색 키)로 보호되는 파일 헤더에 포함됩니다. 테넌트 키는 Microsoft에서 생성하고 관리할 수 있으며 자체 테넌트 키를 생성하여 관리할 수도 있습니다.

Azure RMS가 암호화하거나 암호를 해독하고 권한을 부여하고 제한을 적용하는 보호 프로세스에서는 비밀 수식이 Azure로 전송되지 않습니다.

![Azure RMS의 파일 보호 방식](../media/AzRMS_SecretColaFormula_final.png)

발생하는 작업에 대한 자세한 내용은 이 문서에서 [Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 소비](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) 섹션을 참조하세요.

Azure RMS에서 사용하는 알고리즘 및 키 길이에 대한 자세한 기술 내용은 다음 섹션을 참조하세요.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Azure RMS에서 사용하는 암호화 컨트롤: 알고리즘 및 키 길이
RMS의 작동 방식을 이해할 필요는 없지만 업무 표준의 보안 보호 유지를 위해 어떤 암호화 컨트롤을 사용하는지에 대해 질문을 받을 수는 있습니다.


|암호화 컨트롤|Azure RMS에서 사용|
|-|-|
|알고리즘: AES<br /><br />키 길이: 128비트 및 256비트 [[1]](#footnote-1)|문서 보호|
|알고리즘: RSA<br /><br />키 길이: 2048비트|키 보호|
|SHA-256|인증서 서명|

###### <a name="footnote-1"></a>각주 1 

파일 이름 확장명이 .ppdf이거나 파일이 보호된 텍스트 또는 이미지 파일(예: .ptxt 또는 .pjpg)인 경우 권한 관리 공유 응용 프로그램에서 일반 보호 및 기본 보호에 256비트를 사용합니다.

암호화 키 저장 및 보호 방법:

- Azure RMS의 보호를 받는 각 문서나 메일에 대해 Azure RMS는 단일 AES 키("콘텐츠 키")를 만들고, 이 키가 문서에 포함되며 문서의 모든 버전에서 유지됩니다. 

- 콘텐츠 키는 문서에서 정책의 일부로 조직의 RSA 키("Azure Information Protection 테넌트 키")로 보호되고, 문서 작성자도 정책에 서명합니다. 이 테넌트 키는 조직의 Azure RMS에 의해 보호되는 모든 문서와 메일에 공통적이며, 조직에서 고객을 관리하는 테넌트 키(BYOK(Bring Your Own Key)라고 함)를 사용하는 경우 Azure Information Protection 관리자만 이 키를 변경할 수 있습니다. 

    이 테넌트 키는 Microsoft의 온라인 서비스나 매우 통제가 강화된 환경에서, 그리고 면밀한 모니터링이 진행 중인 경우에 보호됩니다. 고객 관리 테넌트 키(BYOK)를 사용하는 경우 키를 추출하거나 내보내거나 모든 환경에서 공유하는 기능이 없어도 이 보안은 각 Azure 영역의 고급 HSM(하드웨어 보안 모듈) 배열을 사용하여 강화됩니다. 테넌트 키 및 BYOK에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요.

- Windows 장치에 전송되는 라이선스 및 인증서는 클라이언트의 장치 개인 키로 보호되며, 이 키는 사용자가 장치에서 Azure RMS를 처음 사용하는 경우 생성됩니다. 이 개인 키는 클라이언트에서 DPAPI로 보호됩니다. 이 DPAPI는 사용자의 암호에서 파생된 키를 사용하여 이러한 암호를 보호합니다. 모바일 장치에서 키가 한 번만 사용됩니다. 따라서 키가 클라이언트에 저장되지 않으므로 이러한 키를 장치에서 보호하지 않아도 됩니다. 



## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Azure RMS 작동 방식 연습: 첫 번째 사용, 콘텐츠 보호, 콘텐츠 소비
Azure RMS 작동 방식을 좀더 자세히 이해할 수 있도록 [Azure Rights Management Service가 활성화되고](../deploy-use/activate-service.md) 사용자가 해당 Windows 컴퓨터에서 Rights Management Service를 처음 사용하고(**사용자 환경 초기화** 또는 부트스트래핑으로도 알려진 프로세스) **콘텐츠(문서 또는 메일)를 보호하고** 다른 사용자가 보호하는 콘텐츠를 **소비**(열어서 사용)하는 일반적인 흐름을 단계별로 살펴보겠습니다.

사용자 환경이 초기화되면 사용자는 문서를 보호하거나 해당 컴퓨터에서 보호된 문서를 사용할 수 있습니다.

> [!NOTE]
> 이 사용자가 다른 Windows 컴퓨터로 이동하거나 다른 사용자가 이 동일한 Windows 컴퓨터를 사용하면 초기화 프로세스가 반복됩니다.

### <a name="initializing-the-user-environment"></a>사용자 환경 초기화
사용자가 콘텐츠를 보호하거나 Windows 컴퓨터에서 보호된 콘텐츠를 소비하려면 먼저 장치에서 사용자 환경이 준비되어야 합니다. 이것은 일회성 프로세스이며 사용자가 콘텐츠를 보호하거나 보호된 콘텐츠를 사용하려고 할 때 사용자 개입 없이 자동으로 발생합니다.

![RMS 클라이언트 활성화 - 1단계](../media/AzRMS.png)

**1단계에서 발생하는 작업**: 컴퓨터의 RMS 클라이언트는 먼저 Azure Rights Management Service에 연결한 후 Azure Active Directory 계정을 사용하여 사용자를 인증합니다.

사용자 계정이 Azure Active Directory와 페더레이션되면 이 인증은 자동으로 수행되며 사용자에게 자격 증명을 입력하라는 메시지가 표시되지 않습니다.

![RMS 클라이언트 활성화 - 2단계](../media/AzRMS_useractivation2.png)

**2단계에서 발생하는 작업**: 사용자가 인증되면 연결이 조직의 Azure Information Protection 테넌트로 자동으로 리디렉션됩니다. 그러면 테넌트는 사용자가 Azure Rights Management Service에서 인증하여 보호된 콘텐츠를 사용하고 오프라인으로 콘텐츠를 보호할 수 있도록 인증서를 발급합니다.

사용자 인증서 복사본은 Azure에 저장되므로 사용자가 다른 장치로 이동하면 동일한 키를 사용하여 인증서가 만들어집니다.

### <a name="content-protection"></a>콘텐츠 보호
사용자가 문서를 보호하면 RMS 클라이언트는 보호되지 않은 문서에 대해 다음 작업을 수행합니다.

![RMS 문서 보호 - 1단계](../media/AzRMS_documentprotection1.png)

**1단계에서 발생하는 작업**: RMS 클라이언트는 임의 키(콘텐츠 키)를 만든 후 AES 대칭 암호화 알고리즘에 따라 이 키를 사용하여 문서를 암호화합니다.

![RMS 문서 보호 - 2단계](../media/AzRMS_documentprotection2.png)

**2단계에서 발생하는 작업**: 그런 다음 RMS 클라이언트는 템플릿에 따라 또는 문서에 특정 권한을 지정함으로써 문서에 대한 정책을 포함하는 인증서를 만듭니다. 이 정책에는 다른 사용자 또는 그룹에 대한 권한과 기타 제한 사항(예: 만료 날짜)이 포함됩니다.

그러면 RMS 클라이언트는 사용자 환경이 초기화될 때 획득한 조직의 키를 사용하여 정책과 대칭 콘텐츠 키를 암호화합니다. 또한 RMS 클라이언트는 사용자 환경이 초기화되었을 때 획득한 사용자의 인증서로 정책에 서명합니다.

![RMS 문서 보호 - 3단계](../media/AzRMS_documentprotection3.png)

**3단계에서 발생하는 작업**: 마지막으로 RM 클라이언트는 이전에 암호화한 문서 본문이 있는 파일에 정책을 포함하여 보호된 문서를 구성합니다.

이 문서는 어디에든 저장 가능하고 어떤 방법으로도 공유할 수 있으며 정책은 항상 암호화된 문서와 함께 제공됩니다.

### <a name="content-consumption"></a>콘텐츠 소비
사용자가 보호된 문서를 소비하려고 하면 RMS 클라이언트는 먼저 Azure Rights Management Service에 대한 액세스를 요청합니다.

![RMS 문서 사용 - 1단계](../media/AzRMS_documentconsumption1.png)

**1단계에서 발생하는 작업**: 인증된 사용자는 문서 정책과 사용자의 인증서를 Azure Rights Management Service에 전송합니다. 서비스는 정책의 암호를 해독하고 평가한 후 사용자가 문서에 대해 갖는 권한(있는 경우) 목록을 작성합니다.

![RMS 문서 사용 - 2단계](../media/AzRMS_documentconsumption2.png)

**2단계에서 발생하는 작업**: 그런 다음 서비스는 암호가 해독된 정책에서 AES 콘텐츠 키를 추출합니다. 그런 다음 이 키는 요청에 따라 획득된 사용자의 공개 RSA 키를 사용하여 암호화됩니다.

다시 암호화된 콘텐츠 키는 사용자 권한 목록과 함께 암호화된 사용 라이선스에 포함된 후 RMS 클라이언트에 반환됩니다.

![RMS 문서 사용 - 3단계](../media/AzRMS_documentconsumption3.png)

**3단계에서 발생하는 작업**: 마지막으로 RMS 클라이언트는 암호화된 사용 라이선스를 사용하고, 자체 사용자 개인 키를 사용하여 암호를 해독합니다. 따라서 RMS 클라이언트는 필요한 경우 문서 본문의 암호를 해독하고 화면에 렌더링할 수 있습니다.

또한 클라이언트는 권한 목록의 암호를 해독한 후 응용 프로그램에 전달합니다. 그러면 응용 프로그램은 응용 프로그램의 사용자 인터페이스에 해당 권한을 적용합니다.

### <a name="variations"></a>변형 방식
앞의 연습 과정에서는 표준 시나리오를 다뤘지만 이와 다른 변형된 시나리오도 있습니다.

-   **모바일 장치**: 모바일 장치가 Azure Rights Management Service를 사용하여 파일을 보호하거나 파일을 사용하면 프로세스 흐름이 훨씬 더 간단합니다. 각 트랜잭션(콘텐츠 보호 또는 콘텐츠 사용)은 독립적이므로 모바일 장치는 사용자 초기화 프로세스를 먼저 거치지 않습니다. Windows 컴퓨터의 경우처럼 모바일 장치는 Azure Rights Management Service에 연결하고 인증됩니다. 콘텐츠를 보호하기 위해 모바일 장치는 정책을 제출하고 Azure Rights Management Service는 장치에 게시 라이선스 및 대칭 키를 전송하여 문서를 보호합니다. 콘텐츠를 사용하기 위해 모바일 장치가 Azure Rights Management Service에 연결하고 인증을 받을 때 Azure Rights Management Service에 문서 정책을 전송하고 문서 사용을 위한 사용 라이선스를 요청합니다. 이에 대한 응답으로 Azure Rights Management Service는 필요한 키와 제한 사항을 모바일 장치로 보냅니다. 두 프로세스 모두 TLS를 사용하여 키 교환 및 기타 통신을 보호합니다.

-   **RMS 커넥터**: Azure Rights Management Service는 RMS 커넥터와 함께 사용해도 프로세스 흐름은 동일합니다. 유일한 차이점은 커넥터가 온-프레미스 서비스(예: Exchange Server 및 SharePoint Server)와 Azure Rights Management Service 사이에서 릴레이 역할을 한다는 것입니다. 커넥터 자체는 어떤 작업(예: 사용자 환경의 초기화 또는 암호화나 암호 해독)도 수행하지 않습니다. 커넥터는 일반적으로 AD RMS 서버로 가는 통신을 릴레이하며 양쪽에서 사용되는 프로토콜 간의 변환을 처리합니다. 이 시나리오에서는 온-프레미스 서비스와 함께 Azure Rights Management Service를 사용할 수 있습니다.

-   **일반 보호(.pfile)**: Azure Rights Management Service가 일반적인 방식으로 파일을 보호할 때 RMS 클라이언트가 모든 권한을 부여하는 정책을 만든다는 점을 제외하면 흐름은 기본적으로 콘텐츠 보호와 동일합니다. 파일을 사용하면 먼저 암호가 해독된 후 대상 응용 프로그램으로 전달됩니다. 이 시나리오에서는 기본적으로 RMS를 지원하지 않더라도 모든 파일을 보호할 수 있습니다.

-   **보호된 PDF(.ppdf)**: Azure Rights Management Service는 기본적으로 Office 파일을 보호할 때 해당 파일의 복사본을 만들어 동일한 방식으로 보호합니다. 유일한 차이점은 파일 복사본이 PPDF 파일 형식이라는 점입니다. RMS 공유 응용 프로그램에서는 해당 파일 형식을 보는 용도로만 열 수 있습니다. 이 시나리오에서는 모바일 장치에 보호된 Office 파일을 기본적으로 지원하는 앱이 없더라도 모바일 장치의 받는 사람이 항상 첨부 파일을 볼 수 있다는 사실을 알고 있으므로 보호된 첨부 파일을 전자 메일을 통해 전송하도록 합니다.

## <a name="next-steps"></a>다음 단계

Azure Rights Management Service에 대해 자세히 알아보려면 **이해 및 탐색** 섹션에 나와 있는 [응용 프로그램에서 Rights Management Service를 지원하는 방법](applications-support.md) 등의 다른 문서를 사용하여 정보 보호 솔루션을 제공하기 위해 기존 응용 프로그램을 Azure Rights Management와 통합하는 방법을 확인합니다. 

Azure Rights Management Service 구성 및 사용 시 나올 수 있는 용어를 파악할 수 있도록 [Azure Information Protection 용어](../get-started/terminology.md)를 검토하고, 배포를 시작하기 전에 [Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)도 확인하세요. 직접 사용해 보려는 경우에는 [Azure Information Protection에 대한 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요.

그러나 조직에 대해 데이터 보호 배포를 시작할 준비가 되면 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)에서 배포 단계 및 방법 지침 링크를 확인할 수 있습니다.

> [!TIP]
> 추가 정보와 도움말을 확인하려면 [Azure Information Protection에 대한 정보 및 지원](../get-started/information-support.md)의 리소스와 링크를 사용하세요.



<!--HONumber=Nov16_HO1-->


