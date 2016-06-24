---
# required metadata

title: Azure 권한 관리 서비스 해제 및 비활성화 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리 서비스 해제 및 비활성화

*적용 대상: Azure 권한 관리, Office 365*

조직에서 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)](Azure RMS)를 사용하여 콘텐츠를 보호할지 여부를 항상 제어할 수 있으며, 이 정보 보호 솔루션을 더 이상 사용하지 않는 경우에도 이전에 보호했던 콘텐츠에 계속 액세스할 수 있습니다. 이전에 보호하던 콘텐츠에 대해 지속적인 액세스가 필요하지 않은 경우 단순히 서비스를 비활성화하고 Azure 권한 관리에 대한 구독을 만료시키면 됩니다. 예를 들어 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 프로덕션 환경에 배포하기 전에 테스트를 완료한 경우 이와 같이 서비스를 비활성화할 수 있습니다.

그러나 프로덕션에 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 배포한 경우 서비스 비활성화에 앞서 Azure 권한 관리 테넌트 키 사본이 필요하며 구독 만료 전에 이를 수행해야 합니다. 그래야 서비스 비활성화 후에도 Azure 권한 관리에서 보호하던 콘텐츠에 대한 액세스를 유지할 수 있습니다. HSM에서 자체 키를 생성 및 관리하면서 BYOK(Bring Your Own Key)를 사용한 경우 이미 Azure 권한 관리 테넌트 키가 있을 것입니다. 그러나 테넌트 키를 Microsoft에서 관리한 경우(기본값)에는 [Azure 권한 관리 테넌트 키에 대한 작업](operations-tenant-key.md) 문서에서 테넌트 키 내보내기 지침을 참조하세요.

> [!TIP]
> 구독이 만료된 후에도 Azure 권한 관리 테넌트가 그대로 유지되어 연장된 기간 동안 콘텐츠를 사용할 수 있습니다. 그러나 테넌트 키를 내보낼 수는 없습니다.

Azure 권한 관리 테넌트 키가 있으면 온-프레미스에 권한 관리를 배포하고(AD RMS) 테넌트 키를 TPD(Trusted Publishing Domain)로 가져올 수 있습니다. 그러면 Azure 권한 관리 배포 해제에 다음 옵션을 사용할 수 있습니다.

