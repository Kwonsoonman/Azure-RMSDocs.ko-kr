---
# required metadata

title: 개인용 RMS 등록 방법 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 개인용 RMS 등록 방법
이 무료 계정에 등록하려면 사용자가 [Microsoft Rights Management 페이지](https://portal.aadrm.com/)를 방문하여 계정을 요청하고 회사 또는 학교 메일 주소를 제공합니다. 

사용자가 이 등록 페이지로 이동되는 가장 일반적인 방법은 보호된 첨부 파일이 있는 메일 메시지를 받은 경우입니다. 여기에는 등록 방법에 대한 지침이 포함되어 있습니다. Microsoft로부터 응답 메일을 받으면 계정을 만드는 데 필요한 세부 정보를 입력하여 등록 프로세스를 완료할 수 있습니다. Microsoft로부터 메일 확인을 받으면 이 최종 메일 메시지를 통해 다양한 장치용 공유 응용 프로그램을 다운로드할 수 있는 페이지로 이동할 수 있으며, 사용자 가이드 링크도 포함되어 있습니다.

## 개인용 RMS를 등록하려면

1.  Windows 또는 Mac 컴퓨터에서 [Microsoft Rights Management 페이지](https://portal.aadrm.com)로 이동합니다.

2.  **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같은 조직에 사용하는 전자 메일 주소를 입력합니다.

    > [!IMPORTANT]
    > 개인 메일 계정은 지원되지 않으므로 Microsoft 계정(이전의 Microsoft Live ID 계정)이나 가정에서 사용하는 인터넷 공급자가 제공한 다른 개인 계정은 입력하지 마세요.

3.  **시작**을 클릭합니다.

    Microsoft는 사용자의 메일 주소를 사용하여 해당 조직에 이미 [Azure RMS가 포함된 유료 구독](../get-started/requirements-subscriptions.md)이 있는지 확인합니다. 구독이 있으면 개인용 RMS가 필요하지 않고 즉시 로그인되며 개인용 RMS 셀프서비스 가입이 취소됩니다. Azure RMS 유료 구독이 없으면 다음 단계를 진행합니다.

4.  입력한 주소로 확인 메일 메시지가 전송될 때까지 기다립니다. 이 메일은 Microsoft(DoNotReply@microsoft.com)에서 보내는 것이며 제목은 **Microsoft RMS**입니다.

5.  메일을 받으면 지침의 링크를 클릭하여 등록 프로세스를 완료합니다.

6.  링크를 클릭하면 계정에 대한 세부 정보를 입력하는 새 **Microsoft Rights Management** 페이지로 이동합니다. 이름과 성을 임력하고 선택한 암호를 입력 및 확인한 다음 국가(또는 자신의 국가가 목록에 없으면 가장 인접한 국가)를 드롭다운에서 선택한 다음 **만들기**를 클릭합니다.

7.  이제 Microsoft에서 보낸, 계정을 사용할 준비가 되었음을 확인하는 다른 메일 메시지가 올 때까지 기다립니다.

8.  메일을 받으면 링크를 클릭하여 로그인하고 지침에 따라 공유 응용 프로그램을 다운로드 및 설치하거나, 도움말 링크를 클릭하여 공유 응용 프로그램 사용자 가이드를 읽어봅니다. 

이제 계정이 만들어졌으므로 파일을 보호하고 다른 사용자가 보호한 파일을 읽을 수 있습니다. 파일을 보호하거나 보호된 파일을 읽기 위해 로그인하라는 메시지가 나타나면 개인용 RMS 계정을 만들 때 사용한 메일 주소와 암호를 입력하세요.

## 등록 프로세스의 기술 개요
개인용 RMS는 Microsoft 클라우드 기반 기술로 사용자를 인증하는 다른 서비스에서도 사용되는 실시간 메일 계정 생성 프로세스를 사용합니다.

이는 사용자가 개인용 RMS에 등록하고 조직에 Office 365 구독 또는 Azure 구독이 없어 Azure에 사용자를 인증할 디렉터리가 없는 경우에 발생합니다.

1.  조직의 첫 번째 사용자가 개인용 RMS 구독을 요청하면 메일 주소에 입력된 도메인 이름을 통해 이미 Azure 테넌트와 연결되어 있는지 여부를 확인합니다. 기존 테넌트가 없으면 해당 조직에 대해 이 첫 번째 사용자의 계정이 담긴 새로운 테넌트와 Azure 디렉터리가 자동 생성됩니다. Azure의 유료 구독과 달리, 이 첫 번째 계정은 전역 관리자가 아니라 표준 사용자입니다. 새 계정에서는 사용자가 제공한 전자 메일 주소와 암호를 사용합니다.

    > [!NOTE]
    > 일부 도메인 이름은 디렉터리를 만드는 데 사용할 수 없으므로 개인용 RMS에 사용할 수 없습니다. 차단된 도메인 이름 목록은 JavaScript 개체 Object Notation 파일( [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json))에서 확인할 수 있습니다.

    기존 테넌트가 있는 경우 Azure RMS에 대한 구독을 보유하고 있는지 확인합니다. 구독이 없으면 개인용 RMS 무료 구독을 추가할 수 있습니다.

2.  조직에 개인용 RMS 구독이 부여됩니다. 이제 이 사용자는 Azure에서 인증되어 파일을 보호하고, Azure 권한 관리를 사용하여 다른 사용자가 보호한 파일을 읽을 수 있습니다. 파일을 보호하고 보호된 파일을 읽으려면 사용자에게 RMS 지원 응용 프로그램(예: 무료 [Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md))이 있어야 합니다.

3.  동일한 조직의 두 번째 사용자가 개인용 RMS 구독을 요청하면 조직의 개인용 RMS 구독을 통해 새 사용자 계정이 이전에 만든 Azure 디렉터리에 추가됩니다. 이 두 번째 사용자는 첫 번째 사용자가 할 수 있는 모든 작업(파일 보호 및 보호된 파일 읽기)을 수행할 수 있지만, 이 두 사용자는 이제 해당 조직의 Azure 디렉터리의 계정에 대한 액세스를 제한하는 파일에 기본 템플릿을 빠르게 적용할 수 있으므로 보다 쉽고 안전하게 협력할 수 있습니다.

4.  같은 조직의 후속 사용자는 같은 패턴에 따라 조직의 Azure 디렉터리에 사용자 계정을 추가합니다(새 사용자가 등록한 경우). 디렉터리에 계정을 더 추가할수록 더 많은 사용자가 동료 및 파트너와 안전하게 공동 작업을 수행할 수 있으며, 권한 없는 사용자에게 파일에 대한 액세스 권한이 없어야 하는 경우 더 쉽게 이러한 사용자가 파일을 읽지 못하도록 할 수 있습니다.

이 프로세스 전체에서 조직에 부과되는 요금은 없으며 IT 부서에서 해야 할 작업도 없습니다. 그러나 IT 부서는 다음 중 하나를 수행할 수 있습니다.

-   **계정 및 등록 프로세스 관리**: IT 관리자는 Azure에서 자동으로 생성된 디렉터리 및 계정을 소유할 수 있습니다. 그런 다음 암호 동기화 및 Single Sign-On과 같은 디렉터리 통합 솔루션을 구현하여 계정을 관리할 수 있습니다. 또는 사용자가 계정을 만들거나 개인용 RMS에 등록하지 못하도록 할 수 있습니다.

    자세한 내용은 [관리자가 개인용 RMS용으로 만들어진 계정을 제어하는 방법](rms-for-individuals-take-control.md)을 참조하세요.

-   **Rights Management 관리**: IT 관리자는 조직의 개인용 RMS 구독을 Azure 권한 관리가 포함된 유료 구독으로 전환할 수 있습니다. 이렇게 하면 기존 Azure 디렉터리 및 계정이 개인용 RMS를 사용하던 기존 사용자에 대해 원활하게 전환되도록 유지됩니다. 사용자가 이전에 보호한 모든 파일은 계속해서 동일한 정책으로 보호되며, 파일 사용 권한이 부여된 사용자는 계속해서 동일한 방법으로 파일을 사용할 수 있습니다.

    이러한 방침을 취하면 조직은 권한 관리를 해당 워크플로, 서비스 및 데이터 저장소에 통합할 수 있는 이점을 누릴 수 있습니다. 또한 이제 Azure 권한 관리를 위한 조직의 테넌트 키를 제어할 수 있으므로 권한 관리를 수행할 수 있습니다. 이제 다음이 가능합니다.

    -   Exchange 및 SharePoint가 온-프레미스에서 실행되는 경우에도 Azure 권한 관리를 지원하도록 구성할 수 있습니다. Exchange 및 SharePoint는 기본적으로 온라인 서비스에 대해 지원되며, 온-프레미스 서버에 대해 커넥터를 통해 지원됩니다. 자세한 내용은 다음 항목을 참조하세요.

        -   [Office 365: 클라이언트 및 온라인 서비스 구성](../deploy-use/configure-office365.md)에서 Exchange Online 및 SharePoint Online 섹션

        -   [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)

    -   필요한 경우, 권한 관리로 보호되는 파일을 암호 해독할 수 있도록 회사 소유의 데이터에 대해 eDiscovery를 수행할 수 있습니다. 자세한 내용은 [Azure 권한 관리 및 검색 서비스 또는 데이터 검색을 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)을 참조하세요.

    -   조직에서 사용되는 권한 관리의 모든 활동을 기록할 수 있습니다. 이 기능은 매우 강력한데, 보호되고 있는 파일과 보호된 파일에 성공적으로 액세스하는 사용자를 모니터링할 수 있을 뿐만 아니라 보호된 파일에 액세스하려고 시도하는 권한 없는 사용자의 잠재적으로 의심스러운 동작을 식별할 수 있기 때문입니다. 자세한 내용은 [Azure 권한 관리 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.

    -   [Azure RMS 구독](https://technet.microsoft.com/dn858608)에서 지원한다면 사용자에게 보호되는 문서를 추적하고 취소할 수 있는 기능을 제공합니다. 자세한 내용은 [RMS 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)에서 [파일 추적 및 해지](../rms-client/sharing-app-track-revoke.md)를 참조하세요.

    -   Azure 권한 관리의 테넌트 키가 IT 정책에 따라 온-프레미스에서 생성되어 HSM(하드웨어 보안 모듈)을 통해 Microsoft로 안전하게 전송되도록 BYOK(Bring Your Own Key) 솔루션을 구현할 수 있습니다. 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요.


## 다음 단계
[관리자가 개인용 RMS에 대해 생성된 계정을 제어하는 방법](rms-for-individuals-take-control.md)을 참조하세요.




<!--HONumber=Apr16_HO3-->

