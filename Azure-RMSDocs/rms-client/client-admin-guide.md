---
title: Azure Information Protection 클라이언트 관리자 가이드
description: Windows용 Azure Information Protection 클라이언트 배포를 담당하는 엔터프라이즈 네트워크의 관리자를 위한 지침과 정보를 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/28/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7510350957c867e144704af261053b73fa04651a
ms.sourcegitcommit: 8cde6611ab6d95d816e1c80267cacd32443f31cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118009"
---
# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection 클라이언트 관리자 가이드

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

엔터프라이즈 네트워크의 Azure Information Protection 클라이언트를 담당하거나 [Azure Information Protection 클라이언트 사용자 가이드](client-user-guide.md)에 제공된 것보다 더 많은 기술 정보가 필요한 경우 이 가이드의 정보를 사용하세요. 

예를 들면 다음과 같습니다.

- 이 클라이언트 다양한 구성 요소 및 설치해야 하는지 여부 이해

- 사용자를 대상으로 하는 클라이언트 설치 방법, 필수 구성 요소, 설치 옵션 및 매개 변수에 대한 정보와 확인 작업

- 경우에 따라 레지스트리 편집이 필요한 사용자 지정 구성을 수용하는 방법

- 클라이언트 파일 및 사용 현황 로그 찾기

- 클라이언트에서 지원하는 파일 형식 식별

- 사용자를 위한 문서 추적 사이트 구성 및 사용

- 클라이언트에서 명령줄 제어를 위한 PowerShell 사용

