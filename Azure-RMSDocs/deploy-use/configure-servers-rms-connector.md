---
# required metadata

title: Azure 권한 관리 커넥터에 대해 서버 구성 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리 커넥터에 대해 서버 구성

다음 정보를 참조하여 Azure 권한 관리(RMS) 커넥터를 사용할 온-프레미스 서버를 구성할 수 있습니다. 이러한 절차는 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)의 5단계를 설명합니다.

시작하기 전에 RMS 커넥터를 설치 및 구성했으며 커넥터를 사용할 서버에 해당하는 [필수 조건](deploy-rms-connector.md#prerequisites-for-the-rms-connector)을 모두 검사했는지 확인합니다.


## RMS 커넥터를 사용하도록 서버 구성
RMS 커넥터를 설치 및 구성했으면 Rights Management를 사용하고 커넥터를 통해 Azure RMS에 연결하는 온-프레미스 서버를 구성할 준비가 된 것입니다. 즉, 다음 서버를 구성할 수 있습니다.

-   **Exchange 2016 및 Exchange 2013의 경우**: 클라이언트 액세스 서버 및 사서함 서버

-   **Exchange 2010의 경우**: 클라이언트 액세스 서버 및 허브 전송 서버

-   **SharePoint의 경우**: 중앙 관리 서버를 호스트하는 서버를 비롯한 프런트 엔드 SharePoint 웹 서버

-   **파일 분류 인프라**: 파일 리소스 관리자를 설치한 Windows Server 컴퓨터

이 구성에는 레지스트리 설정이 필요합니다. 이 작업을 수행하는 방법에는 Microsoft RMS 커넥터용 서버 구성 도구를 사용하여 자동으로 또는 레지스트리를 편집하여 수동으로 수행하는 두 가지 옵션이 있습니다.

---

**Microsoft RMS 커넥터용 서버 구성 도구를 사용하여 자동으로:**

- 장점:

    - 레지스트리를 직접 편집할 필요가 없습니다. 스크립트를 사용하여 자동으로 수행됩니다.

    - Microsoft RMS URL을 얻기 위해 Windows PowerShell cmdlet을 실행할 필요가 없습니다.

    - 로컬에서 실행하면 필수 구성 요소가 자동으로 확인됩니다(그러나 자동으로 수정되지는 않음).

단점:

- 도구를 실행할 때 이미 RMS 커넥터를 실행 중인 서버에 연결해야 합니다.

---

**레지스트리를 편집하여 수동으로:**

- 장점:

    - RMS 커넥터를 실행 중인 서버에 연결할 필요가 없습니다.

- 단점:

    - 오류가 발생하기 쉬운 관리 오버헤드가 증가합니다.

    - Microsoft RMS URL을 얻어야 하는데, 이렇게 하려면 Windows PowerShell 명령을 실행해야 합니다.

    - 모든 필수 구성 요소를 항상 스스로 확인해야 합니다.


---

> [!IMPORTANT]
> 두 가지 경우 모두에서 수동으로 모든 필수 구성 요소를 설치하고 권한 관리를 사용하도록 Exchange, SharePoint 및 파일 분류 인프라를 구성해야 합니다.

대부분의 조직에게는 수동 구성보다 Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 자동 구성이 효율성과 안정성이 더 우수하기 때문에 더 좋은 옵션입니다.

이러한 서버에서 구성을 변경한 후에는 서버가 Exchange 또는 SharePoint를 실행하고 있고 이전에 AD RMS를 사용하도록 구성되었다면 서버를 다시 시작해야 합니다. 처음으로 서버를 권한 관리용으로 구성하는 경우에는 다시 시작할 필요가 없습니다. 항상 이러한 구성을 변경한 후에는 파일 분류 인프라를 사용하도록 구성된 파일 서버를 다시 시작해야 합니다.

### Microsoft RMS 커넥터용 서버 구성 도구를 사용하려면

1.  Microsoft RMS 커넥터용 서버 구성 도구의 스크립트(GenConnectorConfig.ps1)를 아직 다운로드하지 않은 경우 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=314106)에서 다운로드합니다.

2.  도구를 실행할 컴퓨터에 GenConnectorConfig.ps1 파일을 저장합니다. 이 도구를 로컬로 실행할 경우에는 RMS 커넥터와 통신하도록 구성하려는 서버여야 합니다. 그렇지 않은 경우 아무 컴퓨터에나 저장할 수 있습니다.

