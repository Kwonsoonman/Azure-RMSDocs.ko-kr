---
title: "Azure Information Protection 클라이언트&colon; 버전 릴리스 기록"
description: "Windows용 Azure Information Protection 클라이언트 릴리스에의 새로운 사항이나 변경된 사항에 대해 알아보세요."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/09/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ccd6d0cec6a71527fad0303369baad90dd733958
ms.sourcegitcommit: bcc2f69475f811245d2beaf79c67a3d8569c4821
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2017
---
# <a name="azure-information-protection-client-version-release-history"></a>Azure Information Protection 클라이언트: 버전 릴리스 기록

>*적용 대상: Azure Information Protection*

Azure Information Protection 팀에서는 픽스 및 새 기능을 위해 Azure Information Protection 클라이언트를 정기적으로 업데이트합니다. 이 클라이언트는 Microsoft 업데이트 카탈로그(범주: **Azure Information Protection**)에 포함되어 있으며, 언제든지 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 최신 GA(일반 공급) 릴리스 버전 및 이후 버전(미리 보기 버전)을 다운로드할 수 있습니다.

미리 보기 버전을 프로덕션 네트워크의 최종 사용자에게 배포해서는 안 됩니다. 대신, 미리 보기 버전을 통해 다음 GA 버전의 새로운 기능 또는 수정 사항을 확인하고 사용해 볼 수 있습니다. 

GA 릴리스의 새로운 기능이나 변경 사항을 확인하려면 다음 정보를 참조하세요. 가장 최근 릴리스가 먼저 나열됩니다. 현재 미리 보기 버전에 대한 변경 내용은 다운로드 페이지의 정보를 참조하세요.

