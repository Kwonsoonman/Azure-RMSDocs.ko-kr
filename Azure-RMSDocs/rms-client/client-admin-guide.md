---
title: "Azure Information Protection 클라이언트 관리자 가이드"
description: "Windows용 Azure Information Protection 클라이언트 배포를 담당하는 엔터프라이즈 네트워크의 관리자를 위한 지침과 정보를 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e3910ecc2bed3f95660be86b6139e568815f24a0
ms.sourcegitcommit: ea03477312b64c0a846701e46d991fe2c85b3a1f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2017
---
# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection 클라이언트 관리자 가이드

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

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

- 사용자가 분류 레이블을 선택할 수 있는 Azure Information Protection 표시줄을 설치하는 Office 추가 기능과 추가 옵션용 리본의 **보호** 단추

- 파일에 분류 레이블 및 보호를 적용하기 위한 Windows 파일 탐색기의 오른쪽 클릭 옵션

- 네이티브 응용 프로그램으로 열 수 없을 때 보호된 파일을 표시하는 뷰어

- 파일에서 분류 레이블 및 보호를 적용 및 제거하기 위한 PowerShell 모듈

- Azure RMS(Azure Rights Management) 또는 AD RMS(Active Directory Rights Management Services)와 통신하는 Rights Management 클라이언트

Azure Information Protection 클라이언트는 해당 Azure 서비스인 Azure Information Protection와 해당 데이터 보호 서비스인 Azure Rights Management에서 가장 잘 작동됩니다. 몇 가지 제한 사항이 있으나 Azure Information Protection 클라이언트는 온-프레미스 버전의 Rights Management인 AD RMS에도 잘 작동합니다. Azure Information Protection 및 AD RMS에서 지원하는 기능을 포괄적으로 비교한 내용을 보려면 [Azure Information Protection과 AD RMS 비교](../understand-explore/compare-azure-rms-ad-rms.md)를 참조하세요. 

