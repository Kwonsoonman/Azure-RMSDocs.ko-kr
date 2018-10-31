---
title: Azure Information Protection 스캐너 배포
description: Azure Information Protection 스캐너를 설치, 구성 및 실행하여 데이터 저장소에서 파일을 검색, 분류 및 보호하는 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/24/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 315c1e04d6d941643ee6625053b1cae8bd08b292
ms.sourcegitcommit: 51c99ea4c98b867cde964f51c35450eaa22fac27
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991380"
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Azure Information Protection 스캐너를 배포하여 파일 자동으로 분류 및 보호

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2*

이 정보를 사용하여 Azure Information Protection 스캐너에 대한 정보 및 성공적으로 설치, 구성 및 실행하는 방법을 알아봅니다. 

이 스캐너는 Windows Server에서 서비스로 실행되고 해당 스캐너를 통해 다음 데이터 저장소에서 파일을 검색, 분류 및 보호할 수 있습니다.

- 스캐너를 실행하는 Windows Server 컴퓨터의 로컬 폴더

- SMB(서버 메시지 블록) 프로토콜을 사용하는 네트워크 공유의 UNC 경로

- SharePoint Server 2016 및 SharePoint Server 2013의 사이트 및 라이브러리 [이 버전의 SharePoint에 대한 지원을 확장](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010)한 고객의 경우 SharePoint 2010도 지원됩니다.

