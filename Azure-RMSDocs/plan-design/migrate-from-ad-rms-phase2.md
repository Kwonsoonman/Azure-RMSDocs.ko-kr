---
# required metadata

title: AD RMS에서 Azure 권한 관리로 마이그레이션 - 2단계 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# 마이그레이션 2단계 - 클라이언트 쪽 구성

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*

AD RMS에서 Azure 권한 관리(Azure RMS)로 마이그레이션 2단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 5단계를 설명합니다..


## 5단계. Azure RMS를 사용하도록 클라이언트 다시 구성
Windows 클라이언트:

1.  [마이그레이션 스크립트를 다운로드](http://go.microsoft.com/fwlink/?LinkId=524619)합니다.

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    이러한 스크립트는 AD RMS 보다는 Azure RMS 서비스를 사용하도록 Windows 컴퓨터에서 구성을 다시 설정합니다.

2.  리디렉션 스크립트(Redirect_OnPrem.cmd)의 지침에 따라 새 Azure RMS 테넌트를 가리키도록 스크립트를 수정합니다.

3.  Windows 컴퓨터에서는 사용자의 컨텍스트에서 상승된 권한으로 이러한 스크립트를 실행합니다.

모바일 장치 클라이언트 및 Mac 컴퓨터:

-   [AD RMS 모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포할 때 만든 DNS SRV 레코드를 제거합니다..

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

-   다음 레지스트리 값을 삭제합니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   다음의 각 위치에서 매개 변수로 제공된 각 URL에 대해 다음의 레지스트리 값을 만듭니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    각 항목에는 **https://OldRMSserverURL/_wmcs/licensing** 형식의 데이터를 포함하는 REG_SZ 값 **https://&lt;YourTenantURL&gt;/_wmcs/licensing**이 포함되어 있습니다..

    > [!NOTE]
    > *&lt;YourTenantURL&gt;*의 형식은 다음과 같습니다. **{GUID}.rms.[Region].aadrm.com**.
    > 
    > 예: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Azure RMS에 대해 **Get-AadrmConfiguration** cmdlet를 실행하는 경우 [RightsManagementServiceId](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) 값을 식별하여 이 값을 찾을 수 있습니다.


## 다음 단계
마이그레이션을 계속하려면 [3단계 - 지원 서비스 구성](migrate-from-ad-rms-phase3.md)으로 이동합니다..

<!--HONumber=Apr16_HO4-->


