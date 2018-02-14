---
title: "Rights Management 커넥터 설치 및 구성 - AIP"
description: "Azure Rights Management(RMS) 커넥터를 설치하고 구성하는 데 도움이 되는 정보입니다. 이러한 절차에서는 Azure Rights Management 커넥터 배포에서 1~4단계를 다룹니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/03/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3e4aabc3c571ca132327748935ab3aeafa002db0
ms.sourcegitcommit: e21fb3385de6f0e251167e5dc973e90f0e7f2bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2018
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Azure Rights Management 커넥터 설치 및 구성

>*적용 대상: Azure Information Protection, Office 365*

Azure Rights Management(RMS) 커넥터를 설치하고 구성하는 데 도움이 되는 다음과 같은 정보를 사용합니다. 이러한 절차에서는 [Azure Rights Management 커넥터 배포](deploy-rms-connector.md)에서 1~4단계를 다룹니다.

시작하기 전에 이 배포에 대한 [필수 구성 요소](deploy-rms-connector.md#prerequisites-for-the-rms-connector)를 검토하고 확인해야 합니다.


## <a name="installing-the-rms-connector"></a>RMS 커넥터 설치

1.  RMS 커넥터를 실행하는 컴퓨터(최소 2대)를 식별합니다. 필수 구성 요소에 나열되어 있는 최소 사양을 충족해야 합니다.

    > [!NOTE]
    > 테넌트(Office 365 테넌트 또는 Azure AD 테넌트)당 단일 RMS 커넥터(고가용성을 위해 여러 서버로 구성)를 설치합니다. Active Directory RMS와 달리 각 포리스트에 RMS 커넥터를 설치할 필요가 없습니다.

2.  [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=314106)에서 RMS 커넥터의 원본 파일을 다운로드합니다.

    RMS 커넥터를 설치하려면 RMSConnectorSetup.exe를 다운로드합니다.

    다음 항목도 확인하세요.

    -   나중에 32비트 컴퓨터에서 커넥터를 구성하려면 RMSConnectorAdminToolSetup_x86.exe도 다운로드합니다.

    -   RMS 커넥터에서 서버 구성 도구를 사용하려는 경우 온-프레미스 서버에서 레지스트리 설정 구성을 자동화하려면 GenConnectorConfig.ps1도 다운로드합니다.

3.  RMS 커넥터를 설치하려는 컴퓨터에서 관리자 권한으로 **RMSConnectorSetup.exe**를 실행합니다.

4.  Microsoft Rights Management 커넥터 설치의 시작 페이지에서 **컴퓨터에 Microsoft Rights Management 커넥터 설치**를 선택한 다음, **다음**을 클릭합니다.

5.  RMS 커넥터 사용 조건을 읽고 동의한 다음, **다음**을 클릭합니다.

계속하려면 RMS 커넥터를 구성할 계정 및 암호를 입력합니다.

## <a name="entering-credentials"></a>자격 증명 입력
RMS 커넥터를 구성하려면 먼저 RMS 커넥터를 구성할 수 있는 충분한 권한이 있는 계정의 자격 증명을 입력해야 합니다. 예를 들어 **admin@contoso.com**을 입력한 다음, 이 계정의 암호를 지정합니다.

Microsoft Rights Management 관리 도구에서 이 계정에 MFA를 지원하지 않기 때문에 이 계정은 MFA(Multi-Factor Authentication)를 요구하지 않아야 합니다. 

커넥터는 이 암호에서 몇 가지 문자를 제한합니다. 암호에는 앰퍼샌드(**&**), 왼쪽 꺾쇠 괄호(**[**), 오른쪽 꺾쇠 괄호(**]**), 곧은 따옴표(**"**) 및 아포스트로피(**'**)와 같은 문자를 사용할 수 없습니다. 다른 시나리오에서 이 계정과 암호를 사용하여 성공적으로 로그인할 수 있더라도 암호에 이러한 문자가 포함되면 RMS 커넥터에 대한 인증에 실패하고 **해당 사용자 이름 및 암호 조합이 잘못되었습니다.**라는 오류 메시지가 표시됩니다. 이 시나리오가 암호에 적용되면 이러한 특수 문자가 포함되지 않는 암호를 가진 다른 계정을 사용하거나 이러한 특수 문자가 포함되지 않도록 암호를 다시 설정합니다.

또한 [온보딩 컨트롤](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구현한 경우 지정한 계정이 콘텐츠를 보호할 수 있는지 확인합니다. 예를 들어 "IT 부서" 그룹에 대해 콘텐츠를 보호하는 기능을 제한한 경우 여기에서 지정한 계정은 해당 그룹의 멤버여야 합니다. 그렇지 않으면 다음과 같은 오류 메시지가 표시됩니다. **관리 서비스 및 조직의 위치를 발견하지 못했습니다. 조직에 Microsoft Rights Management 서비스를 사용할 수 있는지 확인합니다.**

다음 권한 중 하나가 있는 계정을 사용할 수 있습니다.

-   **테넌트에 대한 전역 관리자**: Office 365 테넌트 또는 Azure AD 테넌트에 대한 전역 관리자 계정입니다.

-   **Azure Rights Management 전역 관리자**: Azure RMS 전역 관리자 역할이 할당된 Azure Active Directory의 계정입니다.

-   **Azure Rights Management 커넥터 관리자**: 조직에서 RMS 커넥터를 설치하고 관리할 권한이 부여된 Azure Active Directory의 계정입니다.

    > [!NOTE]
    > Azure Rights Management 전역 관리자 역할 및 Azure Rights Management 커넥터 관리자 역할은 Azure RMS [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) cmdlet을 사용하여 계정에 할당됩니다.
    > 
    > 최소 권한으로 RMS 커넥터를 실행하려면 다음을 수행하여 Azure RMS 커넥터 관리자 역할을 할당할 목적으로 전용 계정을 만듭니다.
    >
    > 1.  아직 수행하지 않은 경우 Rights Management에 Windows PowerShell을 다운로드하고 설치합니다. 자세한 내용은 [Azure Rights Management에 Windows PowerShell 설치](install-powershell.md)를 참조하세요.
    >
    >     **관리자 권한으로 실행** 명령을 사용하여 Windows PowerShell을 시작하고, [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) 명령을 사용하여 Azure RMS 서비스에 연결합니다.
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  다음 매개 변수 중 하나를 사용하여 [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) 명령을 실행합니다.
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
    >     예를 들어 **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**를 입력합니다.
    >
    >     이러한 명령은 커넥터 관리자 역할을 할당하지만 GlobalAdministrator 역할도 여기에서 사용할 수 있습니다.

RMS 커넥터 설치 프로세스 중에 모든 필수 구성 요소 소프트웨어의 유효성을 검사하고 설치하고, IIS(인터넷 정보 서비스)를 설치하지 않은 경우 설치하고, 커넥터 소프트웨어를 설치하고 구성합니다. 또한 다음 항목을 만들어 Azure RMS를 구성할 준비를 합니다.

-   Azure RMS와 통신하기 위해 커넥터를 사용할 권한이 있는 서버의 빈 테이블. 나중에 이 테이블에 서버를 추가합니다.

-   커넥터의 보안 토큰 집합은 Azure RMS로 작업 권한을 부여합니다. 이러한 토큰은 Azure RMS에서 다운로드되고 레지스트리의 로컬 컴퓨터에 설치됩니다. DPAPI(데이터 보호 응용 프로그래밍 인터페이스) 및 로컬 시스템 계정 자격 증명을 사용하여 보호됩니다.

마법사의 마지막 페이지에서 다음을 수행한 다음, **마침**을 클릭합니다.

-   이 기능이 설치된 첫 번째 커넥터인 경우 이번에는 **커넥터 관리자 콘솔을 시작하여 서버에 권한 부여**를 선택하지 않습니다. 두 번째(또는 마지막) RMS 커넥터를 설치한 후에 이 옵션을 선택합니다. 대신 한 대 이상의 다른 컴퓨터에서 마법사를 다시 실행합니다. 최소 두 개의 커넥터를 설치해야 합니다.

-   두 번째(또는 마지막) 커넥터를 설치한 경우 **커넥터 관리자 콘솔을 시작하여 서버 권한 부여**를 선택합니다.

> [!TIP]
> 이 시점에서 RMS 커넥터에 대한 웹 서비스가 작동하는지를 테스트하기 위해 수행할 수 있는 확인 테스트가 있습니다.
>
> -   웹 브라우저에서 **http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx**에 연결하면 *&lt;connectoraddress&gt;*를 RMS 커넥터가 설치된 서버 주소 또는 이름으로 바꿉니다. 연결에 성공하면 **ServerCertificationWebService** 페이지가 표시됩니다.

RMS 커넥터를 제거해야 하는 경우 마법사를 다시 실행하고 제거 옵션을 선택합니다.

설치하는 동안 문제가 발생하면 설치 로그 **%LocalAppData%\Temp\Microsoft Rights Management connector_\<date and time>.log**를 확인합니다. 

예를 들어 설치 로그는 C:\Users\Administrator\AppData\Local\Temp\Microsoft Rights Management connector_20170803110352.log와 비슷합니다.

## <a name="authorizing-servers-to-use-the-rms-connector"></a>RMS 커넥터를 사용할 서버 권한 부여
두 대 이상의 컴퓨터에 RMS 커넥터를 설치한 경우 RMS 커넥터를 사용하려는 서버 및 서비스에 권한을 부여할 준비가 되었습니다. 예를 들어 서버가 Exchange Server 2013 또는 SharePoint Server 2013을 실행합니다.

이러한 서버를 정의하려면 RMS 커넥터 관리 도구를 실행하고, 허용된 서버 목록에 항목을 추가합니다. Microsoft Rights Management 커넥터 설치 마법사의 끝에서 **커넥터 관리 콘솔을 시작하여 서버 권한 부여**를 선택하면 이 도구를 실행할 수 있습니다. 또는 마법사에서 별도로 실행할 수 있습니다.

이러한 서버를 인증하는 경우 다음과 같은 고려 사항에 유의하세요.

- 추가한 서버에는 특별한 권한이 부여됩니다. 커넥터 구성에서 Exchange Server 역할에 지정한 모든 계정에는 Azure RMS에서 [슈퍼 사용자 역할](configure-super-users.md)이 부여됩니다. 그러면이 RMS 테넌트의 모든 콘텐츠에 대한 액세스 권한을 부여합니다. 필요한 경우 이 시점에서 자동으로 슈퍼 사용자 기능을 사용하도록 설정합니다. 권한 상승의 보안 위험을 방지하려면 조직의 Exchange Server에서 사용하는 계정만을 지정해야 합니다. SharePoint Server로 구성된 모든 서버 또는 FCI를 사용하는 파일 서버에는 일반 사용자 권한이 부여됩니다.

- Active Directory 보안이나 배포 목록 또는 둘 이상의 서버에서 사용하는 서비스 계정을 지정하여 여러 서버를 단일 항목으로 추가할 수 있습니다. 이 구성을 사용하면 서버 그룹에서는 동일한 RMS 인증서를 공유하고 그 중 하나가 보호하는 콘텐츠의 소유자로 간주됩니다. 관리 오버헤드를 최소화하려면 개별 서버가 아니라 단일 그룹인 이 구성을 사용하여 조직의 Exchange Server 또는 SharePoint Server 팜에 권한을 부여하는 것이 좋습니다.

**커넥터를 사용할 수 있는 서버** 페이지에서 **추가**를 클릭합니다.

> [!NOTE]
> 서버 권한 부여는 서비스 또는 서버 컴퓨터 계정의 ServerCertification.asmx에 NTFS 권한을 수동으로 적용하고 Exchange 계정에 슈퍼 사용자 권한을 수동으로 부여하는 AD RMS 구성에 해당하는 Azure RMS의 구성입니다. 커넥터에서 ServerCertification.asmx에 NTFS 권한을 적용할 필요가 없습니다.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>허용된 서버 목록에 서버 추가
**커넥터를 사용할 수 있는 서버** 페이지에서 개체의 이름을 입력하거나 찾아서 권한을 부여할 개체를 식별합니다.

올바른 개체에 권한을 부여해야 합니다. 커넥터를 사용하는 서버의 경우 권한 부여를 위해 온-프레미스 서비스(예: Exchange 또는 SharePoint)를 실행하는 계정을 선택해야 합니다. 예를 들어 서비스가 구성된 서비스 계정으로 실행되는 경우 해당 서비스 계정의 이름을 목록에 추가합니다. 서비스가 로컬 시스템으로 실행되는 경우 컴퓨터 개체(예: SERVERNAME$)의 이름을 추가합니다. 모범 사례로써 이러한 계정을 포함하는 그룹을 만들고, 개별 서버 이름 대신 그룹을 지정합니다.

다른 서버 역할에 자세한 내용은 다음과 같습니다.

-   Exchange를 실행하는 서버의 경우: 보안 그룹을 지정해야 하고, Exchange에서 포리스트의 모든 Exchange 서버를 자동으로 만들어 유지 관리하는 기본 그룹(**Exchange Servers**)을 사용할 수 있습니다.

-   SharePoint를 실행하는 서버의 경우:

    -   SharePoint 2010 서버가 로컬 시스템으로 실행하도록 구성된 경우(서비스 계정을 사용하지 않음) Active Directory Domain Services에서 수동으로 보안 그룹을 만들고, 이 구성의 서버에 대한 컴퓨터 이름 개체를 이 그룹에 추가합니다.

    -   SharePoint Server가 서비스 계정을 사용하도록 구성된 경우(SharePoint 2010에 권장되는 방법이며 SharePoint 2016 및 SharePoint 2013의 유일한 옵션) 다음을 수행합니다.

        1.  SharePoint를 관리 콘솔에서 구성할 수 있도록 SharePoint 중앙 관리 서비스를 실행하는 서비스 계정을 추가합니다.

        2.  SharePoint 앱 풀에 구성된 계정을 추가합니다.

        > [!TIP]
        > 이러한 두 계정이 다른 경우 관리 오버헤드를 최소화하기 위해 두 계정을 모두 포함하는 단일 그룹을 만드는 것이 좋습니다.

-   파일 분류 인프라를 사용하는 파일 서버의 경우 연결된 서비스가 로컬 시스템 계정으로 실행됩니다. 따라서 해당 컴퓨터 계정을 포함하는 파일 서버(예: SERVERNAME$) 또는 그룹의 컴퓨터 계정에 권한을 부여해야 합니다.

목록에 서버를 추가하는 작업이 완료되면 **닫기**를 클릭합니다.

아직 수행하지 않은 경우 이제 RMS 커넥터가 설치되어 있는 서버에 부하 분산을 구성하고, 이러한 서버와 방금 권한을 부여한 서버 간의 연결을 위해 HTTPS를 사용할지를 결정해야 합니다.

## <a name="configuring-load-balancing-and-high-availability"></a>부하 분산 및 고가용성 구성
RMS 커넥터의 두 번째 또는 마지막 인스턴스를 설치한 후에 커넥터 URL 서버 이름을 정의하고 부하 분산 시스템을 구성합니다.

커넥터 URL 서버 이름으로 사용자가 제어하는 네임스페이스의 모든 이름을 사용할 수 있습니다. 예를 들어 **rmsconnector.contoso.com**에서 DNS 시스템의 항목을 만들고 부하 분산 시스템에서에서 IP 주소를 사용하도록 이 항목을 구성할 수 있습니다. 이 이름에 대한 특별한 요구 사항이 없습니다. 또한 커넥터 서버 자체에서 구성하지 않아도 됩니다. Exchange 및 SharePoint Server가 인터넷을 통해 커넥터와 통신하지 않으면 이 이름은 인터넷에서 확인하지 않아도 됩니다.

> [!IMPORTANT]
> 모든 IRM 구성의 이러한 서버를 지운 다음, 다시 구성해야 하기 때문에 커넥터를 사용하도록 Exchange 또는 SharePoint Server를 구성한 후에 이 이름의 변경하지 않는 것이 좋습니다.

DNS에서 이름을 만들고 IP 주소에 대해 구성한 후에 해당 주소의 부하 분산을 구성합니다. 여기서는 트래픽을 커넥터 서버로 전송합니다. 이를 위해 모든 IP 기반 부하 분산 장치를 사용할 수 있습니다. 여기에는 Windows Server에 NLB(네트워크 부하 분산) 기능이 포함됩니다. 자세한 내용은 [부하 분산 배포 가이드](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx)를 참조하세요.

다음 설정을 사용하여 NLB 클러스터를 구성합니다.

-   포트: 80(HTTP) 또는 443(HTTPS)

    HTTP 또는 HTTPS를 사용할지에 대한 자세한 내용은 다음 섹션을 참조하세요.

-   선호도: 없음

-   배포 방법: 같음

부하 분산 시스템에 대해 정의한 이 이름(RMS 커넥터 서비스를 실행하는 서버의 경우)은 Azure RMS를 사용하도록 온-프레미스 서버를 구성할 때 나중에 사용하는 조직의 RMS 커넥터 이름입니다.

## <a name="configuring-the-rms-connector-to-use-https"></a>HTTPS를 사용하도록 RMS 커넥터 구성
> [!NOTE]
> 이 구성 단계는 선택 사항이지만 추가 보안을 위해 권장됩니다.

TLS 또는 SSL을 사용하는 것은 RMS 커넥터에서 선택 사항이지만 HTTP 기반 보안 관련 서비스에서 권장됩니다. 이 구성에서는 커넥터를 사용하는 Exchange 및 SharePoint Server에 대해 커넥터를 실행하는 서버를 인증합니다. 또한 이러한 서버에서 커넥터로 전송되는 모든 데이터는 암호화됩니다.

RMS 커넥터가 TLS를 사용하도록 설정하려면 RMS 커넥터를 실행하는 각 서버에서 커넥터에 사용하는 이름을 포함하는 서버 인증 인증서를 설치합니다. 예를 들어 DNS에서 정의한 RMS 커넥터 이름이 **rmsconnector.contoso.com**인 경우 인증서 주체에서 **rmsconnector.contoso.com**을 포함하는 서버 인증 인증서를 일반적인 이름으로 배포합니다. 또는 인증서 대체 이름에서 **rmsconnector.contoso.com**을 DNS 값으로 지정합니다. 인증서는 서버의 이름을 포함하지 않아도 됩니다. 그런 다음, IIS에서 이 인증서를 기본 웹 사이트에 바인딩합니다.

HTTPS 옵션을 사용하는 경우 커넥터를 실행하는 모든 서버에 Exchange 및 SharePoint Server가 트러스트하는 루트 CA에 연결된 유효한 서버 인증 인증서가 있는지 확인합니다. 또한 커넥터 서버에 인증서를 발급한 CA(인증 기관)가 CRL(인증서 해지 목록)을 게시하는 경우 Exchange 및 SharePoint Server는 이 CRL을 다운로드할 수 있어야 합니다.

> [!TIP]
> 다음 정보 및 리소스를 사용하여 서버 인증 인증서를 요청하고 설치할 수 있도록 하고 IIS에서 기본 웹 사이트에 이 인증서를 바인딩할 수 있습니다.
>
> -   AD CS(Active Directory 인증서 서비스) 및 엔터프라이즈 CA(인증 기관)를 사용하여 이러한 서버 인증 인증서를 배포하는 경우 웹 서버 인증서 템플릿을 복제한 다음, 사용할 수 있습니다. 이 인증서 템플릿은 인증서 주체 이름에 **요청에서 제공**을 사용합니다. 즉, 인증서를 요청할 때 인증서 주체 이름 또는 주체 대체 이름에 RMS 커넥터 이름의 FQDN을 입력할 수 있습니다.
> -   독립 실행형 CA를 사용하거나 다른 회사에서 이 인증서를 구입하는 경우 TechNet의 [웹 서버(IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) 문서 라이브러리에서 [인터넷 서버 인증서 구성(IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx)을 참조하세요.
> -   인증서를 사용하도록 IIS를 구성하려면 TechNet의 [웹 서버(IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) 문서 라이브러리에서 [사이트에 바인딩 추가(IIS 7)](http://technet.microsoft.com/library/cc731692.aspx)를 참조하세요.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>웹 프록시 서버에 대해 RMS 커넥터 구성
커넥터 서버가 직접 인터넷 연결되어 있지 않은 네트워크에 설치되고 아웃바운드 인터넷 액세스를 위해 웹 프록시 서버를 수동으로 구성해야 하는 경우 RMS 커넥터의 이러한 서버에서 레지스트리를 구성해야 합니다.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>웹 프록시 서버를 사용하도록 RMS 커넥터를 구성하려면

1.  RMS 커넥터를 실행하는 각 서버에서 레지스트리 편집기를 엽니다(예: Regedit).

2.  **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**로 이동합니다.

3.  **ProxyAddress**라는 문자열 값을 추가한 다음, 이 값의 데이터를 **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;**로 설정합니다.

    예: **http://proxyserver.contoso.com:8080**

4.  레지스트리 편집기를 닫은 다음, 서버를 다시 시작하거나 IISReset 명령을 수행하여 IIS를 다시 시작합니다.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>관리 컴퓨터에 RMS 커넥터 관리 도구 설치
해당 컴퓨터가 다음 요구 사항을 충족하는 경우 RMS 커넥터가 설치되지 않은 컴퓨터에서 RMS 커넥터 관리 도구를 실행할 수 있습니다.

-   Windows Server 2012 또는 Windows Server 2012 R2(모든 버전), Windows Server 2008 R2 또는 Windows Server 2008 R2 서비스 팩 1(모든 버전), Windows 8.1, Windows 8 또는 Windows 7을 실행하는 실제 또는 가상 컴퓨터

-   최소 1GB의 RAM

-   최소 64GB의 디스크 공간

-   하나 이상의 네트워크 인터페이스

-   방화벽(또는 웹 프록시)을 통한 인터넷 액세스

RMS 커넥터 관리 도구를 설치하려면 다음 파일을 실행합니다.

-   32비트 컴퓨터의 경우: RMSConnectorAdminToolSetup_x86.exe

-   64비트 컴퓨터의 경우: RMSConnectorSetup.exe

이러한 파일을 아직 다운로드하지 않은 경우 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=314106)에서 다운로드하면 됩니다.


## <a name="next-steps"></a>다음 단계
RMS 커넥터를 설치하고 구성했으므로 온-프레미스 서버를 사용하도록 구성할 준비가 되었습니다. [Azure Rights Management 커넥터에 서버 구성](configure-servers-rms-connector.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
