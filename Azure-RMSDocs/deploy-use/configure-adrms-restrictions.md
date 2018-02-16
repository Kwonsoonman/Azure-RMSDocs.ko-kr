---
title: "Azure Information Protection에 대한 HYOK 제한"
description: "Azure Information Protection에서 HYOK(AD RMS) 보호를 사용하도록 선택한 경우 제한 사항, 필수 구성 요소 및 권장 사항을 파악합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: 00b17536467e2990d807c3494c645fa8a559f241
ms.sourcegitcommit: 6bfbf08b935a7a60e437af44aab72db13f87eff1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2018
---
# <a name="hold-your-own-key-hyok-requirements-and-restrictions-for-ad-rms-protection"></a>AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한

>*적용 대상: Azure Information Protection*

가장 중요한 문서와 메일을 보호하는 경우 Azure RMS(Azure Rights Management) 보호를 적용하여 일반적으로 다음을 수행할 수 있습니다.

- 서버 인프라가 필요하지 않으므로 온-프레미스 솔루션보다 더 빠르고 비용 효과적으로 이 솔루션을 배포 및 유지 관리할 수 있습니다.

- 클라우드 기반 인증을 사용하여 파트너 및 다른 조직의 사용자와 더 쉽게 공유할 수 있습니다.

- 검색, 웹 뷰어, 피벗 뷰, 맬웨어 방지, eDiscovery, Delve 등의 Office 365 서비스와 긴밀하게 통합됩니다.

- 공유한 중요한 문서에 대한 문서 추적, 취소 및 메일 알림을 사용할 수 있습니다.

Azure RMS는 Microsoft에서 관리(기본값)하거나 사용자가 관리("Bring Your Own Key" 또는 BYOK 시나리오)하는 조직의 개인 키를 사용하여 조직의 문서와 메일을 보호합니다. Azure RMS로 보호하는 정보는 클라우드로 전송되지 않습니다. 명시적으로 저장하거나 Azure에 저장하는 다른 클라우드 서비스를 사용하지 않는 한 보호된 문서와 메일은 Azure에 저장되지 않습니다. 테넌트 키 옵션에 대한 자세한 내용은 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요. 

그러나 몇몇 조직은 온-프레미스에 호스트된 키를 사용하여 일부 문서 및 메일을 보호해야 할 수도 있습니다. 예를 들어 규정 및 준수 때문에 필요할 수 있습니다.  

이 구성을 HYOK("Hold Your Own Key")라고도 하며, 다음 섹션에 설명된 요구 사항으로 작동하는 AD RMS(Active Directory Rights Management Services) 배포가 있는 경우 Azure Information Protection에서 지원됩니다.

이 HYOK 시나리오에서 권한 정책 및 이러한 정책을 보호하는 조직의 개인 키는 온-프레미스에서 관리 및 유지되고, 레이블 지정 및 분류에 대한 Azure Information Protection 정책은 계속 Azure에서 관리 및 저장됩니다. Azure RMS 보호와 마찬가지로 AD RMS로 보호하는 정보는 클라우드로 전송되지 않습니다.

> [!NOTE]
> 이 구성은 필요한 경우에만, 그리고 필요한 문서 및 메일에 대해서만 사용하세요. AD RMS 보호는 Azure RMS 보호를 사용할 때 얻을 수 있는 혜택을 제공하지 않으며 "어떤 희생이 따르더라도 데이터 불투명도 유지"를 목적으로 합니다.
>
> 이 구성을 사용하는 조직의 경우에도 일반적으로 보호해야 하는 콘텐츠는 전체 콘텐츠의 10% 미만이 적합합니다. 다음 모든 조건과 일치하는 문서 또는 메일에만 사용하세요.
> 
> **조직에서 최고 분류("일급 비밀")에 속하고 소수의 사용자만 액세스할 수 있도록 제한된 콘텐츠**
> 
> **조직 외부에서 공유되지 않는 콘텐츠**
> 
> **내부 네트워크에서만 사용되는 콘텐츠**
> 
> **Mac 컴퓨터 또는 모바일 장치에서 사용하지 않아야 하는 콘텐츠**

