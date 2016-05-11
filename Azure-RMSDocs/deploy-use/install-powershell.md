---
# required metadata

title: Azure 권한 관리용 Windows PowerShell 설치 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리용 Windows PowerShell 설치
다음 정보를 참조하여 Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)](Azure RMS)용 Windows PowerShell을 설치합니다.

인터넷에 연결되어 있고 다음 섹션에 나열된 필수 구성 요소를 충족하는 컴퓨터를 사용하여 명령줄에서 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 관리하는 데 이 Windows PowerShell 모듈을 사용할 수 있습니다. [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell은 자동화용 스크립팅을 지원하거나 고급 구성 시나리오에 필요할 수 있습니다. 모듈에서 지원하는 관리 작업 및 구성에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Azure 권한 관리 관리](administer-powershell.md)를 참조하세요.

## 필수 구성 요소
아래 표에는 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell을 설치 및 사용하기 위한 필수 조건이 나와 있습니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 모듈을 지원하는 Windows 버전|지원되는 운영 체제 목록은 **Azure Rights Management 관리 도구 다운로드 페이지** 의 [시스템 요구 사항](http://go.microsoft.com/fwlink/?LinkId=257721)섹션에서 확인할 수 있습니다.|
|최소 Windows PowerShell 버전: 2.0|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 모듈은 Windows PowerShell 2.0부터 지원되기 시작했습니다.<br /><br />기본적으로 대부분의 Windows 운영 체제를 설치할 때는 Windows PowerShell 버전 2.0 이상이 함께 설치됩니다. Windows PowerShell 2.0을 설치해야 하는 경우 [Windows PowerShell 2.0 설치](http://msdn.microsoft.com/library/ff637750.aspx)를 참조하세요.<br /><br />팁: Windows PowerShell 세션에서 **$PSVersionTable**을 입력하면 현재 실행 중인 Windows PowerShell 버전을 확인할 수 있습니다.|
|최소 Microsoft .NET Framework 버전: 4.5<br /><br />참고: 이 버전의 Microsoft .NET Framework는 최신 운영 체제에 포함되어 있으므로 클라이언트 운영 체제가 Windows 8.0보다 낮거나 서버 운영 체제가 Windows Server 2012보다 낮은 경우에만 수동으로 설치해야 합니다.|Microsoft .NET Framework의 최소 버전을 아직 설치하지 않은 경우 [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)를 다운로드할 수 있습니다.<br /><br />[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 관리 모듈이 사용하는 일부 클래스에는 이 Microsoft .NET Framework의 최소 버전이 필요합니다.|
|Microsoft Online Services 로그인 도우미 7.0|Microsoft Online Services 로그인 도우미는 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 인증에 필요합니다.<br /><br />자세한 내용은 [다운로드 센터: IT 전문가용 Microsoft Online Services 도우미 RTW](http://www.microsoft.com/en-us/download/details.aspx?id=41950)를 참조하세요.|

## Rights Management 관리 모듈을 설치하는 방법

1.  Microsoft 다운로드 센터로 이동하여 Windows PowerShell용 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 관리 모듈이 포함된 [Azure Rights Management 관리 도구를 다운로드](https://go.microsoft.com/fwlink/?LinkId=257721)합니다.

2.  [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 설치 관리자 파일을 다운로드하여 저장한 로컬 폴더에서 사용 중인 플랫폼용으로 다운로드한 실행 파일(WindowsAzureADRightsManagementAdministration_x64 또는 WindowsAzureADRightsManagementAdministration_x86.exe)을 두 번 클릭하여 Azure AD Rights Management 관리 도구 설치 마법사를 시작합니다.

3.  마법사를 완료합니다.

이제 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]용 Windows PowerShell이 설치되었습니다.

## 다음 단계
사용 가능한 cmdlet를 확인하려면 **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작하고 다음 명령을 입력합니다.

```
Get-Command -Module aadrm
```
특정 cmdlet의 도움말을 확인하려면 `the Get-Help <cmdlet_name>` 명령을 사용합니다.

추가 정보는 다음 항목을 참조하세요.

-   사용 가능한 전체 cmdlet 목록: [Azure Rights Management cmdlet](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Windows PowerShell을 지원하는 주요 구성 시나리오 목록: [Windows PowerShell을 사용하여 Azure 권한 관리 관리](administer-powershell.md)

[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 서비스를 구성하는 명령을 실행하려면 먼저 [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet을 사용하여 서비스에 연결해야 합니다. 원하는 구성 명령을 실행했으면 [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet를 사용하여 서비스에서 연결을 끊습니다.

> [!NOTE]
> [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 아직 활성화하지 않은 경우 서비스에 연결한 후에 [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) cmdlet을 사용하여 활성화할 수 있습니다.

## 참고 항목
[Windows PowerShell을 사용하여 Azure 권한 관리 관리](administer-powershell.md)


<!--HONumber=Apr16_HO3-->


