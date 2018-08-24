---
title: AADRM-AIP용 PowerShell 설치
description: Azure Information Protection의 Azure Rights Management 서비스용 Windows PowerShell 설치 지침 이 모듈의 이름은 AADRM입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/23/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5fe03b296020e28234e439f634074746ff1bd677
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808885"
---
# <a name="installing-the-aadrm-powershell-module"></a>AADRM PowerShell 모듈 설치

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

다음 정보를 통해 Azure Information Protection의 Azure Rights Management 서비스에 대한 Windows PowerShell 모듈을 설치할 수 있습니다. 이 모듈의 이름은 AADRM입니다.

인터넷에 연결되어 있고 다음 섹션에 나열된 필수 구성 요소를 충족하는 컴퓨터를 사용하여 명령줄에서 Azure Rights Management 서비스를 관리하는 데 이 PowerShell 모듈을 사용할 수 있습니다. Azure Rights Management용 Windows PowerShell은 자동화에 대한 스크립팅을 지원하거나 고급 구성 시나리오에 필요할 수 있습니다. 모듈에서 지원하는 관리 작업 및 구성에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Azure 권한 관리 관리](administer-powershell.md)를 참조하세요.

## <a name="prerequisites"></a>전제 조건
이 테이블에는 Azure Information Protection의 Azure Rights Management 서비스에 AADRM PowerShell 모듈을 설치하고 사용하기 위한 필수 구성 요소를 포함합니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|최소 Windows PowerShell 버전: 3.0|PowerShell 세션에서 `$PSVersionTable`을 입력하면 실행 중인 Windows PowerShell 버전을 확인할 수 있습니다. <br /><br /> Windows PowerShell의 최신 버전을 설치해야 할 경우 [기존 Windows PowerShell 업그레이드](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell)를 참조하세요.|
|최소 Microsoft .NET Framework 버전: 4.5<br /><br />참고: 이 버전의 Microsoft .NET Framework는 최신 운영 체제에 포함되어 있으므로 클라이언트 운영 체제가 Windows 8.0보다 낮거나 서버 운영 체제가 Windows Server 2012보다 낮은 경우에만 수동으로 설치해야 합니다.|Microsoft .NET Framework의 최소 버전을 아직 설치하지 않은 경우 [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)를 다운로드할 수 있습니다.<br /><br />AADRM 모듈이 사용하는 일부 클래스에는 이 Mrciosoft .NET Framework의 최소 버전이 필요합니다.|

AADRM 모듈의 2.5.0.0 버전부터는 Microsoft Online Services 로그인 도우미가 더 이상 필요하지 않습니다.

> [!NOTE]
> 
> Azure Rights Management 관리 도구와 함께 AADRM 모듈 버전을 설치한 경우 **프로그램 및 기능**을 사용하여 **Microsoft Azure AD Rights Management 관리**를 제거한 후 PowerShell 갤러리에서 최신 버전의 AADRM 모듈을 설치합니다.


## <a name="how-to-install-the-aadrm-module"></a>AADRM 모듈를 설치하는 방법

AADRM 모듈이 [PowerShell 갤러리](/powershell/gallery/readme)로 이동했고 Microsoft 다운로드 센터에서 더 이상 제공되지 않습니다. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>PowerShell 갤러리에서 AADRM 모듈 설치 

PowerShell 갤러리를 처음 사용하는 경우 [PowerShell 갤러리 시작](/powershell/gallery/psgallery/psgallery_gettingstarted)을 참조하세요. PowerShellGet 모듈 및 NuGet 공급자 설치를 포함하여 갤러리 요구 사항에 대한 지침을 따릅니다.

PowerShell 갤러리에서 AADRM 모듈에 대한 세부 정보를 보려면 [AADRM 페이지](https://www.powershellgallery.com/packages/AADRM)를 방문하세요.

AADRM 모듈을 설치하려면 **관리자 권한으로 실행** 옵션으로 PowerShell 세션을 시작하고 다음을 입력합니다.

    Install-Module -Name AADRM

신뢰할 수 없는 리포지토리에서 설치하는 경우에 대한 경고가 표시되면 Y 키를 눌러 확인하면 됩니다. 또는 N 키를 누르고 `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` 명령을 사용하여 PowerShell 갤러리를 신뢰할 수 있는 리포지토리로 구성한 다음, 명령을 다시 실행하여 AADRM 모듈을 설치합니다.  

이전 버전의 AADRM 모듈을 갤러리에서 설치한 경우에는 다음을 입력하여 최신 버전으로 업데이트합니다.

    Update-Module -Name AADRM


## <a name="next-steps"></a>다음 단계
Windows PowerShell 세션에서 설치된 모듈의 버전을 확인합니다. 이 검사는 이전 버전에서 업그레이드한 경우에 특히 중요합니다.

```
(Get-Module AADRM –ListAvailable).Version
```

참고: 이 명령이 실패하는 경우 먼저 **Import-module AADRM**을 실행합니다.

사용할 수 있는 cmdlet을 보려면 다음을 입력합니다.

```
Get-Command -Module AADRM
```

`Get-Help <cmdlet_name>` 명령을 사용하여 특정 cmdlet에 대한 도움말을 확인하고 **-online** 매개 변수를 사용하여 Microsoft 설명서 사이트에서 최신 도움말을 확인합니다. 예를 들면 다음과 같습니다.

```
Get-Help Connect-AadrmService -online
```

추가 정보는 다음 항목을 참조하세요.

-   사용 가능한 전체 cmdlet 목록: [AADRM 모듈](/powershell/aadrm/vlatest/rightsmanagement)

-   PowerShell을 지원하는 주요 구성 시나리오 목록: [Windows PowerShell을 사용하여 Azure Rights Management 관리](administer-powershell.md)

Azure Rights Management 서비스를 구성하는 명령을 실행하려면 먼저 [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 서비스에 연결해야 합니다. 최상의 방법으로 구성 명령을 실행했으면 [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 서비스에서 연결을 끊습니다. 연결을 끊지 않으면 비활성 기간 후 연결이 자동으로 끊어집니다. 자동 연결 끊기 동작으로 인해 가끔 PowerShell 세션에서 다시 연결해야 할 수 있습니다. 

> [!NOTE]
> Azure Rights Management 서비스가 아직 활성화하지 않은 경우 서비스에 연결한 후에 [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm) cmdlet을 사용하여 활성화할 수 있습니다.