**이 설명서에서 해결되지 않은 질문이 있나요?** [Azure Information Protection Yammer 사이트](https://www.yammer.com/AskIPTeam)를 방문하세요. 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트의 기술 개요

Azure Information Protection 클라이언트에는 다음이 포함됩니다.

- 사용자가 분류 레이블을 선택할 수 있는 Azure Information Protection 표시줄을 설치하는 Office 추가 기능과 추가 옵션용 리본의 **보호** 단추 Outlook의 경우 리본에서도 **전달 금지** 단추를 사용할 수 있습니다.

- 파일에 분류 레이블 및 보호를 적용하기 위한 Windows 파일 탐색기의 오른쪽 클릭 옵션

- 네이티브 응용 프로그램으로 열 수 없을 때 보호된 파일을 표시하는 뷰어

- 파일에서 분류 레이블 및 보호를 적용 및 제거하기 위한 PowerShell 모듈 
    
    이 모듈에는 Windows Server에서 서비스로 실행되는 [Azure Information Protection 스캐너](../deploy-aip-scanner.md)를 설치하고 구성하는 cmdlet이 포함되어 있습니다. 이 서비스를 통해 네트워크 공유 및 SharePoint Server 라이브러리와 같은 데이터 저장소에서 파일을 검색, 분류 및 보호할 수 있습니다.

- Azure RMS(Azure Rights Management) 또는 AD RMS(Active Directory Rights Management Services)와 통신하는 Rights Management 클라이언트

Azure Information Protection 클라이언트는 해당 Azure 서비스인 Azure Information Protection와 해당 데이터 보호 서비스인 Azure Rights Management에서 가장 잘 작동됩니다. 몇 가지 제한 사항이 있으나 Azure Information Protection 클라이언트는 온-프레미스 버전의 Rights Management인 AD RMS에도 잘 작동합니다. Azure Information Protection 및 AD RMS에서 지원하는 기능을 포괄적으로 비교한 내용을 보려면 [Azure Information Protection과 AD RMS 비교](../compare-on-premise.md)를 참조하세요. 

AD RMS가 있고 Azure Information Protection으로 마이그레이션하려면 [AD RMS에서 Azure Information Protection으로 마이그레이션](../migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 배포해야 하나요?

다음이 적용될 경우 Azure Information Protection 클라이언트를 배포합니다.

- Office 응용 프로그램(Word, Excel, PowerPoint, Outlook) 내에서 레이블을 선택하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- 추가 파일 형식, 다중 선택 및 폴더를 지원하는 파일 탐색기를 사용하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- PowerShell 명령을 사용하여 문서를 분류(및 필요에 따라 보호)하는 스크립트를 실행하려고 합니다.

- 저장된 온-프레미스인 파일을 검색하고 분류(및 필요에 따라 보호)하는 서비스를 실행하려고 합니다.

- 네이티브 응용 프로그램이 설치되어 있지 않거나 이러한 문서를 열 수 없을 때 보호된 문서를 보려고 합니다.

- 파일 탐색기를 사용하거나 PowerShell 명령을 사용하여 파일을 보호하려고 합니다.

- 사용자 및 관리자가 보호된 문서를 추적하고 해지할 수 있게 허용하려고 합니다.

- 데이터 복구를 위해 대량으로 파일 및 컨테이너에서 암호화를 제거(보호 해제)하려고 합니다.

- Office 2010을 실행하며, Azure Rights Management 서비스를 사용하여 문서 및 전자 메일 메시지를 보호하려고 합니다.

다음 예제에서는 Office 응용 프로그램의 Azure Information Protection 클라이언트 추가 기능을 보여주고 조직에 대한 분류 레이블 및 리본의 새 **보호** 단추를 표시합니다.

![기본 정책이 적용된 Azure Information Protection 표시줄](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 설치 및 지원

Windows Update, 실행 파일, 또는 Windows Installer 파일을 사용하여 Azure Information Protection 클라이언트를 설치할 수 있습니다. 각각에 대한 자세한 내용은 [사용자를 위한 Azure Information Protection 클라이언트 다운로드 및 설치](client-admin-guide-install.md)를 참조하세요.  

클라이언트를 설치하는 방법에 대한 정보를 지원하기 위해 다음 섹션을 사용합니다. 

### <a name="installation-checks-and-troubleshooting"></a>설치 검사 및 문제 해결

클라이언트를 설치할 때 **도움말 및 피드백** 옵션을 사용하여 **Microsoft Azure Information Protection** 대화 상자를 엽니다.

- Office 응용 프로그램에서: **홈** 탭의 **보호** 그룹에서 **보호**를 선택한 다음 **도움말 및 피드백**을 선택합니다.

- 파일 탐색기에서: 마우스 오른쪽 단추로 파일 또는 폴더를 선택한 다음 **분류 및 보호**를 선택하고 **도움말 및 피드백**을 선택합니다. 

#### <a name="help-and-feedback-section"></a>**도움말 및 피드백** 섹션

**추가 정보 링크**를 클릭하면 기본적으로 [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection) 웹 사이트로 이동되지만 Azure Information Protection 정책의 [정책 설정](../configure-policy-settings.md) 중 하나로 사용자 지정 URL로 이동하도록 이 링크를 구성할 수 있습니다.

**피드백 보내기** 링크(일반 공급 버전)를 사용하여 Information Protection 팀에 제안 사항이나 요청을 보냅니다. 기술 지원을 위해 이 옵션을 사용하지 않는 경우에는 대신 [지원 옵션 및 커뮤니티 리소스](../information-support.md#support-options-and-community-resources)를 참조하세요. 

미리 보기 버전의 클라이언트에서는 **문제 보고** 링크가 **피드백 보내기** 링크를 대체합니다. 기본적으로 이 옵션을 사용하면 Microsoft에 메일이 전송되지만 [고급 클라이언트 설정](client-admin-guide-customizations.md#modify-the-email-address-for-the-report-an-issue-link)을 지정하여 사용자에 대한 HTTP 문자열을 구성할 수 있습니다. 예를 들어, 지원 센터의 메일 주소를 지정합니다.

**로그 내보내기**는 Microsoft 지원에 로그 파일을 보내라는 요청을 받았을 때 Azure Information Protection 클라이언트의 로그 파일을 자동으로 수집하여 첨부합니다. 최종 사용자가 이 옵션을 사용하여 이러한 로그 파일을 지원 센터로 보낼 수도 있습니다.

**설정 재설정**은 사용자를 로그아웃하고, 현재 다운로드한 Azure Information Protection 정책을 삭제하고, Azure Rights Management 서비스에 대한 사용자 설정을 다시 설정합니다.

##### <a name="more-information-about-the-reset-settings-option"></a>설정 재설정 옵션에 대한 자세한 내용

- 이 옵션을 사용하기 위해 로컬 관리자일 필요가 없으며 이 작업은 이벤트 뷰어에 로깅되지 않습니다. 

- 파일이 잠겨 있지 않으면 이 작업은 다음 위치에서 모든 파일을 삭제합니다. 여기에는 클라이언트 인증서, Rights Management 템플릿, Azure Information Protection 정책, 사용자 자격 증명 캐시가 포함됩니다. 클라이언트 로그 파일은 삭제되지 않습니다.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- 다음 레지스트리 키 및 설정이 삭제됩니다. 이 레지스트리 키에 대한 설정에 사용자 지정 값이 있을 경우 클라이언트를 다시 설정한 후 레지스트리 설정을 다시 구성해야 합니다. 
    
    일반적으로 엔터프라이즈 네트워크의 경우 그룹 정책을 사용하여 이러한 설정을 구성하며, 이 경우 컴퓨터에서 그룹 정책을 새로 고치면 이러한 설정이 자동으로 다시 적용됩니다. 하지만 스크립트를 사용하여 한 번 구성하거나 수동으로 구성하는 일부 설정도 있을 수 있습니다. 이러한 경우 해당 설정을 다시 구성하기 위한 추가 단계를 수행해야 합니다. 예를 들어 AD RMS에서 마이그레이션하는 데 네트워크에 서비스 연결 지점이 계속 있기 때문에 컴퓨터에서 스크립트를 한 번 실행하여 Azure Information Protection으로 리디렉션에 대한 설정을 구성할 수 있습니다. 클라이언트를 재설정한 후 컴퓨터에서 이 스크립트를 다시 실행해야 합니다.
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- 현재 로그인된 사용자는 로그아웃됩니다.

#### <a name="client-status-section"></a>**클라이언트 상태** 섹션

**다음으로 연결** 값을 사용하여 표시된 사용자 이름이 Azure Information Protection 인증에 사용할 계정을 나타내는지 확인합니다. 이 사용자 이름은 Office 365 또는 Azure Active Directory에 사용하는 계정과 일치해야 합니다. 또한 계정은 Azure Information Protection에 대해 구성된 테넌트에 속해야 합니다.

표시된 계정과 다른 사용자로 로그인해야 하는 경우 [다른 사용자로 로그인](client-admin-guide-customizations.md#sign-in-as-a-different-user) 사용자 지정 내용을 참조하세요.

**마지막 연결**은 클라이언트가 조직의 Azure Information Protection 서비스에 마지막으로 연결된 시기를 표시합니다. **Information Protection 정책 설치** 날짜 및 시간과 함께 이 정보를 사용하여 Azure Information Protection 정책이 마지막으로 설치되거나 업데이트된 시기를 확인할 수 있습니다. 클라이언트는 서비스에 연결할 때 현재 정책에서 변경된 사항이 발견될 경우, 그리고 24시간마다 최신 정책을 자동으로 다운로드합니다. 표시된 시간 이후에 정책을 변경한 경우 Office 응용 프로그램을 닫았다가 다시 엽니다.

**This client is not licensed for Office Professional Plus**(Office Professional Plus 대상 클라이언트가 아님)이 표시될 경우: Azure Information Protection 클라이언트에서 설치된 버전의 Office가 Rights Management 보호의 적용을 지원하지 않는 것을 감지했습니다. 이 상태가 감지되면 보호를 적용하는 레이블이 Azure Information Protection 막대에 표시되지 않습니다.

**버전** 정보를 사용하여 설치된 클라이언트 버전을 확인합니다. **새로운 기능** 링크를 클릭하고 클라이언트의 [버전 릴리스 기록](client-version-release-history.md)을 읽으면 이 버전이 최신 릴리스 버전인지 여부와 해당 수정 사항 및 새로운 기능을 확인할 수 있습니다.

## <a name="support-for-multiple-languages"></a>다국어 지원

Azure Information Protection 클라이언트는 Office 365가 지원하는 같은 언어를 지원합니다. 이러한 언어 목록은 Office의 [국가별 가용성](https://products.office.com/business/international-availability) 페이지 내 **Office 365, Exchange Online Protection 및 Power BI** 섹션을 참조하세요.

이러한 언어의 경우 Azure Information Protection 클라이언트의 메뉴 옵션, 대화 상자 및 메시지가 사용자의 언어로 표시됩니다. 언어를 감지하는 단일 설치 관리자가 있으므로 다른 언어를 위한 Azure Information Protection 클라이언트를 설치하기 위해 추가로 구성할 필요가 없습니다. 

그러나 지정한 레이블 이름 및 설명은 Azure Information Protection 정책에서 레이블을 구성할 때 자동으로 번역되지 않습니다. 2017년 8월 30일부터 현재 [기본 정책](../configure-policy-default.md)에는 일부 언어에 대한 지원이 포함됩니다. 사용자가 원하는 언어로 레이블을 볼 수 있게 하려면 직접 번역을 제공하고 이러한 번역을 사용하도록 Azure Information Protection 정책을 구성합니다. 자세한 정보는 [Azure Information Protection에서 다른 언어에 대한 레이블을 구성하는 방법](../configure-policy-languages.md)을 참조하세요. 시각적 표시는 번역되지 않으며 둘 이상의 언어를 지원하지 않습니다.

## <a name="post-installation-tasks"></a>설치 후 작업

Azure Information Protection 클라이언트를 설치한 후 문서 및 메일에 레이블을 지정하는 방법에 대한 지침과 특정 시나리오의 경우 선택하는 레이블에 대한 지침을 사용자에게 제공합니다. 예를 들면 다음과 같습니다.

- 온라인 사용자 지침: [Azure Information Protection 사용자 가이드](client-user-guide.md)

- 사용자 지정 가능한 사용자 가이드 다운로드: [Azure Information Protection 최종 사용자 채택 가이드](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

### <a name="update-macros-in-excel-spreadsheets"></a>Excel 스프레드시트에서 매크로 업데이트

매크로가 포함된 Excel 스프레드시트가 있는 경우 다음과 같이 매크로를 편집하여 Azure Information Protection 클라이언트 설치 후 원하는 대로 계속 작동되도록 합니다.

1. 매크로 시작에 다음을 추가합니다.

        Application.EnableEvents = False

2. 매크로 끝에 다음을 추가합니다.

        Application.EnableEvents = True

자세한 내용은 [Application.EnableEvents Property (Excel)](https://msdn.microsoft.com/vba/excel-vba/articles/application-enableevents-property-excel)(Application.EnableEvents 속성(Excel))을 참조하세요.

## <a name="upgrading-and-maintaining-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 업그레이드 및 유지 관리

Azure Information Protection 팀은 새로운 기능과 수정을 위해 Azure Information Protection 클라이언트를 정기적으로 업데이트합니다. 공지 사항은 팀의 [Yammer 사이트](https://www.yammer.com/AskIPTeam)에 게시됩니다.

Windows 업데이트를 사용하는 경우 Azure Information Protection 클라이언트는 클라이언트가 설치된 방법과 관계없이 클라이언트의 일반 공급 버전을 자동으로 업그레이드합니다. 새 클라이언트 릴리스는 릴리스 후 몇 주간 카탈로그에 게시됩니다.

또는 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 새 릴리스를 다운로드하여 수동으로 클라이언트를 업그레이드할 수 있습니다. 그런 다음, 새 버전을 설치하여 클라이언트를 업그레이드하세요. 미리 보기 버전을 업그레이드하려면 이 방법을 사용해야 합니다.

수동으로 업그레이드할 때 설치 방법을 변경하는 경우에만 이전 버전을 먼저 제거하세요. 예를 들어, 클라이언트의 실행 파일(.exe) 버전을 클라이언트의 Windows Installer(.msi) 버전으로 변경하는 경우입니다. 또는 이전 버전의 클라이언트를 설치해야 하는 경우가 있습니다. 예를 들어, 테스트용으로 설치된 최신 미리 보기 버전이므로 현재 일반 공급 버전으로 되돌려야 합니다.

[버전 릴리스 기록 및 지원 정책](client-version-release-history.md)을 사용하여 Azure Information Protection 클라이언트에 대한 지원 정책, 현재 지원되는 버전 및 지원되는 릴리스의 새로운 기능과 변경된 기능을 이해합니다. 

### <a name="upgrading-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너 업그레이드

Azure Information Protection 스캐너를 업그레이드하려면 최신 버전의 Azure Information Protection 클라이언트를 설치하세요. 그런 다음, 다음 일회성 작업 중 하나를 수행합니다.

현재 GA 버전의 경우: 

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)를 사용하여 스캐너 설치 명령을 다시 실행합니다. 스캐너 및 리포지토리에 대한 구성 설정은 유지됩니다. 스캐너를 다시 설치하면 보고서에 필요한 스캐너 데이터베이스에 대한 삭제 권한이 스캐너 서비스 계정에 부여됩니다.

미리 보기 버전: 

- Azure Information Protection 클라이언트를 일반 공급 버전 1.29.5.0 또는 그 이전 버전에서 업그레이드한 후 [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)를 실행합니다. 스캐너 및 리포지토리에 대한 구성 설정은 유지됩니다. 이 cmdlet을 실행하려면 스캐너에 대한 데이터베이스 스키마를 업데이트해야 하고 필요한 경우 스캐너 서비스 계정에 스캐너 데이터베이스에 대한 삭제 권한을 부여합니다. 
    
    이 업데이트 cmdlet을 실행할 때까지 스캐너가 실행되지 않으며 일반적으로 Windows 이벤트 로그에 이벤트 ID **1000**이 보이고 **개체 이름 ‘ScannerStatus’가 잘못되었습니다**라는 오류 메시지가 표시됩니다.

## <a name="uninstalling-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 제거

다음 옵션 중 하나를 사용하여 클라이언트를 제거할 수 있습니다.

- 제어판을 사용하여 프로그램을 제거합니다. **Microsoft Azure Information Protection** > **제거**를 클릭합니다.

- **AzInfoProtection.exe**와 같은 실행 파일을 다시 실행하고 **설치 수정** 페이지에서 **제거**를 클릭합니다. 

- **/uninstall**을 사용하여 실행 파일을 실행합니다. 예를 들어 `AzInfoProtection.exe /uninstall`를 구성할 수 있습니다.

## <a name="next-steps"></a>다음 단계
클라이언트를 설치하려면 [사용자를 위해 Azure Information Protection 클라이언트 설치](client-admin-guide-install.md)를 참조하세요.

클라이언트를 설치했다면 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보는 다음을 참조하세요.

- [사용자 지정](client-admin-guide-customizations.md)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