3.  도구 실행 방법을 결정합니다.

    -   **로컬로**: 이 도구는 RMS 커넥터와 통신하도록 구성할 서버에서 대화형으로 실행할 수 있습니다. 이 방법은 테스트 환경과 같은 일회성 구성에 유용합니다.

    -   **소프트웨어 배포**: 도구를 실행하고 소프트웨어 배포를 지원하는 시스템 관리 응용 프로그램(예: System Center Configuration Manager)을 사용하여 하나 이상의 관련 서버에 배포할 레지스트리 파일을 생성할 수 있습니다.

    -   **그룹 정책**: 도구를 실행하여 구성할 서버의 그룹 정책 개체를 만들 수 있는 관리자에게 제공할 스크립트를 생성할 수 있습니다. 이 스크립트는 구성할 각 서버 유형에 대해 하나의 그룹 정책 개체를 만들며, 관리자는 이 개체를 관련 서버에 할당할 수 있습니다.

    > [!NOTE]
    > 이 도구는 RMS 커넥터와 통신할 서버와 이 섹션의 시작 부분에 나열되어 있는 서버를 구성합니다. RMS 커넥터를 실행하는 서버에서는 이 도구를 실행하지 마세요.

4.  **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작하고 Get-help 명령을 사용하여 선택한 구성 방법용 도구를 사용하는 방법에 대한 지침을 확인합니다.

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

