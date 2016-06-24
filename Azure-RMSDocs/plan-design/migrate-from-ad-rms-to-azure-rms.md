---
# required metadata

title: AD RMS에서 Azure 권한 관리로 마이그레이션 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# AD RMS에서 Azure 권한 관리로 마이그레이션

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*

AD RMS(Active Directory Rights Management Services) 배포를 Azure RMS(Azure 권한 관리)로 마이그레이션하려면 다음 지침을 따르세요. 마이그레이션 후 사용자는 조직에서 AD RMS를 사용하여 보호하는 문서 및 전자 메일 메시지에 여전히 액세스할 수 있으며 새로 보호되는 콘텐츠에는 Azure RMS가 사용됩니다.

이 AD RMS 마이그레이션이 조직에 맞는지 확실하지 않습니까?

-   Azure RMS 소개, Azure RMS로 해결할 수 있는 비즈니스 문제, Azure RMS가 관리자와 사용자에게 표시되는 모양 및 Azure RMS 작동 방식을 보려면 [Azure 권한 관리란?](../understand-explore/what-is-azure-rms.md)을 참조하세요.

-   Azure RMS와 AD RMS를 비교한 내용을 보려면 [Azure 권한 관리와 AD RMS 비교](../understand-explore/compare-azure-rms-ad-rms.md)를 참조하세요.

## AD RMS에서 Azure RMS로 마이그레이션하기 위한 필수 구성 요소
Azure RMS로 마이그레이션을 시작하기 전에 다음의 필수 구성 요소가 있는지와 제한 사항을 이해하고 있는지 확인하세요.


- **지원되는 RMS 배포**

    Windows Server 2008에서 Windows Server 2012 R2에 이르는 모든 AD RMS 릴리스는 Azure RMS로의 마이그레이션을 지원합니다.

    - Windows Server 2008(x86 또는 x64)

    - Windows Server 2008 R2(x64)

    - Windows Server 2012(x64)

    - Windows Server 2012 R2(x64)

    유효한 모든 AD RMS 토폴로지가 지원됩니다.

    - 단일 포리스트, 단일 RMS 클러스터

    - 단일 포리스트, 다중 라이선스 전용 RMS 클러스터

    - 다중 포리스트, 다중 RMS 클러스터

    **참고**: 기본적으로 다중 RMS 클러스터는 단일 Azure RMS 테넌트로 마이그레이션됩니다. 다른 RMS 테넌트를 원하는 경우 다른 마이그레이션으로 처리해야 합니다. 한 RMS 클러스터의 키를 둘 이상의 Azure RMS 테넌트에 가져올 수 없습니다.


- **Azure RMS 테넌트(활성화되지 않음)를 포함하여, Azure RMS를 실행하기 위한 모든 요구 사항**

    [Azure 권한 관리 요구 사항](../get-started/requirements-azure-rms.md)을 참조하세요.

    AD RMS에서 마이그레이션하려면 Azure RMS 테넌트가 있어야 하지만 마이그레이션 전에는 권한 관리 서비스를 활성화하지 않는 것이 좋습니다. 마이그레이션 프로세스에는 AD RMS에서 키와 템플릿을 내보낸 후 Azure RMS로 가져오는 과정 다음에 이 단계가 포함되어 있습니다. 그러나 Azure RMS가 이미 활성화된 경우에는 여전히 AD RMS에서 마이그레이션할 수 있습니다.


- **Azure RMS 준비:**

    - 온-프레미스 디렉터리와 Azure Active Directory 간 디렉터리 동기화

    - Azure Active Directory의 메일 사용이 가능한 그룹

    [Azure 권한 관리 준비](prepare.md)를 참조하세요.


- **AD RMS와 함께 Exchange Server(예: 전송 규칙 및 Outlook Web Access) 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우**:

    - 이러한 서버에서 IRM을 사용할 수 없는 짧은 기간 계획
 
    마이그레이션 후 Azure RMS에서 이러한 서버의 IRM을 계속 사용할 수 있습니다. 그러나 마이그레이션 단계 중 하나는 IRM 서비스를 일시적으로 사용되지 않도록 설정하고, 커넥터를 설치 및 구성하고, 서버를 다시 구성하고, IRM을 다시 사용하도록 설정하는 것입니다.

    마이그레이션 프로세스 중에 이 단계 동안만 서비스가 중단됩니다.


