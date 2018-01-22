---
title: "Azure Rights Management용 PowerShell 설치 - AIP"
description: "Azure Information Protection의 Azure Rights Management 서비스용 Windows PowerShell 설치 지침 이 모듈의 이름은 AADRM입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0deb1b47036a4439f393bf7351c5d149a8e85559
ms.sourcegitcommit: 152b4855e23f443c04ac27fedfdc1dcc9fda8949
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2018
---
# <a name="installing-windows-powershell-for-azure-rights-management"></a>Azure 권한 관리용 Windows PowerShell 설치

>*적용 대상: Azure Information Protection, Office 365*

다음 정보를 통해 Azure Information Protection의 Azure Rights Management 서비스에 대한 Windows PowerShell 모듈을 설치할 수 있습니다.

인터넷에 연결되어 있고 다음 섹션에 나열된 필수 구성 요소를 충족하는 컴퓨터를 사용하여 명령줄에서 Azure Rights Management 서비스를 관리하는 데 이 PowerShell 모듈을 사용할 수 있습니다. [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell은 자동화용 스크립팅을 지원하거나 고급 구성 시나리오에 필요할 수 있습니다. 모듈에서 지원하는 관리 작업 및 구성에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Azure 권한 관리 관리](administer-powershell.md)를 참조하세요.

## <a name="prerequisites"></a>전제 조건
아래 표에는 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell을 설치 및 사용하기 위한 필수 조건이 나와 있습니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 모듈을 지원하는 Windows 버전|지원되는 운영 체제 목록은 **Azure Rights Management 관리 도구 다운로드 페이지** 의 [시스템 요구 사항](http://go.microsoft.com/fwlink/?LinkId=257721)섹션에서 확인할 수 있습니다.|
|최소 Windows PowerShell 버전: 2.0<br /><br /> |기본적으로 대부분의 Windows 운영 체제를 설치할 때는 Windows PowerShell 버전 2.0 이상이 함께 설치됩니다. 이 지원되는 최소 버전을 설치해야 하는 경우 [Windows PowerShell 2.0 설치](https://msdn.microsoft.com/library/ff637750.aspx)를 참조하세요.<br /><br />팁: PowerShell 세션에서 `$PSVersionTable`을 입력하면 실행 중인 Windows PowerShell 버전을 확인할 수 있습니다. <br /><br /> 이 최소 버전이 있는 경우 `Import-Module AADRM`을 실행하여 PowerShell 세션에 모듈을 수동으로 로드해야 해야만 Rights Management 관리 모듈의 cmdlet을 사용할 수 있습니다. Windows PowerShell v3 이상이 있는 경우 모듈이 자동으로 로드되고 이 추가 명령이 필요하지 않습니다.|
|최소 Microsoft .NET Framework 버전: 4.5<br /><br />참고: 이 버전의 Microsoft .NET Framework는 최신 운영 체제에 포함되어 있으므로 클라이언트 운영 체제가 Windows 8.0보다 낮거나 서버 운영 체제가 Windows Server 2012보다 낮은 경우에만 수동으로 설치해야 합니다.|Microsoft .NET Framework의 최소 버전을 아직 설치하지 않은 경우 [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)를 다운로드할 수 있습니다.<br /><br />[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 모듈이 사용하는 일부 클래스에는 이 Microsoft .NET Framework의 최소 버전이 필요합니다.|

> [!NOTE]
> Rights Management 관리 모듈의 2.5.0.0 버전부터는 Microsoft Online Services 로그인 도우미가 더 이상 필요하지 않습니다.
> 
> 이전 버전의 Rights Management 관리 모듈이 설치되어 있는 경우 **프로그램 및 기능**을 사용하여 **Windows Azure AD Rights Management 관리**를 제거한 후 최신 버전을 설치하세요.


## <a name="how-to-install-the-rights-management-administration-module"></a>Rights Management 관리 모듈을 설치하는 방법

1. Microsoft 다운로드 센터로 이동하여 Windows PowerShell용 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 관리 모듈이 포함된 [Azure Rights Management 관리 도구](https://go.microsoft.com/fwlink/?LinkId=257721)를 찾습니다.

2. [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 설치 프로그램 파일, **WindowsAzureADRightsManagementAdministration_x64**를 다운로드하여 저장합니다. 그런 다음 이 파일을 두 번 클릭하여 Azure AD Rights Management 관리 설정 마법사를 시작합니다.

3.  마법사를 완료합니다.

이제 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell이 설치되었습니다.

## <a name="next-steps"></a>다음 단계
Windows PowerShell 세션을 시작하고 설치된 모듈의 버전을 확인합니다. 이 검사는 이전 버전에서 업그레이드한 경우에 특히 중요합니다.

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

[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 서비스를 구성하는 명령을 실행하려면 먼저 [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 서비스에 연결해야 합니다. 

최상의 방법으로 구성 명령을 실행했으면 [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 서비스에서 연결을 끊습니다. 연결을 끊지 않으면 비활성 기간 후 연결이 자동으로 끊어집니다. 자동 연결 끊기 동작으로 인해 가끔 PowerShell 세션에서 다시 연결해야 할 수 있습니다. 

> [!NOTE]
> Azure Rights Management 서비스가 아직 활성화하지 않은 경우 서비스에 연결한 후에 [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm) cmdlet을 사용하여 활성화할 수 있습니다.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]