스크립트를 실행하려면 조직의 RMS 커넥터 URL을 입력해야 합니다. 프로토콜 접두사(HTTP:// 또는 HTTPS://)를 입력하고 DNS에서 커넥터의 부하 분산 주소에 대해 정의한 커넥터 이름을 입력합니다. https://connector.contoso.com을 예로 들 수 있습니다. 그러면 도구에서 해당 URL을 사용하여 RMS 커넥터를 실행 중인 서버에 연결하고 필요한 구성을 만드는 데 사용되는 다른 매개 변수를 가져옵니다.

> [!IMPORTANT]
> 이 도구를 실행할 때는 RMS 커넥터 서비스를 실행하는 단일 서버 이름이 아니라, 조직의 부하 분산된 RMS 커넥터 이름을 지정해야 합니다.

다음 섹션에서 각 서비스 유형에 관련된 정보를 확인하세요.

-   [커넥터를 사용하도록 Exchange Server 구성](#configuring-an-exchange-server-to-use-the-connector)

-   [커넥터를 사용하도록 SharePoint Server 구성](#configuring-a-sharepoint-server-to-use-the-connector)

-   [커넥터를 사용하도록 파일 분류 인프라용 파일 서버 구성](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

> [!NOTE]
> 커넥터를 사용하도록 이러한 서버를 구성한 후에는 해당 서버에서 로컬로 설치된 클라이언트 응용 프로그램이 RMS와 동작하지 않을 수 있습니다. 응용 프로그램이 RMS를 직접 사용하지 않고 커넥터를 사용(지원되지 않음)하려고 하기 때문에 이러한 상황이 발생합니다.
>
> 또한 Office 2010이 Exchange Server에 로컬로 설치된 경우 커넥터를 사용하도록 서버를 구성한 후에 클라이언트 앱의 IRM 기능이 해당 컴퓨터에서 작동할 수도 있지만 이는 지원되지 않습니다.
>
> 두 시나리오 모두에서, 커넥터를 사용하도록 구성되지 않은 별도의 컴퓨터에 클라이언트 응용 프로그램을 설치해야 합니다. 그러면 클라이언트 응용 프로그램이 올바르게 RMS를 직접 사용합니다.

## 커넥터를 사용하도록 Exchange Server 구성
다음 Exchange 역할은 RMS 커넥터와 통신합니다.

-   Exchange 2016 및 Exchange 2013의 경우: 클라이언트 액세스 서버 및 사서함 서버

-   Exchange 2010: 클라이언트 액세스 서버 및 허브 전송 서버

RMS 커넥터를 사용하려면 Exchange를 실행하는 이러한 서버가 다음 소프트웨어 버전 중 하나를 실행 중이어야 합니다.

-   Exchange Server 2016

-   Exchange Server 2013(Exchange 2013 누적 업데이트 3 포함)

-   Exchange Server 2010(Exchange 2010 서비스 팩 3 롤업 업데이트 6 포함)

또한 서버에 RMS 암호화 모드 2에 대한 지원이 포함된 RMS 클라이언트 버전을 설치해야 합니다. Windows Server 2008에서 지원되는 최소 버전은 [Windows Server 2008 R2 및 Windows Server 2008에서 AD RMS의 RSA 키 길이가 2048비트로 증가됨](http://support.microsoft.com/kb/2627272)에서 다운로드할 수 있는 핫픽스에 포함되어 있습니다. Windows Server 2008 R2의 최소 버전은 [Windows 7 또는 Windows Server 2008 R2에서 AD RMS에 대해 RSA 키가 2048비트로 증가함](http://support.microsoft.com/kb/2627273)에서 다운로드할 수 있습니다. Windows Server 2012 및 Windows Server 2012 R2는 기본적으로 암호화 모드 2를 지원합니다.

> [!IMPORTANT]
> 이러한 버전이나 이후 버전의 Exchange와 RMS 클라이언트가 설치되지 않은 경우 커넥터를 사용하도록 Exchange를 구성할 수 없습니다. 계속하기 전에 이러한 버전이 설치되어 있는지 확인하세요.

### 커넥터를 사용하도록 Exchange Server를 구성하려면

1. RMS 커넥터 관리 도구와 [RMS 커넥터를 사용하도록 서버에 권한 부여](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) 섹션의 정보를 사용하여 Exchange 서버에 RMS 커넥터를 사용할 권한이 있는지 확인합니다. 이 구성은 Exchange에서 RMS 커넥터를 사용하는 데 필요합니다.

2.  RMS 커넥터와 통신하는 Exchange Server 역할에 대해 다음 중 하나를 수행합니다.

    -   Microsoft RMS 커넥터용 서버 구성 도구를 실행합니다. 자세한 내용은 이 문서에서 [Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 방법](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector)을 참조하세요.

        예를 들어 로컬로 도구를 실행하여 Exchange 2016 또는 Exchange 2013을 실행하는 서버를 구성하려면 다음을 수행합니다.

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   [RMS 커넥터에 대한 레지스트리 설정](rms-connector-registry-settings.md)의 정보를 참조해서 수동으로 레지스트리를 편집하여 서버의 레지스트리 설정을 수동으로 추가합니다. 

3.  Exchange에서 IRM 기능을 사용합니다. 자세한 내용은 Exchange 라이브러리에서 [정보 권한 관리 절차](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx)를 참조하세요.

## 커넥터를 사용하도록 SharePoint Server 구성
다음 SharePoint 역할은 RMS 커넥터와 통신합니다.

-   중앙 관리 서버를 호스트하는 서버를 비롯한 프런트 엔드 SharePoint 웹 서버

RMS 커넥터를 사용하려면 SharePoint를 실행하는 이러한 서버가 다음 소프트웨어 버전 중 하나를 실행 중이어야 합니다.

-   SharePoint Server 2013

-   SharePoint Server 2010

SharePoint 2013 서버도 RMS 커넥터에서 지원되는 MSIPC 클라이언트 2.1의 한 버전을 실행해야 합니다. 지원되는 버전이 있는지 확인하려면 [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=38396)에서 최신 클라이언트를 다운로드합니다.

> [!WARNING]
> 여러 버전의 MSIPC 2.1 클라이언트가 있으므로 1.0.2004.0 이상 버전이 있는지 확인합니다.
>
> MSIPC.dll(**\Program Files\Active Directory Rights Management Services Client 2.1**에 있음)의 버전 번호를 확인하여 클라이언트 버전을 확인할 수 있습니다. 속성 대화 상자에서 MSIPC 2.1 클라이언트의 버전 번호가 표시됩니다.

SharePoint 2010을 실행하는 이 서버에는 RMS 암호화 모드 2에 대한 지원이 포함된 MSDRM 클라이언트 버전을 설치해야 합니다. Windows Server 2008에서 지원되는 최소 버전은 [Windows Server 2008 R2 및 Windows Server 2008에서 AD RMS의 RSA 키 길이가 2048비트로 증가됨](http://support.microsoft.com/kb/2627272)에서 다운로드할 수 있는 핫픽스에 포함되어 있으며, Windows Server 2008 R2에 대한 최소 버전은 [Windows 7 또는 Windows Server 2008 R2에서 AD RMS의 RSA 키 길이가 2048비트로 증가됨](http://support.microsoft.com/kb/2627273)에서 다운로드할 수 있습니다. Windows Server 2012 및 Windows Server 2012 R2는 기본적으로 암호화 모드 2를 지원합니다.

### 커넥터를 사용하도록 SharePoint Server를 구성하려면

1. RMS 커넥터 관리 도구와 [RMS 커넥터를 사용하도록 서버에 권한 부여](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) 섹션의 정보를 사용하여 SharePoint 서버에 RMS 커넥터를 사용할 권한이 있는지 확인합니다. 이 구성은 Exchange에서 RMS 커넥터를 사용하는 데 필요합니다.

2.  RMS 커넥터와 통신하는 SharePoint 서버에 대해 다음 중 하나를 수행합니다.

    -   Microsoft RMS 커넥터용 서버 구성 도구를 실행합니다. 자세한 내용은 이 문서에서 [Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 방법](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector)을 참조하세요.

        예를 들어, 로컬로 도구를 실행하여 SharePoint 2013을 실행하는 서버를 구성하려면 다음과 같습니다.

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   SharePoint 2013을 사용하는 경우 [RMS 커넥터에 대한 레지스트리 설정](rms-connector-registry-settings.md)의 정보를 참조해서 수동으로 레지스트리를 편집하여 서버의 레지스트리 설정을 수동으로 추가합니다. 

3.  SharePoint에서 IRM을 사용하도록 설정합니다. 자세한 내용은 SharePoint 라이브러리에서 [정보 권한 관리 구성(SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx)을 참조하세요.

    다음 지침을 따를 때는 **이 RMS 서버 사용**을 지정하여 커넥터를 사용하도록 SharePoint를 구성한 후 구성한 부하 분산 커넥터 URL을 입력해야 합니다. 프로토콜 접두사(HTTP:// 또는 HTTPS://)를 입력하고 DNS에서 커넥터의 부하 분산 주소에 대해 정의한 커넥터 이름을 입력합니다. 예를 들어 프로그램 커넥터 이름이 https://connector.contoso.com 인 경우 구성은 다음 그림과 같이 표시됩니다.

    ![](../media/AzRMS_SharePointConnector.png)

    IRM이 SharePoint 팜에서 사용되도록 한 후 각 라이브러리의 **라이브러리 설정** 페이지에서 **정보 권한 관리** 옵션을 사용하여 개별 라이브러리에서 IRM을 사용할 수 있습니다.


## 커넥터를 사용하도록 파일 분류 인프라용 파일 서버 구성
RMS 커넥터 및 파일 분류 인프라를 사용하여 Office 문서를 보호하려면 파일 서버가 다음 운영 체제 중 하나를 실행 중이어야 합니다.

-   Windows Server 2012 R2

-   Windows Server 2012

### 커넥터를 사용하도록 파일 서버를 구성하려면

1.  RMS 커넥터 관리 도구와 [RMS 커넥터를 사용하도록 서버에 권한 부여](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) 섹션의 정보를 사용하여 파일 서버에 RMS 커넥터를 사용할 권한이 있는지 확인합니다. 이 구성은 Exchange에서 RMS 커넥터를 사용하는 데 필요합니다.

2.  파일 분류 인프라용으로 구성되어 있고 RMS 커넥터와 통신할 파일 서버에서 다음 중 하나를 수행합니다.

    -   Microsoft RMS 커넥터용 서버 구성 도구를 실행합니다. 자세한 내용은 이 문서에서 [Microsoft RMS 커넥터용 서버 구성 도구를 사용하는 방법](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector)을 참조하세요.

        예를 들어, 로컬로 도구를 실행하여 FCI를 실행하는 파일 서버를 구성하려면 다음과 같습니다.

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - [RMS 커넥터에 대한 레지스트리 설정](rms-connector-registry-settings.md)의 정보를 참조해서 수동으로 레지스트리를 편집하여 서버의 레지스트리 설정을 수동으로 추가합니다. 

3.  RMS 암호화로 문서를 보호하기 위한 분류 규칙 및 파일 관리 작업을 만들고, RMS 정책을 자동으로 적용하기 위한 RMS 템플릿을 지정합니다. 자세한 내용은 Windows Server 문서 라이브러리의 [파일 서버 리소스 관리자 개요](http://technet.microsoft.com/library/hh831701.aspx) 를 참조하세요.

## 다음 단계
이제 RMS 커넥터가 설치 및 구성되고 서버가 RMS 커넥터를 사용하도록 구성되었으므로, IT 관리자 및 사용자는 Azure RMS를 사용하여 전자 메일 메시지 및 문서를 보호하고 사용할 수 있습니다. 사용자가 이러한 작업을 간편하게 수행할 수 있도록, Office용 추가 기능을 설치하고 파일 탐색기에 새로운 오른쪽 클릭 옵션을 추가하는 RMS 공유 응용 프로그램을 배포합니다. 자세한 내용은 [Rights Management 공유 응용 프로그램 관리자 가이드](../rms-client/sharing-app-admin-guide.md)를 참조하세요.

또한 다음을 통해 RMS 커넥터 및 조직의 Azure RMS 사용 현황을 모니터링할 수 있습니다.

-   기본 제공 **Microsoft Rights Management 커넥터** 성능 카운터

-   RMS 커넥터 옵션을 사용하여 커넥터의 상태를 모니터링하고 모든 구성 문제를 식별하는 데 도움이 되는 [RMS 분석기 도구](https://www.microsoft.com/en-us/download/details.aspx?id=46437)

-   [Azure 권한 관리 사용 현황 로깅 및 분석](log-analyze-usage.md)

[Azure 권한 관리 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용자와 관리자에게 배포하기 전에 수행할 수 있는 다른 구성 단계가 있는지 확인할 수 있습니다. 


<!--HONumber=Apr16_HO3-->