제한 사항:

-   마이그레이션 프로세스는 SLC(서버 라이선스 인증서) 키를 Azure RMS에 대한 HSM(하드웨어 보안 모듈)로 마이그레이션하도록 지원하지만, Exchange Online은 현재 이러한 구성을 지원하지 않습니다. Azure RMS로 마이그레이션한 후에 Exchange Online에서 IRM 기능을 모두 사용하려면 Azure RMS 테넌트 키를 [Microsoft에서 관리](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok-)해야 합니다. 또는 사용자가 Azure RMS 테넌트를 관리할 때는(BYOK) Exchange Online에서 제한된 기능의 IRM을 실행할 수 있습니다. Azure RMS와 함께 Exchange Online을 사용하는 방법에 대한 자세한 내용은 이러한 마이그레이션 지침에서 [6단계. Exchange Online에 대한 IRM 통합 구성](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online)을 참조하세요.

-   Azure RMS에서 지원되지 않는 소프트웨어 및 클라이언트가 있는 경우 Azure RMS로 보호되는 콘텐츠를 보호하거나 사용할 수 없게 됩니다. [Azure 권한 관리 요구 사항](../get-started/requirements-azure-rms.md) 문서에서 지원되는 응용 프로그램 및 클라이언트 섹션을 확인하세요.

-   온-프레미스 키를 Azure RMS에 보관된 형태로 가져오고(가져오기 프로세스 동안 활성화되도록 TPD 설정 안 함) 단계별 마이그레이션을 위해 일괄로 사용자를 마이그레이션하는 경우, 마이그레이션된 사용자가 새롭게 보호하는 콘텐츠를 AD RMS에 원래 있던 사용자가 액세스할 수 없게 됩니다. 이 시나리오에서는 가능하면 마이그레이션 시간을 짧게 유지하고 공동으로 작업하는 사용자들이 함께 마이그레이션되도록 논리적으로 일괄 마이그레이션합니다.

    가져오기 프로세스 중에 TPD가 활성화되도록 설정하는 경우 모든 사용자가 동일한 키를 사용하여 콘텐츠를 보호하기 때문에 이 제한이 적용되지 않습니다. 이 구성을 사용하면 모든 사용자를 원하는 때에 독립적으로 마이그레이션할 수 있기 때문에 권장됩니다.

