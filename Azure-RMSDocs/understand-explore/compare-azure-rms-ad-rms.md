---
title: "Azure Information Protection 및 AD RMS 비교 | Azure Information Protection"
description: "AD RMS(Active Directory Rights Management Services)에 대해 잘 알고 있거나 이전에 AD RMS를 배포한 경우 기능 및 요구 사항 측면에서 Azure Information Protection이 어떻게 다른지를 확인하려면"
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4fd87a530c23905601625b46a241286cf55d025b
ms.openlocfilehash: 69df1c9eee860672a422aa31995386f657a2c39f


---

# Azure Information Protection 및 AD RMS 비교

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS(Active Directory Rights Management Services)에 대해 잘 알고 있거나 이전에 AD RMS를 배포한 경우 정보 보호 솔루션으로써 기능 및 요구 사항 측면에서 Azure Information Protection이 어떻게 다른지를 확인하려면

Azure Information Protection에 대한 주요 차이점 중 일부를 사용합니다.

- **필요한 서버 인프라 없음**: Microsoft Azure에서 자동으로 처리하므로 Azure Information Protection에는 추가 서버 및 AD RMS에 필요한 PKI 인증서가 필요하지 않습니다. 따라서 이 클라우드 솔루션을 빠르게 배포하고 쉽게 유지 관리할 수 있습니다.

- **클라우드 기반 인증**: Azure Information Protection에서는 내부 사용자와 다른 조직의 사용자 모두에 대해 Azure AD를 사용하여 인증합니다. 즉, 내부 네트워크에 연결되지 않았으며 다른 조직의 사용자와 보호된 콘텐츠를 더 쉽게 공유하는 경우에도 모바일 사용자를 인증할 수 있습니다. 대부분의 조직에서는 Azure 서비스를 실행하거나 Office 365를 사용하고 있으므로 이미 Azure AD의 사용자 계정을 갖고 있습니다. 그러나 그렇지 않은 경우 개인용 RMS를 통해 사용자는 무료 계정을 만들 수 있습니다. 다른 조직과 AD RMS로 보호된 콘텐츠를 공유하려면 각 조직에 대한 명시적 트러스트를 구성해야 합니다.

- **모바일 장치에 대한 기본 제공 지원**: 모바일 장치 및 Mac 컴퓨터를 지원하기 위해 Azure RMS에 대한 배포를 변경할 필요가 없습니다. AD RMS를 사용하는 이러한 장치를 지원하려면 모바일 장치 확장을 설치하고, 페더레이션을 위한 AD FS를 구성하며, 공용 DNS 서비스에 대한 추가 레코드를 만듭니다.

- **기본 템플릿**: Azure Information Protection 서비스가 활성화되는 즉시 두 개의 기본 템플릿을 만듭니다. 따라서 중요한 데이터를 매우 쉽게 즉시 보호할 수 있습니다. AD RMS에 대한 기본 템플릿은 없습니다.

- **부서별 템플릿**: Azure Information Protection에서는 만드는 추가 템플릿에 대한 구성 설정으로 부서별 템플릿을 지원합니다. 이 설정을 통해 클라이언트 응용 프로그램(예: Office 앱)에서 템플릿을 볼 수 있는 사용자를 지정할 수 있습니다. 이를 통해 해당 사용자는 서로 다른 사용자 그룹에 대해 정의된 올바른 정책을 쉽게 선택할 수 있습니다. AD RMS에서는 부서별 템플릿을 지원하지 않습니다.

- **문서 추적, 해지 및 메일 알림**: Azure Information Protection에서 RMS 공유 앱으로 이러한 기능을 지원하는 반면 AD RMS에서는 지원하지 않습니다.

- **분류 및 레이블 지정**: Azure Information Protection은 Office 응용 프로그램과 통합된 Azure 정보 보호 표시줄을 사용하여 이 기능을 지원하지만 AD RMS는 지원하지 않습니다.


또한 Azure Information Protection이 클라우드 서비스이므로 온-프레미스 서버 기반 솔루션보다 더 빠르게 새 기능을 제공하고 수정할 수 있습니다. Windows Server 2016에서 AD RMS에 대해 계획 된 새로운 기능은 없습니다.

