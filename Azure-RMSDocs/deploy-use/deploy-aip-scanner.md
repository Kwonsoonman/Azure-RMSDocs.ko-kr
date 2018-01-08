---
title: "Azure Information Protection 스캐너 배포"
description: "Azure Information Protection 스캐너를 설치, 구성 및 실행하여 데이터 저장소에서 파일을 검색, 분류 및 보호하는 지침입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 7dfd670df89b652f8ff55452198d8483b55c59cd
ms.sourcegitcommit: 2a7f20684a041385e2d2425ab886e46917d2da9a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/03/2018
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Azure Information Protection 스캐너를 배포하여 파일 자동으로 분류 및 보호

>*적용 대상: Azure Information Protection, Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> 이 기능은 현재 미리 보기 상태이며 변경될 예정입니다.

이 정보를 사용하여 Azure Information Protection 스캐너에 대한 정보 및 성공적으로 설치, 구성 및 실행하는 방법을 알아봅니다. 

이 스캐너는 Windows Server에서 서비스로 실행되고 해당 스캐너를 통해 다음 데이터 저장소에서 파일을 검색, 분류 및 보호할 수 있습니다.

- 스캐너를 실행하는 Windows Server 컴퓨터의 로컬 폴더

- CIFS(Common Internet File System) 프로토콜을 사용하는 네트워크 공유를 위한 UNC 경로

- SharePoint Server 2016 및 SharePoint Server 2013의 사이트 및 라이브러리

## <a name="overview-of-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너 개요

자동 분류를 적용하는 레이블에 [Azure Information Protection 정책](configure-policy.md)을 구성한 경우 이 스캐너를 검색하는 파일은 레이블이 지정될 수 있습니다. 레이블은 분류를 적용하고 필요에 따라 보호를 적용하거나 제거합니다.

![Azure Information Protection 스캐너 개요](../media/infoprotect-scanner.png)

스캐너는 컴퓨터에 설치된 iFilters를 사용하여 Windows에서 인덱싱하는 파일을 검사할 수 있습니다. 그런 다음, 파일에 레이블을 지정해야 하는지를 결정하려면 스캐너는 Office 365 기본 제공 DLP(데이터 손실 방지) 민감도 정보 유형 및 패턴 감지 또는 Office 365 정규식 패턴을 사용합니다. 스캐너가 Azure Information Protection 클라이언트를 사용하기 때문에 동일한 [파일 형식](../rms-client/client-admin-guide-file-types.md)을 분류하고 보호할 수 있습니다.

스캐너를 검색 모드에서만 실행할 수 있습니다. 여기서는 보고서를 사용하여 파일에 레이블을 적용했을 때 발생한 결과를 확인합니다. 또는 스캐너를 실행하여 레이블을 자동으로 적용할 수 있습니다.

스캐너는 실시간으로 검색하고 레이블을 지정하지 않습니다. 지정한 데이터 저장소의 파일을 체계적으로 크롤링하여 이 주기를 한 번 또는 반복적으로 실행되도록 구성할 수 있습니다.

## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너의 필수 구성 요소
Azure Information Protection 스캐너를 설치하기 전에 다음 요구 사항이 설정되어 있는지 확인하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|스캐너 서비스를 실행할 Windows Server 컴퓨터:<br /><br />- 4개 프로세서<br /><br />- 4GB RAM|Windows Server 2016 또는 Windows Server 2012 R2 <br /><br />참고: 비-프로덕션 환경에서 테스트 또는 평가는 [Azure Information Protection 클라이언트에서 지원하는](../get-started/requirements.md#client-devices) Windows 클라이언트 운영 체제를 사용할 수 있습니다.<br /><br />이 컴퓨터는 검색할 데이터 저장소에 안정적인 고속 네트워크를 연결한 실제 또는 가상 컴퓨터일 수 있습니다. <br /><br />이 컴퓨터가 Azure Information Protection에 필요한 [인터넷이 연결](../get-started/requirements.md#firewalls-and-network-infrastructure)되어 있는지 확인합니다. 또는 [연결이 끊어진 컴퓨터](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers)로 구성해야 합니다. |
|스캐너 구성을 저장할 SQL Server:<br /><br />- 로컬 또는 원격 인스턴스|SQL Server 2012는 다음 버전의 최소 버전입니다.<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express|
|스캐너 서비스를 실행할 서비스 계정|이 계정은 다음과 같은 추가 요구 사항을 포함하여 Azure AD에 동기화된 Active Directory 계정이어야 합니다.<br /><br />- **로컬 로그온** 권한 이 권한은 스캐너를 설치하고 구성하는 데 필요하지만 작동하는 데는 필요하지 않습니다. 서비스 계정에 이 권한을 부여해야 하지만 스캐너가 파일을 검색, 분류 및 보호하는지 확인한 후에 이 권한을 제거할 수 있습니다.<br /><br />- **서비스로 로그온** 권한 스캐너 설치 중에 서비스 계정에 이 권한이 자동으로 부여됩니다. 이 권한은 스캐너의 설치, 구성 및 작동에 필요합니다. <br /><br />- 데이터 리포지토리에 대한 사용 권한: Azure Information Protection 정책에서 파일을 검색한 다음 조건을 충족하는 파일에 분류 및 보호를 적용하는 **읽기** 및 **쓰기** 권한을 부여해야 합니다. 검색 모드 전용으로 스캐너를 실행하려면 **읽기** 권한으로 충분합니다.<br /><br />- 다시 보호하거나 보호를 제거하는 레이블의 경우: 스캐너가 항상 보호된 파일에 액세스할 수 있도록 하려면 이 계정을 Azure Rights Management 서비스에 대한 [슈퍼 사용자](configure-super-users.md)로 지정하고 슈퍼 사용자 기능을 사용하도록 합니다. 보호를 적용하기 위한 계정 요구 사항에 대한 자세한 내용은 [Azure Information Protection을 위한 사용자 및 그룹 준비](../plan-design/prepare.md)를 참조하세요.|
|Azure Information Protection 클라이언트가 Windows Server 컴퓨터에 설치되었습니다.|현재 Azure Information Protection 스캐너에는 Azure Information Protection 클라이언트의 미리 보기 버전이 필요합니다.<br /><br />스캐너를 위해 전체 클라이언트를 설치해야 합니다. PowerShell 모듈만으로 클라이언트를 설치하지 마세요.<br /><br />클라이언트 설치 지침은 [관리자 가이드](../rms-client/client-admin-guide.md)를 참조하세요.|
|자동 분류 및 필요에 따라 보호를 적용하는 구성된 레이블|조건을 구성하는 방법에 대한 자세한 내용은 [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](configure-policy-classification.md)을 참조하세요.<br /><br />파일에 보호를 적용하도록 레이블을 구성하는 방법에 대한 자세한 내용은 [Rights Management 보호를 위한 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요.<br /><br />이러한 레이블은 전역 정책 또는 하나 이상의 [범위 지정 정책](configure-policy-scope.md)에 있을 수 있습니다.|


## <a name="install-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너 설치

1. 스캐너를 실행하기 위해 만든 서비스 계정을 사용하여 스캐너를 실행하는 Windows Server 컴퓨터에 로그인합니다.

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

## <a name="get-an-azure-ad-token-for-the-scanner-service-account-to-authenticate-to-the-azure-information-protection-service"></a>스캐너 서비스 계정에 Azure AD 토큰을 가져와서 Azure Information Protection 서비스에 인증

1. 동일한 Windows Server 컴퓨터 또는 데스크톱에서 Azure Portal에 로그인하여 인증을 위해 액세스 토큰을 지정하는 데 필요한 두 개의 Azure AD 응용 프로그램을 만듭니다. 초기 대화형 로그인 후에 이 토큰을 통해 스캐너를 비대화형으로 실행할 수 있습니다.
    
    이러한 응용 프로그램을 만들려면 관리자 가이드에서 [Azure Information Protection에서 비대화형으로 파일의 레이블을 지정하는 방법](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)에서 지침에 따릅니다.

2. Windows Server 컴퓨터에서 스캐너 서비스 계정을 사용하여 로그인했다면 [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)을 실행하여 이전 단계에서 복사한 값을 지정합니다.
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application>  -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application >
    ```

3. 메시지가 나타나면 Azure AD의 서비스 계정 자격 증명에 대한 암호를 지정하고 **허용**을 클릭합니다.

이제 스캐너에는 Azure AD에 인증한 토큰이 있습니다. 이 토큰은 Azure AD에서 **웹앱/API**의 구성에 따라 1년, 2년 동안 유효하거나 만료되지 않게 됩니다. 토큰이 만료되면 1~3단계를 반복해야 합니다.

이제 검색할 데이터 저장소를 지정할 준비가 되었습니다. 

## <a name="specify-data-stores-for-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너의 데이터 저장소 지정

[Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository) cmdlet을 사용하여 Azure Information Protection 스캐너에서 검색할 데이터 저장소를 지정합니다. SharePoint 사이트 및 라이브러리에 대한 로컬 폴더, UNC 경로 및 SharePoint 서버 URL을 지정할 수 있습니다. 

SharePoint에 지원되는 버전: SharePoint Server 2016 및 SharePoint Server 2013

1. 동일한 Windows Server 컴퓨터의 PowerShell 세션에서 다음 명령을 실행하여 첫 번째 데이터 저장소를 추가합니다.
    
        Add-AIPScannerRepository -Path <path>
    
    예를 들어 `Add-AIPScannerRepository -Path \\NAS\Documents`를 구성할 수 있습니다.
    
    다른 예제는 이 cmdlet에 대한 [온라인 도움말](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples)을 참조하세요.

2. 검색하려는 모든 데이터 저장소에 이 명령을 반복합니다. 추가한 데이터 저장소를 제거해야 하는 경우 [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository) cmdlet을 사용합니다.

3. [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository) cmdlet을 실행하여 올바르게 모든 데이터 저장소를 지정했는지 확인합니다.
    
        Get-AIPScannerRepository

스캐너의 기본 구성에서 이제 검색 모드에서 첫 번째 검색을 실행할 준비가 되었습니다.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-azure-information-protection-scanner"></a>검색 주기 실행 및 Azure Information Protection 스캐너에 대한 보고서 보기

1. **관리 도구** > **서비스**를 사용하여 **Azure Information Protection 스캐너** 서비스를 시작합니다.

2. 스캐너가 해당 주기를 완료할 때까지 기다립니다. 스캐너가 지정한 데이터 저장소에서 모든 파일을 크롤링하면 서비스가 중지됩니다. 로컬 Windows **응용 프로그램 및 서비스** 이벤트 로그, **Azure Information Protection**을 사용하여 서비스가 중지된 시기를 확인할 수 있습니다. 정보 이벤트 ID **911**을 찾아봅니다.

3. %*localappdata*%\Microsoft\MSIP\Scanner\Reports에 저장되고 .csv 파일 형식인 보고서를 검토합니다. 스캐너의 기본 구성에서 자동 분류에 대한 조건을 충족하는 파일만이 이러한 보고서에 포함됩니다.
    
    예상 대로 결과가 발생하지 않는 경우 Azure Information Protection 정책에서 지정한 조건을 세밀하게 조정해야 합니다. 이러한 경우 분류 및 필요에 따라 보호를 적용하도록 구성을 변경할 준비가 될 때까지 1~3단계를 반복합니다. 이러한 단계를 반복할 때마다 Windows Server 컴퓨터에서 다음 PowerShell 명령을 먼저 실행합니다.
    
        Set-AIPScannerConfiguration -Schedule OneTime

스캐너가 검색하는 파일에 레이블을 자동으로 지정할 준비가 되면 다음 절차를 계속합니다. 

## <a name="configure-the-azure-information-protection-scanner-to-apply-classification-and-protection-to-discovered-files"></a>검색된 파일에 분류 및 보호를 적용하도록 Azure Information Protection 스캐너 구성

기본 설정에서 스캐너는 보고 전용 모드로 한 번 실행됩니다. 이러한 설정을 변경하려면 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet을 실행합니다.

1. Windows Server 컴퓨터의 PowerShell 세션에서 다음 명령을 실행합니다.
    
        Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
    
    다른 구성 설정을 변경하려는 경우가 있습니다. 예를 들어 파일 특성의 변경 여부 및 보고서에 기록된 내용을 변경하려고 합니다. 또한 Azure Information Protection 정책에 분류 수준을 낮추거나 보호를 제거하라는 근거 메시지가 필요한 설정을 포함하는 경우 이 cmdlet을 사용하여 해당 메시지를 지정합니다. 각 구성 설정에 대한 자세한 내용은 [온라인 도움말](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters)을 사용합니다. 

2. **관리 도구** > **서비스**를 사용하여 **Azure Information Protection 스캐너** 서비스를 다시 시작합니다.

3. 이전처럼 이벤트 로그 및 보고서를 모니터링하여 레이블이 지정된 파일, 적용된 분류 및 보호 적용 여부를 확인합니다.

일정을 계속해서 실행하도록 구성했기 때문에 스캐너가 모든 파일을 사용할 때 새롭게 변경된 파일이 검색되도록 새 주기를 시작합니다.

## <a name="when-files-are-rescanned-by-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너로 파일을 다시 검사하는 경우

첫 번째 검사 주기에서는 스캐너에서 구성된 데이터 저장소의 모든 파일을 검사한 다음, 후속 검사에서는 새롭거나 수정된 파일만 검사합니다. 

**Full**로 설정된 `-Type` 매개 변수와 함께 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)을 실행하여 스캐너에서 모든 파일을 다시 검사하도록 강제할 수 있습니다. 이 구성은 보고서에 모든 파일이 포함되도록 하려는 경우에 유용하며, 일반적으로 스캐너가 검색 모드로 실행될 때 사용됩니다. 전체 검사가 완료되면 검사 유형이 증분 방식으로 자동으로 변경되어 후속 검사에서 새롭거나 수정된 파일만 검사됩니다.

또한 스캐너에서 새롭거나 변경된 조건이 있는 Azure Information Protection 정책을 다운로드할 때에도 모든 파일이 검사됩니다. 스캐너는 서비스 시작 시 및 매시간 정책을 새로 고칩니다.

## <a name="optimizing-the-performance-of-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너 성능 최적화

스캐너 성능을 최대화하려면:

- **스캐너 컴퓨터와 스캔 대상 데이터 저장소 간에 안정적인 고속 네트워크 연결 확보**
    
    예를 들어 스캐너 컴퓨터를 스캔 대상 데이터 저장소와 동일한 LAN 또는 동일한 네트워크 세그먼트(권장)에 배치합니다.
    
    스캐너는 파일을 검사하기 위해 스캐너 서비스를 실행하는 컴퓨터로 파일의 내용을 전송하기 때문에 네트워크 연결 품질은 스캐너 성능에 영향을 줍니다. 이 데이터가 이동해야 하는 네트워크 홉 수를 줄이거나 제거하는 경우에도 네트워크 로드가 줄어듭니다. 

- **스캐너 컴퓨터에 사용 가능한 프로세서 리소스가 있는지 확인**
    
    파일 내용 중에 구성된 조건과 일치하는 항목이 있는지 검사하고, 파일을 암호화하고 암호를 해독하는 것은 프로세스 집약적 작업입니다. 지정된 데이터 저장소의 일반적인 스캔 주기를 모니터링하여 프로세서 리소스 부족으로 인해 스캐너 성능에 부정적인 영향이 있는지 확인하세요.
    
- **스캐너 서비스를 실행 중인 컴퓨터의 로컬 폴더 스캔 안 함**
    
    Windows 서버에 스캔할 폴더가 있을 경우 다른 컴퓨터에 스캐너를 설치하고 해당 폴더를 스캔할 네트워크 공유로 구성합니다. 파일 호스팅 기능과 파일 스캔 기능을 구분하면 이러한 서비스의 컴퓨팅 리소스가 다른 서비스와 경쟁하지 않습니다.

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

## <a name="list-of-cmdlets-for-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너의 cmdlet 목록 

스캐너의 다른 cmdlet을 사용하여 스캐너의 서비스 계정과 데이터베이스를 변경하고, 스캐너의 현재 설정을 가져오고, 스캐너 서비스를 제거할 수 있습니다. 스캐너는 다음 cmdlet을 사용합니다.

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)


## <a name="event-log-ids-and-descriptions"></a>이벤트 로그 ID 및 설명

다음 섹션을 사용하여 스캐너에 가능한 이벤트 ID 및 설명을 식별합니다. Windows **응용 프로그램 및 서비스** 이벤트 로그 및 **Azure Information Protection**에서 스캐너 서비스를 실행하는 서버에서 이러한 이벤트를 기록합니다.

-----

정보 **910**

**스캐너 주기가 시작되었습니다.**

이 이벤트는 스캐너 서비스가 시작될 때 기록되어 사용자가 지정한 데이터 저장소에서 파일을 검색하기 시작합니다.

----

정보 **911**

**스캐너 주기가 완료되었습니다.**

서버가 시작된 후 스캐너가 일회성 검색을 완료하거나 스캐너가 연속 일정에 대한 주기를 완료할 때 이 이벤트가 기록됩니다.

----

정보 **913**

**스캐너가 안 함으로 설정되어 있으므로 중지됩니다.**

스캐너를 지속적으로 실행하지 않고 한 번 실행하도록 구성하면 이 이벤트가 기록됩니다. Azure Information Protection 스캐너 서비스는 컴퓨터가 시작된 이후 수동으로 다시 시작되었습니다.  

파일을 다시 검색하려면 일정을 **일회성** 또는 **연속**으로 설정하고 서비스를 수동으로 다시 시작해야 합니다. 일정을 변경하려면 [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet 및 **일정** 매개 변수를 사용합니다.

----

오류 **912**

**알 수 없는 오류가 발생했습니다.**

자세한 내용은 %localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_YYYY_MM_DD_HH_MM.csv에 저장된 자세한 보고서에 기록됩니다.

이 이벤트가 지속적으로 기록되는 경우 [Microsoft 지원](../get-started/information-support.md#to-contact-microsoft-support)에 문의하세요. 

----

오류 **914**

**잘못된 구성으로 인해 서비스가 자동으로 중지되었습니다. 정책 파일이 누락되었거나 손상되었습니다.**

이 이벤트는 Azure Information Protection 클라이언트에 실행할 스캐너에 대한 올바른 정책 파일이 없을 때 기록됩니다.

Azure Information Protection 정책은 %localappdata%\Microsoft\MSIP에 저장되고 자동 분류를 적용하는 조건을 포함한 레이블로 구성되어야 합니다. 또는 기본 레이블에 대한 정책을 구성해야 합니다.

방화벽이 인터넷에 대한 필수 연결을 차단하지 않는지 확인합니다. 자세한 내용은 Azure Information Protection에 대한 [방화벽 및 네트워크 인프라](../get-started/requirements.md#firewalls-and-network-infrastructure) 요구 사항을 참조하세요. 인터넷에 연결되지 않으면 [연결되지 않은 컴퓨터](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers)를 지원하는 지침에 따릅니다.


## <a name="next-steps"></a>다음 단계

[Windows Server FCI와 Azure Information Protection 스캐너의 차이점은 무엇인가요?](../get-started/faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner) 확인

PowerShell을 사용하여 데스크톱 컴퓨터의 파일을 대화형으로 분류하고 보호할 수도 있습니다. PowerShell을 사용하는 시나리오에 대한 자세한 내용은 [Azure Information Protection 클라이언트에서 PowerShell 사용](../rms-client/client-admin-guide-powershell.md)을 참조하세요.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
