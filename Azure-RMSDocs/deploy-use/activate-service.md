---
title: "Azure 권한 관리 활성화 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bf5e3561ef24d8f44e791ff7bdc8450a73f79705
ms.openlocfilehash: d66e4e6bca253bc2bf9d12ba22ed0202cba2edaf


---

# Azure 권한 관리 활성화

*적용 대상: Azure 권한 관리, Office 365*

[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)](Azure RMS)를 활성화하면 조직에서 이 정보 보호 솔루션을 지원하는 응용 프로그램 및 서비스를 사용하여 중요한 데이터를 보호할 수 있습니다. 또한 관리자는 조직에서 소유한 보호된 파일 및 전자 메일을 관리하고 모니터링할 수 있습니다. Office, SharePoint 및 Exchange 내에서 IRM(정보 권한 관리) 기능을 사용하고 중요한 파일이나 기밀 파일을 보호하려면 먼저 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 사용하도록 설정해야 합니다.

서비스를 활성화하기 전에 해결되는 비즈니스 문제, 일반적인 몇 가지 사용 사례, 작동 방식 등 Azure 권한 관리에 대해 자세히 알아보려면 [Azure 권한 관리란?](../understand-explore/what-is-azure-rms.md)을 참조하세요.

> [!IMPORTANT]
> [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 활성화하기 전에 조직에 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 서비스가 포함된 서비스 계획이 있는지 확인합니다. 서비스 계획이 없는 경우 Azure RMS를 활성화할 수 없습니다.
>
> 자세한 내용은 [Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.

Azure RMS를 활성화한 후 조직의 모든 사용자는 해당 파일에 정보 보호를 적용할 수 있으며 모든 사용자가 Azure RMS로 보호되는 파일을 열거나 사용할 수 있습니다. 하지만 원하는 경우 단계적 배포용 등록 컨트롤을 사용하여 정보 보호를 적용할 수 있는 사용자를 제한할 수 있습니다. 자세한 내용은 이 문서에서 [단계별 배포용 온보딩 컨트롤 구성](#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

관리 포털에서 Rights Management를 활성화하는 방법에 대한 지침을 보려면 Office 365 관리 센터(미리 보기 또는 클래식)를 사용할지 아니면 Azure 클래식 관리 포털을 사용할지 여부를 선택합니다.


- [Office 365 관리 센터 - 미리 보기](activate-office365-preview.md)
- [Office 365 관리 센터 - 클래식](activate-office365-classic.md)
- [Azure 클래식 포털](activate-azure-classic.md)

또는 Windows PowerShell을 사용하여 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 활성화할 수 있습니다.

1. Azure 권한 관리 관리 모듈을 설치하는 Azure 권한 관리 관리 도구를 설치합니다. 지침은 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

2. Windows PowerShell 세션에서 [Connect-aadrmservice](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx)를 실행하고, 메시지가 표시되면 Azure RMS 테넌트에 대한 전역 관리자 계정 세부 정보를 제공합니다.

3. Azure RMS 서비스를 활성화하는 [Enable-aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx)을 실행합니다.

## 단계적 배포용 등록 컨트롤 구성
일부 사용자만 Azure RMS를 사용하여 즉시 파일을 보호할 수 있게 하려면 [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Windows PowerShell 명령을 사용하여 사용자 등록 컨트롤을 구성할 수 있습니다. Azure RMS를 활성화하기 전이나 후에 이 명령을 실행할 수 있습니다.

> [!IMPORTANT]
> 이 명령을 사용하려면 **2.1.0.0** 버전 이상의 [Azure RMS Windows PowerShell 모듈(영문)](http://go.microsoft.com/fwlink/?LinkId=257721)이 있어야 합니다.
>
> 설치한 버전을 확인하려면 다음을 실행합니다. **(Get-Module aadrm –ListAvailable).Version**

예를 들어 초기에 개체 ID가 fbb99ded-32a0-45f1-b038-38b519009503인 "IT 부서" 그룹의 관리자만 테스트 목적으로 콘텐츠를 보호할 수 있도록 하려면 다음 명령을 사용합니다.

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
이 구성 옵션에 대해서는 그룹을 지정해야 하며 개별 사용자를 지정할 수는 없습니다.

또는 Azure RMS를 사용할 수 있는 라이선스가 부여된 사용자만 콘텐츠를 보호할 수 있게 하려면 다음 명령을 사용합니다.

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
이러한 등록 컨트롤을 사용할 경우 조직의 모든 사용자는 항상 하위 사용자가 보호하는 보호된 콘텐츠를 사용할 수 있지만 클라이언트 응용 프로그램에서 자체적으로 정보 보호를 적용할 수는 없습니다. 예를 들어 Azure RMS가 활성화되면 자동으로 게시된 기본 템플릿 또는 사용자가 구성할 수 있는 사용자 지정 템플릿이 Office 클라이언트에 표시되지 않습니다.  Exchange 등의 서버 쪽 응용 프로그램은 같은 결과를 달성하기 위해 RMS 통합을 위한 자체 사용자별 컨트롤을 구현할 수 있습니다.


## 다음 단계
이제 조직에 대해 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 활성화했으므로 [Azure 권한 관리 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용자 및 관리자에게 배포하기 전에 수행해야 하는 다른 구성 단계가 있는지 확인합니다. 

예를 들어 사용자가 파일에 정보 보호를 적용하기 쉽도록 [사용자 지정 템플릿](configure-custom-templates.md)을 사용하고, [RMS 커넥터](deploy-rms-connector.md)를 설치하여 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용할 온-프레미스 서버를 연결하고, 모든 장치에서 모든 파일 형식 보호를 지원하는 [Rights Management 공유 응용 프로그램](../rms-client/sharing-app-windows.md)을 배포할 수도 있습니다. 

Exchange Online, SharePoint Online 등의 Office 서비스에서 해당 IRM(정보 권한 관리) 기능을 사용하려면 추가 구성이 필요합니다. 사용자 응용 프로그램이 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]에서 작동하는 방식에 대한 자세한 내용은 [응용 프로그램이 Azure 권한 관리를 지원하는 방식](../understand-explore/applications-support.md)을 참조하세요.




<!--HONumber=Jun16_HO4-->


