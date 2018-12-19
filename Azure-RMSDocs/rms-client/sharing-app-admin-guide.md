---
title: RMS 공유 응용 프로그램 관리자 가이드 - AIP
description: Windows용 Microsoft Rights Management 공유 응용 프로그램 배포를 담당하는 엔터프라이즈 네트워크의 관리자를 위한 지침과 정보를 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/27/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 84f013014f0256a01c30d9518089f2604ed9a668
ms.sourcegitcommit: b2414cc00d50ccefe10f8c3719eb3f6c1e78fc65
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246193"
---
# <a name="rights-management-sharing-application-administrator-guide"></a>Rights Management 공유 응용 프로그램 관리자 가이드

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

> [!IMPORTANT]
> **지원 종료 알림**: Windows용 Rights Management 공유 애플리케이션은 [Azure Information Protection 클라이언트](aip-client.md)로 대체될 예정입니다. 이 이전 응용 프로그램에 대한 지원은 2019년 1월 31일에 중지됩니다. 

엔터프라이즈 네트워크에서 Microsoft Rights Management 공유 응용 프로그램을 담당하고 있거나, [Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md) 또는 [Windows용 Microsoft Rights Management 공유 응용 프로그램 FAQ](https://go.microsoft.com/fwlink/?LinkId=303971)에 나와 있는 것보다 자세한 기술 정보를 확인하려는 경우 이 문서의 정보를 참조할 수 있습니다.

RMS 공유 응용 프로그램은 Azure Information Protection에서 가장 효율적으로 작동합니다. 이 배포 구성에서는 다른 조직의 사용자에게 보호된 첨부 파일을 보낼 수 있으며, 메일 알림 및 취소 기능이 포함된 문서 추적 등의 옵션도 지원되기 때문입니다. 그러나 온-프레미스 버전인 AD RMS에서도 해당 응용 프로그램을 사용할 수 있습니다(일부 제한이 적용됨). Azure Information Protection 및 AD RMS에서 지원하는 기능을 포괄적으로 비교한 내용을 보려면 [Azure Information Protection과 AD RMS 비교](../compare-on-premise.md)를 참조하세요. AD RMS가 있고 Azure Information Protection으로 마이그레이션하려면 [AD RMS에서 Azure Information Protection으로 마이그레이션](../migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

Rights Management 공유 응용 프로그램 기술 개요, 기본 및 일반 보호에 대한 정보, 지원되는 파일 형식, 파일 이름 확장명 및 기본 보호 수준을 변경하는 방법은 [Rights Management 공유 응용 프로그램 기술 개요 및 보호 세부 정보](sharing-app-admin-guide-technical.md)를 참조하세요. 

## <a name="automatic-deployment-for-the-microsoft-rights-management-sharing-application"></a>Microsoft Rights Management 공유 응용 프로그램 자동 배포
RMS 공유 응용 프로그램의 Windows 버전은 스크립트 방식 설치를 지원하므로 엔터프라이즈 배포에 적합합니다.

설치의 유일한 필수 조건으로, 컴퓨터에서 Windows 7 서비스 팩 1 이상 버전을 실행하고 Microsoft Framework 버전 4.0 이상이 설치되어 있어야 합니다. Microsoft .NET Framework 4.0을 설치해야 하는 경우 [Microsoft 다운로드 센터에서 설치를 위해 해당 버전을 다운로드](https://www.microsoft.com/download/details.aspx?id=17718)할 수 있습니다.

### <a name="to-download-the-rms-sharing-application-for-automatic-deployment"></a>자동 배포용 RMS 공유 응용 프로그램을 다운로드하려면

1.  Microsoft 다운로드 센터의 [Windows용 Microsoft Rights Management 공유 응용 프로그램](https://www.microsoft.com/download/details.aspx?id=40857) 페이지로 이동하여 **다운로드**를 클릭합니다.

2.  필요한 파일을 선택하여 다운로드합니다. Windows 64비트용(Microsoft Rights Management 공유 응용 프로그램 x64.zip) 및 Windows 32비트용(Microsoft Rights Management 공유 응용 프로그램 x86.zip)의 두 가지 클라이언트 설치 패키지가 있습니다.

3.  압축된 설치 패키지를 두 번 클릭하는 등의 방법으로 파일의 압축을 풉니다. 그런 다음 클라이언트 컴퓨터가 액세스할 수 있는 네트워크 위치에 압축을 푼 파일을 복사합니다.

RMS 공유 응용 프로그램의 설치 패키지는 다음과 같은 다양한 배포 시나리오를 지원합니다.

|설명|배포 시나리오|
|---------------|-----------------------|
|Microsoft Online 로그인 도우미|Office 2010 및 Azure Information Protection<br /><br />[Office 2013용 2015년 6월 9일 업데이트](https://support.microsoft.com/kb/3054853)(KB3054853)를 설치하지 않은 경우 Office 2013 및 Azure Information Protection|
|Office용 핫픽스(KB 2596501)|Office 2010 및 Azure Information Protection<br /><br />Office 2010 및 Active Directory RMS|
|AD RMS 클라이언트 1.0이 Azure Information Protection에서 작동하도록 설정하기 위한 핫픽스(KB 2843630)|Office 2010 및 Azure Information Protection<br /><br />Office 2010 및 Active Directory RMS|
|AD RMS 클라이언트 및 RMS 공유 응용 프로그램|Office 2016 또는 Office 2013 및 Azure Information Protection 또는 Active Directory RMS<br /><br />Office 2010 및 Azure Information Protection<br /><br />Office 2010 및 Active Directory RMS<br /><br />RMS 공유 응용 프로그램 및 Office 추가 기능만|
|리본용 Office 추가 기능|Office 2016 또는 Office 2013 및 Azure Information Protection 또는 Active Directory RMS<br /><br />Office 2010 및 Azure Information Protection<br /><br />Office 2010 및 Active Directory RMS<br /><br />RMS 공유 응용 프로그램 및 Office 추가 기능만|
|Azure Active Directory Rights Management 준비 도구|Office 2010 및 Azure Information Protection|
이러한 배포 시나리오용으로 RMS 공유 응용 프로그램을 배포하는 데 필요한 명령을 확인하려면 다음 절차를 수행합니다.

-   **Office 2016 또는 Office 2013 및 Azure Information Protection 또는 Active Directory RMS**

    사용자가 Office 2016 또는 Office 2013을 실행하고 조직에서 Azure Information Protection 또는 Active Directory RMS를 사용하며 사용자가 Azure Information Protection 또는 Active Directory RMS를 사용하는 다른 조직과 공동 작업을 합니다.

-   **Office 2010 및 Azure Information Protection**

    사용자가 Office 2010을 실행하고 조직에서 Azure Information Protection을 사용하며 사용자가 Azure Information Protection 또는 Active Directory RMS를 사용하는 다른 조직과 공동 작업을 합니다.

-   **Office 2010 및 Active Directory RMS**

    사용자가 Office 2010을 실행하고 조직에서 AD RMS를 사용하며 사용자가 Azure Information Protection을 사용하는 다른 조직과 공동 작업을 합니다.

-   **RMS 공유 응용 프로그램 및 Office 추가 기능만**

    사용자가 Office 2016, Office 2013 또는 Office 2010을 실행하고 조직에서 AD RMS를 사용하며 사용자가 Azure Information Protection을 사용하는 다른 조직과 공동 작업을 할 필요가 없습니다. 이 설치의 경우 공유 응용 프로그램과 Office 추가 기능만 설치하면 됩니다.

> [!NOTE]
> 이러한 시나리오에서 조직이 AD RMS를 실행하는 경우 사용자는 Azure Information Protection을 사용하는 다른 조직으로부터 보호된 콘텐츠를 받을 수는 있지만 Azure Information Protection을 사용하는 조직의 사용자에게 보호된 콘텐츠를 보낼 수는 없습니다. 그러나 조직이 Azure Information Protection을 실행하는 경우에는 사용자가 다른 조직과 보호된 콘텐츠를 주고받을 수 있습니다.

각 절차에 대해 설치를 완료하려면 컴퓨터를 다시 시작해야 합니다. **shutdown /i**와 같은 명령을 사용하여 자동 다시 시작을 시작할 수 있습니다.

### <a name="to-deploy-the-rms-sharing-application-for-office2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Office 2016 또는 Office 2013 및 Azure Information Protection 또는 Active Directory RMS용 RMS 공유 애플리케이션을 배포하려면

-   RMS 공유 응용 프로그램 및 관련 구성 요소를 설치하려는 각 컴퓨터에서 상승된 권한으로 다음 명령을 실행합니다.

    ```
    setup.exe /s
    ```

설치 성공 여부를 확인하려면 이 문서에서 [설치 성공 여부 확인](#verifying-installation-success) 섹션을 참조하세요.

### <a name="to-deploy-the-rms-sharing-application-for-office-2010-and-azure-information-protection"></a>Office 2010 및 Azure Information Protection용 RMS 공유 응용 프로그램을 배포하려면

1.  Azure Active Directory Rights Management 준비 도구를 실행하여 조직의 인증 서비스 URL을 가져올 수 있으려면 Office 365 또는 Azure Active Directory 테넌트에 대한 전역 관리자여야 합니다. 이 도구는 단일 컴퓨터에서 한 번만 실행하면 됩니다. 각 컴퓨터에 RMS 공유 응용 프로그램을 설치할 때 인증 서비스 URL을 사용합니다.

    1.  로컬 관리자 계정을 사용하여 컴퓨터에 로그인합니다.

    2.  해당 컴퓨터에서 [Microsoft Online 로그인 도우미를 다운로드하여 설치](https://www.microsoft.com/download/details.aspx?id=28177)합니다.

    3.  다음 명령을 실행하여 화면에 표시되는 인증 서비스 URL을 확인합니다. 이 URL을 복사한 후 다음 단계에서 사용하기 위해 저장할 수 있습니다.

        -   Windows 8.1 및 Windows 8 64비트:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Windows 8.1 및 Windows 8 32비트:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Windows 7 64비트:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > 이 명령을 실행하면 Azure용 자격 증명을 입력하라는 메시지가 표시될 수 있습니다. 컴퓨터가 도메인에 가입되어 있지 않으면 이 메시지가 표시됩니다. 컴퓨터가 도메인에 가입되어 있으면 이 도구는 캐시된 자격 증명을 사용할 수 있습니다.

2.  RMS 공유 응용 프로그램을 설치할 각 컴퓨터에서 상승된 권한으로 다음 명령을 한 번 실행합니다.

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  RMS 공유 응용 프로그램을 설치할 각 컴퓨터에서 해당 컴퓨터의 각 사용자는 다음 명령을 실행해야 합니다(상승된 권한은 필요하지 않음). 여러 가지 방법으로 이 작업을 수행할 수 있습니다. 예를 들어 메일 메시지나 지원 센터 포털의 링크를 통해 사용자가 명령을 실행하도록 할 수도 있고 로그온 스크립트에 명령을 추가할 수도 있습니다.

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

설치 성공 여부를 확인하려면 이 문서에서 [설치 성공 여부 확인](#verifying-installation-success) 섹션을 참조하세요.

### <a name="to-deploy-the-rms-sharing-application-for-office2010-and-active-directoryrms"></a>Active Directory RMS 및 Office 2010용 RMS 공유 응용 프로그램을 배포하려면

1.  RMS 공유 응용 프로그램을 설치할 각 컴퓨터에서 상승된 권한으로 다음 명령을 실행합니다.

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  RMS 공유 응용 프로그램을 설치할 각 컴퓨터에서 사용자가 다음 명령을 실행해야 합니다(상승된 권한은 필요하지 않음). 여러 가지 방법으로 이 작업을 수행할 수 있습니다. 예를 들어 전자 메일 메시지나 지원 센터 포털의 링크를 통해 사용자가 명령을 실행하도록 할 수도 있고 로그온 스크립트에 명령을 추가할 수도 있습니다.

    -   Windows 10, Windows 8.1 및 Windows 8 64비트:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Windows 10, Windows 8.1 및 Windows 8 32비트:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Windows 7 64비트의 경우:

            pushd x64\win7
            aadrmpep.exe /configureO2010
            popd

    -   Windows 7 32비트:

            pushd x86\win7
            aadrmpep.exe /configureO2010
            popd


설치 성공 여부를 확인하려면 이 문서에서 [설치 성공 여부 확인](#verifying-installation-success) 섹션을 참조하세요.

### <a name="to-install-the-rms-sharing-application-and-office-add-in-only"></a>RMS 공유 응용 프로그램 및 Office 추가 기능만 설치하려면

1.  다음 명령을 사용하고 로그 파일을 만들 기존 폴더를 지정하여 AD RMS 클라이언트 및 RMS 공유 응용 프로그램을 설치합니다.

    -   64비트 Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32비트 Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    예를 들어 `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`를 구성할 수 있습니다.
    
    이 명령이 실행되지 않아도 **/quiet** 매개 변수 때문에 오류 메시지가 표시되지 않습니다. 설치가 실패한 문제를 해결하는 데 도움을 얻으려면 /quiet 없이 명령을 다시 실행하여 오류 메시지를 표시하세요.

2.  다음 명령을 사용하고 로그 파일을 만들 기존 폴더를 지정하여 Office 추가 기능을 설치 합니다.

    -   64비트 버전 Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   32비트 버전 Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    예를 들어 `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`를 구성할 수 있습니다.
    
    이 명령이 실행되지 않아도 **/quiet** 매개 변수 때문에 오류 메시지가 표시되지 않습니다. 설치가 실패한 문제를 해결하는 데 도움을 얻으려면 /quiet 없이 명령을 다시 실행하여 오류 메시지를 표시하세요.

설치 성공 여부를 확인하려면 이 문서에서 [설치 성공 여부 확인](#verifying-installation-success) 섹션을 참조하세요.

## <a name="verifying-installation-success"></a>설치 성공 여부 확인
설치 로그 파일을 통해 제대로 설치되었는지 확인할 수 있습니다.

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Office 2016 또는 Office 2013 및 Azure Information Protection 또는 Active Directory RMS용 RMS 공유 애플리케이션의 설치 성공 여부를 확인하려면

-   Setup.exe 명령이 정상적으로 실행되었는지 확인하려면 각 컴퓨터의 *%temp%\RMS_installer_&lt;guid&gt;* 폴더에서 설치 로그 파일 **RMInstaller.log**를 검색한 다음 종료 코드를 확인합니다.

    설치에 성공한 경우에는 종료 코드가 0이고 기타 모든 숫자는 설치가 실패했음을 나타냅니다.

    로그 파일 이름 예: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office2010-and-azure-information-protection"></a>Office 2010 및 Azure Information Protection용 RMS 공유 애플리케이션의 설치 성공 여부를 확인하려면

1.  Setup.exe 명령이 정상적으로 실행되었는지 확인하려면 각 컴퓨터의 *%temp%\RMS_installer_&lt;guid&gt;* 폴더에서 설치 로그 파일 **RMInstaller.log**를 검색한 다음 종료 코드를 확인합니다.

    설치에 성공한 경우에는 종료 코드가 0이고 기타 모든 숫자는 설치가 실패했음을 나타냅니다.

    로그 파일 이름 예: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  RMSSetup.exe 명령이 정상적으로 실행되었는지 확인하려면 사용자가 *%localappdata%\microsoft\drm* 폴더에 다음 파일을 만들어야 합니다.

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    CLC-&#42;.drm 파일의 예:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2010-and-active-directory-rms"></a>Office 2010 및 Active Directory RMS용 RMS 공유 응용 프로그램의 설치 성공 여부를 확인하려면

1.  Setup.exe 명령이 정상적으로 실행되었는지 확인하려면 각 컴퓨터의 *%temp%\RMS_installer_&lt;guid&gt;* 폴더에서 설치 로그 파일을 검색한 다음 종료 코드를 확인합니다.

    설치에 성공한 경우에는 종료 코드가 0이고 기타 모든 숫자는 설치가 실패했음을 나타냅니다.

    로그 파일 이름 예: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  aadrmprep.exe 명령이 정상적으로 실행되었는지 확인하려면 설치 로그 파일에서 다음 텍스트를 검색합니다. **aadrmprep.exe가 종료되었습니다(SUCCESS 상태).**

    > [!NOTE]
    > 첫 번째 설치가 실패하고 두 번째 설치가 성공하는 경우와 같이 이 설치가 두 번 실행되는 경우도 있습니다.

    이 도구가 변경하는 레지스트리를 수동으로 확인하려는 경우 다음 레지스트리를 확인하면 됩니다.

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

### <a name="to-verify-installation-success-for-the-rms-sharing-application-and-office-add-in-only"></a>RMS 공유 응용 프로그램 및 Office 추가 기능만의 설치 성공 여부를 확인하려면

1.  Setup_ipviewer.exe 명령의 성공을 확인하려면 설치 로그 파일에서 다음 텍스트를 검색합니다. **설치 성공 또는 오류 상태: 0.**

    정상적으로 설치된 경우에 표시되는 줄 예제:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services 클라이언트 2.1. Product Version: 1.0.1179.1. 제품 언어: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.**

2.  Office 추가 기능의 성공을 확인하려면 각 컴퓨터의 설치 로그 파일에서 다음 텍스트를 검색합니다. **설치 성공 또는 오류 상태: 0.**

    정상적으로 설치된 경우에 표시되는 줄 예제:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. 제품 이름: Microsoft RMS Office 추가 기능. 제품 버전: 1.0.7. Product Language: 1033. 제조업체: Microsoft. Installation success or error status: 0.**

## <a name="uninstall-commands"></a>제거 명령
이러한 배포에 필요한 설치 명령 중 일부만이 제거 명령을 지원합니다. AD RMS 클라이언트와 공유 응용 프로그램 및 Office 추가 기능을 제거할 수 있습니다. 이러한 요소를 제거하려면 다음 명령을 사용합니다.

### <a name="to-uninstall-the-adrms-client-and-the-rms-sharing-application"></a>AD RMS 클라이언트 및 RMS 공유 응용 프로그램을 제거하려면

-   다음 명령을 사용합니다.

    -   64비트 Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   32비트 Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### <a name="to-uninstall-the-office-add-in"></a>Office 추가 기능을 제거하려면

-   다음 명령을 사용합니다.

    -   64비트 Windows:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   32비트 Windows:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## <a name="suppressing-automatic-updates"></a>자동 업데이트를 사용하지 않도록 설정
기본적으로는 최신 버전의 RMS 공유 응용 프로그램을 사용할 수 있으면 사용자에게 알림이 표시되며 해당 버전을 다운로드할지를 묻는 메시지가 나타납니다. 다음 레지스트리를 편집하여 이 알림을 표시하지 않도록 설정할 수 있습니다.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**로 이동한 다음 **RmsSharingApp** 키가 아직 없으면 새로 만듭니다.

2.  **RmsSharingApp**을 선택하고 새 DWORD 값 **AllowUpdatePrompt**를 만든 후에 값을 **0**으로 설정합니다.

WSUS에서는 RMS 공유 응용 프로그램을 지원하지 않으므로 다음 기술을 사용하여 새 RMS 공유 응용 프로그램 버전을 모든 사용자에게 배포하기 전에 테스트를 할 수 있습니다.

1.  모든 사용자의 컴퓨터에서 자동 업데이트를 표시하지 않도록 설정하는 스크립트를 실행합니다. 관리자가 새 버전을 테스트하는 데 사용하는 컴퓨터에서는 이 스크립트를 실행하지 마세요.

2.  새 버전을 사용할 수 있게 되면 관리자가 해당 버전을 다운로드하여 테스트합니다.

3.  테스트를 완료하고 모든 문제를 해결한 후 이 가이드에 나와 있는 자동 배포 지침을 사용하여 모든 사용자에게 최신 버전을 배포합니다.

## <a name="azure-information-protection-only-configuring-document-tracking"></a>Azure Information Protection 전용 문서 추적 기능 구성
[문서 추적 기능을 지원하는 구독](https://www.microsoft.com/cloud-platform/azure-information-protection-features)이 있는 경우 기본적으로 조직의 모든 사용자에 대해 문서 추적 사이트를 사용하도록 설정됩니다. 문서 추적 기능에서는 사용자가 공유하는 보호된 문서에 액세스하려고 시도하는 사람의 메일 주소, 해당 문서에 액세스하려고 시도한 시간 및 해당 위치와 같은 정보를 표시합니다. 개인정보취급방침 요구 사항으로 인해 조직에서 이 정보 표시가 금지된 경우 [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature) cmdlet을 사용하여 문서 추적 사이트에 대한 액세스를 사용하지 않도록 설정할 수 있습니다. 언제든지 [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature)를 사용하여 사이트에 대한 액세스를 다시 사용하도록 설정할 수 있고 [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature)를 사용하여 액세스가 현재 사용하거나 사용하지 않도록 설정되어 있는지 확인할 수 있습니다.

이러한 cmdlet을 실행하려면 **2.3.0.0** 이상의 Windows PowerShell용 Azure Information Protection 모듈 버전을 사용하고 있어야 합니다. 설치 지침은 [AADRM PowerShell 모듈 설치](../install-powershell.md)를 참조하세요.

> [!TIP]
> 모듈을 이미 다운로드하여 설치한 경우 `(Get-Module aadrm –ListAvailable).Version`을 실행하여 버전 번호를 확인합니다.

다음 URL은 문서 추적 기능에 사용되며 예를 들어 보안이 강화된 Internet Explorer를 사용 중인 경우 신뢰할 수 있는 사이트에 추가하는 등의 방법으로 허용해야 합니다.

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Bing Maps의 URL입니다.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="tracking-and-revoking-documents-for-users"></a>사용자에 대해 문서 추적 및 취소

사용자가 문서 추적 사이트에 로그인하면 RMS 공유 응용 프로그램을 사용하여 공유한 문서를 추적 및 취소할 수 있습니다. Azure Information Protection에 대한 관리자(전역 관리자) 권한으로 로그인하면 페이지 오른쪽 위에 있는 관리자 아이콘을 클릭하여 관리자 모드로 전환하고 조직의 사용자가 공유한 문서를 확인할 수 있습니다.

관리자 모드에서 수행하는 작업은 감사되어 사용 현황 로그 파일에 기록되며, 계속하려면 확인해야 합니다. 이 로깅에 대한 자세한 내용은 다음 섹션을 참조하세요.

관리자 모드에 있는 경우 사용자 또는 문서로 검색할 수 있습니다. 사용자로 검색하는 경우 지정한 사용자가 공유한 모든 문서가 표시됩니다. 문서로 검색하는 경우 해당 문서를 공유한 조직의 모든 사용자가 표시됩니다. 그런 다음 검색 결과를 드릴하여 사용자가 공유한 문서를 추적하고 필요한 경우 해당 문서를 취소할 수 있습니다. 

관리자 모드를 종료하려면 **관리자 모드 끝내기** 옆에 있는 **X**합니다.

문서 추적 사이트를 사용하는 방법에 대한 자세한 내용은 사용자 가이드에서 [문서 추적 및 취소](sharing-app-track-revoke.md)를 참조하세요.



### <a name="usage-logging-for-the-document-tracking-site"></a>문서 추적 사이트에 대한 사용 현황 로깅

사용 현황 로그 파일의 다음과 같은 두 필드가 문서 추적에 적용됩니다: **AdminAction** 및 **ActingAsUser**.

**AdminAction** - 관리자가 문서 추적 사이트를 관리자 모드로 사용하는 경우(예: 사용자 대신 문서를 취소하거나 언제 공유되었는지 확인하기 위해) 이 필드에 true 값이 포함됩니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다.

**ActingAsUser** - AdminAction 필드가 true이면 이 필드에 관리자가 검색된 사용자 또는 문서 소유자로 대신 작업하는 사용자 이름이 포함됩니다. 사용자가 문서 추적 사이트에 로그인할 때는 이 필드가 비어 있습니다. 

사용자와 관리자가 문서 추적 사이트를 어떻게 사용하고 있는지를 기록하는 요청 유형도 있습니다. 예를 들어 **RevokeAccess**는 사용자 또는 사용자를 대신하는 관리자가 문서 추적 사이트에서 문서를 취소한 경우의 요청 유형입니다. 이 요청 유형을 AdminAction 필드와 함께 사용하여 사용자가 고유한 문서를 취소했는지(AdminAction 필드가 비어 있음), 아니면 관리자가 사용자 대신 문서를 취소했는지(AdminAction이 true임) 확인할 수 있습니다.


사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management Service 사용 현황 로깅 및 분석](../log-analyze-usage.md)을 참조하세요.

## <a name="ad-rms-only-support-for-multiple-email-domains-within-your-organization"></a>AD RMS만 해당: 조직 내의 여러 메일 도메인 지원
AD RMS를 사용하며 합병 또는 인수의 결과로 조직의 사용자에게 여러 메일 도메인이 있는 경우 다음과 같이 레지스트리를 편집해야 합니다.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**로 이동한 다음 **RmsSharingApp** 키가 아직 없으면 새로 만듭니다.

2.  **RmsSharingApp**을 선택하고 새 다중 문자열 값 **FederatedDomains**를 만든 후 조직에서 사용하는 도메인과 모든 하위 도메인을 추가합니다. 와일드카드는 지원되지 않습니다.

    예를 들면 다음과 같습니다. Coho Vineyard &amp; Winery라는 회사의 표준 이메일 도메인은 **cohovineyardandwinery.com**이지만 합병으로 인해 **cohowinery.com**, **eastcoast.cohowinery.com** 및 **cohovineyard** 이메일 도메인도 사용합니다. 이 경우 관리자는 **FederatedDomains** 값 데이터에 **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**를 입력합니다.

레지스트리를 이와 같이 변경하지 않으면 사용자가 조직의 다른 사용자에 의해 보호된 콘텐츠를 사용하지 못할 수도 있습니다. Azure Information Protection을 사용하는 경우에는 레지스트리를 이와 같이 편집할 필요가 없습니다.


## <a name="next-steps"></a>다음 단계
보호 수준(기본 및 일반) 간의 차이점 설명, 지원되는 파일 형식 및 파일 이름 확장명, 기본 보호 수준을 변경하는 방법을 포함하는 자세한 기술 정보는 [Rights Management 공유 응용 프로그램에 대한 기술 개요](sharing-app-admin-guide-technical.md)를 참조하세요.

