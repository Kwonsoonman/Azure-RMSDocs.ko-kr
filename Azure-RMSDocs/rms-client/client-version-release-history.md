---
title: Azure Information Protection 클라이언트 - 버전 릴리스 기록 및 지원 정책
description: Windows용 Azure Information Protection 클라이언트 릴리스에서 새롭거나 변경된 기능을 알아보고 지원에 대한 수명 주기 정책을 파악합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ff9d6a4ce66deed8add68d7b1efc889ee9448f53
ms.sourcegitcommit: 5866509c17872e274720d3014fe218ed95e86ee3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2018
---
# <a name="azure-information-protection-client-version-release-history-and-support-policy"></a>Azure Information Protection 클라이언트: 버전 릴리스 기록 및 지원 정책

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection 팀에서는 픽스 및 새 기능을 위해 Azure Information Protection 클라이언트를 정기적으로 업데이트합니다. 

[Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 최신 GA 릴리스 버전과 현재 미리 보기 버전을 다운로드할 수 있습니다. 이러한 버전은 Microsoft 업데이트 카탈로그(범주: **Azure Information Protection**)에도 포함되어 있으므로, WSUS, Configuration Manager 또는 Microsoft Update를 사용하는 다른 소프트웨어 배포 메커니즘을 사용하여 클라이언트를 배포할 수 있습니다.

### <a name="servicing-information-and-timelines"></a>서비스 정보 및 타임라인

Azure Information Protection 클라이언트의 각 일반 가용성(GA) 버전은 후속 GA 버전이 릴리스된 후 최대 6개월 동안 지원됩니다. 지원되지 않는 버전의 클라이언트는 이 페이지에 포함되지 않습니다. 수정 사항 및 새로운 기능은 항상 최신 GA 버전에 적용되며, 이전의 GA 버전에는 적용되지 않습니다.

미리 보기 버전을 프로덕션 네트워크의 최종 사용자에게 배포해서는 안 됩니다. 대신 최신 미리 보기 버전을 통해 다음 GA 버전에서 제공되는 새로운 기능 또는 수정 사항을 확인하고 사용해 볼 수 있습니다. 현재 존재하지 않는 미리 보기 버전은 지원되지 않습니다.

### <a name="release-history"></a>릴리스 기록

다음 정보를 사용하여 지원되는 Windows용 Azure Information Protection 클라이언트 릴리스에서 새롭거나 변경된 기능에 대해 알아보세요. 가장 최근 릴리스가 먼저 나열됩니다. 

> [!NOTE]
> 사소한 수정 사항은 나열되지 않으므로 Azure Information Protection 클라이언트에 문제가 발생있으면 최신 GA 릴리스로 수정되었는지 확인하는 것이 좋습니다. 문제가 계속되면 현재 미리 보기 버전을 확인하세요.
>  
> 기술 지원의 경우 [지원 옵션 및 커뮤니티 리소스](../get-started/information-support.md#support-options-and-community-resources) 정보를 참조하세요. 또한 Azure Information Protection 팀의 [Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다.

## <a name="versions-later-than-110560"></a>1.10.56.0 이상 버전

1.10.56.0 이상 버전의 클라이언트가 설치된 경우 테스트 및 평가를 위한 미리 보기 빌드입니다.

현재 미리 보기 버전은 **1.21.203.0**이며 클라이언트의 현재 GA 버전 이후에 다음과 같이 변경되었습니다.

이 버전에는 RMS 클라이언트의 MSIPC 버전 1.0.3403.1224가 포함되어 있습니다.

**새로운 기능**:

- Azure Information Protection 스캐너: 클라이언트에 포함된 PowerShell 모듈에는 온-프레미스 데이터 저장소에서 파일을 검색하고, 분류하고, 보호할 수 있도록 스캐너를 설치하고 구성할 새로운 cmdlet이 있습니다. 자세한 내용은 [Azure Information Protection 스캐너를 배포하여 파일 자동으로 분류 및 보호](../deploy-use/deploy-aip-scanner.md)를 참조하세요. 

- Office 앱의 경우 자동 및 권장 분류는 문서를 저장할 때 실행하는 대신 백그라운드에서 계속 실행됩니다. 이제 동작을 이렇게 변경하면 SharePoint Online에 저장된 문서에 대한 자동 및 권장 분류를 적용할 수 있습니다. [추가 정보](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) 

- 이제 텍스트 문자열에서 "If.App" 변수 문을 사용하여 Word, Excel, PowerPoint 및 Outlook에 대새 다른 시각적 표시를 설정하고 응용 프로그램 형식을 식별할 수 있습니다. [추가 정보](../deploy-use/configure-policy-markings.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)

- [정책 설정](../deploy-use/configure-policy-settings.md)인 **Office 앱에 Information Protection 표시줄 표시**에 대한 지원입니다. 이 설정을 끄기로 설정하면 사용자는 리본에 있는 **보호** 단추에서 레이블을 선택합니다.

- 새로운 고급 클라이언트 설정은 Outlook이 Azure Information Protection 정책에서 구성된 기본 레이블을 적용하지 않도록 합니다. 대신 Outlook에서 다른 기본 레이블을 적용할 수 있거나 레이블을 적용하지 않습니다. [추가 정보](client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) 

- Office 앱에서 사용자 지정 권한을 지정하는 경우 이제 주소록 아이콘에서 사용자를 찾아보고 선택할 수 있습니다. 이 옵션을 통해 파일 탐색기를 사용하여 사용자 지정 권한을 지정하는 경우 사용자 환경에 패리티를 제공합니다.

- PowerShell을 사용하고 **로컬로 로그온** 권한을 허용할 수 없는 서비스 계정의 완전한 비대화형 인증 방법에 대한 지원입니다. 이 인증 방법은 [Set-AIPAuthentication](/powershell/module/azureinformationprotection/Set-AIPAuthentication)을 사용하여 새 *토큰* 매개 변수를 사용하고, PowerShell 스크립트를 작업으로 실행해야 합니다. [추가 정보](../rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)

- [Set-RMSServerAuthentication](/powershell/module/azureinformationprotection/set-rmsserverauthentication)의 새 매개 변수인 *IntegratedAuth*입니다. 이 매개 변수는 AD RMS에 서버 모드를 지원합니다. 이 기능은 Windows Server FCI를 지원하기 위해 AD RMS에 필요합니다.


**수정 사항**:

안정성 및 다음을 포함하는 특정 시나리오에 대한 수정

- Office 버전 16.0.8628.2010 이상(간편-실행)의 경우 Azure Information Protection 표시줄은 이전에 Office 응용 프로그램 외부에서 표시줄을 표시할 수 있는 최신 모니터 표시 옵션을 지원합니다.

- Azure Information Protection을 사용하는 두 조직에서 레이블이 지정된 문서와 이메일을 공유하는 경우 해당하는 고유한 레이블이 유지되며 다른 조직의 레이블로 대체되지 않습니다.

- 교차 참조를 포함하는 Excel의 셀에 대한 지원은 이전에 셀에서 텍스트 손상을 발생시켰습니다.

- Office 테마 또는 Windows 테마 변경에 대한 지원은 테마가 변경된 후에 Excel이 데이터를 표시하지 않는 결과를 발생시켰습니다.

- 이제 권장 또는 자동 분류를 위해 .xml 파일 이름 확장명을 가진 파일을 검사할 수 있습니다.

- 이제 뷰어는 20MB를 넘는 보호된 텍스트 기반 파일(.ptxt 및 .pxml)을 열 수 있습니다. 

- Outlook 미리 알림기를 사용하는 경우 Outlook의 작동이 중지되지 않도록 방지합니다.

- 문서와 이메일을 보호할 수 있도록 부트스트랩은 Office 64비트에서 성공합니다.

- 이제 Word, Excel, PowerPoint 및 파일 탐색기에 대한 사용자 정의 사용 권한에 대한 레이블을 구성하고, 고급 클라이언트 설정을 사용하여 사용자 지정 사용 권한 옵션을 숨길 수도 있습니다. [추가 정보](client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users) 

- Azure Information Protection 정책의 시각적 표시가 클라이언트에 설치되어 있지 않은 글꼴 이름에 대해 구성된 경우 Calibri 글꼴로 대체합니다.

- Azure Information Protection 클라이언트를 업그레이드한 후에 Office 충돌을 방지합니다.

- Office 앱의 경우 성능 및 메모리 사용을 향상시킵니다.

- 사용자 정의 사용 권한을 사용자 및 HYOK(AD RMS) 보호에 레이블을 구성하는 경우 보호는 더 이상 Azure Rights Management 서비스를 잘못 사용하지 않습니다.

- 보다 일관된 관리 환경을 위해 하위 레이블은 더 이상 부모 레이블에서 시각적 표시 및 보호 설정을 상속하지 않습니다.


## <a name="version-110560"></a>버전 1.10.56.0

**릴리스 날짜**: 2017년 9월 18일

이 버전에는 RMS 클라이언트의 MSIPC 버전 1.0.3219.0619가 포함되어 있습니다.

**새로운 기능**:

- 레이블에 대해 구성할 수 있는 새로운 Office 365 DLP 조건을 지원합니다. 자세한 내용은 [Azure Information Protection 레이블에 대한 조건 구성](../deploy-use/configure-policy-classification.md)을 참조하세요.

- 사용자 정의 작업에 대해 구성된 레이블을 지원합니다. Outlook의 경우 이 레이블에 따라 자동으로 Outlook 전달 금지 옵션이 적용됩니다. Word, Excel, PowerPoint 및 파일 탐색기의 경우 이 레이블에 따라 사용자 지정 권한을 지정하라는 메시지가 사용자에게 표시됩니다. 자세한 내용은 [보호에 대해 Azure Information Protection 레이블 구성](../deploy-use/configure-policy-protection.md)을 참조하세요.

- 레이블에는 다국어가 지원됩니다. 2017년 8월 30일부터 [기본 정책](../deploy-use/configure-policy-default.md)에 이 버전의 클라이언트가 사용자에게 표시하는 여러 언어에 대한 지원이 포함됩니다. 이 날짜 이전에 기본 정책에서 원하는 언어로 레이블을 볼 수 있는 사용자와 구성 가능한 레이블에 대한 자세한 내용은 [Azure Information Protection에서 다른 언어에 대한 레이블을 구성하는 방법](../deploy-use/configure-policy-languages.md)을 참조하세요.

- 레이블은 Information Protection 표시줄뿐만 아니라 Office 리본의 **보호** 단추에도 표시됩니다. 

- 다음 Visio 파일 형식에 대한 기본 보호: .vsdm, .vsdx, .vssm, .vssx, .vstm, .vstx

- Azure Portal에서 구성하는 고급 클라이언트 구성을 지원합니다. 이러한 구성은 다음과 같습니다.
    
    - [Outlook에서 전달 금지 단추 숨기기 또는 표시](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook)
    
    - [사용자의 사용자 지정 권한 옵션 사용 가능 여부 지정](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users)
    
    - [Azure Information Protection 표시줄을 영구적으로 숨기기](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar)
    
    - [Outlook에서 권장 분류 사용](../rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook)

- PowerShell의 경우 새로운 [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) 및 [Clear-AIPAuthentication](/powershell/module/azureinformationprotection/clear-aipauthentication) PowerShell cmdlet을 사용하여 파일에 레이블을 비대화형으로 지정할 수 있습니다. 이러한 cmdlet을 사용하는 방법에 대한 자세한 내용은 관리자 가이드의 [PowerShell 섹션](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)을 참조하세요.

- [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) 및 [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) PowerShell cmdlet에는 새로운 **Owner** 및 **PreserveFileDetails** 매개 변수가 있습니다. 이러한 매개 변수를 사용하여 Owner 사용자 지정 속성에 대한 이메일 주소를 지정할 수 있지만 레이블이 지정되는 문서의 날짜는 변경되지 않습니다.

**수정 사항**:

안정성 및 다음을 포함하는 특정 시나리오에 대한 수정

- 이전에는 1GB가 넘는 경우 손상될 수 있었던 큰 파일에 대한 보호를 일반적으로 지원합니다. 이제 파일 크기는 사용 가능한 하드 디스크 공간과 사용 가능한 메모리에 의해서만 제한됩니다. 파일 크기 제한에 대한 자세한 내용은 관리자 가이드의 [보호가 지원되는 파일 크기](client-admin-guide-file-types.md#file-sizes-supported-for-protection)를 참조하세요.

- Azure Information Protection 클라이언트 뷰어는 보호된 PDF(.ppdf) 파일을 보기 전용으로 엽니다.

- SharePoint Server에 저장된 파일의 레이블 지정 및 보호를 지원합니다.

- 워터마크는 이제 여러 줄을 지원합니다. 또한 시각적 표시는 이제 문서를 저장할 때마다가 아니라 [문서를 처음 저장할 때만](../deploy-use/configure-policy-markings.md#when-visual-markings-are-applied) 문서에 적용됩니다().

- **도움말 및 피드백** 대화 상자의 **진단 실행** 옵션이 **설정 재설정**으로 바뀌었습니다. 이 작업의 동작에 사용자 로그아웃 및 Azure Information Protection 정책 삭제가 포함되도록 변경되었습니다. 자세한 내용은 관리자 가이드의 [설정 재설정 옵션에 대한 자세한 내용](..\rms-client\client-admin-guide.md#more-information-about-the-reset-settings-option)을 참조하세요.

- 프록시 인증을 지원합니다.

향상된 사용자 환경에 대한 수정

- 사용자가 사용자 지정 권한을 지정할 때 전자 메일의 유효성을 검사합니다. 또한 Enter 키를 눌러 여러 이메일 주소를 지정할 수 있습니다.

- 모든 하위 레이블이 보호를 위해 구성되고 클라이언트에 보호를 지원하는 Office 버전이 없는 경우 부모 레이블이 표시되지 않습니다. 

## <a name="next-steps"></a>다음 단계

클라이언트를 설치하고 사용하는 방법에 대한 자세한 내용은 다음과 같습니다. 

- 사용자: [다운로드 및 클라이언트 설치](install-client-app.md)

- 관리자: [Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
