---
title: "HYOK 제한 | Azure Information Protection"
description: Identify the limitations, prerequisites, and recommendations if you select AD RMS protection with Azure Information Protection. This solution is sometimes referred to as "hold your own key" (HYOK).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
translationtype: Human Translation
ms.sourcegitcommit: f1bf7377e5e8079025dff638a185c825256a5cc7
ms.openlocfilehash: 3a563eccb37cfd660c28fd2308749d1e71771f23


---

# <a name="hold-your-own-key-hyok-requirements-and-restrictions-for-ad-rms-protection"></a>AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한

>*적용 대상: Azure Information Protection*

**[이 기능은 계속 임시로 제공되며 내용은 변경될 수 있습니다.]**

가장 중요한 문서와 메일을 보호하는 경우 일반적으로 Azure 권한 관리 보호를 적용하여 다음을 활용합니다.

- 서버 인프라가 필요하지 않으므로 온-프레미스 솔루션보다 더 빠르고 비용 효과적으로 이 솔루션을 배포 및 유지 관리할 수 있습니다.

- 클라우드 기반 인증을 사용하여 파트너 및 다른 조직의 사용자와 더 쉽게 공유할 수 있습니다.

- 검색, 웹 뷰어, 피벗 뷰, 맬웨어 방지, eDiscovery, Delve 등의 Office 365 서비스와 긴밀하게 통합됩니다.

- 공유한 중요한 문서에 대한 문서 추적, 취소 및 메일 알림을 사용할 수 있습니다.

Azure RMS는 Microsoft에서 관리(기본값)하거나 사용자가 관리("Bring Your Own Key" 또는 BYOK 시나리오)하는 조직의 개인 키를 사용하여 조직의 문서와 메일을 보호합니다. Azure RMS로 보호하는 정보는 클라우드로 전송되지 않습니다. 명시적으로 저장하거나 Azure에 저장하는 다른 클라우드 서비스를 사용하지 않는 한 보호된 문서와 메일은 Azure에 저장되지 않습니다. 테넌트 키 옵션에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요. 

그러나 일부 고객은 온-프레미스에 호스트된 키를 사용하여 선택한 문서와 메일을 보호해야 할 수도 있습니다. 예를 들어 규정 및 준수 때문에 필요할 수 있습니다. 

이 구성을 HYOK("Hold Your Own Key")라고도 하며, 다음 섹션에 설명된 요구 사항으로 작동하는 AD RMS(Active Directory Rights Management Services) 배포가 있는 경우 Azure Information Protection에서 지원됩니다. 이 기능은 미리 보기 상태입니다.

이 HYOK 시나리오에서 권한 정책 및 이러한 정책을 보호하는 조직의 개인 키는 온-프레미스에서 관리 및 유지되고, 레이블 지정 및 분류에 대한 Azure Information Protection 정책은 계속 Azure에서 관리 및 저장됩니다. Azure RMS 보호와 마찬가지로 AD RMS로 보호하는 정보는 클라우드로 전송되지 않습니다.

> [!NOTE]
> 이 구성은 필요한 경우에만, 그리고 필요한 문서 및 메일에 대해서만 사용하세요. AD RMS 보호는 Azure RMS 보호를 사용할 때 얻을 수 있는 혜택을 제공하지 않으며 "어떤 희생이 따르더라도 데이터 불투명도 유지"를 목적으로 합니다.

레이블이 Azure RMS 보호가 아니라 AD RMS 보호를 사용할 때도 사용자는 인식할 수 없습니다. AD RMS 보호에 수반되는 제한 사항 때문에 사용자가 AD RMS 보호를 적용하는 레이블을 선택해야 하는 경우에 대한 명확한 지침을 제공해야 합니다.

## <a name="limitations-when-using-hyok"></a>HYOK 사용 시 제한 사항

Azure RMS 보호를 Azure Information Protection과 사용할 경우 Azure RMS 보호를 사용하면 얻는 나열된 혜택을 지원하지 않을 뿐 아니라 다음과 같은 제한 사항이 있습니다.

- Office 2010 또는 Office 2007을 지원하지 않습니다.

- Azure RMS 보호도 사용하는 경우 Azure RMS 보호에 대한 레이블을 구성할 때 **전달 금지** 옵션을 사용하지 마세요. 또한 사용자에게 Outlook에서 이 옵션을 수동으로 선택하지 말라고 알려줘야 합니다. 

    레이블을 통해 또는 사용자가 수동으로 전달 금지 옵션을 적용하는 경우 필요한 Azure 권한 관리 서비스가 아니라 AD RMS 배포에서 옵션이 적용될 수 있습니다. 이 시나리오에서는 공유하는 사람이 이 전달 금지 옵션이 적용된 메일 메시지를 외부에서 열 수 없습니다.

## <a name="requirements-for-hyok"></a>HYOK에 대한 요구 사항