> [!NOTE]
> 사소한 수정 사항은 나열되지 않으므로 Azure Information Protection 클라이언트에 문제가 있는 경우 먼저 최신 GA 릴리스의 문제가 아닌지 확인하세요. 문제에 해당하는 경우 현재 미리 보기 버전을 확인하세요.
>  
> 문제가 지속되면 [지원 옵션 및 커뮤니티 리소스](../get-started/information-support.md#support-options-and-community-resources) 정보를 참조하세요. 또한 Azure Information Protection 팀의 [Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다.

## <a name="version-110560"></a>버전 1.10.56.0

**릴리스 날짜**: 2017년 9월 18일

이 버전에는 RMS 클라이언트의 MSIPC 버전 1.0.3219.0619가 포함되어 있습니다.

**새로운 기능**:

- 사용자 정의 작업에 대해 구성된 레이블을 지원합니다. Outlook의 경우 이 레이블에 따라 자동으로 Outlook 전달 금지 옵션이 적용됩니다. Word, Excel, PowerPoint 및 파일 탐색기의 경우 이 레이블에 따라 사용자 지정 권한을 지정하라는 메시지가 사용자에게 표시됩니다. 자세한 내용은 [보호에 대해 Azure Information Protection 레이블 구성](../deploy-use/configure-policy-protection.md)을 참조하세요.

- 레이블에 대해 구성할 수 있는 새로운 Office 365 DLP 조건을 지원합니다. 자세한 내용은 [Azure Information Protection 레이블에 대한 조건 구성](../deploy-use/configure-policy-classification.md)을 참조하세요.

- 레이블은 Information Protection 표시줄뿐만 아니라 Office 리본의 **보호** 단추에도 표시됩니다. 

- 다음 Visio 파일 형식에 대한 기본 보호: .vsdm, .vsdx, .vssm, .vssx, .vstm, .vstx

- Azure Portal에서 구성하는 고급 클라이언트 구성을 지원합니다. 이러한 구성은 다음과 같습니다.
    
    - [Outlook에서 전달 금지 단추 숨기기](../rms-client/client-admin-guide-customizations.md#hide-the-do-not-forward-button-in-outlook)
    
    - [사용자가 사용자 지정 권한 옵션을 사용할 수 없음](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
    - [Azure Information Protection 표시줄을 영구적으로 숨기기](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-unavailable-to-users)
    
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

## <a name="version-172100"></a>버전 1.7.210.0

**릴리스 날짜**: 2017년 6월 6일

이 버전에는 RMS 클라이언트의 MSIPC 버전 1.0.2217.1이 포함됩니다.

**새로운 기능**:

- 새 PowerShell cmdlet, [Set-AIPFileClassification](/powershell/module/azureinformationprotection/Set-AIPFileClassification). 이 cmdlet을 실행하면 파일 콘텐츠를 검사한 후 Azure Information Protection 정책에 지정된 조건에 따라 레이블이 지정되지 않은 파일에 자동으로 레이블을 적용합니다.

**수정 사항**:

- 이제 인터넷에 연결되어 있지 않지만 유효한 Azure Information Protection 정책이 지정된 컴퓨터에서는 모든 레이블 지정 및 분류 cmdlet이 지원됩니다.

- 일관성을 위해 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet의 출력 매개 변수는 영국 영어(**IsLabelled**) 미국 영어(**IsLabeled**)로 변경되었습니다. 이 매개 변수를 검색하는 스크립트 또는 자동화 프로세스가 있는 경우 이 매개 변수의 철자를 업데이트하세요.

- 다음을 포함하는 안정성에 대한 일반 수정 내용:

    - Outlook: 충돌, 높은 메모리 사용량 및 메뉴 표시 문제를 수정합니다.
    
    - Word, Excel 및 PowerPoint: 높은 CPU 사용량, 큰 Excel 파일을 저장할 때의 표시 문제 또는 응용 프로그램이 응답을 중지하는 문제를 수정합니다. 
    
    또한 이러한 응용 프로그램에서 SharePoint Online 및 비즈니스용 OneDrive가 있는 Office 2016의 성능을 향상시키기 위해, 파일이 저장될 때(자동으로 저장 또는 사용자가 저장하도록 선택)가 아니라 파일이 닫힐 때 자동 및 권장 레이블이 적용됩니다. 마찬가지로 **모든 문서 및 전자 메일에 레이블이 있어야 함** 설정을 사용하도록 지정되면 파일을 닫을 때까지 레이블을 선택하라는 메시지가 표시되지 않습니다. 예외는 Word 2016 및 Excel 2016이며, 사용자는 **다른 이름으로 저장** 옵션을 선택합니다. 그러면 구성에 따라 이러한 레이블 지정 동작이 트리거됩니다. 

## <a name="version-14210"></a>버전 1.4.21.0

**릴리스 날짜**: 2017년 3월 15일

**요구 사항 변경:**

이전 버전에서 전체 클라이언트에 새로 Microsoft .NET Framework 4.6.2 필수 조건이 도입되었습니다. 권장되지는 않지만, 사용자 지정 매개 변수 **DowngradeDotNetRequirement**을 사용하면 이 필수 조건을 무시할 수 있습니다. 자세한 내용은 관리자 가이드의 [클라이언트 설치 섹션](client-admin-guide.md#how-to-install-the-azure-information-protection-client-for-users)을 참조하세요.

**새로운 기능**:

- 자신, 외부 그룹 또는 다른 조직의 모든 사용자에 대해 Office 응용 프로그램에서 사용자 지정 권한을 설정하는 기능. 자세한 내용은 사용자 가이드의 [문서에 대한 사용자 지정 권한 설정](client-classify-protect.md#set-custom-permissions-for-a-document)을 참조하세요.
    
- 이제 PDF 파일에서 분류 전용을 적용하는 레이블을 지원합니다.

- PDF 파일의 경우 이제 뷰어에서 검색, 확대/축소 및 회전과 같은 옵션을 지원합니다. 이러한 옵션을 사용하려면 파일이 뷰어에 표시되었을 때 마우스 오른쪽 단추로 클릭합니다.

**수정 사항**:

- 매핑된 드라이브 지원을 통한 파일 분류 및 보호.

- Azure Information Protection 클라이언트 뷰어에서 큰 파일(250MB 이상)을 지원합니다. 

- HYOK가 구성되어 있으면, Outlook에서 Azure Rights Management 템플릿 또는 AD RMS 템플릿을 사용하도록 구성된 레이블을 적용할 수 있습니다.

## <a name="version-131552"></a>버전 1.3.155.2

**릴리스 날짜**: 2017년 2월 8일

**새 요구 사항**:

Microsoft .NET Framework

- 이 버전의 Azure Information Protection 클라이언트에는 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 프로그램이 없으면 설치 관리자는 이 프로그램을 다운로드한 후 설치하려고 합니다. Azure Information Protection 클라이언트 설치가 완료된 후 컴퓨터를 다시 시작해야 할 수 있습니다.

- Azure Information Protection 뷰어가 별도로 설치되어 있으면 최소한 Microsoft .NET Framework 4.5.2 버전이 필요하며, 이 프로그램이 없어도 설치 관리자는 다운로드하여 설치하려고 하지 않습니다.

**새로운 기능**:

- Windows용 Rights Management 공유 응용 프로그램을 Azure Information Protection 클라이언트에 결합하는 새로운 통합 클라이언트입니다. 여기에는 다음이 포함됩니다.
    
    - 레이블 및 보호를 적용하기 위해 Windows 파일 탐색기(마우스 오른쪽 단추 클릭)와 통합. 추가 파일 형식 및 여러 파일 선택을 지원합니다.
    - 보호된 문서를 위한 뷰어(SharePoint용 보호된 PDF 포함)
    - 로컬로 또는 네트워크 공유에 저장되는 파일의 레이블을 가져오고 설정하기 위한 PowerShell cmdlet. 이러한 cmdlet은 이전에 RMS 보호 도구(RMSProtection 모듈)와 함께 제공된 cmdlet과 함께 설치됩니다.
    - 적용된 레이블, 적용 방법 및 적용한 사람 등의 정보를 기록하는 클라이언트 사용 로그

이 클라이언트 버전은 2016년 12월에 처음 발표된 미리 보기 클라이언트의 [일반 공급 릴리스](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/)입니다. 이 버전의 클라이언트에 대한 자세한 내용은 다음 가이드를 참조하세요.

- [Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)

- [Azure Information Protection 사용자 가이드](client-user-guide.md)


## <a name="version-1240"></a>버전 1.2.4.0

**릴리스 날짜**: 2016년 10월 27일

**새 기능**:

- Azure Information Protection 클라이언트가 설치되면 사용자가 Office 응용 프로그램에서 실행할 수 있는 진단 테스트 및 다시 설정 옵션: **홈** 탭의 **보호** 그룹에서 **보호**를 클릭하고 **도움말 및 피드백**을 클릭한 다음 **진단 실행**을 클릭합니다. 

    이 옵션에 대한 자세한 내용은 관리자 가이드의 [추가 검사 및 문제 해결](client-admin-guide.md#additional-checks-and-troubleshooting) 섹션을 참조하세요.

**수정 사항**:

- Windows Update 서비스가 비활성화되면 클라이언트 설치가 완료됩니다.

- Office 2016에서 문서를 저장하고 적용한 레이블이 머리글이나 바닥글에 대해 구성되면 커서가 머리글이나 바닥글로 이동하지 않습니다.

- 번들 텍스트 상자의 텍스트에 대해 Word에서 자동 분류가 작동합니다.


## <a name="version-11230"></a>버전 1.1.23.0

**릴리스 날짜**: 2016년 10월 1일

일반 공급.

## <a name="next-steps"></a>다음 단계

클라이언트를 설치하고 사용하는 방법에 대한 자세한 내용은 다음과 같습니다.

- 사용자: [다운로드 및 클라이언트 설치](install-client-app.md)

- 관리자: [Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]