AD RMS가 있고 Azure Information Protection으로 마이그레이션하려면 [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 배포해야 하나요?

다음이 적용될 경우 Azure Information Protection 클라이언트를 배포합니다.

- Office 응용 프로그램(Word, Excel, PowerPoint, Outlook) 내에서 레이블을 선택하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- 추가 파일 형식, 다중 선택 및 폴더를 지원하는 파일 탐색기를 사용하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- PowerShell 명령을 사용하여 문서를 분류(및 필요에 따라 보호)하는 스크립트를 실행하려고 합니다.

- 네이티브 응용 프로그램이 설치되어 있지 않거나 이러한 문서를 열 수 없을 때 보호된 문서를 보려고 합니다.

- 파일 탐색기를 사용하거나 PowerShell 명령을 사용하여 파일을 보호하려고 합니다.

- 사용자 및 관리자가 보호된 문서를 추적하고 해지할 수 있게 허용하려고 합니다.

- 데이터 복구를 위해 대량으로 파일 및 컨테이너에서 암호화를 제거(보호 해제)하려고 합니다.

- Office 2010을 실행하며, Azure Rights Management 서비스를 사용하여 문서 및 전자 메일 메시지를 보호하려고 합니다.

Office 응용 프로그램의 Azure Information Protection 클라이언트 추가 기능, 조직에 대한 분류 레이블 및 리본의 새 **보호** 단추를 보여 주는 예제:

![기본 정책이 적용된 Azure Information Protection 표시줄](../media/word2016-calloutsv2.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>사용자를 위해 Azure Information Protection 클라이언트를 설치하는 방법

클라이언트를 설치하기 전에 컴퓨터에 Azure Information Protection 클라이언트에 필요한 운영 체제 버전 및 응용 프로그램이 있는지 확인합니다([Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)). 

그런 후 Azure Information Protection 클라이언트에 필요할 수 있는 추가 필수 구성 요소를 확인합니다.

### <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 추가 필수 구성 요소

- Microsoft .NET Framework 4.6.2
    
    기본적으로 Azure Information Protection 클라이언트를 전체 설치하려면 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 프로그램이 없으면 설치 관리자는 이 필수 구성 요소를 다운로드한 후 설치하려고 합니다. 이 필수 구성 요소가 클라이언트 설치의 일부로 설치된 경우 컴퓨터를 다시 시작해야 합니다. 권장되지는 않지만 [사용자 지정 설치 매개 변수](#more-information-about-the-downgradedotnetrequirement-installation-parameter)를 사용하면 이러한 필수 구성 요소를 무시할 수 있습니다.

- Microsoft .NET Framework 4.5.2
    
    Azure Information Protection 뷰어가 별도로 설치되어 있으면 최소한 Microsoft .NET Framework 4.5.2 버전이 필요하며, 이 프로그램이 없어도 설치 관리자는 다운로드하여 설치하려고 하지 않습니다.

- Windows PowerShell 버전 4.0
    
    클라이언트용 PowerShell 모듈에는 이전 운영 체제에 설치해야 할 수도 있는 Windows PowerShell 버전 4.0이 필요합니다. 자세한 내용은 [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx)(Windows PowerShell 4.0을 설치하는 방법)을 참조하세요. 설치 관리자는 이러한 필수 구성 요소를 확인하거나 설치하지 않습니다. 실행 중인 Windows PowerShell 버전을 확인하려면 PowerShell 세션에 `$PSVersionTable`을 입력합니다.

- Microsoft Online Services 로그인 도우미 7.250.4303.0
    
    Office 2010을 실행하는 컴퓨터에는 Microsoft Online Services 로그인 도우미 버전 7.250.4303.0이 필요합니다. 이 버전은 클라이언트 설치에 포함되어 있습니다. 최신 버전의 로그인 도우미가 있는 경우 먼저 제거한 후에 Azure Information Protection 클라이언트를 설치해야 합니다. 예를 들어 버전을 확인하고 **제어판** > **프로그램 및 기능** > **프로그램 제거 또는 변경**을 사용하여 로그인 도우미를 제거합니다.

- KB 2533623
    
    Windows 7 서비스 팩 1을 실행하는 컴퓨터에는 KB 2533623이 필요합니다. 이 업데이트에 대한 자세한 내용은 [Microsoft 보안 공지: 비보안 라이브러리 로드 시 원격 코드 실행 허용](https://support.microsoft.com/en-us/kb/2533623)을 참조하세요. 이 업데이트를 직접 설치하거나, 설치하는 다른 업데이트로 대체될 수도 있습니다.
    
    이 업데이트가 필요한데 아직 설치되지 않은 경우 클라이언트 설치에서 설치해야 한다는 경고 메시지가 표시됩니다. 클라이언트가 설치된 후에 이 업데이트를 설치할 수 있지만 일부 작업이 차단되며 메시지가 다시 표시됩니다.  

> [!IMPORTANT]
> Azure Information Protection 클라이언트를 설치하려면 로컬 관리 권한이 필요합니다.

### <a name="options-to-install-the-azure-information-protection-client-for-users"></a>사용자를 위해 Azure Information Protection 클라이언트를 설치하는 옵션

사용자를 위해 클라이언트를 설치하는 옵션에는 다음 세 가지가 있습니다.

**Windows 업데이트**: Azure Information Protection 클라이언트는 Microsoft 업데이트 카탈로그에 포함되어 있으므로 카탈로그를 사용하는 소프트웨어 업데이트 서비스를 사용하여 클라이언트를 설치하고 업데이트할 수 있습니다.

**클라이언트의 실행 파일(.exe) 버전 실행**: 대화형 또는 자동으로 실행할 수 있는 권장 설치 방법입니다. 이 방법은 가장 유연하며, 설치 관리자가 많은 필수 구성 요소를 확인하고 누락된 필수 구성 요소를 자동으로 설치할 수 있으므로 권장됩니다. [지침](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Windows installer(.msi) 버전의 클라이언트 배포**: 그룹 정책, Configuration Manager 및 Microsoft Intune 등의 중앙 배포 메커니즘을 사용하는 자동 설치에만 지원됩니다. 이 방법은 Intune 및 MDM(모바일 장치 관리)에 의해 관리되는 Windows 10 PC에서 필요합니다. 이러한 컴퓨터의 경우 실행 파일로 설치하도록 지원되지 않기 때문입니다. 그러나 이 설치 방법을 사용하면 실행 파일용 설치 관리자가 각 컴퓨터에 대해 수행하는 종속 소프트웨어를 수동으로 확인한 후 설치 또는 제거해야 합니다. [지침](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>실행 파일 설치 관리자를 사용하여 Azure Information Protection 클라이언트를 설치하려면

Microsoft 업데이트 카탈로그를 사용하지 않거나 Intune 같은 중앙 배포 방법을 사용하여 .msi를 배포하는 경우 다음 지침에 따라 클라이언트를 설치합니다.

1. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트 실행 파일 버전을 다운로드합니다. 
    
    미리 보기 버전이 제공되는 경우 이 버전을 테스트용으로만 보관하세요. 이 버전은 프로덕션 환경의 최종 사용자를 위한 것이 아닙니다. 

2. 기본 설치의 경우 **AzInfoProtection.exe**와 같은 실행 파일을 실행하면 됩니다. 그렇지만 설치 옵션을 보려면 먼저 **/help**: `AzInfoProtection.exe /help`를 사용하여 실행 파일을 실행합니다.

    예를 들어 클라이언트를 자동으로 설치하려면 다음 명령을 실행합니다. `AzInfoProtection.exe /quiet`
    
    PowerShell cmdlet만 자동으로 설치하는 예제: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    도움말 화면에 나열되지 않은 추가 매개 변수:
    
    - **ServiceLocation**: Office 2010을 실행하는 컴퓨터에 클라이언트를 설치하며, 사용자가 컴퓨터의 로컬 관리자가 아니거나 사용자에게 메시지가 표시되지 않게 하려는 경우 이 매개 변수를 사용합니다. [추가 정보](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Microsoft Framework .NET 버전 4.6.2 요구 사항을 무시하려면 이 매개 변수를 사용합니다. [추가 정보](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: 이 매개 변수를 사용하여 **Microsoft로 사용 현황 통계를 보내서 Azure Information Protection 개선에 도움을 줍니다.** 설치 옵션을 사용하지 않도록 설정합니다. 
    
3. 대화형으로 설치하는 경우 Office 365 또는 Azure Active Directory에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 **데모 정책**을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다.
    
4. 다음을 수행하여 설치를 완료합니다. 

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작합니다. 
        
        클라이언트를 ServiceLocation 매개 변수를 사용하여 설치하지 않은 경우 먼저 Azure Information Protection 표시줄을 사용하는 Office 응용 프로그램 중 하나(예: Word)를 열고 이 최초 사용을 위해 레지스트리를 업데이트하라는 메시지가 표시되는지 확인합니다. [서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery)을 사용하여 레지스트리 키를 채울 수 있습니다. 
    
    - 기타 버전의 Office에서는 모든 Office 응용 프로그램 및 파일 탐색기의 모든 인스턴스를 다시 시작합니다. 
        
5. 기본적으로 %temp% 폴더에 생성되는 설치 로그 파일을 확인하여 설치가 되었는지 확인할 수 있습니다. **/log** 설치 매개 변수로 이 위치를 변경할 수 있습니다. 
 
    이 파일의 이름 형식은 다음과 같습니다. `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    예: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    이 로그 파일에서 다음 문자열을 검색합니다. **Product: Microsoft Azure Information Protection -- Installation completed successfully.**(제품: Microsoft Azure Information Protection -- 설치를 완료했습니다.) 설치가 실패하면 이 로그 파일에 문제를 식별하고 해결하는 데 도움이 되는 세부 정보가 포함됩니다.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>ServiceLocation 설치 매개 변수에 대한 자세한 정보

Office 2010이 있는 사용자를 위해 클라이언트를 설치하며 이러한 사용자에게 고컬 관리 권한이 없는 경우 ServiceLocation 매개 변수 및 Azure Rights Management 서비스의 URL을 지정합니다. 이 매개 변수 및 값은 다음 레지스트리 키를 만들고 설정합니다.

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

다음 절차에 따라 ServiceLocation 매개 변수에 지정할 값을 식별합니다. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>ServiceLocation 매개 변수에 지정할 값을 식별하려면

1. PowerShell 세션에서 먼저 [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice)를 실행하고 관리자 자격 증명을 지정하여 Azure Rights Management 서비스에 연결합니다. 그런 다음 [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration)을 실행합니다. 
 
    Azure Rights Management 서비스용 PowerShell 모듈을 아직 설치하지 않은 경우 [Azure Rights Management용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

2. 출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.

    예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. 값에서 이 문자열의 **/_wmcs/licensing**을 제거합니다. 예: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    나머지 문자열은 ServiceLocation 매개 변수에 지정할 값입니다.

Office 2010 및 Azure RMS에 대해 클라이언트를 자동으로 설치하는 예: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>DowngradeDotNetRequirement 설치 매개 변수에 대한 자세한 정보

Windows 업데이트를 사용하여 자동 업그레이드를 지원하고 Office 응용 프로그램과 안정적으로 통합하기 위해, Azure Information Protection 클라이언트에서는 Microsoft .NET Framework 버전 4.6.2를 사용합니다. 기본적으로 설치 과정에서 이 버전을 확인하고, 없을 경우 설치하려 합니다. 그리고 컴퓨터를 다시 시작할 것을 요구합니다.

이 최신 버전 Microsoft .NET Framework를 설치하는 것이 적절하지 않을 경우는 Microsoft .NET Framework 버전 4.5.1이 설치되어 있을 때 이 요구 사항을 무시하도록 **DowngradeDotNetRequirement=True** 매개 변수 및 값을 사용하여 클라이언트를 설치할 수 있습니다.

`AzInfoProtection.exe DowngradeDotNetRequirement=True`

이 방법으로 Azure Information Protection 클라이언트를 이전 버전의 Microsoft .NET Framework에서 사용할 경우 Office 응용 프로그램이 멈추는 문제가 보고되어 있으므로 이 매개 변수를 주의해서 사용해야 합니다. 응용 프로그램이 멈추는 문제가 실제로 발생할 경우, 다른 문제 해결 방법을 시도하기 전에 원장 버전으로 업그레이드하는 것이 좋습니다. 

또한 Windows 업데이트를 사용하여 Azure Information Protection 클라이언트를 업데이트된 상태로 유지할 경우 클라이언트를 최신 버전으로 업그레이드할 다른 소프트웨어 배포 메커니즘이 있어야 합니다.

### <a name="to-install-the-azure-information-protection-client-by-using-the-msi-installer"></a>.msi 설치 관리자를 사용하여 Azure Information Protection 클라이언트를 설치하려면

중앙 배포를 위해서는 Azure Information Protection 클라이언트의 .msi 설치 버전에 해당되는 다음 정보를 사용하세요. 

소프트웨어 배포 방법으로 Intune을 사용하는 경우 [Microsoft Intune을 사용하여 앱 추가](/intune/deploy-use/add-apps) 과정과 다음 절차를 진행하세요.

1. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트의 .msi 버전을 다운로드합니다. 
    
    미리 보기 버전이 제공되는 경우 이 버전을 테스트용으로만 보관하세요. 이 버전은 프로덕션 환경의 최종 사용자를 위한 것이 아닙니다. 

2. .msi 파일이 실행되는 각 컴퓨터에 대해 다음과 같은 소프트웨어 종속성이 유지되는지 확인해야 합니다. 예를 들어 이러한 종속성을 .msi 버전의 클라이언트로 패키징하거나 다음 종속성을 충족하는 컴퓨터에만 배포합니다.
    
    |Office 버전|운영 체제|소프트웨어|작업|
    |--------------------|--------------|----------------|---------------------|
    |Office 2013|지원되는 모든 버전|[KB 3054941](https://www.microsoft.com/en-us/download/details.aspx?id=49337)<br /><br /> 파일 이름에 포함된 버전 번호: v3|설치|
    |Office 2010|지원되는 모든 버전|[Microsoft Online Services 로그인 도우미](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> 버전: 2.1|설치|
    |Office 2010|Windows 8.1 및 Windows Server 2012 R2|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> 파일 이름에 포함된 버전 번호: v3|KB 2843630 또는 KB 2919355를 설치하지 않은 경우 설치|
    |Office 2010|Windows 8 및 Windows Server 2012|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> 파일 이름에 포함된 버전 번호: v3|설치|
    |Office 2010|Windows 7|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> 파일 이름에 포함된 버전 번호: v3|KB 3125574를 설치하지 않은 경우 설치|
    |해당 없음|Windows 7|KB 2627273 <br /><br /> 파일 이름에 포함된 버전 번호: v4|제거|

3. 기본 설치의 경우 **/quiet**를 지정하여 .msi를 실행합니다(예: `AzInfoProtection.msi /quiet`). 그렇지만 [실행 가능한 설치 관리자 지침](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)에 설명된 추가 설치 매개 변수를 지정해야 할 수 있습니다.  

## <a name="additional-checks-and-troubleshooting"></a>추가 검사 및 문제 해결

**도움말 및 피드백** 옵션을 사용하여 **Microsoft Azure Information Protection** 대화 상자를 엽니다.

- Office 응용 프로그램에서: **홈** 탭의 **보호** 그룹에서 **보호**를 선택한 다음 **도움말 및 피드백**을 선택합니다.

- 파일 탐색기에서: 마우스 오른쪽 단추로 파일 또는 폴더를 선택한 다음 **분류 및 보호**를 선택하고 **도움말 및 피드백**을 선택합니다. 

### <a name="help-and-feedback-section"></a>**도움말 및 피드백** 섹션

**추가 정보 링크**를 클릭하면 기본적으로 [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection) 웹 사이트로 이동되지만 Azure Information Protection 정책의 [정책 설정](../deploy-use/configure-policy-settings.md) 중 하나로 사용자 지정 URL로 이동하도록 이 링크를 구성할 수 있습니다.

**피드백 보내기** 링크를 사용하여 Information Protection 팀에 제안 사항이나 요청을 보냅니다. 기술 지원을 위해 이 옵션을 사용하지 않는 경우에는 대신 [지원 옵션 및 커뮤니티 리소스](../get-started/information-support.md#support-options-and-community-resources)를 참조하세요. 

**로그 내보내기**는 Microsoft 지원에 로그 파일을 보내라는 요청을 받았을 때 Azure Information Protection 클라이언트의 로그 파일을 자동으로 수집하여 첨부합니다. 최종 사용자가 이 옵션을 사용하여 이러한 로그 파일을 지원 센터로 보낼 수도 있습니다.

진단 정보 및 클라이언트 다시 설정에 대해서는 **진단 실행**을 선택합니다. 진단 테스트가 끝난 후 **결과 복사**를 클릭하여 Microsoft Support에 보내는 메일이나 최종 사용자가 지원 센터에 보내는 메일에 정보를 붙여넣을 수 있습니다. 테스트를 완료하면 클라이언트를 다시 설정할 수도 있습니다.

**다시 설정** 옵션에 대한 자세한 정보:

- 이 옵션을 사용하기 위해 로컬 관리자일 필요가 없으며 이 작업은 이벤트 뷰어에 로깅되지 않습니다. 

- 파일이 잠겨 있지 않은 경우 이 작업을 수행하면 클라이언트 인증서 및 권한 관리 템플릿이 저장되는 위치인 **%localappdata%\Microsoft\MSIPC**의 파일이 모두 삭제됩니다. Azure Information Protection 정책이나 클라이언트 로그 파일은 삭제되지 않으며, 사용자가 로그아웃되지 않습니다.

- 다음 레지스트리 키 및 설정은 삭제됩니다. **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. 이 레지스트리 키에 대한 설정을 구성한 경우 클라이언트를 다시 설정한 후 레지스트리 설정을 다시 구성해야 합니다. 예를 들어 AD RMS에서 마이그레이션하는 데 네트워크에 서비스 연결 지점이 계속 있기 때문에 Azure Information Protection 테넌트로 리디렉션에 대한 설정을 구성한 경우입니다.

- 클라이언트를 다시 설정한 후 사용자 환경을 다시 초기화해야 합니다. 그러면 클라이언트 및 최신 템플릿에 대한 인증서가 다운로드됩니다. 이렇게 하려면 Office의 모든 인스턴스를 닫은 다음 Office 응용 프로그램을 다시 시작합니다. 그러면 최신 Azure Information Protection 정책을 다운로드했는지도 확인됩니다. 이 작업을 완료할 때까지 진단 테스트를 다시 실행하지 마세요.


### <a name="client-status-section"></a>**클라이언트 상태** 섹션

**다음으로 연결** 값을 사용하여 표시된 사용자 이름이 Azure Information Protection 인증에 사용할 계정을 나타내는지 확인합니다. 이 사용자 이름은 Office 365 또는 Azure Active Directory에 사용하는 계정과 일치해야 합니다. 또한 계정은 Azure Information Protection에 대해 구성된 테넌트에 속해야 합니다.

표시된 계정과 다른 사용자로 로그인해야 하는 경우 [다른 사용자로 로그인](client-admin-guide-customizations.md#sign-in-as-a-different-user) 사용자 지정 내용을 참조하세요.

**마지막 연결**은 클라이언트가 조직의 Azure Information Protection 서비스에 마지막으로 연결된 시기를 표시합니다. **Information Protection 정책 설치** 날짜 및 시간과 함께 이 정보를 사용하여 Azure Information Protection 정책이 마지막으로 설치되거나 업데이트된 시기를 확인할 수 있습니다. 클라이언트는 서비스에 연결할 때 현재 정책에서 변경된 사항이 발견될 경우, 그리고 24시간마다 최신 정책을 자동으로 다운로드합니다. 표시된 시간 이후에 정책을 변경한 경우 Office 응용 프로그램을 닫았다가 다시 엽니다.

**This client is not licensed for Office Professional Plus**(Office Professional Plus 대상 클라이언트가 아님)이 표시될 경우: Azure Information Protection 클라이언트에서 설치된 버전의 Office가 Rights Management 보호의 적용을 지원하지 않는 것을 감지했습니다. 이 상태가 감지되면 보호를 적용하는 레이블이 Azure Information Protection 막대에 표시되지 않습니다.

**버전** 정보를 사용하여 설치된 클라이언트 버전을 확인합니다. **새로운 기능** 링크를 클릭하고 클라이언트의 [버전 릴리스 기록](client-version-release-history.md)을 읽으면 이 버전이 최신 릴리스 버전인지 여부와 해당 수정 사항 및 새로운 기능을 확인할 수 있습니다.


## <a name="to-uninstall-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 제거하려면

다음 옵션 중 하나를 사용할 수 있습니다.

- 제어판을 사용하여 프로그램을 제거합니다. **Microsoft Azure Information Protection** > **제거**를 클릭합니다.

- **AzInfoProtection.exe**와 같은 실행 파일을 다시 실행하고 **설치 수정** 페이지에서 **제거**를 클릭합니다. 

- **/uninstall**을 사용하여 실행 파일을 실행합니다. `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트를 설치했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [Customizations](client-admin-guide-customizations.md)(사용자 지정)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