|적용 대상...|… 방법|
|----------------------------|--------------|
|모든 사용자가 Rights Management를 계속 사용하지만 Azure RMS보다 온-프레미스 솔루션을 사용하려는 경우|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) cmdlet을 사용하여 기존 사용자가 변경 후 보호되는 콘텐츠를 사용할 때 온-프레미스 배포를 사용하도록 안내합니다. 사용자가 자동으로 AD RMS 설치를 사용하여 보호되는 콘텐츠를 사용하게 됩니다.<br /><br />사용자가 이 변경 전에 보호한 콘텐츠를 사용하려면 RMS 클라이언트 배포 참고 사항의 [서비스 검색 섹션](../rms-client/client-deployment-notes.md)에 설명된 Office 2016 또는 Office 2013용 **LicensingRedirection** 레지스트리 키 및 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 Office 2010용 **LicenseServerRedirection** 레지스트리 키를 사용하여 클라이언트를 온-프레미스 배포로 리디렉션합니다..|
|권한 관리 기술의 사용을 완전히 중단하려는 경우 →|지정된 관리자에게 [슈퍼 사용자 권한](../deploy-use/configure-super-users.md)을 부여하고 해당 사용자에게 [RMS 보호 도구](http://www.microsoft.com/en-us/download/details.aspx?id=47256)를 제공합니다..<br /><br />그러면 이 관리자가 해당 도구를 사용하여 Azure 권한 관리로 보호되던 폴더의 파일을 대량 해독하여 파일을 보호되지 않는 상태로 되돌릴 수 있으므로 Azure RMS나 AD RMS같은 권한 관리 기술 없이도 읽을 수 있습니다. 이 도구는 Azure RMS 및 AD RMS 모두에 사용할 수 있으므로 Azure RMS를 비활성화하기 전이나 후 또는 둘을 조합하여 파일 해독 시점을 선택할 수 있습니다.|
|Azure RMS로 보호되던 일부 파일을 파악할 수 없거나 모든 사용자가 자동으로 누락된 모든 보호되는 파일을 읽을 수 있게 하려는 경우 →|RMS 클라이언트 배포 참고 사항의 [서비스 검색 섹션](../rms-client/client-deployment-notes.md)에 설명된 Office 2016 및 Office 2013용 **LicensingRedirection** 레지스트리 키와 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 Office 2010용 **LicenseServerRedirection** 레지스트리 키를 사용하여 모든 클라이언트 컴퓨터에서 레지스트리 설정을 배포합니다..<br /><br />또한 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에서 설명한 대로 **DisableCreation**을 **1**로 설정하여 사용자가 새 파일을 보호하지 못하도록 다른 레지스트리 설정을 배포할 수도 있습니다..|
|누락된 모든 파일에 대해 제어되는 수동 복구 서비스를 원하는 경우    →|데이터 복구 그룹에서 지정된 사용자에게 [슈퍼 사용자 권한](../deploy-use/configure-super-users.md)을 부여하고 [RMS 보호 도구](http://www.microsoft.com/en-us/download/details.aspx?id=47256)를 제공하여 표준 사용자의 요청 시 파일 보호를 해제할 수 있게 합니다.<br /><br />모든 컴퓨터에서 [Office 레지스트리 설정](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx)에 설명된 대로 **DisableCreation**을 **1**로 설정하여 사용자가 새 파일을 보호하지 못하도록 레지스트리 설정을 배포합니다..|
이 표의 절차에 대한 자세한 내용은 다음 리소스를 참조하세요.

-   AD RMS 및 배포 참조에 대한 내용은 [Active Directory Rights Management Services 개요](https://technet.microsoft.com/library/hh831364.aspx) 항목을 참조하세요..

-   TPD 파일로 Azure RMS 테넌트 키를 가져오기 위한 지침은 [TPD(신뢰할 수 있는 게시 도메인) 추가](https://technet.microsoft.com/library/cc771460.aspx) 항목을 참조하세요..

-   Azure RMS용 Windows PowerShell 모듈을 설치하고 마이그레이션 URL을 설정하려면 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md) 항목을 참조하세요..

조직에 대한 Azure RMS 서비스를 비활성화할 준비가 되었으면 다음 지침을 사용합니다.

## 권한 관리 비활성화
비활성화하려면 다음 절차 중 하나를 사용하세요. [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Windows PowerShell cmdlet [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx)을 사용하여 비활성화할 수도 있습니다. [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### Office 365 관리 센터에서 권한 관리를 비활성화하려면

1.  Office 365 배포의 관리자인[회사 또는 학교 계정을 사용하여 Office 365에 로그인](https://portal.office.com/) 합니다.

2.  Office 365 관리 센터가 자동으로 표시되지 않으면 왼쪽 위에서 앱 시작 관리자 아이콘을 선택하고 **관리자**를 선택합니다. **관리자** 타일은 Office 365 관리자에게만 나타납니다.

    > [!TIP]
    > 관리 센터 도움말은 [Office 365 관리 센터 정보 - 관리자 도움말](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)을 참조하세요..

3.  왼쪽 창에서 **서비스 설정**을 확장합니다..

4.  **권한 관리**를 클릭합니다..

5.  **권한 관리** 페이지에서 **관리**를 클릭합니다..

6.  **권한 관리** 페이지에서 **비활성화**를 클릭합니다..

7.  **Rights Management를 비활성화하시겠습니까?**라는 메시지가 나타나면 **비활성화**를 클릭합니다..

이제 **Rights Management가 활성화되지 않았습니다.** 가 표시되고 활성화 옵션이 나타납니다.

#### Azure 클래식 포털에서 Rights Management를 비활성화하려면

1.  [Azure 클래식 포털](http://go.microsoft.com/fwlink/p/?LinkID=275081)에 로그인합니다..

2.  왼쪽 창에서 **Active Directory**를 클릭합니다..

3.  **Active Directory** 페이지에서 **권한 관리**를 클릭합니다..

4.  [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]에 대해 관리할 디렉터리를 선택하고 **비활성화**를 클릭한 다음 작업을 확인합니다.

이제 **권한 관리 상태**가 **비활성**으로 표시되고 **비활성화** 옵션이 **활성화**로 바뀝니다..





<!--HONumber=Apr16_HO4-->


