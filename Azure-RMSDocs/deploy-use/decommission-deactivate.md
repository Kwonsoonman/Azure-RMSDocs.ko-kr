---
title: Azure RMS 서비스 해제 및 비활성화
description: Azure Information Protection의 클라우드 기반 보호 서비스를 더 이상 사용하지 않으려는 경우에 적용되는 정보와 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e12ba0bfb60043b46002f35003955b5dc6d9eeb6
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Azure Information Protection 보호 해제 및 비활성화

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection에서 Azure Rights Management 서비스를 사용하여 조직이 콘텐츠를 보호하는지 항상 제어할 수 있습니다. 이 정보 보호 솔루션을 더 이상 사용하지 않으려는 경우 이전에 보호했던 콘텐츠에는 계속 액세스할 수 있습니다.

이전에 보호하던 콘텐츠에 계속 액세스할 필요가 없는 경우 서비스를 비활성화하고 Azure Information Protection에 대한 구독이 만료되게 하면 됩니다. 예를 들어 Azure Information Protection을 프로덕션 환경에 배포하기 전에 테스트를 완료한 경우 이와 같이 서비스를 비활성화할 수 있습니다.

그러나 프로덕션에 Azure Information Protection을 배포하고 문서와 메일을 보호한 경우 Azure Rights Management 서비스를 비활성화하기 전에 Azure Information Protection 테넌트 키의 사본이 있는지 확인합니다. 서비스를 비활성화한 후 Azure Rights Management에서 보호한 콘텐츠에 대한 액세스 권한을 유지할 수 있도록 구독이 만료되기 전에 키의 사본이 있는지 확인합니다. HSM에서 자체 키를 생성 및 관리하면서 BYOK(Bring Your Own Key)를 사용한 경우 이미 Azure Information Protection 테넌트 키가 있을 것입니다. 그러나 테넌트 키를 Microsoft에서 관리한 경우(기본값)에는 [Azure Information Protection 테넌트 키에 대한 작업](operations-tenant-key.md) 문서에서 테넌트 키 내보내기 지침을 참조하세요.

> [!TIP]
> 구독이 만료된 후에도 Azure Information Protection 테넌트가 그대로 유지되어 연장된 기간 동안 콘텐츠를 사용할 수 있습니다. 그러나 테넌트 키를 내보낼 수는 없습니다.

Azure Information Protection 테넌트 키가 있으면 온-프레미스에 권한 관리를 배포하고(AD RMS) 테넌트 키를 TPD(Trusted Publishing Domain)로 가져올 수 있습니다. 그러면 다음 옵션을 사용하여 Azure Information Protection 배포를 해제할 수 있습니다.

