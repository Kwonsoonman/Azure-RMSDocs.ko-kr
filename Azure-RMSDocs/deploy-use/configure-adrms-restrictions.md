---
title: Azure Information Protection에서 HYOK 보호
description: Azure Information Protection에서 HYOK(AD RMS) 보호의 개요, 지원되는 시나리오, 제한 사항, 필수 구성 요소 및 권장 사항입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: 5c8e918bd467d1d7540a129bca266c0f0c077a56
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39474259"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>Azure Information Protection용 HYOK(Hold your own key) 보호

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

다음 정보를 사용하여 Azure Information Protection용 HYOK(Hold your own key) 보호란 무엇인지, 기본 클라우드 기반 보호와 차이점을 알아보세요. HYOK 보호를 사용하기 전에 적절한 시기, 지원되는 시나리오, 제한 사항 및 요구 사항을 이해하도록 하세요. 

## <a name="cloud-based-protection-vs-hyok"></a>클라우드 기반 보호 및 HYOK

Azure Information Protection을 사용하여 가장 중요한 문서와 이메일을 보호하는 경우 Azure RMS(Azure Rights Management) 보호를 사용하는 클라우드 기반 키를 적용하여 일반적으로 다음을 수행할 수 있습니다.

- 서버 인프라가 필요하지 않으므로 온-프레미스 솔루션보다 더 빠르고 비용 효과적으로 이 솔루션을 배포 및 유지 관리할 수 있습니다.

- 클라우드 기반 인증을 사용하여 파트너 및 다른 조직의 사용자와 더 쉽게 공유할 수 있습니다.

- 검색, 웹 뷰어, 피벗 뷰, 맬웨어 방지, eDiscovery, Delve 등의 Office 365 서비스 및 기타 Azure와 긴밀하게 통합됩니다.

- 공유한 중요한 문서에 대한 문서 추적, 취소 및 메일 알림을 사용할 수 있습니다.

클라우드 기반 키는 Microsoft에서 관리(기본값)하거나 사용자가 관리("Bring Your Own Key" 또는 BYOK 시나리오)하는 조직의 개인 키를 사용하여 조직의 문서와 메일을 보호합니다. 테넌트 키 옵션에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요.

보호하는 문서 및 이메일은 클라우드 또는 온-프레미스 환경에 저장할 수 있습니다 이 클라우드 기반 키에 대한 보호 프로세스 작동 방식에 대한 자세한 내용은 [Azure Rights Management란?](../what-is-azure-rms.md )를 참조하세요.

테넌트용 Office 365 서비스 및 클라우드 기반 응용 프로그램은 Azure Information Protection과 통합되어 검색, 인덱싱, 보관 및 맬웨어 방지 서비스와 같은 중요한 비즈니스 기능이 Azure Information Protection의 보호를 받는 콘텐츠에 대해 원활하게 작동합니다. 이러한 시나리오에 대한 암호화된 콘텐츠를 읽을 수 있는 이 기능은 종종 "데이터에 대한 추론"이라고 합니다. 예를 들어 Exchange Online에서 맬웨어 검사를 위한 이메일의 암호를 해독하고 암호화된 이메일에 대한 DLP(데이터 손실 방지) 규칙을 실행하는 기능입니다.

그러나 규정 요구 사항에 따라 일부 조직에서는 클라우드로부터 격리된 키를 사용하여 콘텐츠를 암호화해야 할 수 있습니다. 이러한 격리는 온-프레미스 응용 프로그램 및 온-프레미스 서비스에서만 암호화된 콘텐츠를 읽을 수 있음을 의미합니다. 이 키 관리 옵션은 Azure Information Protection에서 지원되며 "hold your own key" 또는 HYOK라고 합니다. Azure Information Protection을 HYOK와 함께 사용하면 테넌트가 클라우드 기반 키와 온 프레미스 키를 모두 갖게 됩니다.

## <a name="hyok-guidance-and-best-practices"></a>HYOK 지침 및 모범 사례

클라우드로부터 암호화 키를 격리해야 하는 문서 및 이메일에만 HYOK 보호 기능을 사용합니다. HYOK 보호는 클라우드 기반 키 보호를 사용할 때 얻을 수 있는 이점을 제공하지 않으며 종종 "데이터 불투명도"를 희생합니다. 이는 온-프레미스 응용 프로그램 및 서비스만 HYOK 보호 데이터를 열 수 있음을 의미합니다. 클라우드 기반 서비스 및 애플리케이션은 HYOK 보호 데이터를 추론할 수 없습니다.

HYOK 보호 기능을 사용하는 조직도 일반적으로 보호해야 하는 문서가 적은 경우에 적합합니다. 문서에 대해서만 사용하고 다음 기준에 모두 일치할 경우 사용하세요.

