---
title: Rights Management 커넥터 설치 및 구성 - AIP
description: Azure RMS(Rights Management) 커넥터를 설치 및 구성하는 방법을 설명합니다. 이러한 절차는 Azure 권한 관리 커넥터 배포의 1~4단계를 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e9de16a5ed4322dc0a35f89d6a43218a8256c154
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371046"
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Azure 권한 관리 커넥터 설치 및 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

다음 정보를 참조하여 Azure 권한 관리(RMS) 커넥터를 설치 및 구성할 수 있습니다. 이러한 절차는 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)의 1-4단계를 설명합니다.

시작하기 전에 이 배포에 대한 [필수 조건](deploy-rms-connector.md#prerequisites-for-the-rms-connector)을 검토 및 확인해야 합니다.


## <a name="installing-the-rms-connector"></a>RMS 커넥터 설치

1.  RMS 커넥터를 실행할 컴퓨터(최소 2대)를 식별합니다. 이러한 컴퓨터는 필수 조건에 나열되어 있는 최소 사양을 충족해야 합니다.

    > [!NOTE]
    > 테넌트(Office 365 테넌트 또는 Azure AD 테넌트)당 하나의 RMS 커넥터(고가용성을 위해 여러 대의 서버로 구성)를 설치합니다. Active Directory RMS와 달리 각 포리스트에 RMS 커넥터를 설치할 필요가 없습니다.

2.  [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=314106)에서 RMS 커넥터의 원본 파일을 다운로드합니다.

    RMS 커넥터를 설치하려면 RMSConnectorSetup.exe를 다운로드합니다.

    또한,

    -   나중에 32비트 컴퓨터에서 커넥터를 구성하려면 RMSConnectorAdminToolSetup_x86.exe도 다운로드합니다.

    -   RMS 커넥터용 서버 구성 도구를 사용하여 온-프레미스 서버에서 레지스트리 설정 구성을 자동화하려면 GenConnectorConfig.ps1도 다운로드합니다.

3.  RMS 커넥터를 설치할 컴퓨터에서 관리자 권한으로 **RMSConnectorSetup.exe** 를 실행합니다.

4.  Microsoft Rights Management 커넥터 설치의 시작 페이지에서 **컴퓨터에 Microsoft Rights Management 커넥터 설치**를 선택한 다음, **다음**을 클릭합니다.

5.  RMS 커넥터 사용 조건을 읽고 동의한 후 **다음**을 클릭합니다.

계속하려면 계정과 암호를 입력하여 RMS 커넥터를 구성합니다.

## <a name="entering-credentials"></a>자격 증명 입력
RMS 커넥터를 구성하기 전에 먼저 RMS 커넥터를 구성할 수 있는 권한이 있는 계정의 자격 증명을 입력해야 합니다. 예를 들면 **admin@contoso.com**을 입력한 다음 이 계정에 대한 암호를 지정할 수 있습니다.

Microsoft Rights Management 관리 도구는 이 계정에 대해 MFA를 지원하지 않으므로 이 계정은 MFA(Multi-Factor Authentication)가 필요하지 않습니다. 

커넥터에는 이 암호에 대한 몇 가지 문자 제한도 있습니다. 암호에 앰퍼샌드( **&** ), 왼쪽 꺾쇠 괄호( **[** ), 오른쪽 꺾쇠 괄호( **]** ), 곧은 따옴표( **"** ) 및 아포스트로피( **'** )와 같은 문자를 사용할 수 없습니다. 암호에 이러한 문자가 포함된 경우 다른 시나리오에 이 계정과 암호를 사용하여 로그인할 수 있더라도 RMS 커넥터에 대한 인증에 실패하고 **사용자 이름과 암호 조합이 잘못되었습니다.** 라는 오류 메시지가 표시됩니다. 이 시나리오를 암호에 적용할 경우 이러한 특수 문자가 포함되지 않은 암호에 다른 계정을 사용하거나 이러한 특수 문자가 포함되지 않도록 암호를 재설정합니다.

또한 [온보딩 컨트롤](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구현한 경우 지정한 계정이 콘텐츠를 보호할 수 있어야 합니다. 예를 들어 “IT department” 그룹에 콘텐츠를 보호하는 기능을 제한한 경우 여기서 지정한 계정은 해당 그룹의 구성원이어야 합니다. 그렇지 않으면 다음과 같은 오류 메시지가 표시됩니다. **관리 서비스 및 조직의 위치를 검색하려는 시도가 실패했습니다. 조직에 Microsoft Rights Management 서비스를 사용할 수 있는지 확인합니다.**

다음 권한 중 하나가 있는 계정을 사용할 수 있습니다.

-   **테넌트에 대한 전역 관리자**: Office 365 테넌트 또는 Azure AD 테넌트에 대한 전역 관리자인 계정입니다.

-   **Azure Rights Management 전역 관리자**: Azure RMS 전역 관리자 역할이 할당된 Azure Active Directory에 있는 계정입니다.

-   **Azure Rights Management 커넥터 관리자**: 조직의 RMS 커넥터를 설치 및 관리할 권한이 부여된 Azure Active Directory의 계정입니다.

    > [!NOTE]
    > Azure Rights Management 전역 관리자 역할 및 Azure Rights Management 커넥터 관리자 역할은 Azure RMS [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) cmdlet을 사용하여 계정에 할당됩니다.
    > 
    > 최소 권한으로 RMS 커넥터를 실행하려면 다음을 수행하여 Azure RMS 커넥터 관리자 역할이 할당된 전용 계정을 이 용도로 만듭니다.
    >
    > 1.  Rights Management용 Windows PowerShell을 아직 다운로드하여 설치하지 않은 경우 다운로드한 후 설치합니다. 자세한 내용은 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.
    >
    >     **관리자 권한으로 실행** 명령을 사용하여 Windows PowerShell을 시작한 후 [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) 명령을 사용하여 Azure RMS 서비스에 연결합니다.
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  그런 후에 다음 매개 변수 중 하나만 사용하여 [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) 명령을 실행합니다.
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     예를 들어 다음과 같이 입력합니다. **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
    >
    >     이러한 명령은 커넥터 관리자 역할을 할당하지만 여기서 전역 관리자 역할을 사용할 수도 있습니다.

RMS 커넥터 설치 프로세스 동안 모든 필수 구성 요소 소프트웨어가 유효성 검사 및 설치되고, IIS(인터넷 정보 서비스)가 아직 없는 경우 설치되며, 커넥터 소프트웨어가 설치 및 구성됩니다. 또한 다음을 만들어 Azure RMS의 구성을 준비합니다.

-   Azure RMS와 통신하기 위한 커넥터를 만들 수 있는 서버의 빈 테이블입니다. 나중에 이 테이블에 서버를 추가합니다.

-   커넥터에 대한 보안 토큰의 집합은 Azure RMS로 작업 권한을 부여합니다. 이러한 토큰을 Azure RMS에서 다운로드하고 레지스트리의 로컬 컴퓨터에 설치합니다. 데이터 보호 응용 프로그래밍 인터페이스(DPAPI) 및 로컬 시스템 계정 자격 증명을 사용하여 보호합니다.

마법사의 마지막 페이지에서 다음을 수행한 후 **마침**을 클릭합니다.

-   이 커넥터가 처음으로 설치한 커넥터인 경우에는 지금 **커넥터 관리자 콘솔을 시작하여 서버에 권한 부여** 를 선택하지 마세요. 두 번째(또는 마지막) RMS 커넥터를 설치한 후 이 옵션을 선택합니다. 대신, 다른 컴퓨터 한 대 이상에서 마법사를 다시 실행합니다. 최소 두 개의 커넥터를 설치해야 합니다.

-   두 번째 또는 마지막 커넥터를 설치한 후 **커넥터 관리자 콘솔을 시작하여 서버에 권한 부여**를 선택합니다.

> [!TIP]
> 이때 RMS 커넥터의 웹 서비스가 작동하는지를 테스트하기 위해 수행할 수 있는 확인 테스트가 있습니다.
>
> -   웹 브라우저에서 **http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx**에 연결하고 *&lt;connectoraddress&gt;* 를 RMS 커넥터가 설치된 서버 주소 또는 이름으로 바꿉니다. 연결에 성공하면 **ServerCertificationWebService** 페이지가 표시됩니다.

RMS 커넥터를 제거해야 할 경우 마법사를 다시 실행하고 제거 옵션을 선택합니다.

설치 중에 문제가 발생하면 다음 설치 로그를 확인하세요. **%LocalAppData%\Temp\Microsoft Rights Management connector_\<date and time>.log** 

예를 들어 설치 로그가 C:\Users\Administrator\AppData\Local\Temp\Microsoft Rights Management connector_20170803110352.log와 비슷할 수 있습니다.

## <a name="authorizing-servers-to-use-the-rms-connector"></a>RMS 커넥터를 사용하도록 서버에 권한 부여
두 대 이상의 컴퓨터에 RMS 커넥터를 설치한 경우 RMS 커넥터를 사용할 서버 및 서비스에 권한을 부여할 준비가 된 것입니다. Exchange Server 2013 또는 SharePoint Server 2013을 실행하는 서버를 예로 들 수 있습니다.

이러한 서버를 정의하려면 RMS 커넥터 관리 도구를 실행하고 허용된 서버 목록에 항목을 추가합니다. 이 도구는 Microsoft Rights Management 커넥터 설치 마법사의 마지막 부분에서 **커넥터 관리자 콘솔을 시작하여 서버에 권한 부여** 를 선택할 때 실행할 수도 있고 마법사에서 별도로 실행할 수 있습니다.

이러한 서버에 권한을 부여할 때 다음 고려 사항에 주의하세요.

- 추가하는 서버에는 특수 권한이 부여됩니다. 커넥터 구성에서 Exchange Server 역할에 지정하는 모든 계정에 Azure RMS의 [슈퍼 사용자 역할](configure-super-users.md) 권한을 부여하며 이 RMS 테넌트에 대한 모든 콘텐츠를 액세스할 수 있도록 합니다. 이 시점에 필요한 경우 슈퍼 사용자 기능이 자동으로 설정됩니다. 권한 상승으로 인한 보안 위험을 방지하려면 조직의 Exchange Server에서 사용되는 계정을 지정하지 않도록 조심하세요. SharePoint Server 또는 FCI를 사용하는 파일 서버로 구성되는 모든 서버에는 일반 사용자 권한이 부여됩니다.

- Active Directory 보안 또는 메일 그룹이나 둘 이상의 서버에서 사용되는 서비스 계정을 지정하여 여러 서버를 단일 항목으로 추가할 수 있습니다. 이 구성을 사용할 경우 서버 그룹에서 동일한 RMS 인증서를 공유하고 이 서버 그룹에 속한 서버는 모두 이 서버 그룹의 특정 서버가 보호하는 콘텐츠의 소유자로 간주됩니다. 관리 오버헤드를 최소화하기 위해서는 조직의 Exchange Server 또는 SharePoint Server 팜에 권한을 부여하는 데 개별 서버가 아니라 이 단일 그룹 구성을 사용하는 것이 좋습니다.

**커넥터를 사용할 수 있는 서버** 페이지에서 **추가**를 클릭합니다.

> [!NOTE]
> 서버 권한 부여는 서비스 또는 서버 컴퓨터 계정에 대한 ServerCertification.asmx에 NTFS 권한을 수동으로 적용하고 Exchange 계정에 사용자 슈퍼 권한을 수동으로 부여하는 AD RMS 구성과 동등한 Azure RMS의 구성입니다. 커넥터에서는 ServerCertification.asmx에 NTFS 권한을 적용할 필요가 없습니다.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>허용된 서버 목록에 서버를 추가하려면
**서버가 커넥터를 사용할 수 있도록 허용** 페이지에서 개체 이름을 입력하거나 권한을 부여할 개체를 찾아 식별합니다.

올바른 개체에 권한을 부여해야 합니다. 서버가 커넥터를 사용하도록 하려면 온-프레미스 서비스(예: Exchange 또는 SharePoint)를 실행하는 계정을 권한 부여 대상으로 선택해야 합니다. 예를 들어 서비스가 구성된 서비스 계정으로 실행되고 있는 경우 해당 서비스 계정의 이름을 목록에 추가합니다. 서비스가 로컬 시스템으로 실행되고 있는 경우 컴퓨터 개체의 이름을 추가합니다(예: SERVERNAME$). 가장 좋은 방법은 이러한 계정을 포함하는 그룹을 만들고 개별 서버 이름 대신 그룹을 지정하는 것입니다.

다양한 서버 역할에 대한 자세한 내용:

-   Exchange를 실행하는 서버의 경우: 보안 그룹을 지정해야 하며, Exchange가 자동으로 만들어 포리스트의 모든 Exchange 서비스를 유지 관리하는 데 사용하는 기본 그룹(**Exchange Servers**)을 사용할 수 있습니다.

-   SharePoint를 실행하는 서버의 경우:

    -   SharePoint 2010 서버가 로컬 시스템으로 실행되도록 구성되어 있는 경우(서비스 계정을 사용하지 않음) Active Directory 도메인 서비스에서 보안 그룹을 수동으로 만든 다음 이 구성의 서버에 대한 컴퓨터 이름 개체를 이 그룹에 추가합니다.

    -   SharePoint 서버가 서비스 계정을 사용하도록 구성되어 있는 경우(SharePoint 2010에 대한 권장 방식이며 SharePoint 2016 및 SharePoint 2013의 유일한 옵션)에는 다음을 수행합니다.

        1.  SharePoint 중앙 관리 서비스를 실행하는 서비스 계정을 추가하여 관리 콘솔에서 SharePoint를 구성할 수 있도록 합니다.

        2.  SharePoint 앱 풀에 대해 구성된 계정을 추가합니다.

        > [!TIP]
        > 이러한 두 계정이 서로 다른 경우 두 계정을 모두 포함하는 단일 그룹을 만들어 관리 오버헤드를 최소화합니다.

-   파일 분류 인프라를 사용하는 파일 서버의 경우 연결된 서비스가 로컬 시스템 계정으로 실행되므로 파일 서버의 컴퓨터 계정(예: SERVERNAME$) 또는 해당 컴퓨터 계정을 포함하는 그룹에 권한을 부여해야 합니다.

목록에 서버를 추가하는 작업을 마쳤으면 **닫기**를 클릭합니다.

아직 수행하지 않은 경우 지금 RMS 커넥터가 설치되어 있는 서버의 부하 분산을 구성하고 이러한 서버와 방금 권한을 부여한 서버 간의 연결에 HTTPS를 사용할지 여부를 고려해야 합니다.

## <a name="configuring-load-balancing-and-high-availability"></a>부하 분산 및 고가용성 구성
RMS 커넥터의 두 번째 또는 마지막 인스턴스를 설치한 후 커넥터 URL 서버 이름을 정의하고 부하 분산 시스템을 구성합니다.

커넥터 URL 서버 이름은 제어하는 네임스페이스 아래의 어떤 이름도 될 수 있습니다. 예를 들어 DNS 시스템에서 **rmsconnector.contoso.com**에 해당하는 항목을 만들고 부하 분산 시스템에서 IP 주소를 사용하도록 이 항목을 구성할 수 있습니다. 이 이름에 대한 특별한 요구 사항은 없으며 커넥터 서버 자체에서 이름을 구성할 필요가 없습니다. Exchange 및 SharePoint Server가 인터넷을 통해 커넥터와 통신할 것이 아니라면 이 이름을 인터넷에서 확인할 필요가 없습니다.

> [!IMPORTANT]
> 커넥터를 사용하도록 Exchange 또는SharePoint Server를 구성한 후 이 이름을 변경하지 않는 것이 좋습니다. 왜냐하면 변경할 경우 모든 IRM 구성의 이러한 서버를 지운 후 다시 구성해야 하기 때문입니다.

DNS에서 이름을 만들고 IP 주소에 대해 구성한 후 트래픽을 커넥터 서버로 전송하는 해당 주소의 부하 분산을 구성합니다. 이렇게 하기 위해 Windows Server의 NLB(네트워크 부하 분산) 기능 등 모든 IP 기반 부하 분산 장치를 사용할 수 있습니다. 자세한 내용은 [부하 분산 배포 가이드](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx)를 참조하세요.

다음 설정을 사용하여 NLB 클러스터를 구성합니다.

-   포트: 80(HTTP의 경우) 또는 443(HTTPS의 경우)

    HTTP와 HTTPS 중 어느 것을 사용할지 결정하는 방법에 대한 자세한 내용은 다음 섹션을 참조하세요.

-   선호도: 없음

-   배포 방법: 같음

RMS 커넥터 서비스를 실행하는 서버에 대한 부하 분산된 시스템에 대해 정의하는 이 이름은 나중에 Azure RMS를 사용하도록 온-프레미스 서버를 구성할 때 사용하는 조직의 RMS 커넥터 이름입니다.

## <a name="configuring-the-rms-connector-to-use-https"></a>HTTPS를 사용하도록 RMS 커넥터 구성
> [!NOTE]
> 이 구성 단계는 선택 사항이지만 보안 강화를 위해 수행하는 것이 좋습니다.

RMS 커넥터에 대해 TLS 또는 SSL을 사용하는 것이 선택 사항이기는 하지만 모든 HTTP 기반 보안 관련 서비스에 사용하는 것이 좋습니다. 이 구성에서는 커넥터를 실행하는 서버를 커넥터를 사용하는 Exchange 및 SharePoint Server에 대해 인증합니다. 또한 이러한 서버에서 커넥터로 전송되는 모든 데이터는 암호화됩니다.

RMS 커넥터가 TLS를 사용하도록 하려면 RMS 커넥터를 실행하는 각 서버에 커넥터에 대해 사용할 이름이 포함된 서버 인증 인증서를 설치합니다. 예를 들어 DNS에서 정의한 RMS 커넥터 이름이 **rmsconnector.contoso.com**인 경우 인증서 주체에 일반 이름으로 **rmsconnector.contoso.com**이 포함된 서버 인증 인증서를 배포합니다. 또는 인증서 대체 이름에 DNS 값으로 **rmsconnector.contoso.com**을 지정합니다. 인증서에 서버 이름을 포함할 필요는 없습니다. 그런 다음 IIS에서 이 인증서를 기본 웹 사이트에 바인딩합니다.

HTTPS 옵션을 사용하는 경우 커넥터를 실행하는 모든 서버에 Exchange 및 SharePoint Server가 트러스트하는 루트 CA로 체이닝되는 유효한 서버 인증 인증서가 있는지 확인하세요. 또한 커넥터 서버의 인증서를 발급한 CA(인증 기관)가 CRL(인증서 해지 목록)을 게시한 경우 Exchange 및 SharePoint Server가 이 CRL을 다운로드할 수 있어야 합니다.

> [!TIP]
> 다음 정보 및 리소스를 사용하여 서버 인증 인증서를 요청 및 설치하고 IIS에서 이 인증서를 기본 웹 사이트에 바인딩할 수 있습니다.
>
> -   AD CS(Active Directory 인증서 서비스) 및 엔터프라이즈 CA(인증 기관)를 사용하여 이러한 서버 인증 인증서를 배포하는 경우 인증서를 복제한 후 웹 서버 인증서 템플릿을 사용할 수 있습니다. 이 인증서 템플릿에서는 인증서 주체 이름에 **요청에서 제공** 을 사용합니다. 즉, 인증서 요청 시 인증서 주체 이름 또는 주체 대체 이름에 RMS 커넥터 이름의 FQDN을 입력할 수 있습니다.
> -   독립 CA를 사용하거나 다른 회사에서 이 인증서를 구입하는 경우에는 TechNet의 [웹 서버(IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) 문서 라이브러리에서 [인터넷 서버 인증서 구성(IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx)을 참조하세요.
> -   인증서를 사용하도록 IIS를 구성하려면 TechNet의 [Web Server (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx)(웹 서버(IIS)) 문서 라이브러리에서 [Add a Binding to a Site (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx)(사이트에 바인딩 추가(IIS 7))를 참조하세요.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>웹 프록시 서버에 대해 RMS 커넥터 구성
커넥터 서버가 직접 인터넷에 연결되어 있지 않은 네트워크에 설치되어 있고 아웃바운드 인터넷 액세스를 위해 웹 프록시 서버를 수동으로 구성해야 하는 경우 이러한 RMS 커넥터용 서버에서 레지스트리를 구성해야 합니다.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>웹 프록시 서버를 사용하도록 RMS 커넥터를 구성하려면

1.  RMS 커넥터를 실행하는 각 서버에서 레지스트리 편집기(예: Regedit)를 엽니다.

2.  **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**로 이동합니다.

3.  **ProxyAddress**의 문자열 값을 추가한 후 이 값의 데이터가 **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;** 가 되도록 설정합니다.

    예: **http://proxyserver.contoso.com:8080**

4.  레지스트리 편집기를 닫은 후 서버를 다시 시작하거나 IISReset 명령을 수행하여 IIS를 다시 시작합니다.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>관리 컴퓨터에 RMS 커넥터 관리 도구 설치
RMS 커넥터가 설치되어 있지 않은 컴퓨터가 다음 요구 사항을 충족하는 경우, 해당 컴퓨터에서 RMS 커넥터 관리 도구를 실행할 수 있습니다.

-   Windows Server 2012 또는 Windows Server 2012 R2(모든 버전), Windows Server 2008 R2 또는 Windows Server 2008 R2 서비스 팩 1(모든 버전), Windows 8.1, Windows 8 또는 Windows 7을 실행하는 물리적 또는 가상 컴퓨터

-   1GB 이상의 RAM

-   최소 64GB의 디스크 공간

-   하나 이상의 네트워크 인터페이스

-   방화벽(또는 웹 프록시)을 통한 인터넷 액세스

RMS 커넥터 관리 도구를 설치하려면 다음 파일을 실행합니다.

-   32비트 컴퓨터의 경우: RMSConnectorAdminToolSetup_x86.exe

-   64비트 컴퓨터의 경우: RMSConnectorSetup.exe

이러한 파일을 아직 다운로드하지 않았으면 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=314106)에서 다운로드할 수 있습니다.


## <a name="next-steps"></a>다음 단계
이제 RMS 커넥터를 설치 및 구성했으므로 커넥터를 사용하도록 온-프레미스 서버를 구성할 준비가 되었습니다. [Azure 권한 관리 커넥터에 대해 서버 구성](configure-servers-rms-connector.md)으로 이동합니다.

