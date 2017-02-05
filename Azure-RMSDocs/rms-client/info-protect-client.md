---
title: "Azure Information Protection 클라이언트 설치 | Azure Information Protection"
description: "문서와 메일용 분류 레이블을 선택할 수 있도록 Office 응용 프로그램에 Information Protection 표시줄을 추가하는 클라이언트를 설치하는 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 6012049162d0ac9ee53476640ab3a4bcac18287f
ms.openlocfilehash: 92d6b6f13d124c8c7ab7735fa170890263c9011b


---

# <a name="installing-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 설치

>*적용 대상: Azure Information Protection*

Azure Information Protection을 사용하여 문서 및 메일 메시지를 분류하려면 먼저 Azure Information Protection 클라이언트를 설치해야 합니다. 이 설치에서는 Office 응용 프로그램(Word, Excel, PowerPoint, Outlook)에 조직의 분류 레이블을 표시하고, **홈** 탭(Word, Excel, PowerPoint)에 **보호**라는 단추가 있는 **보호** 그룹을 표시하는 Information Protection 표시줄을 추가합니다.

다음 그림에서는 이 Information Protection 표시줄과 [기본 정책](../deploy-use/configure-policy-default.md)의 레이블을 보여 줍니다.

![기본 정책이 적용된 Azure Information Protection 표시줄](../media/info-protect-bar-default.png)

[Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트를 다운로드합니다. 현재는 GA(일반 공급) 버전 및 미리 보기 버전을 설치할 수 있습니다. 미리 보기 버전은 평가용 새 기능을 포함하며 변경될 수 있습니다. 자세한 내용은 다음 블로그 공지 게시물 [Azure Information Protection&12;월 미리 보기 제공](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/)을 참조하세요.

클라이언트를 설치하기 전에 Information Protection 클라이언트에 필요한 운영 체제 버전 및 응용 프로그램이 있는지 확인합니다([Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)). 또한 미리 보기 버전 클라이언트의 경우 Windows 7 SP1을 실행하는 컴퓨터에 [KB 2533623](https://support.microsoft.com/en-us/kb/2533623)이 필요합니다. 클라이언트를 설치한 후에 이 업데이트를 설치할 수 있습니다. 이 업데이트가 필요한데 설치되어 있지 않으면 업데이트를 설치하라는 메시지가 표시됩니다.


## <a name="to-install-the-azure-information-protection-client-manually"></a>Azure Information Protection 클라이언트를 수동으로 설치하려면

> [!NOTE]
> 이 설치에는 로컬 관리 권한이 필요합니다.

    
1. [클라이언트를 다운로드](https://www.microsoft.com/en-us/download/details.aspx?id=53018)한 후 **AzInfoProtection.exe**와 같은 실행 파일을 실행하고 메시지의 지시에 따라 클라이언트를 설치합니다.
    
    Office 365 또는 Azure Active Directory에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 **데모 정책**을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다.
    
    설치되는 항목에 대한 자세한 내용은 다음과 같습니다.

    - 일반 공급 버전은 Office 응용 프로그램용 Azure Information Protection 표시줄을 설치합니다. 
    
    - 클라이언트의 최신 미리 보기 버전은 Office 응용 프로그램용 Azure Information Protection 표시줄, 파일 탐색기의 마우스 오른쪽 단추 클릭 옵션, 보호된 파일 뷰어 및 대량으로 파일을 분류 및 보호하기 위한 Windows PowerShell cmdlet을 설치합니다. 
        
        **PowerShellOnly=true** 매개 변수를 지정하여 PowerShell 모듈(RMSProtection)만 설치할 수 있습니다. 예: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true`

2. 다음을 수행하여 설치를 완료합니다. 

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작합니다. 
        
        **클라이언트의 미리 보기 버전을 설치한 경우**: 컴퓨터를 다시 시작하는 것 외에 Azure Information Protection 표시줄을 사용하는 Office 응용 프로그램 중 하나(예: Word)를 열고 이 최초 사용을 위해 레지스트리를 업데이트하라는 메시지가 표시되는지 확인합니다. [서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery)을 사용하여 레지스트리 키를 채울 수 있습니다. 
    
    - 다른 Office 버전의 경우 Office 응용 프로그램을 다시 시작합니다. 
        
        **클라이언트의 미리 보기 버전을 설치한 경우**: Office 응용 프로그램을 다시 시작하는 것 외에 파일 탐색기도 닫고 다시 시작합니다.

## <a name="to-install-the-azure-information-protection-client-for-users"></a>사용자를 위해 Azure Information Protection 클라이언트를 설치하려면

명령줄 옵션을 사용하여 Azure Information Protection 클라이언트 설치를 스크립트로 작성하고 자동화할 수 있습니다. 설치 옵션을 보려면 **/help**를 사용하여 실행 파일을 실행합니다. `AzInfoProtection.exe /help`

클라이언트의 일반 공급 버전을 자동으로 설치하는 예: `AzInfoProtection.exe /quiet`

미리 보기 클라이언트와 함께 PowerShell 모듈만 자동으로 설치하는 예: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true /quiet`

Office 2010을 실행하는 컴퓨터에 클라이언트의 미리 보기 버전을 설치하는 경우 사용자가 컴퓨터에서 로컬 관리자가 아니면 **ServiceLocation** 매개 변수를 지정합니다. 자세한 내용은 다음 섹션을 참조하세요.

Azure Information Protection 클라이언트는 Microsoft 업데이트 카탈로그에도 포함되어 있으므로 카탈로그를 사용하는 소프트웨어 업데이트 서비스를 사용하여 클라이언트를 설치하고 업데이트할 수 있습니다. 

### <a name="preview-version-and-office-2010-only"></a>미리 보기 버전 및 Office 2010에만 해당

클라이언트의 미리 보기 버전 및 Office 2010의 경우 사용자를 위한 클라이언트를 설치할 때 ServiceLocation 매개 변수 및 Azure Rights Management 서비스의 URL을 지정합니다. 이 매개 변수 및 값은 다음 레지스트리 키를 만들고 설정합니다.

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

다음 절차에 따라 ServiceLocation 매개 변수에 지정할 값을 식별합니다. 

#### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>ServiceLocation 매개 변수에 지정할 값을 식별하려면

1. PowerShell 세션에서 먼저 [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice)를 실행하고 관리자 자격 증명을 지정하여 Azure Rights Management 서비스에 연결합니다. 그런 다음 [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration)을 실행합니다. 
 
    Azure Rights Management 서비스용 PowerShell 모듈을 아직 설치하지 않은 경우 [Azure Rights Management용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

2. 출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.

    예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. 값에서 이 문자열의 **/_wmcs/licensing**을 제거합니다. 예: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    나머지 문자열은 ServiceLocation 매개 변수에 지정할 값입니다.

Office 2010 및 Azure RMS에 대해 클라이언트를 자동으로 설치하는 예: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


## <a name="to-uninstall-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 제거하려면

다음 옵션 중 하나를 사용할 수 있습니다.

- 제어판을 사용하여 프로그램을 제거합니다. **Microsoft Azure Information Protection** > **제거**를 클릭합니다.

- **AzInfoProtection.exe**와 같은 실행 파일을 다시 실행하고 **설치 수정** 페이지에서 **제거**를 클릭합니다. 

- **/uninstall**을 사용하여 실행 파일을 실행합니다. `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-report-a-problem"></a>설치 또는 연결 상태를 확인하거나 문제를 보고하려면

1. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다.

2. **Microsoft Azure Information Protection** 대화 상자에서 다음을 확인합니다.

    - **클라이언트 상태** 섹션에서 **버전** 값을 사용하여 설치가 되었는지 확인합니다. 또한 클라이언트가 언제 조직의 Azure Information Protection 서비스에 마지막으로 연결되었으며 Azure Information Protection 정책이 언제 마지막으로 설치되거나 업데이트되었는지 확인합니다. 클라이언트는 서비스에 연결할 때 현재 정책이 변경된 것을 발견한 경우 최신 정책을 자동으로 다운로드합니다. 표시된 시간 이후에 정책을 변경한 경우 Office 응용 프로그램을 닫았다가 다시 엽니다.
    
        또한 Azure Information Protection에 인증하는 데 사용되는 계정을 식별하는 표시된 사용자 이름을 확인합니다. 이 사용자 이름은 Office 365 또는 Azure Active Directory에 사용하고 Azure Information Protection이 구성된 테넌트에 속한 계정과 일치해야 합니다.

    - **도움말 및 피드백** 섹션에서 **자세히 링크**를 클릭하면 기본적으로 [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection) 웹 사이트로 이동되지만 Azure Information Protection 정책의 [정책 설정](../deploy-use/configure-policy-settings.md) 중 하나로 사용자 지정 URL에 이동하도록 이 링크를 구성할 수 있습니다.
        
        **사용자 의견 보내기** 링크를 사용하면 조사하기 위해 Information Protection 팀에 보낼 수 있는 메일 메시지에 클라이언트 로그를 자동으로 첨부할 수 있습니다. 
    
        진단 정보 및 클라이언트 다시 설정에 대해서는 **진단 실행**을 클릭합니다. 진단 테스트를 완료하면 **결과 복사**를 클릭하여 지원 센터 또는 Microsoft 지원에 보낼 수 있는 메일에 정보를 붙여넣습니다. 테스트를 완료하면 클라이언트를 다시 설정할 수도 있습니다.
        
        **다시 설정** 옵션에 대한 자세한 정보:
        
        - 이 옵션을 사용하기 위해 로컬 관리자일 필요가 없으며 이 작업은 이벤트 뷰어에 로깅되지 않습니다. 
        
        - 파일이 잠겨 있지 않은 경우 이 작업을 수행하면 클라이언트 인증서 및 권한 관리 템플릿이 저장되는 위치인 **%localappdata%\Microsoft\MSIPC**의 파일이 모두 삭제됩니다. Azure Information Protection 정책이나 클라이언트 로그 파일은 삭제되지 않으며, 사용자가 로그아웃되지 않습니다.
        
        - 다음 레지스트리 키 및 설정은 삭제됩니다. **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. 이 레지스트리 키에 대한 설정을 구성하는 경우(예: AD RMS에서 마이그레이션하는데 네트워크에 서비스 연결 지점이 계속 있기 때문에 Azure Information Protection 테넌트로 리디렉션에 대한 설정) 클라이언트를 다시 설정한 후 레지스트리 설정을 다시 구성해야 합니다.
        
        - 클라이언트를 다시 설정한 후 사용자 환경("부트스트랩"이라고도 함)을 다시 초기화해야 합니다. 그러면 클라이언트 및 최신 템플릿에 대한 인증서가 다운로드됩니다. 이렇게 하려면 Office의 모든 인스턴스를 닫은 다음 Office 응용 프로그램을 다시 시작합니다. 그러면 최신 Azure Information Protection 정책을 다운로드했는지도 확인됩니다. 이 작업을 완료할 때까지 진단 테스트를 다시 실행하지 마세요.


## <a name="usage-logging"></a>사용 현황 로깅

**[ 이 기능은 미리 보기 버전 클라이언트가 있어야 사용 가능하며 변경될 수 있습니다. ]**

미리 보기 버전 Azure Information Protection 클라이언트는 사용자 활동을 로컬 Windows **응용 프로그램 및 서비스** 이벤트 로그(**Azure Information Protection**)에 기록합니다. 이벤트에는 다음과 같은 정보가 포함됩니다.

- 날짜, 클라이언트 버전, 정책 ID

- 로그인한 사용자 이름, 컴퓨터 이름

- 파일 이름 및 위치

- 작업:

    - 레이블 설정: 정보 ID 101
    
    - 레이블 설정(하위 수준): 정보 ID 102
    
    - 레이블 설정(상위 수준): 정보 ID 103
    
    - 레이블 제거: 정보 ID 104
   
    - 권장 팁: 정보 105
    
    - 사용자 지정 보호 적용: 정보 ID 201
    
    - 사용자 지정 보호 제거: 정보 ID 202
    
    - 로그인(운영): 정보 ID 902
    
    - 정책 다운로드(운영): 정보 ID 901
    
- 작업 소스:
    
    - 수동 
    
    - 권장
    
    - 자동  
    
    - 시스템(로그인 및 다운로드 정책용)
    
- 작업 전/후의 레이블 
    
- 작업 전/후의 보호
    
- 사용자 근거(해당하는 경우)
    

## <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Azure Information Protection 표시줄을 위한 바로 가기 키

바로 가기 키를 사용하여 Azure Information Protection 표시줄에 액세스하려면 다음과 같은 키 조합을 사용합니다.

- **Ctrl** + **Shift** + **~**를 누릅니다. 

그 다음, 레이블과 표시줄에 있는 다른 컨트롤 (**레이블 숨기기** 아이콘 및 **레이블 제거** 아이콘)을 선택하려면 Tab 키를 사용하고 Enter 키를 사용하여 선택합니다.


## <a name="file-locations"></a>파일 위치

클라이언트 파일:   

- 64비트 운영 체제: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- 32비트 운영 체제: **\Program Files\Microsoft Azure Information Protection**

클라이언트 로그 파일 및 현재 설치된 정책 파일:

- 64비트 및 32비트 운영 체제: **%localappdata%\Microsoft\MSIP**


## <a name="next-steps"></a>다음 단계

Information Protection 표시줄의 레이블을 변경하려면 Azure Information Protection 정책을 구성해야 합니다. 자세한 내용은 [Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)을 참조하세요.

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요.

클라이언트의 릴리스 버전 정보를 확인하려면 [버전 릴리스 기록](client-version-release-history.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO5-->


