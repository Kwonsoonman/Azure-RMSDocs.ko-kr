---
title: "AD RMS에서 Azure Information Protection으로 마이그레이션 | Azure Information Protection"
description: "AD RMS(Active Directory Rights Management Services) 배포를 Azure Information Protection으로 마이그레이션하는 지침을 제공합니다. 마이그레이션 후 사용자는 조직에서 AD RMS를 사용하여 보호하는 문서 및 메일 메시지에 여전히 액세스할 수 있으며 새로 보호되는 콘텐츠에는 Azure Information Protection이 사용됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/27/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 30a154d67db81441cd48c56681ddb6552fc4cd18


---

# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS(Active Directory Rights Management Services) 배포를 Azure Information Protection으로 마이그레이션하려면 다음 지침을 따르세요. 마이그레이션 후 사용자는 조직에서 AD RMS를 사용하여 보호하는 문서 및 메일 메시지에 여전히 액세스할 수 있으며 새로 보호되는 콘텐츠에는 Azure Information Protection의 Azure Rights Management 서비스가 사용됩니다.

이 AD RMS 마이그레이션이 조직에 맞는지 확실하지 않습니까?

-   Azure Information Protection에 대한 자세한 내용은 [Azure Information Protection이란?](../understand-explore/what-is-information-protection.md)을 참조하세요.

-   Azure Information Protection과 AD RMS에 대한 비교는 [Azure Information Protection 및 AD RMS 비교](../understand-explore/compare-azure-rms-ad-rms.md)를 참조하세요.

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Azure Information Protection으로 마이그레이션하기 전에 읽어보면 좋은 자료

반드시 읽어야 하는 자료는 아니지만, 마이그레이션 단계와 관련된 기술의 작동 원리를 이해할 수 있으므로 마이그레이션을 시작하기 전에 다음을 읽으면 유용합니다.