- 조직에서 최고 분류("일급 비밀")에 속하고 소수의 사용자만 액세스할 수 있도록 제한된 콘텐츠

- 조직 외부에서 공유되지 않는 콘텐츠

- 내부 네트워크에서만 사용되는 콘텐츠

HYOK 보호는 레이블에 대한 관리자 구성 옵션이므로 보호가 클라우드 기반 키 또는 HYOK를 사용하는지 여부와 관계없이 사용자 워크플로는 동일하게 유지됩니다.

[범위 지정 정책](configure-policy-scope.md)은 HYOK 보호를 적용해야 하는 사용자만 HYOK 보호가 구성된 레이블을 볼 수 있도록 하는 좋은 방법입니다. 

## <a name="supported-scenarios-for-hyok"></a>HYOK에 대해 지원되는 시나리오

HYOK 보호를 적용하려면 Azure Information Protection 레이블을 사용하세요. 

다음 표는 HYOK용으로 구성된 레이블을 사용하고 HYOK로 보호되는 콘텐츠를 열어(사용하여) 콘텐츠 보호에 지원되는 시나리오를 나열합니다.

|플랫폼|응용 프로그램|지원됨|
|----------------------|----------|-----------|
|Windows|Office 2016 및 Office 2013을 사용하는 Azure Information Protection 클라이언트 <br /><br />- Word, Excel, PowerPoint|보호: 예<br /><br />소비: 예|
|Windows|Office 2016 및 Office 2013을 사용하는 Azure Information Protection 클라이언트 <br /><br />- Outlook|보호: 예<br /><br />소비: 예|
|Windows|파일 탐색기를 사용하는 Azure Information Protection 클라이언트|보호: 예 <br /><br />소비: 예|
|Windows|Azure Information Protection 뷰어|보호: 해당 사항 없음<br /><br />소비: 예|
|Windows|PowerShell 레이블 지정 cmdlet를 사용하는 Azure Information Protection 클라이언트|보호: 예<br /><br />소비: 예|
|Windows|Azure Information Protection 스캐너|보호: 예<br /><br />소비: 예|
|Windows|Rights Management 공유 앱|보호: 아니요<br /><br />소비: 예|
|MacOS|Mac용 Office <br /><br /> - Word, Excel, PowerPoint|보호: 아니요<br /><br />소비: 예|
|MacOS|Mac용 Office<br /><br />- Outlook|보호: 아니요<br /><br />소비: 예|
|MacOS|Rights Management 공유 앱|보호: 아니요<br /><br />소비: 예|
|iOS|Office Mobile <br /><br />- Word, Excel, PowerPoint|보호: 아니요<br /><br />소비: 예|
|iOS|Office Mobile <br /><br />-Outlook|보호: 아니요<br /><br />소비: 아니요|
|iOS|Azure Information Protection 뷰어|보호: 해당 사항 없음<br /><br />소비: 예|
|Android|Office Mobile <br /><br />- Word, Excel, PowerPoint|보호: 아니요<br /><br />소비: 예|
|Android|Office Mobile <br /><br />- Outlook|보호: 아니요<br /><br />소비: 아니요|
|Android|Azure Information Protection 뷰어|보호: 해당 사항 없음<br /><br />소비: 예|
|웹|웹 상의 Outlook|보호: 아니요<br /><br />소비: 아니요|
|웹|Office Online<br /><br />- Word, Excel, PowerPoint|보호: 아니요<br /><br />소비: 아니요|
|유니버설|Office 유니버설 앱<br /><br />- Word, Excel, PowerPoint|보호: 아니요<br /><br />소비: 아니요|


## <a name="additional-limitations-when-using-hyok"></a>HYOK 사용 시 추가 제한 사항

또한 HYOK 보호 기능을 Azure Information Protection 레이블과 함께 사용하면 다음과 같은 제한 사항이 있습니다.

- Office 2010 또는 Office 2007을 지원하지 않습니다.

- Office 365 서비스 및 기타 온라인 서비스는 HYOK 보호 문서 및 이메일을 해독하여 콘텐츠를 검사하고 이에 대한 조치를 취할 수 없습니다. 이 제한 사항은 Rights Management 커넥터로 보호된 HYOK 보호 문서 및 이메일까지 확장됩니다. 
    
    HYOK 보호 이메일에 대한 이러한 기능 손실에는 맬웨어 검사기, DLP(데이터 손실 방지) 솔루션, 메일 라우팅 규칙, 저널링, eDiscovery, 보관 솔루션 및 Exchange ActiveSync가 포함됩니다. 또한 사용자가 일부 장치에서 HYOK 보호 이메일을 열 수 없는 이유를 알지 못해 헬프 데스크로 전화할 수 있습니다. 이러한 많은 제한 사항 때문에 이메일에는 HYOK 보호를 사용하지 않는 것이 좋습니다.