-   예를 들어, 트러스트된 사용자 도메인 또는 페더레이션을 사용하여 외부 파트너와 공동으로 작업하는 경우 해당 파트너가 마이그레이션과 동시에 또는 마이그레이션 후 가능한 빨리 Azure RMS로도 마이그레이션해야 합니다. 외부 파트너가 조직에서 이전에 AD RMS를 사용하여 보호하던 콘텐츠에 계속 액세스하려면 사용자가 변경한 구성(이 문서에 포함됨)과 비슷하게 클라이언트 구성을 변경해야 합니다.

    파트너에서 있을 수 있는 가능한 구성 차이로 인해 이러한 재구성에 대한 정확한 지침은 이 문서에서 다루지 않습니다. 도움이 필요하면 [Microsoft 지원 팀에 문의](../get-started/information-support#support-options-and-community-resources)하세요.

## AD RMS에서 Azure RMS로 마이그레이션하는 단계 개요


9개의 마이그레이션 단계를 각기 다른 시간에 다른 관리자가 수행할 수 있는 네 단계로 나눌 수 있습니다.

[**1단계: AD RMS에 대한 서버 쪽 구성**](migrate-from-ad-rms-phase1.md)

- **1단계: Azure RMS 관리 도구 다운로드**

    마이그레이션 프로세스에서는 Azure RMS 관리의 관리 도구와 함께 설치된 Azure RMS 모듈의 Windows PowerShell cmdlet을 하나 이상 실행해야 합니다.

- **2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기**

    AD RMS에서 XML 파일로 구성 데이터(예: 키, 템플릿, URL)를 내보낸 다음 Import-AadrmTpd Windows PowerShell cmdlet을 사용하여 해당 파일을 Azure RMS로 업로드합니다. AD RMS 키 구성에 따라 추가 단계가 필요할 수 있습니다.

    - **소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 Microsoft에서 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다. 이는 가장 간단한 마이그레이션 경로이며 추가 단계가 필요하지 않습니다.

    - **HSM 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS용 HSM에서 저장한 키에서 고객이 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 온-프레미스 Thales HSM에서 Azure RMS HSM으로 키를 전송하기 위한 추가 단계가 필요합니다. 기존 HSM 보호 키는 모듈로 보호해야 합니다. OCS 보호 키는 BYOK 도구 집합에서 지원하지 않습니다.

    - **소프트웨어 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 고객이 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 먼저 소프트웨어 키를 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 Thales HSM에서 Azure RMS HSM로 키를 전송하기 위한 추가 단계를 수행해야 하기 때문에 대부분의 구성이 필요합니다.

- **3단계. Azure RMS 테넌트 활성화**

    가능하면 가져오기 프로세스가 완료된 후에 이 단계를 수행합니다.

- **4단계. 가져온 템플릿 구성**

    권한 정책 템플릿을 가져오면 해당 상태가 보관됩니다. 사용자가 해당 템플릿을 보고 사용할 수 있도록 하려면, Azure 클래식 포털에서 템플릿 상태를 게시됨으로 변경해야 합니다.


[**2단계: 클라이언트 쪽 구성**](migrate-from-ad-rms-phase2.md)


- **5단계: Azure RMS를 사용하도록 클라이언트 다시 구성**

    AD RMS는 대신 Azure RMS 서비스를 사용하도록 기존 Windows 컴퓨터를 다시 구성해야 합니다. 이 단계는 조직의 컴퓨터, 그리고 AD RMS를 실행하는 동안 공동으로 작업한 경우 파트너 조직의 컴퓨터에 적용됩니다.

    또한 iOS 휴대폰 및 iPad, Android 휴대폰 및 태블릿, Windows Phone 및 Mac 컴퓨터와 같은 모바일 장치를 지원하기 위해 [모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포한 경우, AD RMS를 사용하도록 이러한 클라이언트를 리디렉션한 DNS의 SRV 레코드를 제거해야 합니다.


[**3단계: 지원 서비스 구성**](migrate-from-ad-rms-phase3.md)


- **6단계: Exchange Online과의 IRM 통합 구성**

    이 단계는 Azure RMS에서 Exchange Online을 사용하려는 경우에 필요합니다.


- **7단계: RMS 커넥터 배포**

    이 단계는 Azure RMS에서 다음 온-프레미스 서비스 중 하나를 사용하려는 경우에 필요합니다.

    - Exchange Server(예: 전송 규칙 및 Outlook Web Access)

    - SharePoint Server

    - FCI(파일 분류 인프라)를 실행하는 Windows Server


[**4단계: 마이그레이션 후 작업**](migrate-from-ad-rms-phase4.md )

- **8단계: AD RMS 서비스 해제**

    모든 클라이언트에서 Azure RMS를 사용하고 있으며, AD RMS 서버에 더 이상 액세스하지 않는다는 사실을 확인했으면 AD RMS 배포를 서비스 해제할 수 있습니다.


- **9단계: Azure RMS 테넌트 키 다시 입력**

    이 단계는 마이그레이션 전에 암호화 모드 2에서 실행하고 있지 않은 경우에는 필수이지만, Azure RMS 테넌트 키의 보안을 위해 모든 마이그레이션에 대해 권장됩니다.


## 다음 단계
마이그레이션을 시작하려면 [1단계 - 서버 쪽 구성](migrate-from-ad-rms-phase1.md)으로 이동합니다.



<!--HONumber=Jun16_HO2-->