클라우드 리포지토리에서 파일을 검색하고 레이블을 지정하려면 [Cloud App Security](https://docs.microsoft.com/cloud-app-security/)를 사용합니다.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너 개요

자동 분류를 적용하는 레이블에 [Azure Information Protection 정책](configure-policy.md)을 구성한 경우 이 스캐너를 검색하는 파일은 레이블이 지정될 수 있습니다. 레이블은 분류를 적용하고 필요에 따라 보호를 적용하거나 제거합니다.

![Azure Information Protection 스캐너 아키텍처 개요](./media/infoprotect-scanner.png)

스캐너는 컴퓨터에 설치된 iFilters를 사용하여 Windows에서 인덱싱하는 파일을 검사할 수 있습니다. 그런 다음, 파일에 레이블을 지정해야 하는지를 결정하려면 스캐너는 Office 365 기본 제공 DLP(데이터 손실 방지) 민감도 정보 유형 및 패턴 감지 또는 Office 365 정규식 패턴을 사용합니다. 스캐너가 Azure Information Protection 클라이언트를 사용하기 때문에 동일한 [파일 형식](./rms-client/client-admin-guide-file-types.md)을 분류하고 보호할 수 있습니다.

스캐너를 검색 모드에서만 실행할 수 있습니다. 여기서는 보고서를 사용하여 파일에 레이블을 적용했을 때 발생한 결과를 확인합니다. 또는 스캐너를 실행하여 레이블을 자동으로 적용할 수 있습니다. 또한 스캐너를 실행하여 자동 분류를 적용하는 조건에 대한 레이블을 구성하지 않고 중요한 정보 유형이 포함된 파일을 검색할 수도 있습니다.

스캐너는 실시간으로 검색하고 레이블을 지정하지 않습니다. 지정한 데이터 저장소의 파일을 체계적으로 크롤링하여 이 주기를 한 번 또는 반복적으로 실행되도록 구성할 수 있습니다.

스캔할 파일 형식을 지정하거나 스캔에서 제외할 수 있습니다. 스캐너가 검사하는 파일을 제한하려면 [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)를 사용하여 파일 형식 목록을 정의합니다.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너의 필수 구성 요소
Azure Information Protection 스캐너를 설치하기 전에 다음 요구 사항이 설정되어 있는지 확인하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|스캐너 서비스를 실행할 Windows Server 컴퓨터:<br /><br />- 4 코어 프로세서<br /><br />- 4GB RAM<br /><br />- 임시 파일에 대해 10GB의 사용 가능한 공간(평균)|Windows Server 2016 또는 Windows Server 2012 R2 <br /><br />참고: 비-프로덕션 환경에서 테스트 또는 평가는 [Azure Information Protection 클라이언트에서 지원하는](requirements.md#client-devices) Windows 클라이언트 운영 체제를 사용할 수 있습니다.<br /><br />이 컴퓨터는 검색할 데이터 저장소에 안정적인 고속 네트워크를 연결한 실제 또는 가상 컴퓨터일 수 있습니다.<br /><br /> 스캐너는 검색하는 각 파일에 대한 임시 파일(코어당 4개의 파일)을 생성하기에 충분한 디스크 공간이 필요합니다. 10GB의 권장 디스크 공간을 통해 4 코어 프로세서가 각각 625MB의 파일 크기를 갖는 16개의 파일을 검색할 수 있습니다. <br /><br />이 컴퓨터가 Azure Information Protection에 필요한 [인터넷이 연결](requirements.md#firewalls-and-network-infrastructure)되어 있는지 확인합니다. 조직 정책으로 인해 인터넷에 연결할 수 없는 경우 [대체 구성으로 스캐너 배포](#deploying-the-scanner-with-alternative-configurations) 섹션을 참조하세요.|
|스캐너 구성을 저장할 SQL Server:<br /><br />- 로컬 또는 원격 인스턴스<br /><br />-스캐너를 설치하기 위한 Sysadmin 역할|SQL Server 2012는 다음 버전의 최소 버전입니다.<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express<br /><br />둘 이상의 스캐너 인스턴스를 설치하는 경우 각 스캐너 인스턴스에는 고유한 SQL Server 인스턴스가 필요합니다.<br /><br />스캐너를 설치하고, 계정에 Sysadmin 역할이 있는 경우 설치 프로세스가 자동으로 AzInfoProtectionScanner 데이터베이스를 생성하며 스캐너를 실행하는 서비스 계정에 필요한 db_owner 역할을 부여합니다.  Sysadmin 역할을 부여받을 수 없거나 조직 정책에 따라 데이터베이스를 수동으로 생성하고 구성해야 하는 경우 [대체 구성으로 스캐너 배포](#deploying-the-scanner-with-alternative-configurations) 섹션을 참조하세요.|
|스캐너 서비스를 실행할 서비스 계정|스캐너 서비스를 실행하는 것 외에도 이 계정은 Azure AD에 대해 인증되고 Azure Information Protection 정책을 다운로드합니다. 이 계정은 Active Directory 계정이어야 하며 Azure AD와 동기화되어야 합니다. 조직 정책으로 인해 이 계정을 동기화할 수 없는 경우 [대체 구성으로 스캐너 배포](#deploying-the-scanner-with-alternative-configurations) 섹션을 참조하세요.<br /><br />이 서비스 계정에는 다음과 같은 요구 사항이 있습니다.<br /><br />- **로컬 로그온** 권한 이 권한은 스캐너를 설치하고 구성하는 데 필요하지만 작동하는 데는 필요하지 않습니다. 서비스 계정에 이 권한을 부여해야 하지만 스캐너가 파일을 검색, 분류 및 보호하는지 확인한 후에 이 권한을 제거할 수 있습니다. 조직 정책으로 인해 짧은 시간 동안에도 이 권한을 부여할 수 없는 경우 [대체 구성으로 스캐너 배포](#deploying-the-scanner-with-alternative-configurations) 섹션을 참조하세요.<br /><br />- **서비스로 로그온** 권한 스캐너 설치 중에 서비스 계정에 이 권한이 자동으로 부여됩니다. 이 권한은 스캐너의 설치, 구성 및 작동에 필요합니다. <br /><br />- 데이터 리포지토리에 대한 사용 권한: Azure Information Protection 정책에서 파일을 검색한 다음 조건을 충족하는 파일에 분류 및 보호를 적용하는 **읽기** 및 **쓰기** 권한을 부여해야 합니다. 검색 모드 전용으로 스캐너를 실행하려면 **읽기** 권한으로 충분합니다.<br /><br />- 다시 보호하거나 보호를 제거하는 레이블의 경우: 스캐너가 항상 보호된 파일에 액세스할 수 있도록 하려면 이 계정을 Azure Rights Management 서비스에 대한 [슈퍼 사용자](configure-super-users.md)로 지정하고 슈퍼 사용자 기능을 사용하도록 합니다. 보호를 적용하기 위한 계정 요구 사항에 대한 자세한 내용은 [Azure Information Protection을 위한 사용자 및 그룹 준비](prepare.md)를 참조하세요. 또한 단계적 배포용 [온보딩 컨트롤](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구현한 경우 구성한 온보딩 컨트롤에 이 계정이 포함되어 있는지 확인해야 합니다.|
|Azure Information Protection 클라이언트가 Windows Server 컴퓨터에 설치되었습니다.|스캐너를 위해 전체 클라이언트를 설치해야 합니다. PowerShell 모듈만으로 클라이언트를 설치하지 마세요.<br /><br />클라이언트 설치 지침은 [관리자 가이드](./rms-client/client-admin-guide.md)를 참조하세요. 이전에 스캐너를 설치했는데 이제 스캐너를 최신 버전으로 업그레이드해야 하는 경우 [Azure Information Protection 스캐너 업그레이드](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner)를 참조하세요.|
|자동 분류 및 필요에 따라 보호를 적용하는 구성된 레이블|Azure Information Protection 정책에서 조건을 구성하는 방법에 대한 자세한 내용은 [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](configure-policy-classification.md)을 참조하세요.<br /><br />파일에 보호를 적용하도록 레이블을 구성하는 방법에 대한 자세한 내용은 [Rights Management 보호를 위한 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.<br /><br />이러한 레이블은 전역 정책 또는 하나 이상의 [범위 지정 정책](configure-policy-scope.md)에 있을 수 있습니다.<br /><br />참고: 자동 분류를 적용하는 레이블을 구성하지 않은 경우에도 스캐너를 실행할 수 있지만, 이러한 지침에서는 이 시나리오를 다루지 않습니다. [추가 정보](#using-the-scanner-with-alternative-configurations)|
|검사할 Office 문서의 경우:<br /><br />- Word, Excel, PowerPoint에 대한 97-2003 파일 형식 및 Office Open XML 형식|이러한 파일 형식에 대해 스캐너에서 지원하는 파일 형식에 대한 자세한 내용은 [Azure Information Protection 클라이언트에서 지원하는 파일 형식](./rms-client/client-admin-guide-file-types.md)을 참조하세요. 

요구 사항이 조직 정책에 의해 금지되어 있어 표의 일부 요구 사항을 충족할 수 없는 경우 대안에 대한 다음 섹션을 참조하세요.

모든 요구 사항이 충족되는 경우 [설치 섹션](#install-the-azure-information-protection-scanner)으로 바로 이동하세요.

### <a name="deploying-the-scanner-with-alternative-configurations"></a>대체 구성으로 스캐너 배포

표에 나열된 전제 조건은 스캐너의 기본 요구 사항이며, 스캐너 배포를 위한 가장 단순한 구성이므로 이러한 전제 조건을 충족하는 것이 좋습니다. 이러한 전제 조건은 초기 테스트에 적합하므로 스캐너의 기능을 점검할 수 있습니다. 그러나 제품 환경에서 조직 정책은 다음 제한 중 하나 이상으로 인해 이러한 기본 요구 사항을 금지할 수 있습니다.

- 서버에서 인터넷 연결이 허용되지 않습니다.

- Sysadmin을 부여받을 수 없거나 데이터베이스를 수동으로 생성하고 구성해야 합니다.

- 서비스 계정에 **로컬 로그온** 권한을 부여할 수 없습니다.

- 서비스 계정을 Azure Active Directory와 동기화할 수 없지만, 서버에서 인터넷에 연결할 수 있습니다.

스캐너는 이러한 제한을 수용할 수 있지만, 추가 구성이 필요합니다.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>제한: 스캐너 서버에서 인터넷에 연결할 수 없습니다.

[연결이 끊어진 컴퓨터](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers)에 대한 지침을 따릅니다. 

이 구성에서는 스캐너가 조직의 클라우드 기반 키를 사용하여 보호를 적용(또는 보호를 제거)할 수 없습니다. 대신 스캐너는 분류만 적용하는 레이블을 사용하거나 [HYOK](configure-adrms-restrictions.md)를 활용하는 보호를 사용하도록 제한됩니다. 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>제한: Sysadmin을 부여받을 수 없거나 데이터베이스를 수동으로 생성하고 구성해야 합니다.

스캐너를 설치하기 위해 Sysadmin 역할을 임시로 부여받을 수 있는 경우 스캐너 설치가 완료되면 이 역할을 제거할 수 있습니다. 이 구성을 사용하는 경우 데이터베이스가 자동으로 생성되고 스캐너의 서비스 계정에 필요한 권한이 자동으로 부여됩니다. 그러나 스캐너를 구성하는 사용자 계정에는 AzInfoProtectionScanner 데이터베이스에 대한 db_owner 역할이 필요하므로 이 역할을 사용자 계정에 수동으로 부여해야 합니다.

일시적으로도 Sysadmin 역할을 부여받을 수 없는 경우 스캐너를 설치하기 전에 먼저 AzInfoProtectionScanner라는 데이터베이스를 수동으로 생성해야 합니다. 이 구성을 사용하는 경우 다음 역할을 할당해야 합니다.
    
|계정|데이터베이스 수준 역할|
|--------------------------------|---------------------|
|스캐너의 서비스 계정|db_owner|
|스캐너 설치용 사용자 계정|db_owner|
|스캐너 구성용 사용자 계정 |db_owner|

일반적으로 스캐너를 설치하고 구성하는 데 동일한 사용자 계정을 사용합니다. 그러나 서로 다른 계정을 사용하는 경우 두 계정 모두 AzInfoProtectionScanner 데이터베이스에 대한 db_owner 역할이 필요합니다.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>제한: 스캐너의 서비스 계정에 **로컬 로그온** 권한을 부여할 수 없습니다.

조직 정책에 따라 서비스 계정에 대해 **로컬 로그온** 권한이 금지되어 있지만, **일괄 작업으로 로그온** 권한이 허용되는 경우 관리자 가이드의 [Set-AIPAuthentication에 토큰 매개 변수 지정 및 사용](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)에 나와 있는 지침을 따릅니다.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>제한: 스캐너 서비스 계정을 Azure Active Directory와 동기화할 수 없지만, 서버에서 인터넷에 연결할 수 있습니다.

다음과 같이 한 계정을 사용하여 스캐너 서비스를 실행하고 다른 계정을 사용하여 Azure Active Directory에 인증할 수 있습니다.

- 스캐너 서비스 계정의 경우 로컬 Windows 계정 또는 Active Directory 계정을 사용할 수 있습니다.

- Azure Active Directory 계정의 경우 관리자 가이드의 [Set-AIPAuthentication에 토큰 매개 변수 지정 및 사용](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)에 나와 있는 지침을 따릅니다.


## <a name="install-the-scanner"></a>스캐너 설치

1. 스캐너를 실행하는 Windows Server 컴퓨터에 로그인합니다. 로컬 관리자 권한이 있고 SQL Server 마스터 데이터베이스에 쓸 수 있는 권한이 있는 계정을 사용합니다.

2. **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell 세션을 엽니다.

3. [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) cmdlet을 실행하여 Azure Information Protection 스캐너에 대한 데이터베이스를 만들 SQL Server 인스턴스를 지정합니다. 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    예:
    
    기본 인스턴스의 경우: `Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    명명된 인스턴스의 경우: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    SQL Server Express의 경우: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`
    
    [자세한 예제](/powershell/module/azureinformationprotection/install-aipscanner#examples)가 더 필요할 경우 이 cmdlet에 대한 온라인 도움말을 사용하세요.
    
    메시지가 표시되는 경우 스캐너 서비스 계정(\<domain\user name>) 및 암호에 대한 자격 증명을 입력합니다.

4. **관리 도구** > **서비스**를 사용하여 서비스가 현재 설치되어 있는지 확인합니다. 
    
    설치된 서비스는 **Azure Information Protection 스캐너**이며 만든 스캐너 서비스 계정을 사용하여 실행되도록 구성되어 있습니다.

이제 스캐너를 설치했으므로 스캐너 서비스 계정에 Azure AD 토큰을 가져와서 무인 모드로 실행될 수 있도록 인증합니다. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>스캐너에 대한 Azure AD 토큰 가져오기

Azure AD 토큰을 사용하면 스캐너 서비스 계정으로 Azure Information Protection 서비스에 인증할 수 있습니다.

1. 동일한 Windows Server 컴퓨터 또는 데스크톱에서 Azure Portal에 로그인하여 인증을 위해 액세스 토큰을 지정하는 데 필요한 두 개의 Azure AD 응용 프로그램을 만듭니다. 초기 대화형 로그인 후에 이 토큰을 통해 스캐너를 비대화형으로 실행할 수 있습니다.
    
    이러한 응용 프로그램을 만들려면 관리자 가이드에서 [Azure Information Protection에서 비대화형으로 파일의 레이블을 지정하는 방법](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)에서 지침에 따릅니다.

2. Windows Server 컴퓨터에서 사용 중인 스캐너 서비스 계정에 설치를 위한 **로컬로 로그온** 권한이 부여된 경우 이 계정으로 로그인하고 PowerShell 세션을 시작합니다. [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)을 실행하고 이전 단계에서 복사한 값을 지정합니다.
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    메시지가 나타나면 Azure AD의 서비스 계정 자격 증명에 대한 암호를 지정하고 **허용**을 클릭합니다.
    
    스캐너 서비스 계정에 설치를 위한 **로컬로 로그온** 권한을 부여할 수 없는 경우에는 관리자 가이드의 [Set-AIPAuthentication에 대한 토큰 매개 변수 지정 및 사용](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) 섹션의 지침을 따릅니다. 

이제 스캐너에는 Azure AD에 인증한 토큰이 있습니다. 이 토큰은 Azure AD에서 **웹앱/API**의 구성에 따라 1년, 2년 동안 유효하거나 만료되지 않게 됩니다. 토큰이 만료되면 1단계와 2단계를 반복해야 합니다.

이제 검색할 데이터 저장소를 지정할 준비가 되었습니다. 

## <a name="specify-data-stores-for-the-scanner"></a>스캐너에 대한 데이터 저장소 지정

[Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository) cmdlet을 사용하여 Azure Information Protection 스캐너에서 검색할 데이터 저장소를 지정합니다. SharePoint 사이트 및 라이브러리에 대한 로컬 폴더, UNC 경로 및 SharePoint 서버 URL을 지정할 수 있습니다. 

SharePoint에 지원되는 버전: SharePoint Server 2016 및 SharePoint Server 2013 [이 버전의 SharePoint에 대한 지원을 확장](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010)한 고객의 경우 SharePoint Server 2010도 지원됩니다.

1. 동일한 Windows Server 컴퓨터의 PowerShell 세션에서 다음 명령을 실행하여 첫 번째 데이터 저장소를 추가합니다.
    
        Add-AIPScannerRepository -Path <path>
    
    예를 들어 `Add-AIPScannerRepository -Path \\NAS\Documents`를 구성할 수 있습니다.
    
    다른 예제는 이 cmdlet에 대한 [온라인 도움말](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples)을 참조하세요.

2. 검색하려는 모든 데이터 저장소에 이 명령을 반복합니다. 추가한 데이터 저장소를 제거해야 하는 경우 [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository) cmdlet을 사용합니다.

3. [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository) cmdlet을 실행하여 올바르게 모든 데이터 저장소를 지정했는지 확인합니다.
    
        Get-AIPScannerRepository

스캐너의 기본 구성에서 이제 검색 모드에서 첫 번째 검색을 실행할 준비가 되었습니다.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>스캐너에 대한 검색 주기 실행 및 보고서 보기

1. PowerShell 세션에서 다음 명령을 실행하여 **Azure Information Protection 검사기** 서비스를 다시 시작합니다.
    
        Start-AIPScan

2. 스캐너가 해당 주기를 완료할 때까지 기다립니다. 스캐너가 지정한 데이터 저장소에서 모든 파일을 크롤링하면 스캐너 서비스가 실행 중이더라도 서비스가 중지됩니다. 로컬 Windows **응용 프로그램 및 서비스** 이벤트 로그, **Azure Information Protection**을 사용하여 스캐너가 중지된 시점을 확인할 수 있습니다. 정보 이벤트 ID **911**을 찾아봅니다.

3. %*localappdata*%\Microsoft\MSIP\Scanner\Reports에 저장되고 .csv 파일 형식인 보고서를 검토합니다. 스캐너의 기본 구성에서 자동 분류에 대한 조건을 충족하는 파일만이 이러한 보고서에 포함됩니다.
    
    > [!TIP]
    > 현재 미리 보기에서 이러한 보고서의 정보는 Azure Information Protection으로 전송되므로 Azure Portal에서 볼 수 있습니다. 자세한 내용은 [Azure Information Protection의 보고](reports-aip.md)를 참조하세요. 
        
    예상 대로 결과가 발생하지 않는 경우 Azure Information Protection 정책에서 지정한 조건을 세밀하게 조정해야 합니다. 이러한 경우 분류 및 필요에 따라 보호를 적용하도록 구성을 변경할 준비가 될 때까지 1~3단계를 반복합니다. 

스캐너가 검색하는 파일에 레이블을 자동으로 지정할 준비가 되면 다음 절차를 계속합니다. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>스캐너를 구성하여 분류 및 보호 적용

기본 설정에서 스캐너는 보고 전용 모드로 한 번 실행됩니다. 이러한 설정을 변경하려면 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet을 실행합니다.

1. Windows Server 컴퓨터의 PowerShell 세션에서 다음 명령을 실행합니다.
    
        Set-AIPScannerConfiguration -Enforce On -Schedule Always
    
    다른 구성 설정을 변경하려는 경우가 있습니다. 예를 들어 파일 특성의 변경 여부 및 보고서에 기록된 내용을 변경하려고 합니다. 또한 Azure Information Protection 정책에 분류 수준을 낮추거나 보호를 제거하라는 근거 메시지가 필요한 설정을 포함하는 경우 이 cmdlet을 사용하여 해당 메시지를 지정합니다. 각 구성 설정에 대한 자세한 내용은 [온라인 도움말](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters)을 사용합니다. 

2. 다음 명령을 실행하여 **Azure Information Protection 검사기** 서비스를 다시 시작합니다.
    
        Start-AIPScan

3. 이전처럼 이벤트 로그 및 보고서를 모니터링하여 레이블이 지정된 파일, 적용된 분류 및 보호 적용 여부를 확인합니다.

일정을 계속해서 실행하도록 구성했기 때문에 스캐너가 모든 파일을 사용할 때 새롭게 변경된 파일이 검색되도록 새 주기를 시작합니다.


## <a name="how-files-are-scanned"></a>파일 검사 방법

스캐너는 [분류 및 보호에서 제외](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)된 파일(예: 실행 파일 및 시스템 파일)을 자동으로 건너뜁니다.

검색할 파일 형식 목록을 정의하여 이 동작을 변경하거나 검색에서 제외할 수 있습니다. 이 목록을 지정하고 데이터 리포지토리를 지정하지 않으면 지정된 자체 목록이 없는 모든 데이터 리포지토리에 이 목록이 적용됩니다. 이 목록을 지정하려면 [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)를 사용합니다. 파일 형식 목록을 지정한 후 [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)를 사용하여 새 파일 형식을 목록에 추가하고 [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes)를 사용하여 목록에서 파일 형식을 제거할 수 있습니다.

그런 다음, 스캐너는 Windows iFilter를 사용하여 다음 파일 형식을 검색합니다. 이러한 파일 형식에 대해 레이블에 지정한 조건을 사용하여 문서의 레이블을 지정합니다.

|응용 프로그램 유형|파일 형식|
|--------------------------------|-------------------------------------|
|Word|.docx; .docm; .dotm; .dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |.pdf|
|텍스트|.txt; .xml; .csv|

기본적으로 Office 파일 형식만 스캐너에서 보호되므로 [레지스트리를 편집](#editing-the-registry-for-the-scanner)하여 파일 형식을 지정하지 않는 경우 PDF 및 텍스트 파일은 보호되지 않습니다.

- 레지스트리에 .pdf 파일 형식을 추가하지 않는 경우: 이 파일 이름 확장명의 파일은 레이블이 지정되지만 이 레이블이 보호되도록 구성된 경우 보호가 적용되지 않습니다.

- 레지스트리에 .txt, .xml 또는 .csv 파일 형식을 추가하지 않는 경우: 이러한 파일 형식에서 분류 전용을 지원하지 않으므로 이러한 파일 이름 확장명의 파일은 레이블이 지정되지 않습니다.

마지막으로 나머지 파일 형식의 경우 스캐너는 Azure Information Protection 정책의 기본 레이블 또는 스캐너에 대해 구성한 기본 레이블을 적용합니다.

|응용 프로그램 유형|파일 형식|
|--------------------------------|-------------------------------------|
|프로젝트|.mpp; .mpt|
|게시자|.pub|
|Visio|.vsd; .vdw; .vst; .vss; .vsdx; .vsdm; .vssx; .vssm; .vstx; .vstm|
|XPS|.xps; .oxps; .dwfx|
|Solidworks|.sldprt; .slddrw; .sldasm|
|Jpeg |.jpg; .jpeg; .jpe; .jif; .jfif; .jfi|
|Png |.png|
|Gif|.gif|
|비트맵|.bmp; .giff|
|Tiff|.tif; .tiff|
|Photoshop|.psdv|
|DigitalNegative|.dng|
|Pfile|.pfile|

스캐너에서 보호를 사용하는 레이블을 적용하는 경우 기본적으로 Office 파일 형식만 보호됩니다. 추가 파일 형식이 보호되도록 이 동작을 변경할 수 있습니다. 그러나 레이블이 문서에 일반 보호를 적용하는 경우 파일 이름 확장명을 .pfile로 변경합니다. 다른 파일 유형은 파일 이름 확장명도 변경할 수 있습니다. 또한 이러한 파일은 권한이 있는 사용자가 열어 원시 형식으로 저장할 때까지 읽기 전용 상태입니다.

### <a name="editing-the-registry-for-the-scanner"></a>스캐너의 레지스트리 편집

Office 파일 이외의 파일 유형을 보호하기 위한 기본 스캐너 동작을 변경하려면 레지스트리를 수동으로 편집하고 보호할 추가 파일 형식을 지정해야 합니다. 자세한 내용은 개발자 지침의 [파일 API 구성](develop/file-api-configuration.md)을 참조하세요. 개발자를 위한 이 설명서에서는 일반 보호를 "PFile"이라고 합니다. 또한 스캐너에만 한정되는 사항은 다음과 같습니다.

- 스캐너에는 고유한 기본 동작이 있습니다. 즉, 기본적으로 Office 파일 형식만 보호됩니다. 레지스트리가 수정되지 않은 경우, 다른 파일 형식은 스캐너에서 보호되지 않습니다.

- 모든 파일이 기본 또는 일반 보호로 자동 보호되는 경우 Azure Information Protection 클라이언트와 동일한 기본 보호 동작이 필요하면 `*` 와일드카드를 레지스트리 키로, `Default`를 값 데이터로 지정합니다.

레지스트리를 편집할 때 **MSIPC** 키와 **FileProtection** 키가 없으면 수동으로 생성하고 각 파일 이름 확장명에 대한 키도 생성합니다.

예를 들어 스캐너가 Office 파일 이외에 PDF 파일을 보호하려면 편집 후 레지스트리의 모양이 다음 그림과 같아야 합니다.

![스캐너가 보호를 적용할 수 있도록 레지스트리 편집](./media/editregistry-scanner.png)

## <a name="when-files-are-rescanned"></a>파일이 다시 검사되는 경우

첫 번째 검사 주기에서는 스캐너에서 구성된 데이터 저장소의 모든 파일을 검사한 다음, 후속 검사에서는 새롭거나 수정된 파일만 검사합니다. 

`-Reset` 매개 변수와 함께 [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)을 실행하여 강제로 검사 기능이 모든 파일을 다시 검사하도록 할 수 있습니다. 수동 일정에 대해 스캐너를 구성해야 합니다. 그러려면 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)을 사용하여 `-Schedule` 매개 변수를 **수동**으로 설정해야 합니다.

모든 파일을 다시 검사하는 작업은 보고서에 모든 파일이 포함되도록 하려는 경우에 유용하며, 이 구성은 일반적으로 스캐너가 검색 모드로 실행될 때 사용됩니다. 전체 검사가 완료되면 검사 유형이 증분 방식으로 자동으로 변경되어 후속 검사에서 새롭거나 수정된 파일만 검사됩니다.

또한 스캐너에서 새롭거나 변경된 조건이 있는 Azure Information Protection 정책을 다운로드할 때에도 모든 파일이 검사됩니다. 스캐너는 서비스를 시작할 때, 정책이 1시간보다 오래되었을 때 및 매시간 정책을 새로 고칩니다.  

> [!TIP]
> 이 1시간 간격보다 더 자주 정책을 새로 고쳐야 하는 경우(예: 테스트 기간 동안) **%LocalAppData%\Microsoft\MSIP\Policy.msip** 및 **%LocalAppData%\Microsoft\MSIP\Scanner** 모두에서 정책 파일 **Policy.msip**를 수동으로 삭제합니다. 그런 다음, Azure Information Scanner 서비스를 다시 시작합니다.
> 
> 정책에서 보호 설정을 변경한 경우 서비스를 다시 시작하기 전에 보호 설정을 저장한 후 15분 동안 기다립니다.

구성된 자동 조건이 없는 정책을 스캐너가 다운로드하면 스캐너 폴더에서 정책 파일의 복사본이 업데이트되지 않습니다. 이 시나리오에서 레이블이 자동 조건에 대해 올바르게 구성되어 있는 새로 다운로드한 정책 파일을 스캐너에서 사용할 수 있으려면 **%LocalAppData%\Microsoft\MSIP\Policy.msip** 및 **%LocalAppData%\Microsoft\MSIP\Scanner** 모두에서 정책 파일 **Policy.msip**를 삭제해야 합니다.

## <a name="using-the-scanner-with-alternative-configurations"></a>대체 구성으로 스캐너 사용

Azure Information Protection 스캐너에서 지원하는 다음 두 가지 대체 시나리오에서는 어떤 조건에도 레이블을 구성할 필요가 없습니다. 

- 데이터 리포지토리의 모든 파일에 기본 레이블을 적용합니다.
    
    이 구성에서는 [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository) cmdlet을 사용하여 *MatchPolicy* 매개 변수를 **Off**로 설정합니다. 
    
    파일 콘텐츠는 검사되지 않고 데이터 리포지토리의 모든 파일에는 데이터 리포지토리에 대해 지정한 기본 레이블(*SetDefaultLabel* 매개 변수 사용) 또는 기본 레이블이 지정되지 않은 경우에는 스캐너 계정에 대한 정책 설정으로 지정된 기본 레이블에 따라 레이블이 지정됩니다.
    

- 모든 사용자 지정 조건 및 알려진 중요한 정보 유형을 식별합니다.
    
    이 구성에서는 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet을 사용하여 *DiscoverInformationTypes* 매개 변수를 **All**로 설정합니다.
    
    스캐너는 Azure Information Protection 정책의 레이블에 대해 지정한 모든 사용자 지정 조건과 Azure Information Protection 정책의 레이블에 대해 지정할 수 있는 정보 유형 목록을 사용합니다. 

## <a name="optimizing-the-performance-of-the-scanner"></a>스캐너 성능 최적화

스캐너 성능을 최대화하려면:

- **스캐너 컴퓨터와 스캔 대상 데이터 저장소 간에 안정적인 고속 네트워크 연결 확보**
    
    예를 들어 스캐너 컴퓨터를 스캔 대상 데이터 저장소와 동일한 LAN 또는 동일한 네트워크 세그먼트(권장)에 배치합니다.
    
    스캐너는 파일을 검사하기 위해 스캐너 서비스를 실행하는 컴퓨터로 파일의 내용을 전송하기 때문에 네트워크 연결 품질은 스캐너 성능에 영향을 줍니다. 이 데이터가 이동해야 하는 네트워크 홉 수를 줄이거나 제거하는 경우에도 네트워크 로드가 줄어듭니다. 

- **스캐너 컴퓨터에 사용 가능한 프로세서 리소스가 있는지 확인**
    
    파일 내용 중에 구성된 조건과 일치하는 항목이 있는지 검사하고, 파일을 암호화하고 암호를 해독하는 것은 프로세스 집약적 작업입니다. 지정된 데이터 저장소의 일반적인 스캔 주기를 모니터링하여 프로세서 리소스 부족으로 인해 스캐너 성능에 부정적인 영향이 있는지 확인하세요.
    
- **스캐너 서비스를 실행 중인 컴퓨터의 로컬 폴더 스캔 안 함**
    
    Windows 서버에 스캔할 폴더가 있을 경우 다른 컴퓨터에 스캐너를 설치하고 해당 폴더를 스캔할 네트워크 공유로 구성합니다. 파일 호스팅 기능과 파일 스캔 기능을 구분하면 이러한 서비스의 컴퓨팅 리소스가 다른 서비스와 경쟁하지 않습니다.

필요한 경우 이 스캐너의 다중 인스턴스를 설치하세요. 스캐너 각 스캐너 인스턴스에는 SQL Server 인스턴스가 다른 고유한 구성 데이터베이스가 필요합니다.

스캐너 성능에 영향을 주는 다른 요소:

- 스캔할 파일이 포함된 데이터 저장소의 현재 로드 및 응답 시간

- 스캐너 실행 모드(검색 모드 또는 강제 적용 모드)
    
    검색에는 단일 파일 읽기 작업이 필요한 반면 강제 적용 모드에는 읽기 및 쓰기 작업이 필요하므로 검색 모드는 일반적으로 강제 적용 모드보다 스캔 속도가 더 빠릅니다.

- Azure Information Protection의 조건 변경
    
    스캐너가 모든 파일을 검사해야 하는 첫 번째 검색 주기는 기본적으로 새로 추가되거나 변경된 파일만 검사하는 후속 스캔 주기보다 분명히 더 오래 걸립니다. 그러나 Azure Information Protection 정책의 조건을 변경하면 [이전 섹션](#when-files-are-rescanned-by-the-azure-information-protection-scanner)에 설명된 것처럼 모든 파일이 다시 스캔됩니다.

- 선택한 로깅 수준
    
    스캐너 보고서에 대해 **디버그**, **정보**, **오류** 및 **끄기** 중에서 선택할 수 있습니다. **끄기**는 최상의 성능을 가져다 줍니다. **디버그**는 스캐너 속도를 상당히 저하시키며 문제 해결용으로만 사용해야 합니다. 자세한 내용은 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet의 *ReportLevel* 매개 변수를 참조하세요.

- 파일 자체:
    
    - Office 파일은 PDF 파일보다 더 빠르게 스캔됩니다.
    
    - 보호되지 않는 파일은 보호되는 파일보다 더 빠르게 스캔됩니다.
    
    - 큰 파일은 작은 파일보다 분명히 스캔하는 데 더 오랜 시간이 걸립니다.

- 추가 필수 구성 요소:
    
    - 스캐너를 실행하는 서비스 계정에 [스캐너 필수 구성 요소](#prerequisites-for-the-azure-information-protection-scanner) 섹션에 설명된 권한만 있는지 확인한 다음, 스캐너에 대해 낮은 무결성 수준을 사용하지 않도록 [고급 클라이언트 속성](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner)을 구성합니다.
    
    - 스캐너는 파일 콘텐츠를 검사하지 않으므로 [대체 구성](#using-the-scanner-with-alternative-configurations)을 사용하여 기본 레이블을 모든 파일에 적용하면 스캐너가 더 빠르게 실행됩니다.
    
    - [대체 구성](#using-the-scanner-with-alternative-configurations)을 사용하여 모든 사용자 지정 조건 및 알려진 중요한 정보 유형을 식별하면 스캐너가 더 느리게 실행됩니다.
    

## <a name="list-of-cmdlets-for-the-scanner"></a>스캐너에 대한 cmdlet 목록 

스캐너의 다른 cmdlet을 사용하여 스캐너의 서비스 계정과 데이터베이스를 변경하고, 스캐너의 현재 설정을 가져오고, 스캐너 서비스를 제거할 수 있습니다. 스캐너는 다음 cmdlet을 사용합니다.

- [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>스캐너에 대한 이벤트 로그 ID 및 설명

다음 섹션을 사용하여 스캐너에 가능한 이벤트 ID 및 설명을 식별합니다. Windows **응용 프로그램 및 서비스** 이벤트 로그 및 **Azure Information Protection**에서 스캐너 서비스를 실행하는 서버에서 이러한 이벤트를 기록합니다.

-----

정보 **910**

**스캐너 주기가 시작되었습니다.**

이 이벤트는 스캐너 서비스가 시작될 때 기록되어 사용자가 지정한 데이터 저장소에서 파일을 검색하기 시작합니다.

----

정보 **911**

**스캐너 주기가 완료되었습니다.**

서버가 시작된 후 스캐너가 일회성 검색을 완료하거나 스캐너가 연속 일정에 대한 주기를 완료할 때 이 이벤트가 기록됩니다.

스캐너가 연속적이지 않고 한 번 실행되도록 구성된 경우 파일을 다시 검색하려면 일정을 **일회성** 또는 **연속**으로 설정한 후 서비스를 수동으로 다시 시작해야 합니다. 일정을 변경하려면 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet 및 **일정** 매개 변수를 사용합니다.

----

## <a name="next-steps"></a>다음 단계

[Windows Server FCI와 Azure Information Protection 스캐너의 차이점은 무엇인가요?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner) 확인

PowerShell을 사용하여 데스크톱 컴퓨터의 파일을 대화형으로 분류하고 보호할 수도 있습니다. PowerShell을 사용하는 시나리오에 대한 자세한 내용은 [Azure Information Protection 클라이언트에서 PowerShell 사용](./rms-client/client-admin-guide-powershell.md)을 참조하세요.