레이블이 Azure RMS 보호가 아니라 AD RMS 보호를 사용할 때도 사용자는 인식할 수 없습니다. AD RMS 보호에 수반되는 제한 사항 때문에 사용자가 AD RMS 보호를 적용하는 레이블을 선택해야 하는 경우에 대한 명확한 지침 및 예외 사항을 제공해야 합니다. 

[범위 지정 정책](configure-policy-scope.md)은 AD RMS 보호를 적용해야 하는 사용자만 AD RMS 보호가 구성된 레이블을 볼 수 있도록 하는 좋은 방법입니다. 

## <a name="additional-limitations-when-using-hyok"></a>HYOK 사용 시 추가 제한 사항

Azure RMS 보호를 Azure Information Protection과 사용할 경우 Azure RMS 보호를 사용하면 얻는 나열된 혜택을 지원하지 않을 뿐 아니라 다음과 같은 제한 사항이 있습니다.

- Office 2010 또는 Office 2007을 지원하지 않습니다.

- 사용자에게 Outlook에서 **전달 금지**를 선택하지 않도록 알리거나 구체적인 지침을 제공합니다. 

    HYOK 또는 Azure Rights Management 서비스를 사용하도록 **전달 금지**에 대한 레이블을 구성할 수는 있지만, 사용자가 스스로 [전달 금지]를 선택할 수도 있습니다. 사용자는 Office 리본의 **메시지** 탭에 있는 **전달 금지** 단추를 사용하거나 Outlook 메뉴 옵션을 사용하여 이 옵션을 선택할 수 있습니다. **전달 금지** 메뉴 옵션은 **파일** > **사용 권한** 및 리본의 **옵션** 탭에 있는 **사용 권한** 단추에 있습니다. 
    
    Azure Information Protection 클라이언트에서는 사용자가 Outlook에서 **전달 금지** 단추를 선택하면 항상 Azure RMS를 사용합니다. 이 동작을 원치 않는 경우 **Outlook 리본에 전달 금지 단추 추가** [정책 설정](../deploy-use/configure-policy-settings.md)을 **끄기**로 설정하여 이 단추를 숨길 수 있습니다. 
    
    사용자가 Outlook 메뉴 옵션에서 **전달 금지**를 선택하면 Azure RMS 또는 AD RMS 중에서 선택할 수 있지만, 메일 메시지에 대해 선택할 옵션을 알지 못할 수도 있습니다. Azure RMS를 사용해야 할 때 AD RMS를 사용하는 경우 외부에서 공유하는 사용자는 이러한 전자 메일 메시지를 열 수 없습니다.

- Word, Excel, PowerPoint 및 파일 탐색기에 대한 사용자 정의 권한을 구성하는 경우 파일 탐색기에서 HYOK(AD RMS) 보호 대신 Azure RMS를 사용한 보호가 항상 적용됩니다. 이 제한은 클라이언트의 현재 미리 보기 버전에는 적용되지 않습니다.

- 사용자가 Outlook에서 AD RMS 보호를 적용하는 레이블을 선택한 다음 메일을 보내기 전에 마음이 바뀌어 Azure RMS 보호를 적용하는 레이블을 선택하는 경우, 새로 선택한 레이블은 적용되지 않습니다. 다음 오류 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. You don't have permission to perform this action.**(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 이 작업을 수행할 권한이 없습니다.)
    
    유일한 해결책은 메일 메시지를 닫고 다시 시작하는 것입니다. 사용자가 처음에 Azure RMS 보호를 적용하는 레이블을 선택한 다음 AD RMS 보호를 적용하는 레이블로 레이블을 변경하는 경우에도 동일한 제한이 적용됩니다.

## <a name="requirements-for-hyok"></a>HYOK에 대한 요구 사항

AD RMS 배포가 Azure Information Protection에 대해 AD RMS 보호를 제공하기 위한 다음 요구 사항을 충족하는지 확인합니다.

