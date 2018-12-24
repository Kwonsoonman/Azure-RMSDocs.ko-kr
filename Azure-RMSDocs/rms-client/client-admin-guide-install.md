---
title: 사용자를 위해 Azure Information Protection 클라이언트 설치
description: 엔터프라이즈 네트워크에서 Windows용 Azure Information Protection 클라이언트를 배포하는 관리자를 위한 지침 및 정보입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 8df9ded90829c620751529f011a0113e6f51b30e
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218530"
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>관리자 가이드: 사용자를 위해 Azure Information Protection 클라이언트 설치

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

엔터프라이즈 네트워크에 Azure Information Protection 클라이언트를 설치하기 전에 컴퓨터에 Azure Information Protection에 대한 필수 운영 체제 버전 및 애플리케이션이 있는지 확인합니다: [Azure Information Protection에 대한 요구 사항](../requirements.md). 

그런 후 다음 섹션에서 설명한 대로 Azure Information Protection 클라이언트에 필요할 수 있는 추가 필수 구성 요소를 확인합니다. 설치 프로그램에서는 일부 필수 구성 요소만 확인합니다.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 추가 필수 구성 요소

- Microsoft .NET Framework 4.6.2
    
    기본적으로 Azure Information Protection 클라이언트를 전체 설치하려면 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 프로그램이 없으면 실행 가능한 설치 관리자의 설치 마법사는 이 필수 구성 요소를 다운로드한 후 설치하려고 합니다. 이 필수 구성 요소가 클라이언트 설치의 일부로 설치된 경우 컴퓨터를 다시 시작해야 합니다. 권장되지는 않지만 [사용자 지정 설치 매개 변수](#more-information-about-the-downgradedotnetrequirement-installation-parameter)를 사용하면 설치 마법사를 사용할 때 이 필수 구성 요소를 무시할 수 있습니다.
    
    실행 가능한 설치 관리자, Windows 업데이트 또는 Windows Installer를 사용하여 클라이언트를 자동으로 설치할 경우, 이 필수 구성 요소는 자동으로 설치되지 않습니다. 이러한 시나리오의 경우 필요하면 이 필수 구성 요소를 조건을 별도로 설치해야 합니다. 그렇지 않으면 설치에 실패합니다. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53344)에서 Microsoft .NET Framework 4.6.2(오프라인 설치 관리자)를 다운로드할 수 있습니다.

- Microsoft .NET Framework 4.5.2
    
    Azure Information Protection 뷰어가 별도로 설치되어 있으면 최소한 Microsoft .NET Framework 4.5.2 버전이 필요하며, 이 프로그램이 없어도 실행 가능한 설치 관리자는 다운로드하여 설치하려고 하지 않습니다.

- Windows PowerShell 버전 4.0
    
    클라이언트용 PowerShell 모듈에는 이전 운영 체제에 설치해야 할 수도 있는 Windows PowerShell 버전 4.0이 필요합니다. 자세한 내용은 [How to Install Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx)(Windows PowerShell 4.0을 설치하는 방법)을 참조하세요. 설치 관리자는 이러한 필수 구성 요소를 확인하거나 설치하지 않습니다. 실행 중인 Windows PowerShell 버전을 확인하려면 PowerShell 세션에 `$PSVersionTable`을 입력합니다.

- 화면 해상도 800x600 이상
    
    800x600 이하의 해상도에서는 파일 탐색기에서 파일이나 폴더를 마우스 오른쪽 단추로 클릭할 때 **분류 및 보호 - Azure Information Protection** 대화 상자를 완전히 표시할 수 없습니다.


- Microsoft Online Services 로그인 도우미 7.250.4303.0
    
    Office 2010을 실행하는 컴퓨터에는 Microsoft Online Services 로그인 도우미 버전 7.250.4303.0이 필요합니다. 이 버전은 클라이언트 설치에 포함되어 있습니다. 최신 버전의 로그인 도우미가 있는 경우 먼저 제거한 후에 Azure Information Protection 클라이언트를 설치해야 합니다. 예를 들어 버전을 확인하고 **제어판** > **프로그램 및 기능** > **프로그램 제거 또는 변경**을 사용하여 로그인 도우미를 제거합니다.