자세한 내용과 다른 차이점은, 아래 표에서 Azure Information Protection 및 AD RMS의 기능과 이점을 비교한 내용을 통해 확인할 수 있습니다. 보안 관련 비교 사항에 대한 문의 사항이 있으면 이 문서에서 [서명 및 암호화를 위한 암호화 컨트롤](compare-azure-rms-ad-rms.md#cryptographic-controls-for-signing-and-encryption) 섹션을 참조하세요.

> [!NOTE]
> 보다 간편한 비교를 위해 이 표에 나와 있는 일부 정보는 [Azure Information Protection 요구 사항](../get-started/requirements-azure-rms.md)의 정보와 중복됩니다. [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]에 대한 더욱 구체적인 지원 및 버전 정보는 해당 소스를 참조하세요.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Exchange Online, SharePoint Online 등의 Microsoft Online 서비스와 Office 365의 IRM(정보 권한 관리) 기능을 지원합니다.<br /><br />Exchange Server, SharePoint Server 등의 온-프레미스 Microsoft 서버 제품과 Windows Server 및 FCI(파일 분류 인프라)를 실행하는 파일 서버도 지원합니다.|Exchange Server, SharePoint Server 등의 온-프레미스 Microsoft 서버 제품과 Windows Server 및 FCI(파일 분류 인프라)를 실행하는 파일 서버를 지원합니다.|
|조직의 사용자와 조직 간의 암시적 트러스트를 사용하도록 설정합니다. 즉, 같은 조직 내의 사용자 또는 여러 조직의 사용자(사용자가 [!INCLUDE[o365_1](../includes/o365_1_md.md)] 또는 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용하거나 개인용 RMS에 등록한 경우) 간에 보호된 콘텐츠를 공유할 수 있습니다.|AD FS(Active Directory Federation Services)를 사용하여 만드는 페더레이션 트러스트 또는 TUD(트러스트된 사용자 도메인)를 통해 두 조직 간의 직접 지점 간 관계에서 트러스트를 명시적으로 정의해야 합니다.|
|조직의 콘텐츠 액세스를 제한하는 기본 권한 정책 템플릿 두 개가 제공됩니다. 그 중 하나는 보호된 콘텐츠에 대한 읽기 전용 보기 권한을 제공하고 다른 하나는 보호된 콘텐츠에 대한 쓰기 또는 수정 권한을 제공합니다.<br /><br />또한 하위 집합의 사용자에게만 표시되는 부서별 템플릿을 포함한 사용자 지정 템플릿을 만들 수 있습니다. 자세한 내용은 [Azure Rights Management 서비스용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.<br /><br />템플릿의 권한만으로는 부족한 경우 사용자가 원하는 권한 집합을 정의할 수도 있습니다.|기본 권한 정책 템플릿은 없습니다. 이러한 템플릿을 만든 후 배포해야 합니다. 자세한 내용은 [AD RMS 정책 템플릿 고려 사항](http://go.microsoft.com/fwlink/?LinkId=154765)을 참조하세요.<br /><br />템플릿의 권한만으로는 부족한 경우 사용자가 원하는 권한 집합을 정의할 수도 있습니다.|
|지원되는 최소 버전의 Microsoft Office는 Office 2010이며, 여기에는 [RMS 공유 응용 프로그램](../rms-client/sharing-app-windows.md)이 필요합니다.<br /><br />Microsoft Office for Mac:<br /><br />- Microsoft Office for Mac 2016: 지원됨<br /><br />- Microsoft Office for Mac 2011: 지원되지 않음|지원되는 최소 Microsoft Office 버전은 Office 2007입니다.<br /><br />Microsoft Office for Mac:<br /><br />- Microsoft Office for Mac 2016: 지원됨<br /><br />- Microsoft Office for Mac 2011: 지원됨|
|Windows, Mac 컴퓨터 및 모바일 장치용 [RMS 공유 응용 프로그램](../rms-client/sharing-app-windows.md)이 지원됩니다.<br /><br />또한 RMS 공유 응용 프로그램은 다음을 지원합니다.<br /><br />- 다른 조직의 사용자와 공유합니다.<br /><br />- 메일 알림은 누군가가 보호된 첨부 파일을 열려고 할 때 보낸 사람에게 알려줍니다.<br /><br />- 사용자에 대한 사이트를 추적하는 문서는 해지하는 기능을 포함합니다.|Windows, Mac 컴퓨터 및 모바일 장치용 [RMS 공유 응용 프로그램](../rms-client/sharing-app-windows.md)이 지원됩니다. 그러나 공유는 다른 조직, 전자 메일 알림 또는 사이트를 추적하는 문서 및 문서를 해지하려는 사용자를 위한 기능을 사람들과 공유하도록 지원하지 않습니다.|
|[RMS 공유 응용 프로그램을 사용하는 경우 기본 또는 일반 보호](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic)를 사용하여 모든 파일 형식을 보호할 수 있습니다.<br /><br />다른 응용 프로그램의 경우 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](../get-started/requirements-applications.md)의 표를 확인합니다.|[RMS 공유 응용 프로그램을 사용하는 경우 기본 또는 일반 보호](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic)를 사용하여 모든 파일 형식을 보호할 수 있습니다.<br /><br />다른 응용 프로그램의 경우 [Azure Rights Management 데이터 보호를 지원하는 응용 프로그램](../get-started/requirements-applications.md)의 표를 확인합니다.|
|지원되는 최소 Windows 클라이언트 버전은 Windows 7입니다.|지원되는 최소 Windows 클라이언트 버전은 Windows Vista 서비스 팩 2입니다.|
|Windows Phone, Android, iOS, Windows RT 모바일 장치가 지원됩니다.<br /><br />Exchange ActiveSync IRM을 사용한 메일 지원도 이 프로토콜을 지원하는 모든 모바일 장치 플랫폼에서 지원됩니다.|모바일 장치 지원에는 Windows Phone, Android, iOS 및 Windows RT가 포함되며, [Active Directory Rights Management Services 모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)이 필요합니다.<br /><br />이 프로토콜을 지원하는 모든 모바일 장치 플랫폼에서 Exchange ActiveSync IRM을 사용하여 전자 메일을 지원할 수 있습니다.|
|컴퓨터와 모바일 장치용 Multi-Factor Authentication(MFA)을 지원합니다.<br /><br />자세한 내용은 [MFA(Multi-Factor Authentication) 및 Azure Information Protection](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms)을 참조하세요.|IIS가 인증서를 요청하도록 구성된 경우 스마트 카드 인증을 지원합니다.|
|추가 구성 없이도 암호화 모드 2가 지원되므로 키 길이 및 암호화 알고리즘에 대해 보다 강력한 보안 기능이 제공됩니다.<br /><br />자세한 내용은 이 문서의 [서명 및 암호화를 위한 암호화 컨트롤](#cryptographic-controls-for-signing-and-encryption) 섹션 및 [AD RMS 암호화 모드](http://go.microsoft.com/fwlink/?LinkId=266659)를 참조하세요.|기본적으로 암호화 모드 1을 지원하며, 보안을 강화하기 위해 암호화 모드 2를 지원하려면 추가 구성을 수행해야 합니다.<br /><br />자세한 내용은 이 문서의 [서명 및 암호화를 위한 암호화 컨트롤](#cryptographic-controls-for-signing-and-encryption) 섹션 및 [AD RMS 암호화 모드](http://go.microsoft.com/fwlink/?LinkId=266659)를 참조하세요.|
|AD RMS로부터의 마이그레이션을 지원하고 필요한 경우 AD RMS로의 마이그레이션 지원:<br /><br />- [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Azure Information Protection 해제 및 비활성화](../deploy-use/decommission-deactivate.md)|Azure Information Protection에서 Azure Information Protection으로 마이그레이션 지원<br /><br />- [Azure 권한 관리 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)<br /><br />- [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|콘텐츠를 보호하려면 Azure Information Protection 라이선스가 필요합니다. Azure Information Protection로 보호되는 콘텐츠를 사용하는 데 필요한 Azure Information Protection 라이선스가 없습니다(다른 조직의 사용자 포함).<br /><br />자세한 내용은 Azure Information Protection 사이트의 [가격 책정](https://go.microsoft.com/fwlink/?LinkId=827589) 페이지를 참조하세요.|콘텐츠를 보호하고 AD RMS로 보호되는 콘텐츠를 사용하려면 RMS 라이선스가 필요합니다.<br /><br />AD RMS 라이선스에 대한 자세한 내용은 일반 정보의 [CAL(클라이언트 액세스 라이선스) 및 라이선스 관리](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) 를 참조하되, 특정 정보는 Microsoft 파트너 또는 Microsoft 담당자에게 문의하세요.|

## 서명 및 암호화를 위한 암호화 컨트롤
Azure Information Protection은 모든 공개 키 암호화에는 RSA 2048을, 서명 작업에는 SHA 256을 항상 사용합니다. 반면 AD RMS는 RSA 1024 및 RSA 2048과 서명 작업을 위한 SHA 1 또는 SHA 256을 지원합니다.

Azure Information Protection 및 AD RMS는 둘 다 대칭형 암호화에 AES 128을 사용합니다.

Azure Information Protection은 Microsoft에서 테넌트 키를 만들고 관리하거나(기본값) 사용자가 테넌트 키를 직접 관리하는 경우(BYOK 방식) FIPS 140-2를 준수합니다. 테넌트 키 관리에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요.

## 다음 단계
AD RMS에서 Azure Information Protection으로 마이그레이션하려면 [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.





<!--HONumber=Sep16_HO5-->


