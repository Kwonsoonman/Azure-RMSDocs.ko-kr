---
title: "Azure Information Protection 클라이언트 관리자 가이드"
description: "Windows용 Azure Information Protection 클라이언트 배포를 담당하는 엔터프라이즈 네트워크의 관리자를 위한 지침과 정보를 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: adb444f7777304ed40b5b5f988e4efb73268ae14
ms.sourcegitcommit: cbdbabd626fa5b91c418d84cd6228c9ca94a2525
translationtype: HT
---
# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection 클라이언트 관리자 가이드

>*적용 대상: Active Directory Rights Management 서비스, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*


엔터프라이즈 네트워크의 Azure Information Protection 클라이언트를 담당하거나 [Azure Information Protection 클라이언트 사용자 가이드](client-user-guide.md)에 제공된 것보다 더 많은 기술 정보가 필요한 경우 다음 정보를 사용하세요.

Azure Information Protection 클라이언트에는 다음이 포함됩니다.

- 사용자가 분류 레이블을 선택할 수 있는 Azure Information Protection 표시줄을 설치하는 Office 추가 기능과 추가 옵션용 리본의 **보호** 단추

- 파일에 분류 레이블 및 보호를 적용하기 위한 Windows 파일 탐색기의 오른쪽 클릭 옵션

- 네이티브 응용 프로그램으로 열 수 없을 때 보호된 파일을 표시하는 뷰어

- 파일에서 분류 레이블 및 보호를 적용 및 제거하기 위한 PowerShell 모듈

- Azure RMS(Azure Rights Management) 또는 AD RMS(Active Directory Rights Management Services)와 통신하는 Rights Management 클라이언트

