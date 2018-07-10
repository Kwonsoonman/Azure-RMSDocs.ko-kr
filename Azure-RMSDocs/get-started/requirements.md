---
title: Azure Information Protection에 대한 요구 사항
description: Azure Information Protection을 조직에 배포하기 위한 필수 구성 요소를 식별합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 18168f89c762011146f7f3f131079f5a502820ac
ms.sourcegitcommit: 3f524c5af39bee39169f86d9c4e72c661c960d83
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37069379"
---
# <a name="requirements-for-azure-information-protection"></a>Azure Information Protection에 대한 요구 사항

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection을 조직에 배포하기 전에 다음 필수 구성 요소가 준비되어 있는지 확인하세요. 

## <a name="subscription-for-azure-information-protection"></a>Azure Information Protection 구독

**분류, 레이블 지정 및 보호의 경우**: [Azure Information Protection 계획](https://azure.microsoft.com/pricing/details/information-protection/)이 있어야 합니다. 

**보호 전용의 경우**: [Azure Information Protection이 포함된 Office 365 계획](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)이 있어야 합니다.

조직의 구독에 사용하려는 Azure Information Protection 기능이 포함되어 있는지 확인하려면 [Azure Information Protection 가격 책정](https://azure.microsoft.com/pricing/details/information-protection) 페이지에서 기능 목록을 검토합니다.

> [!TIP]
> 개인 이메일 주소에 보호된 메일을 보내려면, Office 365 계획 또는 Exchange Online 독립 실행형 계획이 [Office 365 메시지 암호화의 새로운 기능](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)을 지원하는지 확인하세요. 예: Gmail, Yahoo 및 Microsoft 다음 리소스를 확인합니다.
>
> [Exchange Online 서비스 설명](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> [Office 365 Education](https://technet.microsoft.com/library/mt844095.aspx)
>
> [Office 365 US Government](https://technet.microsoft.com/library/mt774581.aspx)

구독 또는 라이선스에 대한 질문이 있는 경우 이 페이지에 게시하지 말고, Microsoft 계정 관리자 또는 [Microsoft 지원](information-support.md#to-contact-microsoft-support)에 문의하세요.

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Information Protection에 대해 사용자 인증 및 권한 부여를 지원하려면 조직에 Azure AD(Azure Active Directory)가 있어야 합니다. 또한 온-프레미스 디렉터리(AD DS)의 사용자 계정을 사용하려는 경우 디렉터리 통합도 구성해야 합니다.

Azure Information Protection에 대해 SSO(Single Sign-On)가 지원되므로 사용자에게 자격 증명을 입력하라는 메시지가 반복해서 표시되지 않습니다. 페더레이션에 다른 공급업체 솔루션을 사용하는 경우에는 해당 공급업체에 Azure AD용으로 구성하는 방법을 확인하세요. WS-Trust는 이러한 솔루션에서 Single Sign-On을 지원하기 위해 공통으로 필요합니다. 

MFA(Multi-Factor Authentication)는 필수 클라이언트 소프트웨어 및 올바르게 구성된 MFA 지원 인프라가 있는 경우 Azure Information Protection에서 지원됩니다.

조건부 액세스는 Azure Information Protection으로 보호되는 문서에 대한 미리 보기에서 지원됩니다. 자세한 내용은 다음 FAQ를 참조하세요. [Azure Information Protection이 조건부 액세스를 위한 사용 가능한 클라우드 앱으로 나열되어 있습니다. 작동 방법은 무엇인가요?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

인증 요구 사항에 대한 자세한 내용은 [Azure Information Protection에 대한 Azure Active Directory 요구 사항](requirements-azure-ad.md)을 참조하세요. 

권한을 부여할 사용자 및 그룹의 요구 사항에 대한 자세한 내용은 [Azure Information Protection을 위한 사용자 및 그룹 준비](../plan-design/prepare.md)를 참조하세요.

## <a name="client-devices"></a>클라이언트 장치

사용자에게 Azure Information Protection을 지원하는 운영 체제를 실행하는 클라이언트 장치(컴퓨터 또는 모바일 장치)가 있어야 합니다.

다음은 사용자가 문서 및 메일을 분류하여 레이블을 지정할 수 있도록 Azure Information Protection 클라이언트를 지원하는 장치입니다.

- Windows 10(x86, x64)
    
    - 참가자용 Windows 10 RS4 빌드에는 필기 지원이 없습니다. 

- Windows 8.1(x86, x64)

- Windows 8(x86, x64)

- Windows 7 서비스 팩 1(x86, x64)

- Windows Server 2016 

- Windows Server 2012 R2 및 Windows Server 2012

- Windows Server 2008 R2 

나열된 서버 버전의 경우 Azure Information Protection 클라이언트가 원격 데스크톱 서비스에 대해 지원됩니다. 원격 데스크톱 서비스와 함께 Azure Information Protection 클라이언트를 사용할 때 사용자 프로필을 삭제하는 경우 **%Appdata%\Microsoft\Protect** 폴더는 삭제하지 마세요.

Azure Information Protection 클라이언트에서 Azure Rights Management 서비스를 통해 데이터를 보호하는 경우 Azure Rights Management 서비스를 지원하는 [동일한 장치](requirements-client-devices.md)에서 이 데이터를 사용할 수 있습니다.

Azure Information Protection 클라이언트에는 관리자 가이드에 나열된 [추가적인 전제 조건](../rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client)이 있습니다.

## <a name="applications"></a>응용 프로그램

Azure Information Protection 클라이언트는 다음 Office 버전의 Office 응용 프로그램인 **Word**, **Excel**, **PowerPoint** 및 **Outlook**을 사용하여 문서 및 메일의 레이블을 지정하고 보호할 수 있습니다.

- Office 365 ProPlus(2016 앱 또는 2013 앱 포함)(간편 실행 또는 Windows Installer 기반 설치)
    
    이러한 Office 버전은 Azure Information Protection에서 데이터 보호를 포함하는 Office 365 구독의 전부는 아니지만 대부분이 포함됩니다. Office 365 ProPlus가 포함되어 있는지 확인하려면 구독 정보를 확인합니다. 또한 이 정보는 [Azure Information Protection 데이터 시트](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)에서 찾을 수 있습니다.

- Office Professional Plus 2016

- Office Professional Plus 2013 서비스 팩 1

- Office Professional Plus 2010 서비스 팩 2

다른 버전의 Office는 권한 관리 서비스를 사용하여 문서와 메일을 보호할 수 없습니다. 이러한 버전에서는 Azure Information Protection이 분류용으로만 지원됩니다. 따라서 보호를 적용하는 레이블은 Azure Information Protection 모음이나 Office 리본의 **보호** 단추에서 사용자에게 표시되지 않습니다. 

Azure Information Protection 클라이언트는 동일한 컴퓨터에 여러 버전의 Office를 지원하지 않습니다. 또한 이 클라이언트는 Office의 사용자 계정 전환을 지원하지 않습니다.

데이터 보호 서비스를 지원하는 Office 버전에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](requirements-applications.md)을 참조하세요.

## <a name="firewalls-and-network-infrastructure"></a>방화벽 및 네트워크 인프라

특정 연결을 허용하도록 구성되는 방화벽이나 유사한 중개 네트워크 장치가 있는 경우 Office 문서 [Office 365 URL 및 IP 주소 범위](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)의 [Office 365 포털 및 공유](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) 섹션에 있는 **Azure RMS(Rights Management)** 정보를 참조하세요.

이 Office 문서의 지침에 따라 RSS 피드를 구독하여 이 정보에 대한 최신 변경 내용을 확인하세요.

Office 문서의 정보 외에 Azure Information Protection과 관련하여 다음 사항에 유의하세요.

- TCP 443에서 **api.informationprotection.azure.com**으로의 HTTPS 트래픽을 허용합니다.

- TCP 443의 HTTPS 트래픽을 **mobile.pipe.aria.microsoft.com**에 허용합니다.

- 인증이 필요한 웹 프록시를 사용하는 경우 사용자의 Active Directory 로그온 자격 증명으로 통합된 Windows 인증을 사용하도록 구성해야 합니다.

- Azure Rights Management 서비스에 대한 TLS 클라이언트-서비스 연결을 종료하지 마세요(예: 패킷 수준 조사를 수행하려면). 연결을 종료하면 Azure Rights Management 서비스와의 통신 보안 유지를 위해 Microsoft에서 관리하는 CA와 함께 RMS 클라이언트가 사용하는 인증서 고정이 끊어집니다.
    
    - 팁: Chrome에서 주소 표시줄에 보안 연결을 표시하는 방법으로 이 브라우저를 사용하여 Azure Rights Management 서비스에 연결하기 전에 클라이언트 연결이 종료되는지를 신속하게 확인할 수 있습니다. 브라우저 주소 표시줄에 URL(`https://admin.na.aadrm.com/admin/admin.svc`)을 입력합니다. 
    
        브라우저 창에 표시되는 내용은 걱정하지 않아도 됩니다. 대신 주소 표시줄의 자물쇠를 클릭하여 사이트 정보를 보세요. 사이트 정보를 사용하면 발행 인증 기관(CA)을 볼 수 있습니다. Microsoft CA에서 인증서를 발행하지 않은 경우 보안 클라이언트-서비스 연결이 종료되어 방화벽을 재구성해야 할 가능성이 큽니다. 다음 그림은 Microsoft 발행 CA의 예제를 보여줍니다. 내부 CA에서 인증서를 발행한 경우 이 구성은 Azure Information Protection과 호환되지 않습니다.
        
        ![Azure Information Protection 연결을 위해 발급된 인증서 확인](../media/certificate-checking.png)

### <a name="on-premises-servers"></a>온-프레미스 서버

온-프레미스 서버에서 Azure Information Protection의 Azure Rights Management 서비스를 사용하려는 경우에 지원되는 제품은 다음과 같습니다.

- Exchange Server

- SharePoint Server

- 파일 분류 인프라를 지원하는 Windows Server 파일 서버

이 시나리오에 대한 추가 요구 사항에 대한 자세한 내용은 [Azure Rights Management 데이터 보호를 지원하는 온-프레미스 서버](requirements-servers.md)를 참조하세요.

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Azure RMS와 AD RMS 함께 사용

다음 배포 시나리오는 [HYOK 보호](../deploy-use/configure-adrms-restrictions.md)용 AD RMS를 Azure Information Protection과 함께 사용하는 경우(“hold your own key” 구성)에만 지원됩니다.

- [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)에 설명된 대로, 마이그레이션 중인 경우를 제외하고 같은 조직에서 AD RMS와 Azure RMS를 함께 실행하는 경우.

[AD RMS에서 Azure Information Protection으로](http://technet.microsoft.com/library/Dn858447.aspx), [Azure Information Protection에서 AD RMS로](/powershell/module/aadrm/Set-AadrmMigrationUrl)의 지원되는 마이그레이션 경로가 있습니다. Azure Information Protection을 배포한 후 이 클라우드 서비스를 더 이상 사용하지 않겠다고 결정한 경우 [Azure Information Protection 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


