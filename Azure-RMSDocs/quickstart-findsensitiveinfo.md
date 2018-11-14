---
title: 빠른 시작 - Azure Information Protection 스캐너를 사용하여 온-프레미스에 저장된 파일에 있는 중요한 정보 찾기
description: Azure Information Protection 검사 기능을 사용하여 온-프레미스에 저장된 파일에 있는 중요한 정보를 찾습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: a69972ec4371c808b7a295bfc993a257e440d1e1
ms.sourcegitcommit: 227f54a8e90aa57d778ab60c646179c10e5edb44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51272400"
---
# <a name="quickstart-find-what-sensitive-information-you-have-in-files-stored-on-premises"></a>빠른 시작: 온-프레미스에 저장된 파일에 있는 중요한 정보 찾기

이 빠른 시작에서 Azure Information Protection 검사 기능을 설치 및 구성하여 온-프레미스 데이터 저장소에 저장된 파일에 있는 중요한 정보를 찾습니다. 예를 들어, 로컬 폴더, 네트워크 공유 또는 SharePoint Server의 파일에서 중요한 정보를 찾습니다. 

이 구성은 10분 이내에 완료할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 빠른 시작을 완료하려면 다음이 필요합니다.

1. Azure Information Protection 플랜 1 또는 플랜 2를 포함하는 구독.
    
    이러한 구독 중 하나라도 없으면 조직을 위해 [무료](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) 계정을 만들 수 있습니다.

2. Azure Information Protection 클라이언트가 컴퓨터에 설치되어 있습니다. 
    
    클라이언트를 설치하려면 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동한 후 Azure Information Protection 페이지에서 **AzInfoProtection.exe**를 다운로드합니다.
    
3. SQL Server Express도 컴퓨터에 설치되어 있습니다.
    
    이 SQL Server 버전이 아직 설치되지 않은 경우 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/sql-server/sql-server-editions-express)에서 다운로드한 후 기본 설치를 선택할 수 있습니다.

4. 도메인 계정이 Azure AD와 동기화되어 있습니다.

Azure Information Protection을 사용하기 위한 필수 구성 요소의 전체 목록을 보려면 [Azure Information Protection에 대한 요구 사항](requirements.md)을 참조하세요.

## <a name="prepare-a-test-folder-and-file"></a>테스트 폴더 및 파일 준비

초기 테스트에서 이 검사 기능이 작동하는지 확인하려면 다음을 수행합니다.

1. 컴퓨터에 로컬 폴더를 만듭니다. 예를 들어, 로컬 C 드라이브에 **TestScanner**를 만듭니다.

2. 해당 폴더에 텍스트 **4242-4242-4242-4242**(테스트용으로 알려진 신용 카드 번호)가 있는 Word 문서를 만든 후 저장합니다.

## <a name="install-the-scanner"></a>스캐너 설치

1. **관리자 권한으로 실행** 옵션을 사용하여 PowerShell 세션을 엽니다.

2. 다음 명령을 사용하고 고유한 컴퓨터 이름을 지정하여 검사 기능을 설치합니다.
    
        Install-AIPScanner -SqlServerInstance <your computer name>\SQLEXPRESS
    
    자격 증명을 요구하는 메시지가 나타나면 \<domain\user name> 형식으로 검사 기능에 대해 고유한 자격 증명을 제공하고 암호를 지정합니다. 

## <a name="specify-your-test-data-store"></a>테스트 데이터 저장소 지정

PowerShell 세션에서 다음 명령을 입력합니다.

    Add-AIPScannerRepository -Path C:\TestScanner

## <a name="configure-the-scanner-to-discover-all-information-types"></a>모든 정보 유형을 검색하도록 검사 기능을 구성합니다.

PowerShell 세션에서 다음 명령을 입력합니다.

    Set-AIPScannerConfiguration -Enforce Off -Schedule Manual -DiscoverInformationTypes All

이 명령은 지정된 데이터 리포지토리에서 모든 파일의 일회성 검색을 수행하도록 검사 기능을 구성합니다. 이 검색은 알려진 중요한 정보 유형을 찾으며, 사용자가 먼저 Azure Information Protection 레이블 또는 정책 설정을 구성할 필요가 없습니다.

## <a name="start-the-scan-and-confirm-it-finished"></a>검색 시작 및 완료되었는지 확인