AD RMS 배포가 Azure Information Protection에 대해 AD RMS 보호를 제공하기 위한 다음 요구 사항을 충족하는지 확인합니다.

- AD RMS 구성:
    
    - 최소 버전의 Windows Server 2012 R2: 프로덕션 환경에 대해 필요하지만 테스트 및 평가용으로는 최소 버전의 Windows Server 2008 R2 서비스 팩 1을 사용할 수 있습니다.
    
    - 단일 AD RMS 루트 클러스터.
    
    - [암호화 모드 2](https://technet.microsoft.com/library/hh867439.aspx): [RMS 분석기 도구](https://www.microsoft.com/en-us/download/details.aspx?id=46437)를 사용하여 AD RMS 클러스터의 암호화 모드의 버전 및 전반적인 상태를 확인할 수 있습니다.   
    
    - AD RMS 서버는 연결 중인 클라이언트에서 신뢰할 수 있는 유효한 x.509 인증서와 SSL/TLS를 사용하도록 구성되어 있습니다. 프로덕션 환경에 필요하지만 테스트 또는 평가용으로는 필요하지 않습니다.
    
    - 구성된 권한 템플릿.

- 온-프레미스 Active Directory와 Azure Active Directory 간에 디렉터리 동기화가 구성되었으며 AD RMS 보호를 사용할 사용자에 대해 Single Sign-On이 구성되었습니다.

- AD RMS로 보호되는 문서 또는 메일을 조직 외부의 다른 사용자와 공유할 경우: TUD(트러스트된 사용자 도메인) 또는 AD FS(Active Directory Federation Services)를 통해 만들어진 페더레이션 트러스트를 사용하여 다른 조직과의 직접 지점 간 관계에서 명시적으로 정의된 트러스트에 대해 AD RMS가 구성되었습니다.

- 사용자가 Office 2013 Pro Plus 서비스 팩 1 또는 Office 2016 Pro Plus인 Office 버전을 Windows 7 서비스 팩 1 이상에서 실행하고 있습니다. Office 2010과 Office 2007은 이 시나리오에서 지원되지 않습니다.

> [!IMPORTANT]
> 이 시나리오에서 제공하는 높은 보증을 충족하려면 AD RMS 서버가 DMZ에 있지 않고 잘 관리된 컴퓨터에서만 사용하는 것이 좋습니다(예: 모바일 장치 또는 작업 그룹 컴퓨터 아님). 
> 
> 또한 AD RMS 배포가 위반되거나 손상되는 경우 SLC(서버 사용 허가자 인증서)의 개인 키가 노출되거나 도난당하지 않도록 AD RMS 클러스터에서 HSM(하드웨어 보안 모듈)을 사용하는 것이 좋습니다. 

배포 정보 및 AD RMS에 대한 지침은 Windows Server 라이브러리에서 [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx)를 참조하세요. 


## <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Azure Information Protection 레이블을 사용하여 AD RMS 보호를 지정하는 데 필요한 정보 찾기

AD RMS 보호에 대한 레이블을 구성하는 경우 AD RMS 클러스터의 템플릿 GUID 및 라이선스 URL을 지정해야 합니다. 이러한 두 값은 Active Directory Rights Management Services 콘솔에서 확인할 수 있습니다.

- 템플릿 GUID를 찾으려면: 클러스터를 확장하고 **권한 정책 템플릿**을 클릭합니다. **분산 권한 정책 템플릿** 정보에서 사용할 템플릿의 GUID를 복사할 수 있습니다. 예: 82bf3474-6efe-4fa1-8827-d1bd93339119

- 라이선스 URL을 찾으려면: 클러스터 이름을 클릭합니다. **클러스터 세부 정보**에서 **/_wmcs/licensing** 문자열을 제외하고 **라이선스**니다. 예: https://rmscluster.contoso.com 
    
    인트라넷 라이선스값뿐 아니라 엑스트라넷 라이선스 값도 있고 두 값이 서로 다른 경우: 명시적 지점 간 트러스트를 사용하여 정의한 파트너와 보호된 문서 또는 메일을 공유할 경우에만 엑스트라넷 값을 지정합니다. 그렇지 않은 경우 인트라넷 값을 사용하고 Azure Information Protection에 AD RMS 보호를 사용하는 모든 클라이언트 컴퓨터에서 인트라넷 연결을 사용하여 연결하도록 합니다(예: 원격 컴퓨터에서 VPN 연결 사용).

## <a name="next-steps"></a>다음 단계

이 미리 보기 기능에 대한 자세한 내용은 블로그 게시물 공지인 [Azure Information Protection with HYOK (Hold Your Own Key)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/)(Azure Information Protection 및 HYOK(Hold Your Own Key))를 참조하세요.

AD RMS 보호에 대한 레이블을 구성하려면 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)을 참조하세요. 



<!--HONumber=Nov16_HO2-->


