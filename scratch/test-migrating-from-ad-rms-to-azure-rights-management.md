---
title: 테스트 AD RMS에서 Azure 권한 관리로 마이그레이션
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# 이전: AD RMS에서 Azure 권한 관리로 마이그레이션
AD RMS(Active Directory Rights Management Services) 배포를 Azure RMS(Azure 권한 관리)로 마이그레이션하려면 다음 지침을 따르세요. 마이그레이션 후 사용자는 조직에서 AD RMS를 사용하여 보호하는 문서 및 전자 메일 메시지에 여전히 액세스할 수 있으며 새로 보호되는 콘텐츠에는 Azure RMS가 사용됩니다.

이 AD RMS 마이그레이션이 조직에 맞는지 확실하지 않습니까?

-   Azure RMS 소개, Azure RMS로 해결할 수 있는 비즈니스 문제, Azure RMS가 관리자와 사용자에게 표시되는 모양 및 Azure RMS 작동 방식을 보려면 [Azure 권한 관리란?](what-is-azure-rms.md)을 참조하세요.

-   Azure RMS와 AD RMS를 비교한 내용을 보려면 [Azure 권한 관리와 AD RMS 비교](compare-azure-rms-ad-rms.md)를 참조하세요.

## AD RMS에서 Azure RMS로 마이그레이션하기 위한 필수 구성 요소
Azure RMS로 마이그레이션을 시작하기 전에 다음의 필수 구성 요소가 있는지와 제한 사항을 이해하고 있는지 확인하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|지원되는 RMS 배포|Windows Server 2008에서 Windows Server 2012 R2에 이르는 모든 AD RMS 릴리스는 Azure RMS로의 마이그레이션을 지원합니다.<br /><br />Windows Server 2008(x86 또는 x64)<br /><br />Windows Server 2008 R2(x64)<br /><br />Windows Server 2012(x64)<br /><br />Windows Server 2012 R2(x64)<br /><br />유효한 모든 AD RMS 토폴로지가 지원됩니다.<br /><br />단일 포리스트, 단일 RMS 클러스터<br /><br />단일 포리스트, 다중 라이선스 전용 RMS 클러스터<br /><br />다중 포리스트, 다중 RMS 클러스터<br /><br />**참고**: 기본적으로 다중 RMS 클러스터는 단일 Azure RMS 테넌트로 마이그레이션됩니다. 다른 RMS 테넌트를 원하는 경우 다른 마이그레이션으로 처리해야 합니다. 한 RMS 클러스터의 키를 둘 이상의 Azure RMS 테넌트에 가져올 수 없습니다.|
|Azure RMS 테넌트(활성화되지 않음)를 포함하여, Azure RMS를 실행하기 위한 모든 요구 사항|[Azure 권한 관리 요구 사항](requirements-azure-rms.md)을 참조하세요.<br /><br />AD RMS에서 마이그레이션하려면 Azure RMS 테넌트가 있어야 하지만 마이그레이션 전에는 권한 관리 서비스를 활성화하지 않는 것이 좋습니다. 마이그레이션 프로세스에는 AD RMS에서 키와 템플릿을 내보낸 후 Azure RMS로 가져오는 과정 다음에 이 단계가 포함되어 있습니다. 그러나 Azure RMS가 이미 활성화된 경우에는 여전히 AD RMS에서 마이그레이션할 수 있습니다.|
|Azure RMS 준비:<br /><br />온-프레미스 디렉터리와 Azure Active Directory 간 디렉터리 동기화<br /><br />Azure Active Directory의 메일 사용이 가능한 그룹|[Azure 권한 관리 준비](prepare.md)를 참조하세요.|
|AD RMS에서 Exchange Server(예: 전송 규칙 및 Outlook Web Access) 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우:<br /><br />이러한 서버에서 IRM을 사용할 수 없는 짧은 기간 계획|마이그레이션 후 Azure RMS에서 이러한 서버의 IRM을 계속 사용할 수 있습니다. 그러나 마이그레이션 단계 중 하나는 IRM 서비스를 일시적으로 사용되지 않도록 설정하고, 커넥터를 설치 및 구성하고, 서버를 다시 구성하고, IRM을 다시 사용하도록 설정하는 것입니다.<br /><br />마이그레이션 프로세스 중에 이 단계 동안만 서비스가 중단됩니다.|
제한 사항:

-   마이그레이션 프로세스는 SLC(서버 라이선스 인증서) 키를 Azure RMS에 대한 HSM(하드웨어 보안 모듈)로 마이그레이션하도록 지원하지만, Exchange Online은 현재 이러한 구성을 지원하지 않습니다. Azure RMS로 마이그레이션한 후에 Exchange Online에서 IRM 기능을 모두 사용하려면 Azure RMS 테넌트 키를 [Microsoft에서 관리](http://technet.microsoft.com/library/dn440580.aspx)해야 합니다. 또는 사용자가 Azure RMS 테넌트를 관리할 때는(BYOK) Exchange Online에서 제한된 기능의 IRM을 실행할 수 있습니다. Azure RMS와 함께 Exchange Online을 사용하는 방법에 대한 자세한 내용은 이러한 지침에서 [6단계. Exchange Online에 대한 IRM 통합 구성](#BKMK_Step6Migration)을 참조하세요.

-   Azure RMS에서 지원되지 않는 소프트웨어 및 클라이언트가 있는 경우 Azure RMS로 보호되는 콘텐츠를 보호하거나 사용할 수 없게 됩니다. [Azure 권한 관리 요구 사항](requirements-azure-rms.md) 항목에서 지원되는 응용 프로그램 및 클라이언트 섹션을 확인하세요.

-   온-프레미스 키를 Azure RMS에 보관된 형태로 가져오고(가져오기 프로세스 동안 활성화되도록 TPD 설정 안 함) 단계별 마이그레이션을 위해 일괄로 사용자를 마이그레이션하는 경우, 마이그레이션된 사용자가 새롭게 보호하는 콘텐츠를 AD RMS에 원래 있던 사용자가 액세스할 수 없게 됩니다. 이 시나리오에서는 가능하면 마이그레이션 시간을 짧게 유지하고 공동으로 작업하는 사용자들이 함께 마이그레이션되도록 논리적으로 일괄 마이그레이션합니다.

    가져오기 프로세스 중에 TPD가 활성화되도록 설정하는 경우 모든 사용자가 동일한 키를 사용하여 콘텐츠를 보호하기 때문에 이 제한이 적용되지 않습니다. 이 구성을 사용하면 모든 사용자를 원하는 때에 독립적으로 마이그레이션할 수 있기 때문에 권장됩니다.

-   예를 들어, 트러스트된 사용자 도메인 또는 페더레이션을 사용하여 외부 파트너와 공동으로 작업하는 경우 해당 파트너가 마이그레이션과 동시에 또는 마이그레이션 후 가능한 빨리 Azure RMS로도 마이그레이션해야 합니다. 외부 파트너가 조직에서 이전에 AD RMS를 사용하여 보호하던 콘텐츠에 계속 액세스하려면 사용자가 변경한 구성(이 문서에 포함됨)과 비슷하게 클라이언트 구성을 변경해야 합니다.

    파트너에서 있을 수 있는 가능한 구성 차이로 인해 이러한 재구성에 대한 정확한 지침은 이 문서에서 다루지 않습니다. 도움이 필요하면 Microsoft CSS(고객 지원 서비스)에 문의하세요.

## AD RMS에서 Azure RMS로 마이그레이션하기 위한 단계

|마이그레이션 단계|추가 정보|
|------------------|--------------------|
|**1. Azure RMS 관리 도구 다운로드**|지침은 [1단계: Azure 권한 관리의 관리 도구 다운로드](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step1Migration)를 참조하세요.|
|**2. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기**|AD RMS에서 XML 파일로 구성 데이터(예: 키, 템플릿, URL)를 내보낸 다음 Import-AadrmTpd Windows PowerShell cmdlet을 사용하여 해당 파일을 Azure RMS로 업로드합니다. AD RMS 키 구성에 따라 추가 단계가 필요할 수 있습니다.<br /><br />**소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션**: AD RMS의 중앙에서 관리되는 암호 기반 키에서 Microsoft가 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다. 이는 가장 간단한 마이그레이션 경로이며 추가 단계가 필요하지 않습니다.<br /><br />**HSM 보호된 키-HSM 보호된 키 마이그레이션**: AD RMS용 HSM에서 저장한 키에서 고객이 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 온-프레미스 Thales HSM에서 Azure RMS HSM으로 키를 전송하기 위한 추가 단계가 필요합니다. 기존 HSM 보호 키는 모듈로 보호해야 합니다. OCS 보호 키는 BYOK 도구 집합에서 지원하지 않습니다.<br /><br />**소프트웨어 보호된 키-HSM 보호된 키 마이그레이션**: AD RMS의 중앙에서 관리되는 암호 기반 키에서 고객이 관리하는 Azure RMS 테넌트 키로 마이그레이션합니다("bring your own key" 또는 BYOK 시나리오). 이를 위해 먼저 소프트웨어 키를 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 Thales HSM에서 Azure RMS HSM로 키를 전송하기 위한 추가 단계를 수행해야 하기 때문에 대부분의 구성이 필요합니다.<br /><br />지침은 [2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step2Migration)를 참조하세요.|
|**3. RMS 테넌트를 활성화합니다.**|가능하면 가져오기 프로세스가 완료된 후에 이 단계를 수행합니다.<br /><br />자세한 내용 및 지침은 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration)를 참조하세요.|
|**4. 가져온 템플릿을 구성합니다.**|권한 정책 템플릿을 가져오면 해당 상태가 보관됩니다. 사용자가 해당 템플릿을 보고 사용할 수 있도록 하려면, Azure 클래식 포털에서 템플릿 상태를 게시됨으로 변경해야 합니다.<br /><br />지침은 [4단계. 가져온 템플릿 구성](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step4Migration)을 참조하세요.|
|**5. Azure RMS를 사용하도록 클라이언트 다시 구성**|AD RMS는 대신 Azure RMS 서비스를 사용하도록 기존 Windows 컴퓨터를 다시 구성해야 합니다. 이 단계는 조직의 컴퓨터, 그리고 AD RMS를 실행하는 동안 공동으로 작업한 경우 파트너 조직의 컴퓨터에 적용됩니다.<br /><br />또한 iOS 휴대폰 및 iPad, Android 휴대폰 및 태블릿, Windows Phone 및 Mac 컴퓨터와 같은 모바일 장치를 지원하기 위해 [모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx) 을 배포한 경우, AD RMS를 사용하도록 이러한 클라이언트를 리디렉션한 DNS의 SRV 레코드를 제거해야 합니다.<br /><br />지침은 [5단계. Azure RMS를 사용하도록 클라이언트 다시 구성](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step5Migration)을 참조하세요.|
|**6. Exchange Online과의 IRM 통합 구성**|이 단계는 Azure RMS에서 Exchange Online을 사용하려는 경우에 필요합니다.<br /><br />지침은 [6단계. Exchange Online에 대한 IRM 통합 구성](#BKMK_Step6Migration)을 참조하세요.|
|**7. RMS 커넥터를 배포합니다.**|이 단계는 Azure RMS에서 다음 온-프레미스 서비스 중 하나를 사용하려는 경우에 필요합니다.<br /><br />Exchange Server(예: 전송 규칙 및 Outlook Web Access)<br /><br />SharePoint Server<br /><br />파일 분류 인프라를 실행하는 Windows Server<br /><br />지침은 [7단계. RMS 커넥터 배포](#BKMK_Step7Migration)를 참조하세요.|
|**8. AD RMS 서비스 해제**|모든 클라이언트에서 Azure RMS를 사용하고 있으며, AD RMS 서버에 더 이상 액세스하지 않는다는 사실을 확인했으면 AD RMS 배포를 서비스 해제할 수 있습니다.<br /><br />지침은 [8단계. AD RMS 서비스 해제](#BKMK_Step8Migration)를 참조하세요.|
|**9. Azure RMS 테넌트 키를 다시 입력합니다.**|이 단계는 마이그레이션 전에 암호화 모드 2에서 실행하고 있지 않은 경우에는 필수이지만, Azure RMS 테넌트 키의 보안을 위해 모든 마이그레이션에 대해 권장됩니다.<br /><br />지침은 [9단계. Azure RMS 테넌트 키 다시 입력](#BKMK_Step9Migration)을 참조하세요.|

### <a name="BKMK_Step1Migration"></a>1단계: Azure 권한 관리의 관리 도구 다운로드
Microsoft 다운로드 센터로 이동하여 Windows PowerShell용 Azure RMS 관리 모듈이 포함된 [Azure Rights Management 관리 도구를 다운로드](http://go.microsoft.com/fwlink/?LinkId=257721)합니다.

### <a name="BKMK_Step2Migration"></a>2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기
이 단계는 다음의 두 부분으로 이루어진 프로세스입니다.

1.  TPD(트러스트된 게시 도메인)를 .xml 파일로 내보내 AD RMS에서 구성 데이터를 내보냅니다. 이 프로세스는 모든 마이그레이션에서 동일합니다.

2.  구성 데이터를 Azure RMS로 가져옵니다. 현재 AD RMS 배포 구성 및 Azure RMS 테넌트 키에 대한 기본 설정 토폴로지에 따라 이 단계의 프로세스가 다를 수 있습니다.

#### AD RMS에서 구성 데이터 내보내기
조직에 대해 보호된 콘텐츠가 있는 트러스트된 모든 게시 도메인에 대해 모든 AD RMS 클러스터에서 다음 절차를 수행합니다. 라이선스 전용 클러스터에서는 이 작업을 수행할 필요가 없습니다.

> [!NOTE]
> Windows Server 2003 Rights Management를 사용하는 경우 이러한 지침 대신 [Windows RMS에서 다른 인프라의 AD RMS로 마이그레이션](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) 항목에 있는 [SLC, TUD, TPD 및 RMS 개인 키 내보내기](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) 절차를 따릅니다.

###### 구성 데이터(트러스트된 게시 도메인 정보)를 내보내려면

1.  AD RMS 관리 권한이 있는 사용자로 AD RMS 클러스터에 로그온합니다.

2.  AD RMS 관리 콘솔(**Active Directory Rights Management Services**)에서 AD RMS 클러스터 이름을 확장하고, **트러스트 정책**를 확장한 후 **트러스트된 게시 도메인**을 클릭합니다.

3.  결과 창에서 트러스트된 게시 도메인을 선택하고 작업 창에서 **트러스트된 게시 도메인 내보내기**를 클릭합니다.

4.  **트러스트된 게시 도메인 내보내기** 대화 상자에서 다음을 수행합니다.

    -   **다른 이름으로 저장** 을 클릭하고 선택한 경로와 파일 이름으로 저장합니다. 파일 이름 확장명으로 **.xml**을 지정해야 합니다. 파일 이름 확장명은 자동으로 추가되지 않습니다.

    -   강력한 암호를 지정하고 확인합니다. 나중에 구성 데이터를 Azure RMS로 가져올 때 필요하므로, 이 암호를 기억해둡니다.

    -   RMS 버전 1.0에서 트러스트된 도메인 파일을 저장하려면 이 확인란을 선택하지 않도록 합니다.

트러스트된 모든 게시 도메인을 내보낸 경우 이 데이터를 Azure RMS로 가져오는 절차를 시작할 준비가 된 것입니다.

#### 구성 데이터를 Azure RMS로 가져오기
이 단계의 정확한 절차는 현재 AD RMS 배포 구성 및 Azure RMS 테넌트 키에 대한 기본 설정 토폴로지에 따라 달라집니다.

현재 AD RMS 배포는 SLC(서버 사용 허가자 인증서) 키에 대해 다음 구성 중 하나를 사용합니다.

-   AD RMS 데이터베이스의 암호 보호. 이것이 기본 구성입니다.

-   Thales HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

-   Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호.

-   외부 암호화 공급자를 사용하여 암호 보호.

> [!NOTE]
> AD RMS에서 하드웨어 보안 모듈을 사용하는 방법에 대한 자세한 내용은 [하드웨어 보안 모듈에서 AD RMS 사용](http://technet.microsoft.com/library/jj651024.aspx)을 참조하세요.

두 Azure RMS 테넌트 키 토폴로지 옵션은 Microsoft에서 테넌트 키를 관리하는 방식(**Microsoft 관리**) 또는 사용자가 테넌트 키를 관리하는 방식(**고객 관리**)입니다. 자체 Azure RMS 테넌트 키를 관리할 경우를 BYOK("bring your own key")라고도 하며, Thales의 HSM(하드웨어 보안 모듈)이 필요합니다. 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 항목에서 [테넌트 키 토폴로지 선택: Microsoft가 관리(기본값) 또는 고객이 직접 관리(BYOK)](plan-implement-tenant-key.md#BKMK_ChooseTenantKey) 섹션을 참조하세요.

> [!IMPORTANT]
> Exchange Online은 현재 Azure RMS BYOK와 호환되지 않습니다.  마이그레이션 후에 BYOK를 사용하고 Exchange Online을 사용하려는 경우 이 구성에서 Exchange Online에 대한 IRM 기능이 축소되는 방식을 이해해야 합니다. [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 항목의 [BYOK 가격 및 제한 사항](plan-implement-tenant-key.md#BKMK_Pricing) 섹션에 제공된 정보를 검토하여 마이그레이션에 가장 적합한 Azure RMS 테넌트 키 토폴로지를 선택합니다.

다음 테이블을 사용하여 마이그레이션에 사용할 절차를 식별하세요. 목록에 없는 조합은 지원되지 않습니다.

|현재 AD RMS 배포|선택한 Azure RMS 테넌트 키 토폴로지|마이그레이션 지침|
|-----------------------------|----------------------------------------|--------------------------|
|AD RMS 데이터베이스의 암호 보호|Microsoft 관리|이 표 다음에 나오는 **소프트웨어 보호된 키-소프트웨어 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이것은 가장 간단한 마이그레이션 경로이며, Azure RMS로 구성 데이터를 전송하기만 하면 됩니다.|
|Thales nShield HSM(하드웨어 보안 모듈)을 사용한 HSM 보호|고객 관리(BYOK)|이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 BYOK 도구 집합과, 온-프레미스 HSM의 키를 Azure RMS HSM으로 전송한 다음 구성 데이터를 Azure RMS으로 전송하는 두 단계가 필요합니다.|
|AD RMS 데이터베이스의 암호 보호|고객 관리(BYOK)|이 표 다음에 나오는 **소프트웨어 보호된 키-HSM 보호된 키** 마이그레이션 절차를 참조하세요.<br /><br />이 작업을 위해서는 BYOK 도구 집합과, 소프트웨어 키를 먼저 추출하고 온-프레미스 HSM으로 가져온 다음, 온-프레미스 HSM의 키를 Azure RMS HSM으로 전송하고, 마지막으로 구성 데이터를 Azure RMS로 전송하는 세 단계가 필요합니다.|
|Thales 이외의 공급업체가 제공한 HSM(하드웨어 보안 모듈)을 사용한 HSM 보호|고객 관리(BYOK)|이 HSM에서 Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 HSM 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키 마이그레이션 **절차의 지침을 따르세요.|
|외부 암호화 공급자를 사용하여 암호 보호|고객 관리(BYOK)|Thales nShield HSM(하드웨어 보안 모듈)로 키를 전송하는 방법에 대한 지침은 암호화 공급자의 공급업체에 문의하세요. 그런 다음 이 표 다음에 나오는 **HSM 보호된 키-HSM 보호된 키 마이그레이션 **절차의 지침을 따르세요.|
이러한 절차를 시작하기 전에 트러스트된 게시 도메인을 내보낼 때 만든 .xml 파일에 액세스할 수 있는지 확인하세요. 예를 들어, 이러한 파일은 AD RMS 서버에서 인터넷에 연결된 워크스테이션으로 가져오는 USB 드라이브에 저장되어 있을 수 있습니다.

> [!NOTE]
> 하지만 이 데이터에 개인 키가 포함되어 있으므로 이러한 파일을 저장한 후 최적의 보안 권장 방법으로 파일을 보호합니다.

##### 소프트웨어 보호 키-소프트웨어 보호 키 마이그레이션
이 절차를 사용하여 Azure RMS에 AD RMS 구성을 가져옵니다. 그러면 Microsoft에서 관리하는 Azure RMS 테넌트 키를 만들 수 있습니다.

###### 구성 데이터를 Azure RMS로 가져오려면

1.  인터넷에 연결된 워크스테이션에서 Azure RMS용 Windows PowerShell 모듈(최소 버전 2.1.0.0)을 다운로드한 후 설치합니다. 여기에는 [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) cmdlet이 포함되어 있습니다.

    > [!TIP]
    > 이전에 모듈을 다운로드하여 설치한 경우 다음을 실행하여 버전 번호를 확인합니다. `(Get-Module aadrm -ListAvailable).Version`

    설치 지침은 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

2.  **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작하고, [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) cmdlet을 사용하여 Azure RMS 서비스에 연결합니다.

    ```
    Connect-AadrmService
    ```
    메시지가 표시되면 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).

3.  [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) cmdlet을 사용하여 처음에 내보낸 트러스트된 게시 도메인(.xml) 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure RMS에서 콘텐츠를 보호하는 데 사용할 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    예: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    이전에 지정한 암호를 입력하라는 메시지가 표시되면 입력한 후 이 작업을 수행할 것임을 확인합니다.

4.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 3단계를 반복합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다. 예: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) cmdlet를 사용하여 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration)로 이동할 준비가 되었습니다.

##### HSM 보호 키-HSM 보호 키 마이그레이션:

> [!NOTE]
> 이러한 지침에서는 AD RMS 키가 모듈로 보호되어 있다고 가정합니다. 이것은 일반적인 경우입니다. AD RMS 키가 OCS로 보호되어 있는 경우 이러한 지침을 수행하기 전에 [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key)에 문의하세요.

HSM 키와 AD RMS 구성을 Azure RMS로 가져오는 두 부분으로 된 절차이며, 결과적으로 직접 관리하는 Azure RMS 테넌트 키가 생성됩니다(BYOK).

먼저 Azure RMS로 전송할 수 있도록 HSM 키를 패키지한 다음에 구성 데이터와 함께 가져와야 합니다.

###### 1부: HSM 키를 Azure RMS로 전송할 수 있도록 패키지

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#BKMK_ImplementBYOK) 섹션에 있는 단계를 수행합니다. 다음 경우를 제외하고 **인터넷을 통해 테넌트 키 생성 및 전송** 절차를 따릅니다.

    -   AD RMS 배포에서 생성된 동일한 키가 이미 있으므로 **테넌트 키 생성**단계는 따르지 마세요. Thales 설치의 AD RMS 서버에서 사용되는 키를 식별하고, 마이그레이션 중에 이 키를 사용해야 합니다. Thales 암호화된 키 파일 이름은 일반적으로 서버에서 로컬로 **key_(keyAppName)_(keyIdentifier)**입니다.

    -   Add-AadrmKey 명령을 사용하는 **Azure RMS로 테넌트 키 전송** 단계는 따르지 마세요.  대신 내보낸 트러스트된 게시 도메인을 업로드할 때 Import-AadrmTpd 명령을 사용하여 준비된 HSM 키를 전송합니다.

2.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 Azure RMS 서비스에 다시 연결합니다.

이제 Azure RMS용 HSM 키를 준비했으므로 HSM 키 파일과 AD RMS 구성 데이터를 가져올 수 있습니다.

###### 2부: Azure RMS로 HSM 키 및 구성 데이터 가져오기

1.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 처음에 내보낸 트러스트된 게시 도메인(.xml) 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure RMS에서 콘텐츠를 보호하는 데 사용할 HSM 키에 해당하는 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    예: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    이전에 지정한 암호를 입력하라는 메시지가 표시되면 입력한 후 이 작업을 수행할 것임을 확인합니다.

2.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 1단계를 반복합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다.  예: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet를 사용하여 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration)로 이동할 준비가 되었습니다.

##### 소프트웨어 보호 키-HSM 보호 키 마이그레이션
다음은 Azure RMS에 AD RMS 구성을 가져오기 위한 세 부분으로 구성된 절차로, 이 작업을 수행하면 사용자가 관리하는(BYOK) Azure RMS 테넌트 키를 만들 수 있습니다.

먼저 구성 데이터에서 SLC(서버 사용 허가자 인증서) 키를 추출하여 온-프레미스 Thales HSM에 전송하고, HSM 키를 패키지하고 Azure RMS로 전송한 다음 구성 데이터를 가져와야 합니다.

###### 1부: 구성 데이터에서 SLC를 추출하고 온-프레미스 HSM으로 키 가져오기

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 항목의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#BKMK_ImplementBYOK) 섹션에 있는 다음 단계를 수행합니다.

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **인터넷에 연결된 워크스테이션 준비**

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **연결이 끊어진 워크스테이션 준비**

    내보낸 구성 데이터(.xml) 파일에 테넌트 키가 이미 있으므로, 테넌트 키를 생성하는 단계는 수행하지 않도록 합니다. 대신 파일에서 이 키를 추출한 후 온-프레미스 HSM으로 가져오는 명령을 실행합니다.

2.  연결이 끊어진 워크스테이션에서는 다음 명령을 실행합니다.

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    예를 들어 북미의 경우: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    추가 정보:

    -   ImportRmsCentrallyManagedKey 매개 변수는 이 작업이 SLC 키를 가져오는 작업임을 나타냅니다.

    -   명령에 암호를 지정하지 않으면 지정하라는 메시지가 표시됩니다.

    -   KeyIdentifier 매개 변수는 키 파일 이름을 만드는 키 이름을 나타냅니다. ASCII 소문자만 사용해야 합니다.

    -   ExchangeKeyPackage 매개 변수는 이름이 BYOK-KEK-pkg-로 시작하는 지역별 KEK(키 교환 키) 패키지를 지정합니다.

    -   NewSecurityWorldPackage 매개 변수는 이름이 BYOK-SecurityWorld-pkg-로 시작하는 지역별 보안 권역 패키지를 지정합니다.

    이 명령을 수행하면 다음 결과가 발생합니다.

    -   HSM 키 파일: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   SLC가 제거된 RMS 구성 데이터 파일: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml

3.  둘 이상의 RMS 구성 데이터 파일이 있는 경우 나머지 파일에 대해 2단계를 반복합니다.

HSM 기반 키로 사용할 수 있도록 SLC를 추출했으므로, 이 키를 패키지한 후 Azure RMS에 전송할 수 있습니다.

###### 2부: HSM 키를 패키지한 후 Azure RMS로 전송

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#BKMK_ImplementBYOK) 섹션에 있는 다음 단계를 수행합니다.

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **테넌트 키 전송 준비**

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **Azure RMS로 테넌트 키 전송**

HSM 키를 Azure RMS에 전송했으므로, 새로 전송된 테넌트 키에 대한 포인터만 포함된 AD RMS 구성 데이터를 가져올 준비가 된 것입니다.

###### 3부: 구성 데이터를 Azure RMS로 가져오기

1.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 SLC가 제거된 RMS 구성 파일을 복사합니다(연결이 끊어진 워크스테이션의 경우 %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml).

2.  첫 번째 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure RMS에서 콘텐츠를 보호하는 데 사용할 HSM 키에 해당하는 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    예: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    이전에 지정한 암호를 입력하라는 메시지가 표시되면 입력한 후 이 작업을 수행할 것임을 확인합니다.

3.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 2단계를 반복합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다. 예: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet를 사용하여 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration)로 이동할 준비가 되었습니다.

### <a name="BKMK_Step3Migration"></a>3단계. RMS 테넌트 활성화
이 단계에 대한 지침은 [Azure 권한 관리 활성화](activate-service.md) 항목에 자세히 나와 있습니다.

> [!TIP]
> Office 365 구독이 있는 경우 Office 365 관리 센터 또는 Azure 클래식 포털에서 Azure RMS를 활성화할 수 있습니다. 이 관리 포털을 사용하여 다음 단계를 완료하게 되므로 Azure 클래식 포털을 사용하는 것이 좋습니다.

**Azure RMS 테넌트가 이미 활성화되어 있으면 어떻게 되나요?** 조직에 대해 Azure RMS 서비스가 이미 활성화된 경우 사용자는 이미 Azure RMS를 사용하여 AD RMS의 기존 키(및 템플릿) 대신 자동으로 생성된 테넌트 키(및 기본 템플릿)로 콘텐츠를 보호하고 있을 수 있습니다. 인트라넷에서 잘 관리되는 컴퓨터는 AD RMS 인프라에 대해 자동으로 구성되므로 여기에 해당되지 않을 수 있습니다. 하지만 작업 그룹 컴퓨터 또는 인트라넷에 자주 연결되지 않는 컴퓨터는 여기에 해당될 수 있습니다. 아쉽게도 이러한 컴퓨터를 식별하는 것은 어려운 일이므로 AD RMS에서 구성 데이터를 가져오기 전에 서비스를 활성화하지 않는 것이 좋습니다.

5단계에서 설명한 대로 Azure RMS 테넌트가 이미 활성화되어 있고 이러한 컴퓨터를 식별할 수 있으면 이러한 컴퓨터에서 CleanUpRMS_RUN_Elevated.cmd 스크립트를 실행해야 합니다. 이 스크립트를 실행하면 사용자 환경이 강제로 다시 초기화되므로 업데이트된 테넌트 키와 가져온 템플릿을 다운로드합니다.

### <a name="BKMK_Step4Migration"></a>4단계. 가져온 템플릿 구성
가져온 템플릿의 기본 상태는 **보관됨**이므로 사용자가 Azure RMS에서 이러한 템플릿을 사용할 수 있도록 하려면 이 상태를 **게시됨** 으로 변경해야 합니다.

또한 AD RMS의 템플릿이 **ANYONE** 그룹을 사용하는 경우 이 그룹은 Azure RMS에 템플릿을 가져올 때 자동으로 제거됩니다. 따라서 가져온 템플릿에 해당 그룹 또는 사용자와 동일한 권한을 수동으로 추가해야 합니다. Azure RMS에 해당하는 그룹의 이름은 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<tenant_name>.onmicrosoft.com**입니다. 예를 들어 Contoso에 대한 이 그룹은 **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**과 같을 수 있습니다.

AD RMS 템플릿에 ANYONE 그룹이 포함되어 있는지 여부가 확실하지 않은 경우 이 단계의 [ANYONE 그룹을 포함하는 AD RMS 템플릿을 식별하기 위한 샘플 Windows PowerShell 스크립트](#BKMK_ScriptForANYONE) 섹션을 확장하고 샘플 PowerShell 스크립트를 복사 및 사용하여 이러한 템플릿을 식별할 수 있습니다. AD RMS와 함께 Windows PowerShell을 사용하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 AD RMS 관리](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx)를 참조하세요.

Azure 클래식 포털에서 기본 권한 정책 템플릿 중 하나를 복사하고 **권한** 페이지에서 **사용자 이름**을 확인하면 조직에서 자동으로 생성된 그룹을 볼 수 있습니다. 그러나 Azure 클래식 포털을 사용하여 이 그룹을 수동으로 만들거나 가져온 템플릿에 추가할 수는 없습니다. 대신에 다음과 같은 Azure RMS PowerShell 옵션 중 하나를 사용해야 합니다.

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell cmdlet을 사용하여 "AllStaff" 그룹 및 권한을 권한 정의 개체로 정의하고, ANYONE 그룹 외에도 원래 템플릿의 각 그룹 또는 권한이 이미 부여된 사용자에 대해 이 명령을 다시 실행합니다. 그런 다음 [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) cmdlet을 사용하여 이러한 모든 권한 정의 개체를 템플릿에 추가합니다.

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) cmdlet을 사용하여 "AllStaff" 그룹 및 권한을 기존 그룹 및 권한에 추가할 수 있도록 편집할 수 있는 .XML 파일에 템플릿을 내보낸 다음 [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) cmdlet을 사용하여 이 변경 내용을 Azure RMS로 다시 가져옵니다.

> [!NOTE]
> "AllStaff"의 이러한 동등한 그룹이 AD RMS의 ANYONE 그룹과 정확히 동일하지는 않습니다. "AllStaff" 그룹에는 Azure 테넌트의 모든 사용자가 포함되지만 ANYONE 그룹에는 조직의 외부에 있을 수 있는 인증된 모든 사용자가 포함됩니다.
> 
> 두 그룹 간의 이러한 차이 때문에 "AllStaff" 그룹뿐 아니라 외부 사용자도 추가해야 할 수 있습니다. 그룹에 대한 외부 전자 메일 주소는 현재 지원되지 않습니다.

AD RMS에서 가져오는 템플릿은 Azure 클래식 포털에서 만들 수 있는 사용자 지정 템플릿과 모양 및 동작이 유사합니다. 사용자가 응용 프로그램에서 보고 선택할 수 있도록 가져온 템플릿을 게시되도록 변경하거나 다르게 변경하려면 [Azure 권한 관리용 사용자 지정 템플릿 구성](configure-custom-templates.md)을 참조하세요.

> [!TIP]
> 마이그레이션 프로세스 중에 사용자에게 보다 일관된 환경을 제공하려면, 이러한 두 가지 변경 외에는 가져온 템플릿을 변경하지 않도록 하고 Azure RMS와 함께 제공된 2개의 기본 템플릿을 게시하거나 새 템플릿을 만들지 않도록 합니다. 대신 마이그레이션 프로세스가 완료되고 AD RMS 서버를 서비스 해제할 때까지 기다립니다.

#### <a name="BKMK_ScriptForANYONE"></a>ANYONE 그룹을 포함하는 AD RMS 템플릿을 식별하기 위한 샘플 Windows PowerShell 스크립트
이 섹션에는 이전 섹션에서 설명한 것과 같이 정의된 ANYONE 그룹이 있는 AD RMS 템플릿을 식별하는 데 도움이 되는 샘플 스크립트가 포함되어 있습니다.

**고지 사항:** 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.*

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>5단계. Azure RMS를 사용하도록 클라이언트 다시 구성
Windows 클라이언트:

1.  [마이그레이션 스크립트를 다운로드](http://go.microsoft.com/fwlink/?LinkId=524619)합니다.

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    이러한 스크립트는 AD RMS 보다는 Azure RMS 서비스를 사용하도록 Windows 컴퓨터에서 구성을 다시 설정합니다.

2.  리디렉션 스크립트(Redirect_OnPrem.cmd)의 지침에 따라 새 Azure RMS 테넌트를 가리키도록 스크립트를 수정합니다.

3.  Windows 컴퓨터에서는 사용자의 컨텍스트에서 상승된 권한으로 이러한 스크립트를 실행합니다.

모바일 장치 클라이언트 및 Mac 컴퓨터:

-   [AD RMS 모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포할 때 만든 DNS SRV 레코드를 제거합니다.

#### 마이그레이션 스크립트로 인한 변경 내용
이 섹션에서는 마이그레이션 스크립트로 인한 변경 내용을 설명합니다. 이 정보는 참조용으로만 또는 문제 해결을 위해 사용할 수 있고, 직접 변경을 수행하려는 경우에 참조할 수 있습니다.

CleanUpRMS_RUN_Elevated.cmd:

-   긴 파일 이름을 포함하는 하위 폴더 및 파일을 비롯하여, %userprofile%\AppData\Local\Microsoft\DRM 및 %userprofile%\AppData\Local\Microsoft\MSIPC 폴더의 내용을 삭제합니다.

-   다음 레지스트리 키의 내용을 삭제합니다.

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   다음 레지스트리 값을 삭제합니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   다음의 각 위치에서 매개 변수로 제공된 각 URL에 대해 다음의 레지스트리 값을 만듭니다.

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    각 항목에는 **https://&lt;YourTenantURL&gt;/_wmcs/licensing** 형식의 데이터를 포함하는 REG_SZ 값 **https://OldRMSserverURL/_wmcs/licensing**이 있습니다.

    > [!NOTE]
    > &lt;YourTenantURL&gt;의 형식은 다음과 같습니다. **{GUID}.rms.[Region].aadrm.com**.
    > 
    > 예: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Azure RMS에 대해 **Get-AadrmConfiguration** cmdlet를 실행하는 경우 [RightsManagementServiceId](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) 값을 식별하여 이 값을 찾을 수 있습니다.

### <a name="BKMK_Step6Migration"></a>6단계. Exchange Online에 대한 IRM 통합 구성
이전에 AD RMS에서 Exchange Online으로 TDP를 가져온 경우 Azure RMS로 마이그레이션한 후에 템플릿 및 정책 충돌을 방지하기 위해 이 TDP를 제거해야 합니다. 이렇게 하려면 Exchange Online에서 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) cmdlet을 사용합니다.

Azure RMS 테넌트 키 토폴로지로 **Microsoft 관리**를 선택한 경우

-   [Azure 권한 관리에 대해 응용 프로그램 구성](configure-applications.md) 항목에서 [Exchange Online: IRM 구성](configure-applications.md#BKMK_ExchangeOnline) 섹션을 참조하세요. 이 섹션에는 Exchange Online 서비스에 연결하고, Azure RMS에서 테넌트 키를 가져오고, Exchange Online에 대해 IRM 기능을 사용하도록 설정하는 일반적인 명령이 포함되어 있습니다. 이러한 단계를 완료한 후에 Exchange Online에서 전체 RMS 기능을 사용할 수 있게 됩니다.

Azure RMS 테넌트 키 토폴로지로 **고객 관리(BYOK)**를 선택한 경우

-   [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 항목의 [BYOK 가격 및 제한 사항](plan-implement-tenant-key.md#BKMK_Pricing) 섹션에 설명된 대로 Exchange Online에서 사용할 수 있는 RMS 기능이 줄어듭니다.

### <a name="BKMK_Step7Migration"></a>7단계. RMS 커넥터 배포
AD RMS에서 Exchange Server 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우 먼저 이러한 서버에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성을 제거해야 합니다. 그런 다음 온-프레미스 서버와 Azure RMS 간에 통신 인터페이스(릴레이) 역할을 하는 RMS(권한 관리) 커넥터를 배포합니다.

이 단계를 위해 마지막으로, 여러 TPD를 메일 메시지를 보호하는 데 사용된 Azure RMS로 가져온 경우 모든 TPD URL을 RMS 커넥터로 리디렉션하도록 Exchange Server 컴퓨터의 레지스트리를 수동으로 편집해야 합니다.

> [!NOTE]
> 시작하기 전에 [Azure 권한 관리 요구 사항](requirements-azure-rms.md) 항목의 [Azure RMS를 지원하는 응용 프로그램](requirements-azure-rms.md#BKMK_SupportedApplications) 섹션에 있는 "Azure RMS를 지원하는 온-프레미스 서버"에서 RMS 커넥터가 지원하는 온-프레미스 서버 버전을 확인합니다.

##### Exchange Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  각 Exchange Server에서 다음 폴더를 찾아 해당 폴더의 항목을 모두 삭제합니다. \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Exchange Server 중 하나에서 Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) cmdlet를 사용하여 내부의 받는 사람에게 전송되는 메시지에 대한 IRM 기능을 사용하지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  그런 후 동일한 cmdlet를 사용하여 외부의 받는 사람에게 전송되는 메시지에 대해 IRM 기능이 사용되지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  다음에는 동일한 cmdlet를 사용하여 Microsoft Office Outlook Web App 및 Microsoft Exchange ActiveSync에서 IRM이 사용되지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  마지막으로 동일한 cmdlet를 사용하여 캐시된 모든 인증서를 지웁니다.

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  예를 들어 각 Exchange Server에서 관리자 권한으로 명령 프롬프트를 실행하고 **iisreset**을 입력하여 IIS를 초기화합니다.

##### SharePoint Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  RMS로 보호된 라이브러리에서 체크 아웃된 문서가 없는지 확인합니다. 체크 아웃된 문서가 있는 경우 이 절차가 끝나면 액세스할 수 없게 됩니다.

2.  Sharepoint 중앙 관리 웹 사이트의 **빠른 실행** 섹션에서 **보안**을 클릭합니다.

3.  **보안** 페이지의 **정보 정책** 섹션에서 **정보 권한 관리 구성**을 클릭합니다.

4.  **정보 권한 관리** 페이지의 **정보 권한 관리** 섹션에서 **이 서버에서 IRM 사용 안 함**을 선택하고 **확인**을 클릭합니다.

5.  각 SharePoint Server 컴퓨터에서 \ProgramData\Microsoft\MSIPC\Server\*&lt;SharePoint Server를 실행하는 계정의 SID&gt;* 폴더의 내용을 삭제합니다.

##### RMS 커넥터 설치 및 구성

-   [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md) 항목의 지침을 따릅니다.

##### Exchange만 및 여러 TPD: 레지스트리 편집

-   각 Exchange Server에서 가져온 각 추가 TPD에 대해 다음 레지스트리 키를 수동으로 추가하여 TPD URL을 RMS 커넥터로 리디렉션합니다. 이러한 레지스트리 항목은 마이그레이션에만 관련되며 Microsoft RMS 커넥터용 서버 구성 도구를 통해 추가되지 않습니다.

    이와 같이 레지스트리를 편집할 때는 다음 지침을 따르세요.

    -   ConnectorFQDN 을 DNS에서 커넥터에 대해 정의한 이름으로 바꿉니다. **rmsconnector.contoso.com**을 예로 들 수 있습니다.

    -   온-프레미스 서버와 통신하는 데 HTTP 또는 HTTPS 중 어느 것을 사용하도록 커넥터를 구성했는지에 따라 커넥터 URL에 대해 HTTP 또는 HTTPS 접두사를 사용합니다.

    **Exchange 2013:**

    |레지스트리 경로|Type|값|Data|
    |-----------------|--------|---------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 인트라넷 라이선스 URL&gt;/_wmcs/licensing|Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:<br /><br />http://&lt;connectorFQDN&gt;/_wmcs/licensing<br /><br />https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 엑스트라넷 라이선스 URL&gt;/_wmcs/licensing|Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:<br /><br />http://&lt;connectorFQDN&gt;/_wmcs/licensing<br /><br />https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **Exchange Server 2010:**

    |레지스트리 경로|Type|값|Data|
    |-----------------|--------|---------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 인트라넷 라이선스 URL&gt;/_wmcs/licensing|Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:<br /><br />http://&lt;connectorName&gt;/_wmcs/licensing<br /><br />https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 엑스트라넷 라이선스 URL&gt;/_wmcs/licensing|Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:<br /><br />http://&lt;connectorName&gt;/_wmcs/licensing<br /><br />https://&lt;connectorName&gt;/_wmcs/licensing|

이러한 절차를 완료했으면 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md) 항목에서 **다음 단계** 섹션을 읽어야 합니다.

### <a name="BKMK_Step8Migration"></a>8단계: AD RMS 서비스 해제
선택 사항: 온-프레미스 권한 관리 인프라에서 컴퓨터를 검색하지 못하게 하려면 Active Directory에서 SCP(서비스 연결 지점)를 제거합니다. 이는 레지스트리에서 마이그레이션 스크립트를 실행하는 등의 방법으로 구성한 리디렉션이므로 선택 사항입니다. 서비스 연결 지점을 제거하려면 [Rights Management Services 관리 도구 키트](http://www.microsoft.com/download/details.aspx?id=1479)의 AD SCP 레지스터 도구를 사용합니다.

[시스템 상태 보고서의 요청](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [ServiceRequest 테이블](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx), [보호된 콘텐츠에 대한 사용자 액세스 감사](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx) 등을 확인하여 AD RMS 서버에서 활동을 모니터링합니다. RMS 클라이언트가 이러한 서버와 더 이상 통신하지 않으며 클라이언트가 Azure RMS를 성공적으로 사용하고 있는지 확인한 다음, 이러한 서버에서 AD RMS 서버 역할을 제거할 수 있습니다. 전용 서버를 사용하는 경우, 일정 기간 동안 서버를 종료한 후 이러한 서버를 다시 시작해야 하는 문제가 보고되지 않았는지 확인하는 준비 단계를 거쳐 클라이언트가 Azure RMS를 사용하지 않는 이유를 조사할 때 서비스가 중단되지 않도록 할 수 있습니다.

AD RMS 서버를 서비스 해제한 후에는 Azure 클래식 포털에서 템플릿을 검토하고 통합하여 사용자가 보다 적은 수의 템플릿 중에서 선택하거나, 템플릿을 다시 구성하거나, 새 템플릿을 추가할 기회를 제공할 수 있습니다. 이때 기본 템플릿을 게시하는 것도 좋습니다. 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](configure-custom-templates.md)을 참조하세요.

### <a name="BKMK_Step9Migration"></a>9단계: Azure RMS 테넌트 키 다시 입력
이 단계는 AD RMS 배포에서 RMS 암호화 모드 1을 사용한 경우 마이그레이션이 완료되었을 때 필요합니다. 키를 다시 입력하면 RMS 암호화 모드 2를 사용하는 새 테넌트 키가 생성되기 때문입니다. 암호화 모드 1에서 Azure RMS를 사용하는 방식은 마이그레이션 프로세스 중에만 지원됩니다.

이 단계는 선택 사항이지만, RMS 암호화 모드 2에서 실행한 경우 마이그레이션이 완료되었을 때 권장됩니다. 잠재적인 보안 위반으로부터 Azure RMS 테넌트 키를 보호하는 데 도움이 되기 때문입니다. Azure RMS 테넌트 키를 다시 입력하면("키 롤링"이라고도 함) 새 키가 만들어지고 원래 키는 보관됩니다. 하지만 한 키에서 다른 키로 바로 이동되지 않고 몇 주 이상이 걸립니다. 따라서 원래 키에 대해 의심스러운 위반이 발생할 때까지 기다리지 말고, 마이그레이션이 완료되는 즉시 RMS 테넌트 키를 다시 입력합니다.

Azure RMS 테넌트 키를 다시 입력하려면

-   RMS 테넌트 키를 Microsoft에서 관리하는 경우: Microsoft CSS(고객 지원 서비스)에 전화하여 본인이 RMS 테넌트 관리자임을 입증합니다.

-   RMS 테넌트 키를 사용자가 직접 관리하는 경우(BYOK): BYOK 절차를 반복하여 인터넷을 통해 또는 직접 새 키를 생성하고 만듭니다.

RMS 테넌트 키 관리에 대한 자세한 내용은 [Azure 권한 관리 테넌트 키에 대한 작업](operations-tenant-key.md)을 참조하세요.

## 참고 항목
[Azure Rights Management 구성](configuring-azure-rights-management.md)



<!--HONumber=Apr16_HO3-->