- AD RMS 구성:
    
    - 최소 버전의 Windows Server 2012 R2: 프로덕션 환경에 대해 필요하지만 테스트 및 평가용으로는 최소 버전의 Windows Server 2008 R2 서비스 팩 1을 사용할 수 있습니다.
    
    - 다음 토폴로지 중 하나입니다.
        
        - 단일 AD RMS 루트 클러스터가 있는 단일 포리스트 
        
        - 독립 AD RMS 루트 클러스터 및 다른 포리스트의 사용자로 보호되는 콘텐츠에 액세스할 수 없는 사용자가 있는 다중 포리스트
        
        - 각각에서 AD RMS 클러스터가 있는 다중 포리스트 각 AD RMS 클러스터는 동일한 AD RMS 클러스터를 가리키는 라이선스 URL을 공유합니다. 이 AD RMS 클러스터에서 다른 모든 AD RMS 클러스터에서 모든 TUD(신뢰할 수 있는 사용자 도메인) 인증서를 가져와야 합니다. 이 토폴로지에 대한 자세한 내용은 [신뢰할 수 있는 사용자 도메인](https://technet.microsoft.com/library/dd983944(v=ws.10\).aspx)을 참조하세요.
        
    별도 포리스트에 여러 AD RMS 클러스터가 있는 경우 HYOK(AD RMS) 보호를 적용하는 글로벌 정책에서 모든 레이블을 삭제하고 각 클러스터에 대한 [범위 지정 정책](configure-policy-scope.md)을 구성합니다. 그런 다음 사용자를 둘 이상의 범위 지정 정책에 할당하게 하는 그룹을 사용하지 않도록 각 클러스터에 대한 사용자를 해당 범위 지정 정책에 할당합니다. 결과는 각 사용자에 하나의 AD RMS 클러스터에 대한 레이블이 있어야 합니다. 
    
    - [암호화 모드 2](https://technet.microsoft.com/library/hh867439.aspx): AD RMS 클러스터 속성, **일반** 탭을 확인하여 모드를 확인할 수 있습니다.
    
    - SCP(서비스 연결 지점)가 Active Directory에 등록되어 있지 않습니다. Azure Information Protection과 함께 AD RMS 보호를 사용하는 경우 SCP가 사용되지 않습니다. AD RMS 배포에 대한 SCP를 등록한 경우 이 SCP를 제거해야만 Azure Rights Management 보호를 위한 [서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery)이 성공합니다.
    
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

**HYOK(AD RMS)** 보호에 대한 레이블을 구성하는 경우 AD RMS 클러스터의 라이선스 URL을 지정해야 합니다. 또한 사용자에게 부여할 권한에 대해 구성한 템플릿을 지정하거나, 사용자가 권한 및 사용자를 정의할 수 있도록 해야 합니다. 

Active Directory Rights Management Services 콘솔에서 템플릿 GUID 및 라이선스 URL 값을 찾을 수 있습니다.

- 템플릿 GUID를 찾으려면: 클러스터를 확장하고 **권한 정책 템플릿**을 클릭합니다. **분산 권한 정책 템플릿** 정보에서 사용할 템플릿의 GUID를 복사할 수 있습니다. 예: 82bf3474-6efe-4fa1-8827-d1bd93339119

- 라이선스 URL을 찾으려면: 클러스터 이름을 클릭합니다. **클러스터 세부 정보**에서 **/_wmcs/licensing** 문자열을 제외하고 **라이선스**입니다. 예: https://rmscluster.contoso.com 
    
    인트라넷 라이선스 값뿐 아니라 엑스트라넷 라이선스 값도 있고 두 값이 서로 다른 경우: 명시적 지점 간 트러스트를 사용하여 정의한 파트너와 보호된 문서 또는 메일을 공유할 경우에만 엑스트라넷 값을 지정합니다. 그렇지 않은 경우 인트라넷 값을 사용하고 Azure Information Protection에 AD RMS 보호를 사용하는 모든 클라이언트 컴퓨터에서 인트라넷 연결을 사용하여 연결하도록 합니다(예: 원격 컴퓨터에서 VPN 연결 사용).

## <a name="next-steps"></a>다음 단계

이 기능에 대한 자세한 내용과 사용 시 지침은 블로그 게시물 공지인 [Azure Information Protection with HYOK (Hold Your Own Key)](https://cloudblogs.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/)(Azure Information Protection 및 HYOK(Hold Your Own Key))를 참조하세요.

AD RMS 보호에 대한 레이블을 구성하려면 [Rights Management 보호를 적용하도록 레이블을 구성하는 방법](../deploy-use/configure-policy-protection.md)을 참조하세요. 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]