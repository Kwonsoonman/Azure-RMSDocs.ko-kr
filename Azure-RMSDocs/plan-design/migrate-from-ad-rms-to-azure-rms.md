---
title: AD RMS-Azure Information Protection 마이그레이션
description: AD RMS(Active Directory Rights Management Services) 배포를 Azure Information Protection으로 마이그레이션하는 지침을 제공합니다. 마이그레이션 후 사용자는 조직에서 AD RMS를 사용하여 보호하는 문서 및 메일 메시지에 여전히 액세스할 수 있으며 새로 보호되는 콘텐츠에는 Azure Information Protection이 사용됩니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 937d9b1e91690ed7633d2112725f49e1325afcbd
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473929"
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

AD RMS(Active Directory Rights Management Services) 배포를 Azure Information Protection으로 마이그레이션하려면 다음 지침을 사용합니다. 

마이그레이션 후 AD RMS 서버는 더 이상 사용되지 않지만, 사용자는 Azure RMS로 보호되는 조직의 문서 및 메일 메시지에 여전히 액세스할 수 있습니다. 새로 보호된 콘텐츠는 Azure Information Protection의 Azure RMS(Azure Rights Management 서비스)를 사용합니다.

이 AD RMS 마이그레이션이 조직에 맞는지 확실하지 않습니까?

- Azure Information Protection에 대한 자세한 내용은 [Azure Information Protection이란?](../what-is-information-protection.md)을 참조하세요.

- Azure Information Protection과 AD RMS에 대한 비교는 [Azure Information Protection 및 AD RMS 비교](../compare-on-premise.md)를 참조하세요.

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Azure Information Protection으로 마이그레이션하기 전에 읽어보면 좋은 자료

필요하지는 않지만, 마이그레이션을 시작하기 전에 다음 문서를 읽으면 유용합니다. 마이그레이션 단계와 관련된 경우 기술의 원리를 보다 잘 이해하는 데 도움이 되는 지식을 제공합니다.