|적용 대상...|… 방법|
|----------------------------|--------------|
|모든 사용자가 Rights Management를 계속 사용하지만 Azure Information Protection보다 온-프레미스 솔루션을 사용하려는 경우|[Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl) cmdlet을 사용하여 기존 사용자가 변경 후 보호되는 콘텐츠를 사용할 때 온-프레미스 배포를 사용하도록 안내합니다. 사용자가 자동으로 AD RMS 설치를 사용하여 보호되는 콘텐츠를 사용하게 됩니다.<br /><br />이 변경 전에 보호된 콘텐츠를 사용할 수 있도록 Office 2016 또는 Office 2013의 **LicensingRedirection** 레지스트리 키를 사용하여 클라이언트를 온-프레미스 배포로 리디렉션합니다. 지침은 RMS 클라이언트 배포 참고 사항의 [서비스 검색 섹션](../rms-client/client-deployment-notes.md) 및 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 대로 Office 2010의 **LicenseServerRedirection** 레지스트리 키를 참조하세요.|
|권한 관리 기술의 사용을 완전히 중단하려는 경우 →|지정된 관리자에게 [슈퍼 사용자 권한](../deploy-use/configure-super-users.md)을 부여하고 이 사용자에 대해 [Azure Information Protection 클라이언트](../rms-client/client-admin-guide-install.md)를 설치합니다.<br /><br />그러면 이 관리자가 이 클라이언트의 PowerShell 모듈을 사용하여 Azure Rights Management 서비스를 통해 보호되는 폴더의 파일을 대량 해독할 수 있습니다. 파일을 보호되지 않은 상태로 되돌리므로, Azure Information Protection 또는 AD RMS와 같은 Rights Management 기술 없이도 읽을 수 있습니다. 이 PowerShell 모듈은 Azure Information Protection의 Azure Rights Management 서비스 및 AD RMS 모두에 사용할 수 있으므로 Azure Rights Management 서비스를 비활성화하기 전이나 후 또는 둘을 조합하여 파일 해독 시점을 선택할 수 있습니다.|
|Azure Information Protection의 Azure Rights Management 서비스에서 보호한 모든 파일을 식별할 수 없습니다. 또는 모든 사용자가 누락된 모든 보호 파일을 자동으로 읽을 수 있게 합니다.  →|RMS 클라이언트 배포 참고 사항의 [서비스 검색 섹션](../rms-client/client-deployment-notes.md)에 설명된 Office 2016 및 Office 2013용 **LicensingRedirection** 레지스트리 키와 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 Office 2010용 **LicenseServerRedirection** 레지스트리 키를 사용하여 모든 클라이언트 컴퓨터에서 레지스트리 설정을 배포합니다.<br /><br />또한 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에서 설명한 대로 **DisableCreation**을 **1**로 설정하여 사용자가 새 파일을 보호하지 못하도록 다른 레지스트리 설정을 배포할 수도 있습니다.|
|누락된 모든 파일에 대해 제어되는 수동 복구 서비스를 원하는 경우    →|데이터 복구 그룹에서 지정된 사용자에게 [슈퍼 사용자 권한](../deploy-use/configure-super-users.md)을 부여하고 이러한 사용자에 대해 [Azure Information Protection 클라이언트](../rms-client/client-admin-guide-install.md)를 설치하여 표준 사용자가 요청 시 파일 보호를 해제할 수 있게 합니다.<br /><br />모든 컴퓨터에서 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 대로 **DisableCreation**을 **1**로 설정하여 사용자가 새 파일을 보호하지 못하도록 레지스트리 설정을 배포합니다.|
이 표의 절차에 대한 자세한 내용은 다음 리소스를 참조하세요.

- AD RMS 및 배포 참조에 대한 내용은 [Active Directory Rights Management Services 개요](https://technet.microsoft.com/library/hh831364.aspx)를 참조하세요.

- TPD 파일로 Azure Information Protection 테넌트 키를 가져오는 방법에 대한 자세한 내용은 [TPD(트러스트된 게시 도메인) 추가](https://technet.microsoft.com/library/cc771460.aspx)를 참조하세요.

- Azure Rights Management용 Windows PowerShell 모듈을 설치하고 마이그레이션 URL을 설정하려면 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.

- Azure Information Protection 클라이언트에서 PowerShell을 사용하려면 [Azure Information Protection 클라이언트에서 PowerShell 사용](../rms-client/client-admin-guide-powershell.md)을 참조하세요.

조직에 대한 Azure Rights Management 서비스를 비활성화할 준비가 되었으면 다음 지침을 사용합니다.

## <a name="deactivating-rights-management"></a>권한 관리 비활성화
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 비활성화하려면 다음 절차 중 하나를 사용하세요.

> [!TIP]
> Windows PowerShell cmdlet [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm)을 사용하여 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]를 비활성화할 수도 있습니다.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Office 365 관리 센터에서 권한 관리를 비활성화하려면

1. Office 365 관리자를 위한 [Rights Management 페이지](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx)로 이동합니다.
    
    로그인하라는 메시지가 나타나면 Office 365에 대한 전역 관리자 계정을 사용합니다.    

2. **Rights Management** 페이지에서 **비활성화**를 클릭합니다.

3.  **Rights Management를 비활성화하시겠습니까?**라는 메시지가 나타나면 **비활성화**를 클릭합니다.

이제 **Rights Management가 활성화되지 않았습니다.** 가 표시되고 활성화 옵션이 나타납니다.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Azure 포털에서 Rights Management를 비활성화하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 초기 **Azure Information Protection** 블레이드에서 **보호 활성화**를 선택합니다. 

3.  **Azure Information Protection - 보호 활성화** 블레이드에서 **비활성화**를 선택합니다. **예**를 선택하여 확인합니다.

정보 표시줄에 **비활성화가 성공적으로 완료됨**이 표시되고 **비활성화**는 이제 **활성화**로 바뀝니다. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