Azure Information Protection 클라이언트는 해당 Azure 서비스인 Azure Information Protection와 해당 데이터 보호 서비스인 Azure Rights Management에서 가장 잘 작동됩니다. 몇 가지 제한 사항이 있으나 Azure Information Protection 클라이언트는 온-프레미스 버전의 Rights Management인 AD RMS에도 잘 작동합니다. Azure Information Protection 및 AD RMS에서 지원하는 기능을 포괄적으로 비교한 내용을 보려면 [Azure Information Protection과 AD RMS 비교](../understand-explore/compare-azure-rms-ad-rms.md)를 참조하세요. AD RMS가 있고 Azure Information Protection으로 마이그레이션하려면 [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

**이 설명서에서 답변되지 않은 질문이 있나요?** [Azure Information Protection Yammer 사이트](https://www.yammer.com/AskIPTeam)를 방문하세요. 


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 배포해야 하나요?

다음이 적용될 경우 Azure Information Protection 클라이언트를 배포합니다.

- Office 응용 프로그램(Word, Excel, PowerPoint, Outlook) 내에서 레이블을 선택하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- 추가 파일 형식, 다중 선택 및 폴더를 지원하는 파일 탐색기를 사용하여 문서 및 전자 메일 메시지를 분류(및 필요에 따라 보호)하려고 합니다.

- PowerShell 명령을 사용하여 문서를 분류(및 필요에 따라 보호)하는 스크립트를 실행하려고 합니다.

- 네이티브 응용 프로그램이 설치되어 있지 않거나 이러한 문서를 열 수 없을 때 보호된 문서를 보려고 합니다.

- 파일 탐색기를 사용하거나 Powershell 명령을 사용하여 파일을 보호하려고 합니다.

- 사용자 및 관리자가 보호된 문서를 추적하고 해지할 수 있게 허용하려고 합니다.

- 데이터 복구를 위해 대량으로 파일 및 컨테이너에서 암호화를 제거(보호 해제)하려고 합니다.

- Office 2010을 실행하며, Azure Rights Management 서비스를 사용하여 문서 및 전자 메일 메시지를 보호하려고 합니다.

Office 응용 프로그램의 Azure Information Protection 클라이언트 추가 기능, 조직에 대한 분류 레이블 및 리본의 새 **보호** 단추를 보여 주는 예제:

![기본 정책이 적용된 Azure Information Protection 표시줄](../media/info-protect-bar-default.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>사용자를 위해 Azure Information Protection 클라이언트를 설치하는 방법

클라이언트를 설치하기 전에 Information Protection 클라이언트에 필요한 운영 체제 버전 및 응용 프로그램이 있는지 확인합니다([Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)). 

이 밖에도 다음 지침을 따릅니다.

- Azure Information Protection 클라이언트를 전체 설치하려면 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 프로그램이 없으면 설치 관리자는 이 필수 구성 요소를 다운로드한 후 설치하려고 합니다. 이 필수 구성 요소가 클라이언트 설치의 일부로 설치된 경우 컴퓨터를 다시 시작해야 합니다.

- Azure Information Protection 뷰어가 별도로 설치되어 있으면 최소한 Microsoft .NET Framework 4.5.2 버전이 필요하며, 이 프로그램이 없어도 설치 관리자는 다운로드하여 설치하려고 하지 않습니다.

- PowerShell 모듈에는 이전 운영 체제에 설치해야 할 수도 있는 Windows PowerShell 버전 4.0이 필요합니다. 자세한 내용은 [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx)(Windows PowerShell 4.0을 설치하는 방법)을 참조하세요. 설치 관리자는 이러한 필수 구성 요소를 확인하거나 설치하지 않습니다. 실행 중인 Windows PowerShell 버전을 확인하려면 PowerShell 세션에 **$PSVersionTable**을 입력합니다.

- Windows 7 서비스 팩 1을 실행하는 컴퓨터에는 KB 2533623이 필요합니다. 이 업데이트에 대한 자세한 내용은 [Microsoft 보안 공지: 비보안 라이브러리 로드 시 원격 코드 실행 허용](https://support.microsoft.com/en-us/kb/2533623)을 참조하세요. 이 업데이트를 직접 설치하거나, 설치하는 다른 업데이트로 대체될 수도 있습니다.
    
    이 업데이트가 필요한데 아직 설치되지 않은 경우 클라이언트 설치에서 설치해야 한다는 경고 메시지가 표시됩니다. 클라이언트가 설치된 후에 이 업데이트를 설치할 수 있지만 일부 작업이 차단되며 메시지가 다시 표시됩니다.  

> [!NOTE]
> 설치에는 로컬 관리 권한이 필요합니다.

다음 지침을 따르는 것 외에도, Azure Information Protection 클라이언트가 Microsoft 업데이트 카탈로그에도 포함되어 있으므로 카탈로그를 사용하는 소프트웨어 업데이트 서비스를 통해 클라이언트를 설치하고 업데이트할 수 있습니다. 

1. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 Azure Information Protection 클라이언트를 다운로드합니다. 
    
    미리 보기 버전이 제공되는 경우 이 버전을 테스트용으로 보관하세요. 이 버전은 프로덕션 환경의 최종 사용자를 위한 것이 아닙니다. 

2. 기본 설치의 경우 **AzInfoProtection.exe**와 같은 실행 파일을 실행하면 됩니다. 그렇지만 설치 옵션을 보려면 먼저 **/help**: `AzInfoProtection.exe /help`를 사용하여 실행 파일을 실행합니다.

   예를 들어 클라이언트를 자동으로 설치하려면 다음 명령을 실행합니다. `AzInfoProtection.exe /quiet`
   
   PowerShell cmdlet만 자동으로 설치하는 예제: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
   
   또한 Office 2010을 실행하는 컴퓨터에 클라이언트를 설치하는 경우 사용자가 컴퓨터에서 로컬 관리자가 아니면 **ServiceLocation** 매개 변수(도움말 화면에 포함되지 않음)를 지정해야 합니다. 자세한 내용은 다음 섹션을 참조하세요.

3. 대화형으로 설치하는 경우 Office 365 또는 Azure Active Directory에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 **데모 정책**을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다.
    
4. 다음을 수행하여 설치를 완료합니다. 

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작합니다. 
        
        클라이언트를 ServiceLocation 매개 변수를 사용하여 설치하지 않은 경우 먼저 Azure Information Protection 표시줄을 사용하는 Office 응용 프로그램 중 하나(예: Word)를 열고 이 최초 사용을 위해 레지스트리를 업데이트하라는 메시지가 표시되는지 확인합니다. [서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery)을 사용하여 레지스트리 키를 채울 수 있습니다. 
    
    - 기타 버전의 Office에서는 모든 Office 응용 프로그램 및 파일 탐색기의 모든 인스턴스를 다시 시작합니다. 
        
5. %temp% 폴더에서 설치 로그 파일을 확인하여 설치가 되었는지 확인할 수 있습니다. 이 파일의 이름 형식은 다음과 같습니다. `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    예: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    이 로그 파일에서 다음 문자열을 검색합니다. **Product: Microsoft Azure Information Protection -- Installation completed successfully.**(제품: Microsoft Azure Information Protection -- 설치를 완료했습니다.) 설치가 실패하면 이 로그 파일에 문제를 식별하고 해결하는 데 도움이 되는 세부 정보가 포함됩니다.

### <a name="additional-instructions-for-office-2010-only"></a>Office 2010에만 해당되는 추가 지침

Office 2010이 있는 사용자를 위해 클라이언트를 설치하며 이러한 사용자에게 고컬 관리 권한이 없는 경우 ServiceLocation 매개 변수 및 Azure Rights Management 서비스의 URL을 지정합니다. 이 매개 변수 및 값은 다음 레지스트리 키를 만들고 설정합니다.

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


## <a name="additional-checks-to-verify-installation-connection-status-or-send-feedback"></a>추가 확인: 설치 또는 연결 상태를 확인하거나 피드백을 보내려면

1. Office 응용 프로그램을 열고 **홈** 탭의 **보호** 그룹에서 **보호**를 클릭한 다음 **도움말 및 피드백**을 클릭합니다.

2. **Microsoft Azure Information Protection** 대화 상자에서 다음을 확인합니다.

    - **클라이언트 상태** 섹션에서 **버전** 값을 사용하여 설치가 되었는지 확인합니다. 또한 클라이언트가 언제 조직의 Azure Information Protection 서비스에 마지막으로 연결되었으며 Azure Information Protection 정책이 언제 마지막으로 설치되거나 업데이트되었는지 확인합니다. 클라이언트는 서비스에 연결할 때 현재 정책이 변경된 것을 발견한 경우 최신 정책을 자동으로 다운로드합니다. 표시된 시간 이후에 정책을 변경한 경우 Office 응용 프로그램을 닫았다가 다시 엽니다.
    
        또한 Azure Information Protection에 인증하는 데 사용되는 계정을 식별하는 표시된 사용자 이름을 확인합니다. 이 사용자 이름은 Office 365 또는 Azure Active Directory에 사용하고 Azure Information Protection이 구성된 테넌트에 속한 계정과 일치해야 합니다.

    - **도움말 및 피드백** 섹션에서 **자세히 링크**를 클릭하면 기본적으로 [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection) 웹 사이트로 이동되지만 Azure Information Protection 정책의 [정책 설정](../deploy-use/configure-policy-settings.md) 중 하나로 사용자 지정 URL에 이동하도록 이 링크를 구성할 수 있습니다.
        
        **사용자 의견 보내기** 링크를 사용하여 Information Protection 팀에 제안 사항이나 요청을 보냅니다. 기술 지원을 위해 이 옵션을 사용하지 않는 경우에는 대신 [지원 옵션 및 커뮤니티 리소스](../get-started/information-support.md#support-options-and-community-resources)를 참조하세요. 
    
        진단 정보 및 클라이언트 다시 설정에 대해서는 **진단 실행**을 클릭합니다. 진단 테스트를 완료하면 **결과 복사**를 클릭하여 지원 센터 또는 Microsoft 지원에 보낼 수 있는 메일에 정보를 붙여넣습니다. 테스트를 완료하면 클라이언트를 다시 설정할 수도 있습니다.
        
        **다시 설정** 옵션에 대한 자세한 정보:
        
        - 이 옵션을 사용하기 위해 로컬 관리자일 필요가 없으며 이 작업은 이벤트 뷰어에 로깅되지 않습니다. 
        
        - 파일이 잠겨 있지 않은 경우 이 작업을 수행하면 클라이언트 인증서 및 권한 관리 템플릿이 저장되는 위치인 **%localappdata%\Microsoft\MSIPC**의 파일이 모두 삭제됩니다. Azure Information Protection 정책이나 클라이언트 로그 파일은 삭제되지 않으며, 사용자가 로그아웃되지 않습니다.
        
        - 다음 레지스트리 키 및 설정은 삭제됩니다. **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. 이 레지스트리 키에 대한 설정을 구성하는 경우(예: AD RMS에서 마이그레이션하는데 네트워크에 서비스 연결 지점이 계속 있기 때문에 Azure Information Protection 테넌트로 리디렉션에 대한 설정) 클라이언트를 다시 설정한 후 레지스트리 설정을 다시 구성해야 합니다.
        
        - 클라이언트를 다시 설정한 후 사용자 환경("부트스트랩"이라고도 함)을 다시 초기화해야 합니다. 그러면 클라이언트 및 최신 템플릿에 대한 인증서가 다운로드됩니다. 이렇게 하려면 Office의 모든 인스턴스를 닫은 다음 Office 응용 프로그램을 다시 시작합니다. 그러면 최신 Azure Information Protection 정책을 다운로드했는지도 확인됩니다. 이 작업을 완료할 때까지 진단 테스트를 다시 실행하지 마세요.


## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트를 설치했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [클라이언트 파일 및 사용 현황 로깅](client-admin-guide-files-and-logging.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