## <a name="implementing-hyok"></a>HYOK 구현

HYOK는 다음 섹션에 설명된 요구 사항으로 작동하는 AD RMS(Active Directory Rights Management Services) 배포가 있는 경우 Azure Information Protection에서 지원됩니다. 이 시나리오에서 사용 권한 정책 및 이러한 정책을 보호하는 조직의 개인 키는 온-프레미스에서 관리 및 유지되고, 레이블 지정 및 분류에 대한 Azure Information Protection 정책은 계속 Azure에서 관리 및 저장됩니다. 

HYOK 및 Azure Information Protection을 전체 배포된 AD RMS 및 Azure Information Protection 사용과 혼동하거나 AD RMS를 Azure Information Protection으로 마이그레이션하는 대안으로서 오해하지 마세요. HYOK는 레이블 적용만 지원되며 AD RMS를 사용하여 기능 패리티를 제공하지 않으며, AD RMS 배포 구성을 모두 지원하지 않습니다.

- HYOK가 콘텐츠 보호 및 보호된 콘텐츠 소비를 지원하는 시나리오에 대한 자세한 내용은 [HYOK에 대해 지원되는 시나리오](#supported-scenarios-for-hyok) 섹션을 참조하세요.

- AD RMS에서 마이그레이션 지침에 대한 내용은 [AD RMS에서 Azure Information Protection으로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

- AD RMS 배포 요구 사항에 대한 자세한 내용은 다음 섹션을 참조하세요.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>HYOK를 지원하는 AD RMS에 대한 요구 사항

AD RMS 배포는 Azure Information Protection 레이블에 대해 HYOK 보호를 제공하기 위해 다음 요구 사항을 충족해야 합니다.

- AD RMS 구성:
    
    - 최소 버전의 Windows Server 2012 R2: 프로덕션 환경에 대해 필요하지만 테스트 및 평가용으로는 최소 버전의 Windows Server 2008 R2 서비스 팩 1을 사용할 수 있습니다.
    
    - 다음 토폴로지 중 하나입니다.
        
        - 단일 AD RMS 루트 클러스터가 있는 단일 포리스트 
        
        - 독립 AD RMS 루트 클러스터 및 다른 포리스트의 사용자로 보호되는 콘텐츠에 액세스할 수 없는 사용자가 있는 다중 포리스트
        
        - 각각에서 AD RMS 클러스터가 있는 다중 포리스트 각 AD RMS 클러스터는 동일한 AD RMS 클러스터를 가리키는 라이선스 URL을 공유합니다. 이 AD RMS 클러스터에서 다른 모든 AD RMS 클러스터에서 모든 TUD(신뢰할 수 있는 사용자 도메인) 인증서를 가져와야 합니다. 이 토폴로지에 대한 자세한 내용은 [트러스트된 사용자 도메인](https://technet.microsoft.com/library/dd983944(v=ws.10\).aspx)을 참조하세요.
        
    별도 포리스트에 여러 AD RMS 클러스터가 있는 경우 HYOK(AD RMS) 보호를 적용하는 글로벌 정책에서 모든 레이블을 삭제하고 각 클러스터에 대한 [범위 지정 정책](configure-policy-scope.md)을 구성합니다. 그런 다음 사용자를 둘 이상의 범위 지정 정책에 할당하게 하는 그룹을 사용하지 않도록 각 클러스터에 대한 사용자를 해당 범위 지정 정책에 할당합니다. 결과는 각 사용자에 하나의 AD RMS 클러스터에 대한 레이블이 있어야 합니다. 
    
    - [암호화 모드 2](https://technet.microsoft.com/library/hh867439.aspx): AD RMS 클러스터 속성, **일반** 탭을 확인하여 모드를 확인할 수 있습니다.
    
    - 각 AD RMS 서버에 인증 URL이 구성되어 있습니다. [지침](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
    - SCP(서비스 연결 지점)가 Active Directory에 등록되어 있지 않습니다. Azure Information Protection과 함께 AD RMS 보호를 사용하는 경우 SCP가 사용되지 않습니다. 
    
        - AD RMS 배포에 대한 SCP를 등록한 경우 이 SCP를 제거해야만 Azure Rights Management 보호를 위한 [서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery)이 성공합니다. 
        
        - HYOK에 대해 새 AD RMS 클러스터를 설치하는 경우에는 첫 번째 노드를 구성할 때 SCP를 등록하는 단계를 건너뜁니다. 노드를 추가할 때마다 AD RMS 역할을 추가하고 기존 클러스터를 연결하기 전에 서버에 인증 URL이 구성되어 있는지 확인합니다.
    
    - AD RMS 서버는 연결 중인 클라이언트에서 신뢰할 수 있는 유효한 x.509 인증서와 SSL/TLS를 사용하도록 구성되어 있습니다. 프로덕션 환경에 필요하지만 테스트 또는 평가용으로는 필요하지 않습니다.
    
    - 구성된 권한 템플릿.
    
    - Exchange IRM에 대해 구성되지 않았습니다.
    
    - 모바일 장치 및 Mac 컴퓨터의 경우: [Active Directory Rights Management Services Mobile Device Extension](https://technet.microsoft.com/library/dn673574.aspx)이 설치되고 구성됩니다.

- 온-프레미스 Active Directory와 Azure Active Directory 간에 디렉터리 동기화가 구성되었으며 HYOK 보호를 사용할 사용자에 대해 Single Sign-On이 구성되었습니다.

- AD RMS로 보호되는 문서 또는 메일을 조직 외부의 다른 사용자와 공유할 경우: TUD(트러스트된 사용자 도메인) 또는 AD FS(Active Directory Federation Services)를 통해 만들어진 페더레이션 트러스트를 사용하여 다른 조직과의 직접 지점 간 관계에서 명시적으로 정의된 트러스트에 대해 HYOK가 구성되었습니다.

- 사용자가 Office 2016 Professional Plus 또는 Office 2013 Professional Plus 서비스 팩 1인 Office 버전을 Windows 7 서비스 팩 1 이상에서 실행하고 있습니다. Office 2010과 Office 2007은 이 시나리오에서 지원되지 않습니다.
    
    - Office 2016, Microsoft Installer(.msi) 기반 버전의 경우: [2018년 3월 6일에 출시된 Microsoft Office 2016용 업데이트 4018295](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295)를 설치했습니다.

> [!IMPORTANT]
> HYOK 보호에서 제공하는 높은 보증을 충족하려면 AD RMS 서버가 DMZ에 있지 않고 잘 관리된 장치에서만 사용하는 것이 좋습니다. 
> 
> 또한 AD RMS 배포가 위반되거나 손상되는 경우 SLC(서버 사용 허가자 인증서)의 개인 키가 노출되거나 도난당하지 않도록 AD RMS 클러스터에서 HSM(하드웨어 보안 모듈)을 사용하는 것이 좋습니다. 

배포 정보 및 AD RMS에 대한 지침은 Windows Server 라이브러리에서 [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx)를 참조하세요. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>AD RMS 서버를 구성하여 인증 URL 찾기

1. 클러스터의 각 AD RMS 서버에서 다음 레지스트리 항목을 작성합니다.

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    \<문자열 값>에는 다음 중 하나를 지정합니다.
    
    - SSL/TLS를 사용하는 AD RMS 클러스터의 경우:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - SSL/TLS를 사용하지 않는 AD RMS 클러스터의 경우(테스트 네트워크에만 해당):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. IIS를 다시 시작합니다.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Azure Information Protection 레이블을 사용하여 AD RMS 보호를 지정하는 데 필요한 정보 찾기

**HYOK(AD RMS)** 보호에 대한 레이블을 구성하는 경우 AD RMS 클러스터의 라이선스 URL을 지정해야 합니다. 또한 사용자에게 부여할 권한에 대해 구성한 템플릿을 지정하거나, 사용자가 권한 및 사용자를 정의할 수 있도록 해야 합니다. 

Active Directory Rights Management Services 콘솔에서 템플릿 GUID 및 라이선스 URL 값을 찾을 수 있습니다.

- 템플릿 GUID를 찾으려면: 클러스터를 확장하고 **권한 정책 템플릿**을 클릭합니다. **분산 권한 정책 템플릿** 정보에서 사용할 템플릿의 GUID를 복사할 수 있습니다. 예: 82bf3474-6efe-4fa1-8827-d1bd93339119

- 라이선스 URL을 찾으려면: 클러스터 이름을 클릭합니다. **클러스터 세부 정보**에서 **/_wmcs/licensing** 문자열을 제외하고 **라이선스**입니다. 예를 들어 https://rmscluster.contoso.com를 구성할 수 있습니다. 
    
    인트라넷 라이선스 값뿐 아니라 엑스트라넷 라이선스 값도 있고 두 값이 서로 다른 경우: 명시적 지점 간 트러스트를 사용하여 정의한 파트너와 보호된 문서 또는 메일을 공유할 경우에만 엑스트라넷 값을 지정합니다. 그렇지 않은 경우 인트라넷 값을 사용하고 Azure Information Protection에 AD RMS 보호를 사용하는 모든 클라이언트 컴퓨터에서 인트라넷 연결을 사용하여 연결하도록 합니다(예: 원격 컴퓨터에서 VPN 연결 사용).


## <a name="next-steps"></a>다음 단계

HYOK 보호에 대한 레이블을 구성하려면 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)을 참조하세요. 
