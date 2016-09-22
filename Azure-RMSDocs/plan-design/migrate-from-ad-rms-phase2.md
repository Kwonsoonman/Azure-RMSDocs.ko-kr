---
title: "AD RMS에서 Azure 권한 관리로 마이그레이션 - 2단계 | Azure RMS"
description: "AD RMS에서 Azure RMS(Azure Rights Management)로 마이그레이션하는 과정의 두 번째 단계로, AD RMS에서 Azure Rights Management로의 마이그레이션 5단계가 포함됩니다."
author: cabailey
manager: mbaldwin
ms.date: 09/09/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4184c8b78d8ca6beb88efad79e0372367c523f2f
ms.openlocfilehash: 2d8abaec220074531724ce4e95b4aefe23d0b2d6


---
# 마이그레이션 2단계 - 클라이언트 쪽 구성

>*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*

AD RMS에서 Azure 권한 관리(Azure RMS)로 마이그레이션 2단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 5단계를 설명합니다.


## 5단계. Azure RMS를 사용하도록 클라이언트 다시 구성
Windows 클라이언트:

1.  [마이그레이션 스크립트 다운로드](https://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    이러한 스크립트는 AD RMS 보다는 Azure RMS 서비스를 사용하도록 Windows 컴퓨터에서 구성을 다시 설정합니다.

2.  리디렉션 스크립트(Redirect_OnPrem.cmd)의 지침에 따라 새 Azure RMS 테넌트를 가리키도록 스크립트를 수정합니다.

    > [!IMPORTANT]
    > 지침에는 **adrms** 및 **adrms.contoso.com**의 예제 주소를 고유의 AD RMS 서버 주소로 바꾸는 것이 포함되어 있습니다. 이렇게 할 때에는 주소의 앞뒤에 추가 공백이 없도록 주의해야 합니다. 추가 공백이 있으면 마이그레이션 스크립트가 중단되어 문제의 근본 원인으로 확인하기가 매우 어렵습니다. 일부 편집 도구는 텍스트를 붙여넣은 후 자동으로 공백을 추가합니다.

3. 사용자에게 Office 2016이 있는 경우: Office 2016에 대한 구성을 포함하도록 스크립트가 아직 업데이트되지 않았으므로 사용자에게 이 버전의 Office가 있다면 스크립트를 수동으로 업데이트해야 합니다.

    - **CleanUpRMS.cmd**의 경우 - `reg delete HKCU\Software\Microsoft\Office\15.0\Common\DRM /f` 줄을 검색하고 이 행의 바로 아래에서 다음 줄을 추가합니다.

            reg delete HKCU\Software\Microsoft\Office\16.0\Common\DRM /f

    - **Redirect_Onprem.cmd**의 경우 - `reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F` 줄을 검색하고 이 행의 바로 아래에서 다음의 2줄을 추가합니다.

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServerUrl" /d "https://%CloudRMS%/_wmcs/licensing" /F 

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F

    선택 사항: 스크립트가 주석에서 Office 2016을 참조하지 않습니다. Office 2016에 대한 이러한 추가 사항을 반영하도록 주석을 업데이트하려는 경우에는 **Redirect_Onprem.cmd**를 다음과 같이 변경하세요.

    - `::     or MSIPC (Office 2013) with on-premises AD RMS`를 검색하고 이것을 다음과 같이 바꿉니다.
    
            ::     or MSIPC (Office 2013 and 2016) with on-premises AD RMS

    - `echo Redirect SCP for Office 2013`을 검색하고 이것을 다음과 같이 바꿉니다.
    
            echo Redirect SCP for Office versions based on MSIPC

    - `echo Redirect MSIPC for Office 2013`을 검색하고 다음과 같이 바꿉니다.
    
            echo Redirect MSIPC for Office versions based on MSIPC

4.  Windows 컴퓨터:

    - 사용자의 컨텍스트에서 상승된 권한으로 이러한 스크립트를 실행합니다.

    모바일 장치 클라이언트 및 Mac 컴퓨터:

    -  [AD RMS 모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포할 때 만든 DNS SRV 레코드를 제거합니다.

#### 마이그레이션 스크립트로 인한 변경 내용
이 섹션에서는 마이그레이션 스크립트로 인한 변경 내용을 설명합니다. 이 정보는 참조용으로만 또는 문제 해결을 위해 사용할 수 있고, 직접 변경을 수행하려는 경우에 참조할 수 있습니다.

CleanUpRMS_RUN_Elevated.cmd:

-   긴 파일 이름을 포함하는 하위 폴더 및 파일을 비롯하여, %userprofile%\AppData\Local\Microsoft\DRM 및 %userprofile%\AppData\Local\Microsoft\MSIPC 폴더의 내용을 삭제합니다.

-   다음 레지스트리 키의 내용을 삭제합니다.

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   다음 레지스트리 값을 추가합니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   다음의 각 위치에서 매개 변수로 제공된 각 URL에 대해 다음의 레지스트리 값을 만듭니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    각 항목에는 **https://&lt;YourTenantURL&gt;/_wmcs/licensing** 형식의 데이터를 포함하는 REG_SZ 값 **https://OldRMSserverURL/_wmcs/licensing**이 포함되어 있습니다.

    > [!NOTE]
    > *&lt;YourTenantURL&gt;*의 형식은 다음과 같습니다. **{GUID}.rms.[Region].aadrm.com**
    > 
    > 예: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Azure RMS에 대해 **Get-AadrmConfiguration** cmdlet를 실행하는 경우 [RightsManagementServiceId](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) 값을 식별하여 이 값을 찾을 수 있습니다.


## 다음 단계
마이그레이션을 계속하려면 [3단계 - 지원 서비스 구성](migrate-from-ad-rms-phase3.md)으로 이동합니다.


<!--HONumber=Sep16_HO2-->


