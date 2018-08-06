---
title: Azure Rights Management 활성화 - AIP
description: 조직에서 이 정보 보호 솔루션을 지원하는 응용 프로그램 및 서비스를 사용하여 문서 및 전자 메일 보호를 시작할 수 있도록 하려면 Azure Rights Management 서비스를 활성화해야 합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/06/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ec1de298a5baa09132af524f0556badbf99d7955
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473885"
---
# <a name="activating-azure-rights-management"></a>Azure 권한 관리 활성화

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> 이 구성 정보는 조직의 모든 사용자에게 적용되는 서비스를 담당하는 관리자를 위해 작성되었습니다. 특정 응용 프로그램용 Rights Management 기능을 사용하기 위한 사용자 도움말 및 정보 또는 권한으로 보호된 파일 또는 메일을 여는 방법에 대한 정보를 원하는 경우 응용 프로그램을 함께 제공되는 지침 및 도움말을 사용하세요.
>
> 예를 들어 Office 응용 프로그램의 경우 도움말 아이콘을 클릭하고 **Rights Management** 또는 **IRM**과 같은 검색 용어를 입력합니다. Windows용 Azure Information Protection 클라이언트의 경우 [Azure Information Protection 클라이언트 사용자 가이드](../rms-client/client-user-guide.md)를 참조하세요.
>
> 서비스에 대한 기술 지원 및 기타 질문은 [지원 옵션 및 커뮤니티 리소스](../information-support.md#support-options-and-community-resources) 정보를 참조하세요.

Azure Information Protection용 Azure Rights Management 서비스가 조직에 활성화되면, 관리자와 사용자는 이 정보 보호 솔루션을 지원하는 응용 프로그램 및 서비스를 사용하여 중요한 데이터 보호를 시작할 수 있습니다. 또한 관리자는 조직에서 소유한 보호된 문서 및 이메일을 관리하고 모니터링할 수 있습니다. 


## <a name="do-you-need-to-activate-azure-rights-management"></a>Azure Rights Management를 활성화해야 하나요?

Azure Rights Management가 포함된 서비스 계획을 가지고 있는 경우, 서비스를 활성화하지 않아도 됩니다.

- **Azure Rights Management 또는 Azure Information Protection이 포함된 구독을 2018년 2월 말경 또는 그 이후에 얻은 경우:** 서비스가 자동으로 활성화됩니다. 사용자 또는 조직의 다른 전역 관리자가 Azure Rights Management를 비활성하지 않으면 서비스를 활성화할 필요가 없습니다.

- **Azure Rights Management 또는 Azure Information Protection이 포함된 구독을 2018년 2월 이전 또는 2월 중에 얻은 경우:** 테넌트가 Exchange Online을 사용하는 경우 Microsoft에서 이러한 구독에 대해 Azure Rights Management 서비스를 활성화하기 시작합니다. 이러한 구독의 경우 [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration?view=exchange-ps)을 실행할 때 **AutomaticServiceUpdateEnabled**가 **false**로 설정되지 않는 한 서비스가 활성화될 때 2018년 8월 1일에 자동 활성화가 롤아웃되기 시작합니다. 

후속 시나리오 중 어느 것도 적용되지 않는 경우 보호 서비스를 수동으로 활성화해야 합니다. 

서비스가 활성화되면 조직의 모든 사용자가 해당 문서 및 메일에 정보 보호를 적용할 수 있으며, 모든 사용자가 Azure Rights Management 서비스로 보호되는 문서 및 메일을 열거나 사용할 수 있습니다. 하지만 원하는 경우 단계적 배포용 등록 컨트롤을 사용하여 정보 보호를 적용할 수 있는 사용자를 제한할 수 있습니다. 자세한 내용은 이 문서에서 [단계별 배포용 온보딩 컨트롤 구성](#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

## <a name="how-to-activate-or-confirm-the-status-of-the-azure-rights-management-service"></a>Azure Rights Management 서비스의 상태를 활성화하거나 확인하는 방법 

> [!IMPORTANT]
> 조직에서 사용하도록 AD RMS(Active Directory Rights Management Services)를 배포한 경우 Azure Rights Management 서비스를 활성화하지 마세요. [추가 정보](prepare-environment-adrms.md)

이 데이터 보호 솔루션을 사용하려면 조직에 Azure Information Protection에서 Azure Rights Management 서비스가 포함된 서비스 계획이 있어야 합니다. 이렇게 하지 않으면 Azure Rights Management 서비스는 활성화할 수 없습니다. 다음 중 하나가 있어야 합니다.

- [Azure Information Protection 요금제](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- [Rights Management가 포함된 Office 365 요금제](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Azure Rights Management 서비스가 활성화되면 조직의 모든 사용자가 해당 문서 및 메일에 정보 보호를 적용할 수 있으며, 모든 사용자가 Azure Rights Management 서비스로 보호되는 문서 및 메일을 열거나 사용할 수 있습니다. 하지만 원하는 경우 단계적 배포용 등록 컨트롤을 사용하여 정보 보호를 적용할 수 있는 사용자를 제한할 수 있습니다. 자세한 내용은 이 문서에서 [단계별 배포용 온보딩 컨트롤 구성](#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

## <a name="choosing-your-activation-method"></a>정품 인증 방법 선택

관리 포털에서 Rights Management 서비스를 활성화하는 방법에 대한 지침을 보려면 Office 365 관리 센터를 사용할지, Azure Portal을 사용할지를 선택합니다.

- [Office 365 관리 센터](activate-office365.md) - 전역 관리자 계정 필요

- [Azure Portal](activate-azure.md) - 전역 관리자 계정이 필요하지 않음

또는 다음의 PowerShell 명령을 사용할 수 있습니다.

1. AADRM 모듈을 설치하여 보호 서비스를 구성하고 관리합니다. 자세한 지침은 [AADRM PowerShell 모듈 설치](../deploy-use/install-powershell.md)를 참조하세요.

2. PowerShell 세션에서 [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice)를 실행하고, 메시지가 표시되면 Azure Information Protection 테넌트에 대한 전역 관리자 계정 세부 정보를 제공합니다.

3. [Get-Aadrm](/powershell/aadrm/vlatest/get-aadrm)을 실행하여 Azure Rights Management 서비스가 활성화되었는지 확인합니다. **Enabled** 상태는 활성화를 확인합니다. **비활성화**는 서비스가 비활성화되었음을 나타냅니다.

4. 서비스를 활성화하려면 [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm)을 실행합니다.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>단계적 배포용 등록 컨트롤 구성
일부 사용자만 Azure Rights Management를 사용하여 즉시 문서 및 메일을 보호할 수 있게 하려면 [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) PowerShell 명령을 사용하여 사용자 온보딩 컨트롤을 구성할 수 있습니다. Azure Rights Management 서비스를 활성화하기 전이나 후에 이 명령을 실행할 수 있습니다.

> [!IMPORTANT]
> 이 명령을 사용하려면 **2.1.0.0** 버전 이상의 [Azure Rights Management PowerShell 모듈](https://go.microsoft.com/fwlink/?LinkId=257721)이 있어야 합니다.
>
> 설치한 버전을 확인하려면 다음을 실행합니다. **(Get-Module aadrm –ListAvailable).Version**

예를 들어 초기에 개체 ID가 fbb99ded-32a0-45f1-b038-38b519009503인 "IT 부서" 그룹의 관리자만 테스트 목적으로 콘텐츠를 보호할 수 있도록 하려면 다음 명령을 사용합니다.

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fbb99ded-32a0-45f1-b038-38b519009503"
```

이 구성 옵션에 대해서는 그룹을 지정해야 하며 개별 사용자를 지정할 수는 없습니다. 그룹의 개체 ID를 얻으려면 Azure AD PowerShell을 사용할 수 있습니다. 예를 들어 버전 1.0의 모듈인 경우 [Get-MsolGroup](/powershell/msonline/v1/get-msolgroup) 명령을 사용합니다. Azure Portal에서 그룹의 **개체 ID**를 복사할 수도 있습니다.

또는 Azure Information Protection을 사용할 수 있는 라이선스가 부여된 사용자만 콘텐츠를 보호할 수 있게 하려면 다음 명령을 사용합니다.

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True
```

온보딩 컨트롤을 더 이상 사용할 필요가 없으면 그룹을 사용하든 라이선싱 옵션을 사용하든 다음을 실행합니다.

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
```

이 cmdlet 및 추가 예제에 대한 자세한 내용은 [Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy) 도움말을 참조하세요.

이러한 등록 컨트롤을 사용할 경우 조직의 모든 사용자는 항상 하위 사용자가 보호하는 보호된 콘텐츠를 사용할 수 있지만 클라이언트 응용 프로그램에서 자체적으로 정보 보호를 적용할 수는 없습니다. 예를 들어 Azure Rights Management 서비스가 활성화되면 자동으로 게시된 기본 템플릿 또는 사용자가 구성할 수 있는 사용자 지정 템플릿이 Office 앱에 표시되지 않습니다. Exchange 등의 서버 쪽 응용 프로그램은 같은 결과를 달성하기 위해 Rights Management 통합을 위한 자체 사용자별 컨트롤을 구현할 수 있습니다. 예를 들어, 사용자가 웹용 Outlook에서 메일을 보호하지 못하도록 하려면 [Set-OwaMailboxPolicy](/powershell/module/exchange/client-access/set-owamailboxpolicy?view=exchange-ps)를 사용하여 *IRMEnabled* 매개 변수를 *$false*로 설정합니다.


## <a name="next-steps"></a>다음 단계
Azure Rights Management 서비스가 조직에 활성화되면, [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)을 사용하여 Azure Information Protection을 사용자 및 관리자에게 배포하기 전에 수행해야 하는 다른 구성 단계가 있는지 확인합니다. 

예를 들어, 사용자가 파일에 정보 보호를 적용하기 쉽도록 [템플릿](configure-policy-templates.md)을 사용하고, [Rights Management 커넥터](deploy-rms-connector.md)를 설치하여 Azure Rights Management를 사용할 온-프레미스 서버를 연결하며, 모든 장치에서 모든 파일 형식을 보호하도록 지원하는 [Azure Information Protection 클라이언트](../rms-client/aip-client.md)를 배포할 수 있습니다. 

Exchange Online, SharePoint Online 등의 Office 서비스에서 해당 IRM(정보 권한 관리) 기능을 사용하려면 추가 구성이 필요합니다. 사용자 응용 프로그램이 Rights Management Service에서 작동하는 방식에 대한 자세한 내용은 [응용 프로그램에서 Azure Rights Management Service를 지원하는 방법](../applications-support.md)을 참조하세요.