- KB 2533623
    
    Windows 7 서비스 팩 1을 실행하는 컴퓨터에는 KB 2533623이 필요합니다. 이 업데이트에 대한 자세한 내용은 [Microsoft 보안 공지: 보안되지 않는 라이브러리를 로드하면 원격 코드 실행이 허용됨](https://support.microsoft.com/en-us/kb/2533623)을 참조하세요. 이 업데이트를 직접 설치하거나, 설치하는 다른 업데이트로 대체될 수도 있습니다.
    
    이 업데이트가 필요한데 아직 설치되지 않은 경우 클라이언트 설치에서 설치해야 한다는 경고 메시지가 표시됩니다. 클라이언트가 설치된 후에 이 업데이트를 설치할 수 있지만 일부 작업이 차단되며 메시지가 다시 표시됩니다.  

- Visual Studio 2015용 Visual C++ 재배포 가능 패키지(32비트 버전)
    
    Windows 7 서비스 팩 1을 실행하는 컴퓨터의 경우 다음의 다운로드 페이지에서 **vc_redist.x86.exe**를 설치합니다: [Visual Studio 2015용 Visual C++ 재배포 가능 패키지](https://www.microsoft.com/en-us/download/details.aspx?id=48145).
    
    클라이언트 설치는 이러한 전제 조건을 확인하지 않지만 Azure Information Protection 클라이언트가 PDF 파일을 분류하고 보호하는 데 필요합니다.

- Azure Information Protection 추가 기능을 사용하지 않도록 설정할 수 없도록 그룹 정책을 구성합니다.
    
    Office 2013 이후 버전의 경우 Office 애플리케이션용 **Microsoft Azure Information Protection** 추가 기능을 항상 사용할 수 있도록 그룹 정책을 구성합니다. 이렇게 구성하지 않으면 Microsoft Azure Information Protection 추가 기능을 사용하지 않도록 설정할 수 있고 사용자가 Office 애플리케이션에서 문서 및 메일에 레이블을 지정할 수 없습니다.
    
    - Outlook의 경우 Office 설명서의 [시스템 관리자 추가 기능 제어](https://docs.microsoft.com/office/vba/outlook/concepts/getting-started/support-for-keeping-add-ins-enabled#system-administrator-control-over-add-ins)에 설명된 그룹 정책 설정을 사용합니다.
    
    - Word, Excel 및 PowerPoint의 경우 지원 문서 [Office 2013 및 Office 2016 프로그램의 그룹 정책 설정으로 인해 추가 기능이 로드되지 않음](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off)에 설명된 **관리형 추가 기능의 그룹 정책 설정 목록**을 사용합니다. 
        
        Azure Information Protection에 대한 다음과 같은 프로그래밍 방식 식별자(ProgID)를 지정하고 **1: 추가 기능 항상 사용** 옵션을 설정합니다.
        
        Word의 경우: `MSIP.WordAddin`
        
        Excel의 경우: `MSIP.ExcelAddin`
        
        PowerPoint의 경우: `MSIP.PowerPointAddin`

> [!IMPORTANT]
> Azure Information Protection 클라이언트를 설치하려면 로컬 관리 권한이 필요합니다.


## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>사용자를 위해 Azure Information Protection 클라이언트를 설치하는 옵션

사용자를 위해 클라이언트를 설치하는 옵션에는 다음 두 가지가 있습니다.

**실행 파일(.exe) 버전의 클라이언트 실행**: 대화형 또는 자동으로 실행할 수 있는 권장 설치 방법입니다. 이 방법은 가장 유연하며, 설치 관리자가 많은 필수 구성 요소를 확인하고 누락된 필수 구성 요소를 자동으로 설치할 수 있으므로 권장됩니다. [지침](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Windows 설치 관리자(.msi) 버전의 클라이언트 배포**: 그룹 정책, Configuration Manager 및 Microsoft Intune 등의 중앙 배포 메커니즘을 사용하는 자동 설치에만 지원됩니다. 이 방법은 Intune 및 MDM(모바일 디바이스 관리)에 의해 관리되는 Windows 10 PC에서 필요합니다. 이러한 컴퓨터의 경우 실행 파일로 설치하도록 지원되지 않기 때문입니다. 그러나 이 설치 방법을 사용하면 실행 파일용 설치 관리자가 각 컴퓨터에 대해 수행하는 종속 소프트웨어를 수동으로 확인한 후 설치 또는 제거해야 합니다. [지침](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

Azure Information Protection 클라이언트를 설치한 후에는 선택한 설치 방법을 반복하여 이 클라이언트를 업데이트하거나 Windows 업데이트를 사용하여 클라이언트가 계속 자동으로 업그레이드되도록 할 수 있습니다. 업그레이드에 대한 자세한 내용은 [Azure Information Protection 클라이언트 업그레이드 및 유지 관리](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client) 섹션을 참조하세요.

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>실행 파일 설치 관리자를 사용하여 Azure Information Protection 클라이언트를 설치하려면

Microsoft 업데이트 카탈로그를 사용하지 않거나 Intune 같은 중앙 배포 방법을 사용하여 .msi를 배포하는 경우 다음 지침에 따라 클라이언트를 설치합니다.

1. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트 실행 파일 버전을 다운로드합니다. 
    
    미리 보기 버전이 제공되는 경우 이 버전을 테스트용으로만 보관하세요. 이 버전은 프로덕션 환경의 최종 사용자를 위한 것이 아닙니다. 

2. 기본 설치의 경우 **AzInfoProtection.exe**와 같은 실행 파일을 실행하면 됩니다. 그렇지만 설치 옵션을 보려면 먼저 **/help**: `AzInfoProtection.exe /help`를 사용하여 실행 파일을 실행합니다.

    예를 들어 클라이언트를 자동으로 설치하려면 다음 명령을 실행합니다. `AzInfoProtection.exe /quiet`
    
    PowerShell cmdlet만 자동으로 설치하는 예제: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    도움말 화면에 나열되지 않은 추가 매개 변수:
    
    - **ServiceLocation**: Office 2010을 실행하는 컴퓨터에 클라이언트를 설치하고 사용자가 컴퓨터의 로컬 관리자가 아니거나 사용자에게 메시지가 표시되지 않게 하려는 경우 이 매개 변수를 사용합니다. [추가 정보](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Microsoft Framework .NET 버전 4.6.2 요구 사항을 무시하려면 이 매개 변수를 사용합니다. [추가 정보](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: 이 매개 변수를 사용하여 **Microsoft에 사용 현황 통계를 보내 Azure Information Protection 개선 지원** 설치 옵션을 사용하지 않도록 설정합니다. 
    
3. 대화형으로 설치하는 경우 Office 365 또는 Azure Active Directory에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 **데모 정책**을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다.
    
4. 다음을 수행하여 설치를 완료합니다. 

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작합니다. 
        
        클라이언트를 ServiceLocation 매개 변수를 사용하여 설치하지 않은 경우 먼저 Azure Information Protection 표시줄을 사용하는 Office 응용 프로그램 중 하나(예: Word)를 열고 이 최초 사용을 위해 레지스트리를 업데이트하라는 메시지가 표시되는지 확인합니다. [서비스 검색](client-deployment-notes.md#rms-service-discovery)을 사용하여 레지스트리 키를 채울 수 있습니다. 
    
    - 기타 버전의 Office에서는 모든 Office 응용 프로그램 및 파일 탐색기의 모든 인스턴스를 다시 시작합니다. 
        
5. 기본적으로 %temp% 폴더에 생성되는 설치 로그 파일을 확인하여 설치가 되었는지 확인할 수 있습니다. **/log** 설치 매개 변수로 이 위치를 변경할 수 있습니다. 
 
    이 파일의 이름 형식은 다음과 같습니다. `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    예를 들면 다음과 같습니다. **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    이 로그 파일에서 다음의 문자열을 검색합니다. **제품: Microsoft Azure Information Protection - 설치를 성공적으로 완료**. 설치가 실패하면 이 로그 파일에 문제를 식별하고 해결하는 데 도움이 되는 세부 정보가 포함됩니다.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>ServiceLocation 설치 매개 변수에 대한 자세한 정보

Office 2010이 있는 사용자를 위해 클라이언트를 설치하며 이러한 사용자에게 고컬 관리 권한이 없는 경우 ServiceLocation 매개 변수 및 Azure Rights Management 서비스의 URL을 지정합니다. 이 매개 변수 및 값은 다음 레지스트리 키를 만들고 설정합니다.

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

다음 절차에 따라 ServiceLocation 매개 변수에 지정할 값을 식별합니다. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>ServiceLocation 매개 변수에 지정할 값을 식별하려면

1. PowerShell 세션에서 먼저 [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice)를 실행하고 관리자 자격 증명을 지정하여 Azure Rights Management 서비스에 연결합니다. 그런 다음 [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration)을 실행합니다. 
 
    Azure Rights Management 서비스용 PowerShell 모듈을 아직 설치하지 않은 경우 [AADRM PowerShell 모듈 설치](../install-powershell.md)를 참조하세요.

2. 출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.

    예를 들면 다음과 같습니다. **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. 값에서 이 문자열의 **/_wmcs/licensing**을 제거합니다. 예: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    나머지 문자열은 ServiceLocation 매개 변수에 지정할 값입니다.

Office 2010 및 Azure RMS에 대해 클라이언트를 자동으로 설치하는 예: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>DowngradeDotNetRequirement 설치 매개 변수에 대한 자세한 정보

Windows 업데이트를 사용하여 자동 업그레이드를 지원하고 Office 응용 프로그램과 안정적으로 통합하기 위해, Azure Information Protection 클라이언트에서는 Microsoft .NET Framework 버전 4.6.2를 사용합니다. 기본적으로 실행 파일 검사를 사용한 대화형 설치는 이 버전이 있는지 확인하고 없을 경우 설치하려 합니다. 그리고 컴퓨터를 다시 시작할 것을 요구합니다.

이 최신 버전 Microsoft .NET Framework를 설치하는 것이 적절하지 않을 경우는 Microsoft .NET Framework 버전 4.5.1이 설치되어 있을 때 이 요구 사항을 무시하도록 **DowngradeDotNetRequirement=True** 매개 변수 및 값을 사용하여 클라이언트를 설치할 수 있습니다.

예를 들어 `AzInfoProtection.exe DowngradeDotNetRequirement=True`를 구성할 수 있습니다.

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
    |Office 2016|지원되는 모든 버전|64비트: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=55007)<br /><br />32비트: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=54999)<br /><br /> 버전: 1.0|설치|
    |Office 2013|지원되는 모든 버전|64비트: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32비트: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />버전: 1.0|설치|
    |Office 2010|지원되는 모든 버전|[Microsoft Online Services 로그인 도우미](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> 버전: 2.1|설치|
    |Office 2010|Windows 8.1 및 Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> 파일 이름에 포함된 버전 번호: v3|KB2843630 또는 KB2919355를 설치하지 않은 경우 설치|
    |Office 2010|Windows 8 및 Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> 파일 이름에 포함된 버전 번호: v3|설치|
    |Office 2010|Windows 7 및 Windows Server 2008 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> 파일 이름에 포함된 버전 번호: v3|KB3125574를 설치하지 않은 경우 설치|
    |해당 없음|Windows 7|[vc_redist.x86.exe](https://www.microsoft.com/en-us/download/details.aspx?id=48145)|설치|
    |해당 없음|Windows 7|KB2627273 <br /><br /> 파일 이름에 포함된 버전 번호: v4|제거|

3. 기본 설치의 경우 **/quiet**를 지정하여 .msi를 실행합니다(예: `AzInfoProtection.msi /quiet`). 그렇지만 [실행 가능한 설치 관리자 지침](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)에 설명된 추가 설치 매개 변수를 지정해야 할 수 있습니다.  


## <a name="how-to-install-the-azure-information-protection-scanner"></a>Azure Information Protection 스캐너를 설치하는 방법

Azure Information Protection 클라이언트에 포함된 PowerShell 모듈에는 스캐너를 설치하고 구성하는 cmdlet이 있습니다. 하지만 스캐너를 사용하려면 전체 버전의 클라이언트를 설치해야 하며 PowerShell 모듈만 설치할 수는 없습니다.

스캐너에 클라이언트를 설치하려면 이전 섹션에서 동일한 지침을 따릅니다. 그러면 스캐너를 설치할 준비가 된 것입니다. 자세한 내용은 [Azure Information Protection 스캐너를 배포하여 파일 자동으로 분류 및 보호](../deploy-aip-scanner.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트를 설치했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [사용자 지정](client-admin-guide-customizations.md)

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