1. PowerShell 세션에서 다음 명령을 입력하여 검사 기능을 시작합니다.
    
        Start-AIPScan
    
    작은 파일 하나만 검사하면 되므로 이 초기 테스트 검색은 매우 빠르게 진행됩니다. 

2. Windows **이벤트 뷰어** > **애플리케이션 및 서비스** > **Azure Information Protection** 이벤트 로그로 이동합니다. 
    
    Azure Information Protection이 **MSIP.Scanner** 프로세스에 대해 정보 이벤트 ID **911**을 표시하는지 확인합니다. 이벤트 로그 항목에는 검사 결과의 요약도 포함됩니다.

## <a name="see-detailed-results"></a>자세한 결과 보기

파일 탐색기를 사용하여 %*localappdata*%\Microsoft\MSIP\Scanner\Reports에서 검사 보고서를 찾습니다. .csv 파일 형식의 세부 보고서 파일을 엽니다.

Excel에서 처음 두 개의 열에 데이터 저장소 리포지토리 및 파일 이름이 표시됩니다. 열을 살펴보다 보면 **정보 유형 이름**이라는 열에 관심이 생길 것입니다. 이 초기 테스트를 위해 이 열에는 검사 기능이 찾을 수 있는 많은 중요한 정보 유형 중 하나인 **신용 카드 번호**가 표시됩니다.

## <a name="scan-your-own-data"></a>자체 데이터 검사

1. Add-AIPScannerRepository를 다시 실행합니다. 이번에는 중요한 정보를 검사하려는 고유한 온-프레미스 데이터 저장소를 지정합니다. 
    
    로컬 폴더, 네트워크 공유(UNC 경로) 또는 SharePoint 사이트나 라이브러리에 대한 SharePoint Server URL을 지정할 수 있습니다. 
    
    - 로컬 폴더 예제:
        
            Add-AIPScannerRepository -Path D:\Data\Finance
    
    - 네트워크 공유 예제
        
            Add-AIPScannerRepository -Path \\NAS\HR
    
    - SharePoint 폴더 예제:
        
            Add-AIPScannerRepository -Path "http://sp2016/Shared Documents"

2. 검사 기능을 다시 시작합니다.
    
        Start-AIPScan

3. 검사가 완료되면 새 결과를 확인합니다. 
    
    이 검사에 걸리는 시간은 데이터 저장소에 있는 파일 개수, 해당 파일의 크기 및 파일의 형식에 따라 다릅니다. 

## <a name="clean-up-resources"></a>리소스 정리

프로덕션 환경에서는 Azure Information Protection 서비스에서 자동으로 인증되는 서비스 계정을 사용하여 Windows Server에서 검사 기능을 실행합니다. 또한 SQL Server의 엔터프라이즈급 버전을 사용하고 여러 데이터 저장소를 지정할 수도 있습니다. 

프로덕션 배포용으로 준비된 리소스를 정리하려면 PowerShell 세션에서 다음 명령을 실행하여 검사 기능을 제거합니다.

    Uninstall-AIPScanner

그런 후 컴퓨터를 다시 시작합니다.

이 명령을 실행해도 아래 항목은 제거되지 않으므로, 빠른 시작 후에 필요에 따라 수동으로 제거해야 합니다.

- Azure Information Protection 검사 기능을 설치할 때 Install-AIPScanner cmdlet을 실행하여 만든 **AzInfoProtection**라는 SQL Server 데이터베이스 

- %*localappdata*%\Microsoft\MSIP\Scanner\Reports에 있는 스캐너 보고서

- 로컬 컴퓨터의 도메인 계정에 부여된 **서비스로 로그온** 사용자 권한 할당


## <a name="next-steps"></a>다음 단계

이 빠른 시작에는 최소 구성이 포함되므로 검사 기능이 네트워크 공유에서 중요한 정보를 찾는 방법을 빠르게 확인할 수 있습니다. 프로덕션 환경에서 검사 기능을 설치할 준비가 되면 [Azure Information Protection 검사 기능을 배포하여 파일 자동으로 분류 및 보호](deploy-aip-scanner.md)를 참조하세요.

중요한 정보를 포함하는 파일을 분류하고 보호하려는 경우 자동 분류 및 보호를 위해 Azure Information Protection 레이블을 구성해야 합니다.

- [Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](configure-policy-classification.md)

- [Rights Management 보호에 대해 레이블을 구성하는 방법](configure-policy-protection.md)