---
title: "Azure RMS를 통해 해결할 수 있는 문제 | Azure Information Protection"
description: "조직에 해당될 수 있는 요구 사항이나 문제에 대해 알아보고 Azure RMS 기술을 통해 이러한 요구 사항을 충족하고 문제를 해결하는 방법을 파악합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 949cbe07234f78ca046aec1fc2590adf86f00a06
ms.openlocfilehash: 40f242c31553545651794e6e5a8f744963bb541b


---


# <a name="what-problems-does-azure-rms-solve"></a>Azure RMS를 통해 해결할 수 있는 문제

>*적용 대상: Azure Information Protection, Office 365*

다음 표를 통해 문서와 메일 보호를 위해 조직에 해당될 수 있는 비즈니스 요구 사항이나 문제 및 Azure RMS(Azure Rights Management) 기술로 이러한 사항을 해결하는 방법을 파악할 수 있습니다.

Azure RMS는 [Azure Information Protection](what-is-information-protection.md)에서 사용하는 보호 기술입니다.

|요구 사항 또는 문제|Azure RMS를 통한 해결 방법|
|--------------------------|-----------------------|
|여러 파일 형식 보호|√ 이전 Rights Management 구현에서는 기본 Rights Management 보호 기능을 통해 Office 파일만 보호할 수 있었습니다. 이제 Rights management 공유 응용 프로그램에서 처음 제공했으며 현재는 Azure Information Protection 클라이언트에서 제공하는 **일반 보호**는 더 많은 [파일 형식](../rms-client/client-admin-guide-file-types.md)이 지원됨을 의미합니다.|
|어디서나 파일 보호|√ 파일이 [보호되면](../rms-client/client-classify-protect.md) 클라우드 저장소 서비스 등 IT에서 제어하지 않는 저장소에 파일을 저장하거나 복사해도 보호 기능이 계속 적용됩니다.|
|안전하게 정보 공유|√ 파일이 [보호되면](../rms-client/client-classify-protect.md) 다른 사용자와 공유해도 안전합니다. 전자 메일 첨부 파일 또는 SharePoint 사이트에 대한 링크를 예로 들 수 있습니다. 중요한 정보가 전자 메일 메시지 안에 들어 있으면 전자 메일을 보호하거나 간단히 Outlook의 전달 금지 옵션을 사용할 수 있습니다. <br /><br />전체 전자 메일 메시지를 보호하지 않고 보호된 파일을 첨부할 경우의 이점은 전자 메일 텍스트가 암호화되지 않으므로 전자 메일이 조직 외부로 전송될 때 최초 사용에 대한 지침을 포함할 수 있습니다. 누구든지 지침을 읽을 수 있으나 첨부된 문서는 보호되므로 해당 메일이나 문서를 다른 사용자에게 전달하더라도 권한이 있는 사용자만이 첨부된 문서를 열 수 있습니다.|
|감사 및 모니터링|√ 보호된 파일이 조직의 경계를 벗어나더라도 해당 파일의 [사용을 감사하고 모니터링](../deploy-use/log-analyze-usage.md)할 수 있습니다.<br /><br />Contoso, Ltd. 소속 직원이 Fabrikam, Inc. 직원&3;명과 공동 프로젝트를 진행 중인 경우를 예로 들어 보겠습니다. 이 직원&3;명에게 읽기 전용으로 제한하여 보호한 문서를 메일로 보낼 때 Azure Rights Management 감사에서는 다음과 같은 정보를 제공할 수 있습니다.<br /><br />- Fabrikam에서 지정한 직원이 문서를 열었는지 여부 및 문서를 연 시간<br /><br />- 지정하지 않은 다른 직원이 문서 열기를 시도했는지(그리고 실패했는지) 여부. 다른 사용자가 액세스할 수 있는 공유 위치로 문서가 전달되었거나 저장되었을 수 있습니다.<br /><br />- 지정한 직원이 문서 인쇄 또는 변경을 시도했는지(그리고 실패했는지) 여부<br /><br />또한 [문서 추적 사이트](../rms-client/client-track-revoke.md)에서 사용자와 관리자는 보호된 문서를 추적할 수 있으며 필요한 경우 보호된 문서에 대한 액세스 권한을 취소할 수 있습니다.|
|Windows 컴퓨터만이 아닌 일반적으로 사용되는 장치 지원|√ [지원되는 장치](../get-started/requirements-client-devices.md)는 다음과 같습니다.<br /><br />- Windows 컴퓨터 및 휴대폰<br /><br />- Mac 컴퓨터<br /><br />- iOS 태블릿 및 휴대폰<br /><br />- Android 태블릿 및 휴대폰|
|기업 간 공동 작업 지원|√ Azure Rights Management는 클라우드 서비스이므로 보호된 콘텐츠를 공유하기 전에 다른 조직과의 트러스트를 명시적으로 구성할 필요가 없습니다. Office 365 또는 Azure AD 디렉터리가 이미 있으면 조직 간의 공동 작업이 자동으로 지원됩니다. 해당 디렉터리가 없는 사용자는 무료 [개인용 RMS](rms-for-individuals.md) 구독을 신청할 수 있습니다.|
|온-프레미스 서비스 및 Office 365 지원|√ Azure Rights Management는 [Office 365와 원활하게](office-apps-services-support.md) 연동될 뿐만 아니라 [RMS 커넥터](../deploy-use/deploy-rms-connector.md)를 배포할 때 다음 온-프레미스 서비스에서도 사용할 수 있습니다.<br /><br />- Exchange Server<br /><br />- SharePoint Server<br /><br />- 파일 분류 인프라를 실행하는 Windows Server|
|쉬운 활성화|√ 관리 포털에서 몇 번만 클릭하면 사용자의 [Rights Management 서비스를 활성화](../deploy-use/activate-service.md)할 수 있습니다. 또는 명령줄 컨트롤을 선호하는 경우 두 개의 PowerShell 명령만 있으면 됩니다.|
|필요에 따라 조직 환경을 확장하는 기능|√ Azure Rights Management는 클라우드 서비스로 실행되며 Azure의 탄력성으로 수직 및 수평 확장할 수 있으므로 추가 온-프레미스 서버를 프로비전하거나 배포하지 않아도 됩니다.|
|단순한 정책과 유동적인 정책을 만드는 기능|√ [사용자 지정된 권한 템플릿](../deploy-use/configure-custom-templates.md)을 통해 관리자는 정책을 빠르고 쉽게 적용할 수 있으며 사용자는 각 문서에 올바른 수준의 보호를 적용하고 조직 내 사용자만 액세스하도록 제한할 수 있습니다.<br /><br />예를 들어 회사 전체 전략 문서를 모든 직원과 공유하려는 경우 모든 내부 직원에게 읽기 전용 정책을 적용할 수 있습니다. 재무 보고서와 같은 보다 중요한 문서는 임원만 액세스하도록 제한할 수도 있습니다.|
|폭넓은 응용 프로그램 지원|√ Azure Rights Management는 Microsoft Office 응용 프로그램 및 서비스와 긴밀하게 통합되며 [Azure Information Protection 클라이언트](../rms-client/aip-client.md )를 사용하여 다른 응용 프로그램에 대한 지원을 확장합니다.<br /><br />√ [Azure Information Protection SDK](../develop/developers-guide.md)는 Azure Information Protection을 지원하는 사용자 지정 응용 프로그램을 작성하기 위한 API를 내부 개발자 및 소프트웨어 공급업체에 제공합니다.<br /><br />자세한 내용은 [Rights Management API를 지원하는 기타 응용 프로그램](api-support.md)을 참조하세요.|
|IT 부서에서 데이터 제어권을 유지해야 함|√ 조직은 자체 테넌트 키를 관리하고 "BYOK([Bring Your Own Key](../plan-design/plan-implement-tenant-key.md))" 솔루션을 사용하며 테넌트 키를 HSM(하드웨어 보안 모듈)에 저장하도록 선택할 수 있습니다.<br /><br />√ 감사 및 [사용 현황 로깅](../deploy-use/log-analyze-usage.md)이 지원되므로 비즈니스 정보를 분석하고, 남용을 모니터링하고, 정보 유출 시에는 법정 분석을 수행할 수 있습니다.<br /><br />√ 직원이 문서를 보호해 놓은 상태에서 퇴사하더라도 IT 부서는 [슈퍼 사용자 기능](../deploy-use/configure-super-users.md)을 사용하여 위임된 액세스를 통해 보호된 콘텐츠에 항상 액세스할 수 있습니다. 반면 피어 투 피어 암호화 솔루션에서는 회사 데이터에 액세스하지 못할 위험이 있습니다.<br /><br />√ Azure AD Connect와 같은 [디렉터리 동기화 도구](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)를 사용하여 Azure RMS가 온-프레미스 Active Directory 계정에 대한 일반 ID를 지원하는 데 필요한 [디렉터리 특성만](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) 동기화합니다.<br /><br />√ AD FS를 사용하여 클라우드에 암호를 복제할 필요 없이 Single-Sign On을 사용하도록 설정합니다.<br /><br />√ 조직에서는 이전에 Azure Rights Management를 통해 보호되었던 콘텐츠에 계속 액세스하면서 언제든지 Azure Rights Management 서비스 사용을 중지할 수 있습니다. 서비스 해제 옵션에 대한 자세한 내용은 [Azure 권한 관리 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요. 또한 AD RMS(Active Directory Rights Management Services)를 배포한 조직은 이전에 AD RMS를 통해 보호되었던 데이터에 계속 액세스하면서 [Azure Rights Management 서비스로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)할 수 있습니다.|
> [!TIP]
> 온-프레미스 권한 관리 버전인 AD RMS(Active Directory Rights Management Services)에 대해 잘 알고 있는 경우 [Azure 권한 관리와 AD RMS 비교](compare-azure-rms-ad-rms.md)의 비교 표를 확인하면 도움이 됩니다.

## <a name="security-compliance-and-regulatory-requirements"></a>보안, 준수 및 규정 요구 사항
Azure Rights Management는 다음과 같은 보안, 준수 및 규정 요구 사항을 지원합니다.

√ 업계 표준 암호화가 사용되며 FIPS 140-2가 지원됩니다. 자세한 내용은 [Azure RMS에서 사용하는 암호화 컨트롤: 알고리즘 및 키 길이](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths) 정보를 참조하세요.

√ Microsoft Azure 데이터 센터에 테넌트 키를 저장할 수 있도록 Thales HSM(하드웨어 보안 모듈)이 지원됩니다. Azure Rights Management는 북아메리카, EMEA(유럽, 중동 및 아시아) 및 아시아의 데이터 센터에 별도의 보안 권역을 사용하여 사용자의 지역에서만 해당 키를 사용할 수 있도록 합니다.

√ Azure RMS는 다음과 같은 인증을 받았습니다.

-   ISO/IEC 27001:2013([ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/) 포함)

-   SOC 2 SSAE 16/ISAE 3402 증명

-   HIPAA BAA

-   EU 모범 조항

-   Office 365 인증에서 Azure Active Directory의 일부로 HHS의 FedRAMP Agency ATO(Authority to Operate)가 발급한 FedRAMP

-   PCI DSS 수준 1

이러한 외부 인증에 대한 자세한 내용은 [Azure 보안 센터](http://azure.microsoft.com/support/trust-center/compliance/)를 참조하세요.

## <a name="next-steps"></a>다음 단계

관리자와 사용자에게 Azure Rights Management 서비스가 표시되는 모양을 보려면 [Azure RMS 실행](what-admins-users-see.md)을 참조하세요.

Azure Rights Management 서비스 작동 방식에 대한 보다 기술적인 정보에 관심이 있는 경우 [Azure RMS 작동 방식](how-does-it-work.md)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