- [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md): 클라우드에서 동일한 SLC 키를 Microsoft(기본값) 또는 사용자(BYOK(Bring Your Own Key 구성)가 관리하는 Azure Information Protection 테넌트에 대해 설정하는 키 관리 옵션을 이해합니다. 

- [RMS 서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery): RMS 클라이언트 배포 참고 사항에 관한 이 섹션에서는 서비스 검색 순서가 **레지스트리** > **SCP** > **클라우드**임을 설명합니다. SCP가 계속 설치되어 있을 때 마이그레이션 프로세스 중 SCP에서 반환한 AD RMS 클러스터를 사용하지 않도록 Azure Information Protection 테넌트에 대한 레지스트리 설정으로 클라이언트를 구성합니다.

- [Microsoft Rights Management 커넥터 개요](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): RMS 커넥터 문서의 이 섹션에서는 온-프레미스 서버에서 Azure Rights Management Service에 연결하여 문서 및 메일을 보호하는 방법을 설명합니다.

또한 AD RMS 작동 방법에 대해 잘 알고 있다면 [Azure RMS는 어떤 방식으로 작동하나요? 기본적인 이해](../understand-explore/how-does-it-work.md)를 읽으면 유용합니다. 클라우드 버전과 같거나 다른 기술 프로세스를 파악하는 데 도움이 됩니다.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션하기 위한 필수 구성 요소
Azure Information Protection으로 마이그레이션을 시작하기 전에 다음의 필수 구성 요소가 있는지와 제한 사항을 이해하고 있는지 확인하세요.

- **지원되는 RMS 배포:**
    
    - 다음 AD RMS 릴리스는 Azure Information Protection으로 마이그레이션을 지원합니다.
    
        - Windows Server 2008 R2(x64)
        
        - Windows Server 2012(x64)
        
        - Windows Server 2012 R2(x64)
        
        - Windows Server 2016(x64)
        
    - 암호화 모드 2:

        - Azure Information Protection으로 마이그레이션을 시작하기 전에 AD RMS 서버 및 클라이언트가 암호화 모드 2에서 실행되어야 합니다.
        
        현재 SLC(서버 사용 허가자 인증서) 키는 암호화 모드 2를 사용해야 하지만 암호화 모드 1에 맞게 구성된 이전 키는 Azure Information Protection에서 보관된 키로 지원됩니다. 암호화 모드 및 암호화 모드 2로 전환하는 방법에 대한 자세한 내용은 [AD RMS Cryptographic Modes](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx)(AD RMS 암호화 모드)를 참조하세요.
        
    - 유효한 모든 AD RMS 토폴로지가 지원됩니다.
    
        - 단일 포리스트, 단일 RMS 클러스터
        
        - 단일 포리스트, 다중 라이선스 전용 RMS 클러스터
        
        - 다중 포리스트, 다중 RMS 클러스터
        
    참고: 기본적으로 다중 RMS 클러스터는 단일 Azure Information Protection 테넌트로 마이그레이션됩니다. 별도의 Azure Information Protection 테넌트를 원하는 경우 다른 마이그레이션으로 처리해야 합니다. 한 RMS 클러스터의 키를 둘 이상의 Azure Information Protection 테넌트에 가져올 수 없습니다.

- **Azure Information Protection 테넌트(활성화되지 않음)를 포함하여 Azure Information Protection을 실행하기 위한 모든 요구 사항:**

    [Azure Information Protection에 대한 요구 사항](../get-started/requirements-azure-rms.md)을 참조하세요.

    AD RMS에서 마이그레이션하려면 Azure Information Protection 테넌트가 있어야 하지만 마이그레이션 전에는 Rights Management 서비스를 활성화하지 않는 것이 좋습니다. 마이그레이션 프로세스에는 AD RMS에서 키와 템플릿을 내보낸 후 Azure Information Protection으로 가져오는 과정 다음에 이 단계가 포함되어 있습니다. 그러나 Rights Management 서비스가 이미 활성화된 경우에는 여전히 AD RMS에서 마이그레이션할 수 있습니다.


- **Azure Information Protection 준비:**

    - 온-프레미스 디렉터리와 Azure Active Directory 간 디렉터리 동기화

    - Azure Active Directory의 메일 사용이 가능한 그룹

    [Azure Information Protection 준비](prepare.md)를 참조하세요.


- **AD RMS와 함께 Exchange Server(예: 전송 규칙 및 Outlook Web Access) 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우**:

    - 이러한 서버에서 IRM을 사용할 수 없는 짧은 기간 계획
 
    마이그레이션 후 Azure Rights Management 서비스에서 이러한 서버의 IRM을 계속 사용할 수 있습니다. 그러나 마이그레이션 단계 중 하나는 IRM 서비스를 일시적으로 사용되지 않도록 설정하고, 커넥터를 설치 및 구성하고, 서버를 다시 구성하고, IRM을 다시 사용하도록 설정하는 것입니다.

    마이그레이션 프로세스 중에 이 단계 동안만 서비스가 중단됩니다.

- **HSM 보호된 키를 사용하여 고유한 Azure Information Protection 테넌트 키를 관리하려는 경우**:

    - 이 선택적 구성에는 Azure 주요 자격 증명 모음 및 HSM 보호된 키를 사용하여 주요 자격 증명 모음을 지원하는 Azure 구독이 필요합니다. 자세한 내용은 [Azure Key Vault Pricing(Azure 주요 자격 증명 모음 가격)](https://azure.microsoft.com/en-us/pricing/details/key-vault/) 페이지를 참조하세요. 


제한 사항:

-   마이그레이션 프로세스는 SLC(서버 라이선스 인증서) 키를 Azure Information Protection에 대한 HSM(하드웨어 보안 모듈)로 마이그레이션하도록 지원하지만, Exchange Online은 현재 Azure Information Protection에서 사용되는 Rights Management 서비스에 대해 이러한 구성을 지원하지 않습니다. Azure Information Protection으로 마이그레이션한 후에 Exchange Online에서 IRM 기능을 모두 사용하려면 Azure Information Protection 테넌트 키를 [Microsoft에서 관리](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok)해야 합니다. 또는 사용자가 Azure Information Protection 테넌트를 관리할 때는(BYOK) Exchange Online에서 제한된 기능의 IRM을 실행할 수 있습니다. Azure Information Protection 서비스와 함께 Exchange Online을 사용하는 방법에 대한 자세한 내용은 이러한 마이그레이션 지침에서 [6단계. Exchange Online에 대한 IRM 통합 구성](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online)을 참조하세요.

-   Azure Information Protection에서 사용되는 Rights Management 서비스에 의해 지원되지 않는 소프트웨어 및 클라이언트에서는 Azure Rights Management로 보호되는 콘텐츠를 보호하거나 사용할 수 없습니다. [Azure 권한 관리 요구 사항](../get-started/requirements-azure-rms.md) 문서에서 지원되는 응용 프로그램 및 클라이언트 섹션을 확인하세요.

-   온-프레미스 키를 Azure Information Protection에 보관된 형태로 가져오고(가져오기 프로세스 동안 활성화되도록 TPD 설정 안 함) 단계별 마이그레이션을 위해 일괄로 사용자를 마이그레이션하는 경우, 마이그레이션된 사용자가 새롭게 보호하는 콘텐츠를 AD RMS에 원래 있던 사용자가 액세스할 수 없게 됩니다. 이 시나리오에서는 가능하면 마이그레이션 시간을 짧게 유지하고 공동으로 작업하는 사용자들이 함께 마이그레이션되도록 논리적으로 일괄 마이그레이션합니다.

    가져오기 프로세스 중에 TPD가 활성화되도록 설정하는 경우 모든 사용자가 동일한 키를 사용하여 콘텐츠를 보호하기 때문에 이 제한이 적용되지 않습니다. 이 구성을 사용하면 모든 사용자를 원하는 때에 독립적으로 마이그레이션할 수 있기 때문에 권장됩니다.

-   예를 들어, 트러스트된 사용자 도메인 또는 페더레이션을 사용하여 외부 파트너와 협업하는 경우 해당 파트너가 마이그레이션과 동시에 또는 마이그레이션 후 최대한 빨리 Azure Information Protection으로도 마이그레이션해야 합니다. 외부 파트너가 조직에서 이전에 Azure Information Protection을 사용하여 보호하던 콘텐츠에 계속 액세스하려면 사용자가 변경한 구성(이 문서에 포함됨)과 비슷하게 클라이언트 구성을 변경해야 합니다.

    파트너에서 있을 수 있는 가능한 구성 차이로 인해 이러한 재구성에 대한 정확한 지침은 이 문서에서 다루지 않습니다. 도움이 필요하면 [Microsoft 지원 팀에 문의](../get-started/information-support.md#support-options-and-community-resources)하세요.

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션하는 단계 개요


마이그레이션 단계를 각기 다른 시간에 다른 관리자가 수행할 수 있는 네 단계로 나눌 수 있습니다.

[**1단계: AD RMS에 대한 서버 쪽 구성**](migrate-from-ad-rms-phase1.md)

- **1단계: Azure RMS 관리 도구 다운로드**

    마이그레이션 프로세스에서는 Azure RMS 관리의 관리 도구와 함께 설치된 Azure RMS 모듈의 Windows PowerShell cmdlet을 하나 이상 실행해야 합니다.

- **2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure Information Protection으로 가져오기**

    AD RMS에서 XML 파일로 구성 데이터(예: 키, 템플릿, URL)를 내보낸 다음 Import-AadrmTpd Windows PowerShell cmdlet을 사용하여 해당 파일을 Azure Information Protection에서 Azure Rights Management 서비스로 업로드합니다. AD RMS 키 구성에 따라 추가 단계가 필요할 수 있습니다.

    - **소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 Microsoft에서 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다. 이는 가장 간단한 마이그레이션 경로이며 추가 단계가 필요하지 않습니다.

    - **HSM 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS용 HSM에서 저장한 키에서 고객이 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 온-프레미스 Thales HSM에서 Azure Key Vault로 키를 전송하고 Azure Rights Management 서비스에서 이 키를 사용할 권한을 부여하기 위한 추가 단계가 필요합니다. 기존 HSM 보호 키는 모듈로 보호해야 합니다. OCS 보호 키는 권한 관리 서비스에서 지원하지 않습니다.

    - **소프트웨어 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 고객이 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 먼저 소프트웨어 키를 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 Thales HSM에서 Azure Key Vault HSM으로 키를 전송하기 위한 추가 단계를 수행하고, Azure Rights Management 서비스에 키를 저장하는 주요 자격 증명 모음을 사용할 권한을 부여해야 하기 때문에 대부분의 구성이 필요합니다.

- **3단계. Azure Information Protection 테넌트 활성화**

    가능하면 가져오기 프로세스가 완료된 후에 이 단계를 수행합니다.

- **4단계. 가져온 템플릿 구성**

    권한 정책 템플릿을 가져오면 해당 상태가 보관됩니다. 사용자가 해당 템플릿을 보고 사용할 수 있도록 하려면, Azure 클래식 포털에서 템플릿 상태를 게시됨으로 변경해야 합니다.


[**2단계: 클라이언트 쪽 구성**](migrate-from-ad-rms-phase2.md)


- **5단계: Azure Information Protection을 사용하도록 클라이언트 다시 구성**

    AD RMS 대신에 Azure Information Protection 서비스를 사용하도록 기존 Windows 컴퓨터를 다시 구성해야 합니다. 이 단계는 조직의 컴퓨터, 그리고 AD RMS를 실행하는 동안 공동으로 작업한 경우 파트너 조직의 컴퓨터에 적용됩니다.

    또한 iOS 휴대폰 및 iPad, Android 휴대폰 및 태블릿, Windows Phone 및 Mac 컴퓨터와 같은 모바일 장치를 지원하기 위해 [모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포한 경우, AD RMS를 사용하도록 이러한 클라이언트를 리디렉션한 DNS의 SRV 레코드를 제거해야 합니다.


[**3단계: 지원 서비스 구성**](migrate-from-ad-rms-phase3.md)


- **6단계: Exchange Online과의 IRM 통합 구성**

    이 단계는 Exchange Online을 Azure Information Protection의 Azure Rights Management 서비스와 함께 사용하려는 경우에 필요합니다.


- **7단계: RMS 커넥터 배포**

    이 단계는 다음 온-프레미스 서비스를 Azure Rights Management 서비스와 함께 사용하여 Office 문서 및 메일을 보호하려는 경우에 필요합니다.

    - Exchange Server(예: 전송 규칙 및 Outlook Web Access)

    - SharePoint Server

    - FCI(파일 분류 인프라)를 실행하는 Windows Server


[**4단계: 마이그레이션 후 작업**](migrate-from-ad-rms-phase4.md )

- **8단계: AD RMS 서비스 해제**

    모든 클라이언트에서 Azure Information Protection을 사용하고 있으며, AD RMS 서버에 더 이상 액세스하지 않는다는 사실을 확인했으면 AD RMS 배포를 서비스 해제할 수 있습니다.


- **9단계: Azure Information Protection 테넌트 키 다시 입력**

    이 단계는 선택 사항이지만 2단계에서 선택한 Azure Information Protection 테넌트 키 토폴로지가 Microsoft 관리인 경우 권장됩니다. 선택한 Azure Information Protection 테넌트 키 토폴로지가 고객 관리(BYOK)인 경우 이 단계는 적용되지 않습니다.


## <a name="next-steps"></a>다음 단계
마이그레이션을 시작하려면 [1단계 - 서버 쪽 구성](migrate-from-ad-rms-phase1.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