- [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md): 클라우드에서 동일한 SLC 키를 Microsoft(기본값) 또는 사용자(BYOK(Bring Your Own Key 구성)가 관리하는 Azure Information Protection 테넌트에 대해 설정하는 키 관리 옵션을 이해합니다. 

- [RMS 서비스 검색](../rms-client/client-deployment-notes.md#rms-service-discovery): RMS 클라이언트 배포 참고 사항의 이 섹션에서는 서비스 검색 순서가 **레지스트리**, **SCP**, **클라우드**임을 설명합니다. SCP가 계속 설치되어 있을 때 마이그레이션 프로세스 중 SCP에서 반환한 AD RMS 클러스터를 사용하지 않도록 Azure Information Protection 테넌트에 대한 레지스트리 설정으로 클라이언트를 구성합니다.

- [Microsoft Rights Management 커넥터 개요](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): RMS 커넥터 문서의 이 섹션에서는 온-프레미스 서버에서 Azure Rights Management Service에 연결하여 문서 및 메일을 보호하는 방법을 설명합니다.

또한 AD RMS 작동 방법에 대해 잘 알고 있다면 [Azure RMS는 어떤 방식으로 작동하나요? 기본적인 이해](../how-does-it-work.md)를 읽으면 유용합니다. 클라우드 버전과 같거나 다른 기술 프로세스를 파악하는 데 도움이 됩니다.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션하기 위한 필수 구성 요소

Azure Information Protection으로 마이그레이션을 시작하기 전에 다음의 필수 구성 요소가 있는지와 제한 사항을 이해하고 있는지 확인하세요.

- **지원되는 RMS 배포:**
    
    - 다음 AD RMS 릴리스는 Azure Information Protection으로 마이그레이션을 지원합니다.
    
        - Windows Server 2008 R2(x64)
        
        - Windows Server 2012(x64)
        
        - Windows Server 2012 R2(x64)
        
        - Windows Server 2016(x64)
        
    - 유효한 모든 AD RMS 토폴로지가 지원됩니다.
    
        - 단일 포리스트, 단일 RMS 클러스터
        
        - 단일 포리스트, 다중 라이선스 전용 RMS 클러스터
        
        - 다중 포리스트, 다중 RMS 클러스터
        
    참고: 기본적으로 다중 AD RMS 클러스터는 Azure Information Protection의 단일 테넌트로 마이그레이션됩니다. Azure Information Protection에 대한 별도의 테넌트를 원하는 경우 다른 마이그레이션으로 처리해야 합니다. 한 RMS 클러스터의 키를 둘 이상의 테넌트로 가져올 수 없습니다.

- **Azure Information Protection에 대한 구독을 포함하여 Azure Information Protection을 실행하기 위한 모든 요구 사항(Azure Rights Management 서비스는 활성화되지 않음):**

    [Azure Information Protection에 대한 요구 사항](../requirements.md)을 참조하세요.

    Office 2010을 실행하는 컴퓨터가 있는 경우 Azure Information Protection 클라이언트가 클라우드 서비스에 대해 사용자를 인증하는 기능을 제공하므로 이 클라이언트를 설치해야 합니다. 이후 버전 Office의 경우 분류 및 레이블 지정에 Azure Information Protection 클라이언트가 필요하며, 데이터를 보호하기만 하려는 경우 이는 선택 사항이지만 권장됩니다. 자세한 내용은 [Azure Information Protection 클라이언트 관리자 가이드](../rms-client/client-admin-guide.md)를 참조하세요.

    AD RMS에서 마이그레이션하려면 Azure Information Protection에 대한 구독이 있어야 하지만, 마이그레이션을 시작하기 전에 테넌트에 대해 Rights Management 서비스를 활성화하지 않는 것이 좋습니다. 마이그레이션 프로세스에는 AD RMS에서 키와 템플릿을 내보낸 후 Azure Information Protection의 테넌트로 가져오는 과정 다음에 이 활성화 단계가 포함됩니다. 그러나 Rights Management 서비스가 이미 활성화된 경우에도 여전히 일부 추가 단계를 통해 AD RMS에서 마이그레이션할 수 있습니다.


- **Azure Information Protection 준비:**

    - 온-프레미스 디렉터리와 Azure Active Directory 간 디렉터리 동기화

    - Azure Active Directory의 메일 사용이 가능한 그룹

    [Azure Information Protection을 위한 사용자 및 그룹 준비](prepare.md)를 참조하세요.

- **AD RMS와 함께 Exchange Server(예: 전송 규칙 및 Outlook Web Access) 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우**:

    - 이러한 서버에서 IRM을 사용할 수 없는 짧은 기간 계획
 
    마이그레이션 후 이러한 서버에서 IRM을 계속 사용할 수 있습니다. 그러나 마이그레이션 단계 중 하나는 IRM 서비스를 일시적으로 사용되지 않도록 설정하고, 커넥터를 설치 및 구성하고, 서버를 다시 구성하고, IRM을 다시 사용하도록 설정하는 것입니다.

    마이그레이션 프로세스 중에 이 단계 동안만 서비스가 중단됩니다.

- **HSM 보호된 키를 사용하여 고유한 Azure Information Protection 테넌트 키를 관리하려는 경우**:

    - 이 선택적 구성에는 Azure 주요 자격 증명 모음 및 HSM 보호된 키를 사용하여 주요 자격 증명 모음을 지원하는 Azure 구독이 필요합니다. 자세한 내용은 [Azure Key Vault Pricing(Azure 주요 자격 증명 모음 가격)](https://azure.microsoft.com/pricing/details/key-vault/) 페이지를 참조하세요. 


### <a name="cryptographic-mode-considerations"></a>암호화 모드 고려 사항

AD RMS 클러스터가 현재 암호화 모드 1인 경우 마이그레이션을 시작하기 전에 클러스터를 암호화 모드 2로 업그레이드하지 마세요. 대신 암호화 모드 1을 사용하여 마이그레이션하고 마이그레이션 종료 시 마이그레이션 후 작업의 하나로 테넌트 키를 다시 생성할 수 있습니다.

AD RMS 암호화 모드를 확인하려면
 
- Windows Server 2012 R2 및 Windows 2012의 경우: AD RMS 클러스터 속성 > **일반** 탭 

- Windows Server 2008 R2의 경우: [Windows Server 2008 R2 및 Windows Server 2008에서 AD RMS에 대해 RSA 키가 2048비트로 증가함](https://support.microsoft.com/help/2627272/rsa-key-length-is-increased-to-2048-bits-for-ad-rms-in-windows-server ) 핫픽스가 설치되었는지 확인합니다. 그렇지 않은 경우 AD RMS 클러스터가 암호화 모드 1에서 실행 중입니다.

### <a name="migration-limitations"></a>마이그레이션 제한 사항

- Azure Information Protection에서 사용되는 Rights Management 서비스에 의해 지원되지 않는 소프트웨어 및 클라이언트에서는 Azure Rights Management로 보호되는 콘텐츠를 보호하거나 사용할 수 없습니다. [Azure Rights Management에 대한 요구 사항](../requirements.md)의 지원되는 응용 프로그램 및 클라이언트 섹션을 확인하세요.

- 외부 파트너와 공동 작업하도록 AD RMS 배포가 구성된 경우(예: 트러스트된 사용자 도메인 또는 페더레이션 사용) 해당 파트너가 마이그레이션과 동시에 또는 마이그레이션 후 최대한 빨리 Azure Information Protection으로도 마이그레이션해야 합니다. 외부 파트너가 조직에서 이전에 Azure Information Protection을 사용하여 보호하던 콘텐츠에 계속 액세스하려면 사용자가 변경한 구성(이 문서에 포함됨)과 비슷하게 클라이언트 구성을 변경해야 합니다.
    
    파트너에서 있을 수 있는 가능한 구성 차이로 인해 이러한 재구성에 대한 정확한 지침은 이 문서에서 다루지 않습니다. 그러나 계획 지침의 다음 섹션을 참조하고 추가로 도움이 필요하면 [Microsoft 지원에 문의](../information-support.md#support-options-and-community-resources)하세요.

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>외부 파트너와 공동 작업하는 경우 마이그레이션 계획

AD RMS 파트너도 Azure Information Protection으로 마이그레이션해야 하므로 마이그레이션에 대한 계획 단계에 이러한 파트너를 포함합니다. 다음 마이그레이션 단계를 수행하기 전에 다음 사항이 마련되어 있는지 확인합니다.

- AD RMS 파트너가 Azure Rights Management 서비스를 지원하는 Azure Active Directory 테넌트를 보유하고 있습니다.  
    
    예를 들어 Office 365 E3이나 E5 구독, Enterprise Mobility + Security 구독, 또는 Azure Information Protection에 대한 독립 실행형 구독을 보유하고 있습니다.

- 파트너의 Azure Rights Management 서비스는 아직 활성화되지 않았지만, 파트너가 해당 Azure Rights Management 서비스 URL을 알고 있습니다.

    파트너는 Azure Rights Management 도구를 설치하고 서비스에 연결([Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice))한 다음 Azure Rights Management 서비스에 대한 테넌트 정보를 확인([Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration))하여 이 정보를 얻을 수 있습니다.

- 파트너의 AD RMS로 보호된 콘텐츠에 대한 요청을 해당 테넌트의 Azure Rights Management 서비스로 리디렉션하도록 마이그레이션된 클라이언트를 구성할 수 있도록 파트너는 해당 AD RMS 클러스터의 URL 및 Azure Rights Management 서비스 URL을 제공합니다. 클라이언트 리디렉션 구성에 대한 지침은 7단계에 있습니다.

- 사용자 마이그레이션을 시작하기 전에 파트너가 해당 AD RMS 클러스터 루트 키(SLC)를 해당 테넌트로 가져옵니다. 마찬가지로, 파트너가 사용자 마이그레이션을 시작하기 전에 AD RMS 클러스터 루트 키를 가져와야 합니다. 키 가져오기에 대한 지침은 이 마이그레이션 프로세스의 [4단계에 설명되어 있습니다. AD RMS에서 구성 데이터를 내보낸 후 Azure Information Protection으로 가져오기](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection)에 설명되어 있습니다. 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>AD RMS에서 Azure Information Protection으로 마이그레이션하는 단계 개요

마이그레이션 단계를 각기 다른 시간에 서로 다른 관리자가 수행할 수 있는 다섯 단계로 나눌 수 있습니다.

[**1단계: 마이그레이션 준비**](migrate-from-ad-rms-phase1.md)

- **1단계: AADRM PowerShell 모듈을 설치하고 테넌트 URL 식별**

    마이그레이션 프로세스를 수행하려면 하나 이상의 PowerShell cmdlets을 AADRM 모듈에서 실행해야 합니다. 많은 마이그레이션 단계를 완료하려면 테넌트의 Azure Rights Management 서비스 URL을 알아야 하고, PowerShell을 사용하여 이 값을 식별할 수 있습니다.

- **2단계. 클라이언트 마이그레이션에 대한 준비**

    모든 클라이언트를 한 번에 마이그레이션할 수 없어 배치로 마이그레이션하는 경우 온보딩 컨트롤을 사용하고 마이그레이션 전 스크립트를 배포합니다. 그러나 단계별로 마이그레이션하지 않고 모든 항목을 동시에 마이그레이션하려는 경우 이 단계를 건너뛸 수 있습니다.

- **3단계: 마이그레이션에 대한 Exchange 배포 준비**

    이 단계는 현재 Exchange Online 또는 Exchange 온-프레미스의 IRM 기능을 사용하여 메일을 보호하는 경우에만 필요합니다. 그러나 단계별로 마이그레이션하지 않고 모든 항목을 동시에 마이그레이션하려는 경우 이 단계를 건너뛸 수 있습니다.

[**2단계: AD RMS에 대한 서버 쪽 구성**](migrate-from-ad-rms-phase2.md)

- **4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure Information Protection으로 가져오기**

    AD RMS에서 XML 파일로 구성 데이터(키, 템플릿, URL)를 내보낸 다음 Import-AadrmTpd PowerShell cmdlet을 사용하여 해당 파일을 Azure Information Protection에서 Azure Rights Management 서비스로 업로드합니다. 그런 다음 Azure Rights Management 서비스에 대해 테넌트 키로 사용할 가져온 SLC(서버 사용 허가자 인증서) 키를 식별합니다. AD RMS 키 구성에 따라 추가 단계가 필요할 수도 있습니다.

    - **소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 Microsoft에서 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다. 이는 가장 간단한 마이그레이션 경로이며 추가 단계가 필요하지 않습니다.

    - **HSM 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS용 HSM에서 저장한 키에서 고객이 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 온-프레미스 Thales HSM에서 Azure Key Vault로 키를 전송하고 Azure Rights Management 서비스에서 이 키를 사용할 권한을 부여하기 위한 추가 단계가 필요합니다. 기존 HSM 보호 키는 모듈로 보호해야 합니다. OCS 보호 키는 권한 관리 서비스에서 지원하지 않습니다.

    - **소프트웨어 보호된 키-HSM 보호된 키 마이그레이션**:

        AD RMS의 중앙에서 관리되는 암호 기반 키에서 고객이 관리하는 Azure Information Protection 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 먼저 소프트웨어 키를 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 Thales HSM에서 Azure Key Vault HSM으로 키를 전송하기 위한 추가 단계를 수행하고, Azure Rights Management 서비스에 키를 저장하는 주요 자격 증명 모음을 사용할 권한을 부여해야 하기 때문에 대부분의 구성이 필요합니다.

- **5단계. Azure Rights Management 서비스 활성화**

    가능하면 가져오기 프로세스가 완료된 후에 이 단계를 수행합니다. 서비스가 가져오기 전에 활성화된 경우 추가 단계가 필요합니다.

- **6단계. 가져온 템플릿 구성**

    권한 정책 템플릿을 가져오면 해당 상태가 보관됩니다. 사용자가 해당 템플릿을 보고 사용할 수 있도록 하려면, Azure 클래식 포털에서 템플릿 상태를 게시됨으로 변경해야 합니다.


[**3단계: 클라이언트 쪽 구성**](migrate-from-ad-rms-phase3.md)

- **7단계: Azure Information Protection을 사용하도록 Windows 컴퓨터 다시 구성**

    AD RMS 대신 Azure Rights Management 서비스를 사용하도록 기존 Windows 컴퓨터를 다시 구성해야 합니다. 이 단계는 조직의 컴퓨터, 그리고 AD RMS를 실행하는 동안 공동으로 작업한 경우 파트너 조직의 컴퓨터에 적용됩니다.

[**4단계: 지원 서비스 구성**](migrate-from-ad-rms-phase4.md)

- **8단계: Exchange Online에 대한 IRM 통합 구성**

    이 단계에서는 이제 Azure Rights Management 서비스를 사용하기 위한 Exchange Online에 대한 AD RMS 마이그레이션을 완료합니다.

- **9단계: Exchange Server 및 SharePoint Server에 대한 IRM 통합 구성**

    이 단계에서는 이제 Azure Rights Management 서비스를 사용하기 위한 Exchange 또는 SharePoint 온-프레미스에 대한 AD RMS 마이그레이션을 완료합니다(Rights Management 커넥터를 배포해야 함).


[**5단계: 마이그레이션 후 작업**](migrate-from-ad-rms-phase5.md )

- **10단계: AD RMS 프로비전 해제**

    모든 Windows 컴퓨터에서 Azure Rights Management 서비스를 사용하고 있으며 더 이상 AD RMS 서버에 액세스하지 않음을 확인했으면 AD RMS 배포 프로비전을 해제할 수 있습니다.

- **11단계: 클라이언트 마이그레이션 작업 완료**

    iOS 휴대폰 및 iPad, Android 휴대폰 및 태블릿, Windows 휴대폰 및 Mac 컴퓨터와 같은 모바일 장치를 지원하기 위해 [모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포한 경우, AD RMS를 사용하도록 이러한 클라이언트를 리디렉션한 DNS의 SRV 레코드를 제거해야 합니다. 
    
    준비 단계 중에 구성한 온보딩 컨트롤이 더 이상 필요하지 않습니다. 그러나 단계별로 마이그레이션하지 않고 모든 항목을 동시에 마이그레이션하도록 선택함에 따라 온보딩 컨트롤을 사용하지 않은 경우 온보딩 컨트롤을 제거하도록 요구하는 지침을 건너뛸 수 있습니다.
    
    Windows 컴퓨터가 Office 2010을 실행 중인 경우 **AD RMS Rights Policy Template Management(자동)** 작업을 비활성화해야 하는지 확인해야 합니다.

- **12단계: Azure Information Protection 테넌트 키 다시 입력**

    이 단계는 마이그레이션 전에 암호화 모드 2에서 실행하지 않은 경우에 권장됩니다.


## <a name="next-steps"></a>다음 단계
마이그레이션을 시작하려면 [1단계 - 준비](migrate-from-ad-rms-phase1.md)로 이동합니다.

