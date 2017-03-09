---
title: "Azure Information Protection 클라이언트&colon; 버전 릴리스 기록"
description: "Windows용 Azure Information Protection 클라이언트 릴리스에의 새로운 사항이나 변경된 사항에 대해 알아보세요."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 343ac5f79902379e45efcb6979a115ba4c00d1c5
ms.openlocfilehash: 503cb76825d0092e8562d39281b1d702edaf6438
ms.lasthandoff: 03/02/2017


---

# <a name="azure-information-protection-client-version-release-history"></a>Azure Information Protection 클라이언트: 버전 릴리스 기록

>*적용 대상: Azure Information Protection*

Azure Information Protection 팀에서는 픽스 및 새 기능을 위해 Azure Information Protection 클라이언트를 정기적으로 업데이트합니다. 클라이언트는 Microsoft 업데이트 카탈로그(범주: **Azure Information Protection**)에 포함되며 언제든지 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 최신 버전을 다운로드할 수 있습니다.

다음 정보를 통해 새로운 기능이나 릴리스 변경을 확인합니다. 가장 최근 릴리스가 먼저 나열됩니다. 일반 공급 이전 버전은 나열되지 않습니다.

> [!NOTE]
> 사소한 수정 사항은 나열되지 않으므로 Azure Information Protection 클라이언트에 문제가 있는 경우 먼저 최신 릴리스의 문제가 아닌지 확인하세요.
>  
> 문제가 지속되면 [지원 옵션 및 커뮤니티 리소스](../get-started/information-support.md#support-options-and-community-resources) 정보를 참조하세요. 또한 Azure Information Protection 팀의 [Yammer 사이트](https://www.yammer.com/askipteam/)에 여러분을 초대합니다.

## <a name="version-131552"></a>버전 1.3.155.2

**릴리스 날짜**: 2017년 2월 8일

**새 요구 사항**:

Microsoft .NET Framework

- 이 버전의 Azure Information Protection 클라이언트에는 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 프로그램이 없으면 설치 관리자는 이 프로그램을 다운로드한 후 설치하려고 합니다. Azure Information Protection 클라이언트 설치가 완료된 후 컴퓨터를 다시 시작해야 할 수 있습니다.

- Azure Information Protection 뷰어가 별도로 설치되어 있으면 최소한 Microsoft .NET Framework 4.5.2 버전이 필요하며, 이 프로그램이 없어도 설치 관리자는 다운로드하여 설치하려고 하지 않습니다.

**새로운 기능**:

- Windows용 Rights Management 공유 응용 프로그램을 Azure Information Protection 클라이언트에 결합하는 새로운 통합 클라이언트입니다. 여기에는 다음이 포함됩니다.
    
    - 레이블 및 보호를 적용하기 위해 Windows 파일 탐색기(마우스 오른쪽 단추 클릭)와 통합. 추가 파일 형식 및 다중 파일 선택을 지원합니다.
    - 보호된 문서를 위한 뷰어(SharePoint용 보호된 PDF 포함)
    - 로컬로 또는 네트워크 공유에 저장되는 파일의 레이블을 가져오고 설정하기 위한 PowerShell cmdlet. 이러한 cmdlet은 이전에 RMS 보호 도구(RMSProtection 모듈)와 함께 제공된 cmdlet과 함께 설치됩니다.
    - 적용된 레이블, 적용 방법 및 적용한 사람 등의 정보를 기록하는 클라이언트 사용 로그

이 클라이언트 버전은 2016년 12월에 처음 발표된 미리 보기 클라이언트의 [일반 공급 릴리스](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/)입니다. 이 버전의 클라이언트에 대한 자세한 내용은 다음 가이드를 참조하세요.

- [Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)

- [Azure Information Protection 사용자 가이드](client-user-guide.md)


## <a name="version-1240"></a>버전 1.2.4.0

**릴리스 날짜**: 2016년 10월 27일

**수정 사항**:

- Windows Update 서비스가 비활성화되면 클라이언트 설치가 완료됩니다.

- Office 2016에서 문서를 저장하고 적용한 레이블이 머리글이나 바닥글에 대해 구성되면 커서가 머리글이나 바닥글로 이동하지 않습니다.

- 번들 텍스트 상자의 텍스트에 대해 Word에서 자동 분류가 작동합니다.

**새 기능**:

- Azure Information Protection 클라이언트가 설치되면 사용자가 Office 응용 프로그램에서 실행할 수 있는 진단 테스트 및 다시 설정 옵션: **홈** 탭의 **보호** 그룹에서 **보호**를 클릭하고 **도움말 및 피드백**을 클릭한 다음 **진단 실행**을 클릭합니다. 

    이 옵션에 대한 자세한 내용은 클라이언트 설치 설명서에서 [설치 또는 연결 상태를 확인하거나 피드백을 보내려면](client-admin-guide.md#additional-checks-to-verify-installation-connection-status-or-send-feedback) 섹션을 참조하세요.

## <a name="version-11230"></a>버전 1.1.23.0

**릴리스 날짜**: 2016년 10월 1일

일반 공급.

## <a name="next-steps"></a>다음 단계

클라이언트를 설치하는 방법에 대한 자세한 정보:

- 사용자: [다운로드 및 클라이언트 설치](install-client-app.md)

- 관리자: [Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
