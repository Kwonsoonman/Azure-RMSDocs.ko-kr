---
# required metadata

title: Azure 권한 관리 테넌트 키 계획 및 구현 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리 테넌트 키 계획 및 구현

*적용 대상: Azure 권한 관리, Office 365*

이 문서의 정보는 Azure RMS용 권한 관리(RMS) 테넌트 키를 계획 및 관리하는 데 도움이 됩니다. 예를 들어 Microsoft에서 테넌트 키(기본값)를 관리하는 대신, 조직에 적용되는 특정 규정을 준수하도록 자체 테넌트 키를 관리하려고 할 수 있습니다.  자체 테넌트 키를 관리하는 것을 BYOK(bring your own key)라고도 합니다.

> [!NOTE]
> RMS 테넌트 키는 SLC(서버 사용 허가자 인증서) 키라고도 합니다. Azure RMS는 Azure RMS를 구독하는 각 조직에 대해 하나 이상의 키를 유지 관리합니다. 조직 내에서 키가 RMS에 사용될 때마다(예: 사용자 키, 컴퓨터 키, 문서 암호화 키), 이러한 키는 RMS 테넌트 키에 암호화 방식으로 체이닝됩니다.

**한 눈에 보기:** 다음 표를 참조하여 권장되는 테넌트 키 토폴로지를 빠르게 확인할 수 있습니다. 자세한 내용은 추가 설명서를 참조하세요.

Microsoft에서 관리하는 테넌트 키를 사용하여 Azure RMS를 배포하는 경우 나중에 BYOK로 변경할 수 있습니다. 그러나 현재는 Azure RMS 테넌트 키를 BYOK에서 Microsoft 관리 유형으로 변경할 수 없습니다.

|비즈니스 요구 사항|권장되는 테넌트 키 토폴로지|
|------------------------|-----------------------------------|
|특수한 하드웨어 필요 없이 신속하게 Azure RMS 배포|Microsoft에서 관리|
|Azure RMS가 있는 Exchange Online에서 전체 IRM 기능 필요|Microsoft에서 관리|
|사용자가 생성한 키를 HSM(하드웨어 보안 모듈)에서 보호|BYOK<br /><br />현재 이 구성을 사용하면 Exchange Online에서 IRM 기능이 축소됩니다. 자세한 내용은 [BYOK 가격 및 제한 사항](byok-price-restrictions.md)을 참조하세요.|

## 테넌트 키 토폴로지 선택: Microsoft가 관리(기본값) 또는 고객이 직접 관리(BYOK)
조직에 가장 적합한 테넌트 키 토폴로지를 결정하세요. 기본적으로 Azure RMS는 고객의 테넌트 키를 생성하고 테넌트 키 수명 주기의 대부분의 측면을 관리합니다. 이 옵션은 관리 오버헤드가 가장 낮은 가장 간단한 옵션입니다. 대부분의 경우 고객은 테넌트 키를 가지고 있다는 사실조차 알 필요가 없습니다. Azure RMS에 등록하기만 하면 나머지 키 관리 프로세스는 Microsoft에서 처리합니다.

또는 테넌트 키를 만들고 고객의 프레미스에 마스터 복사본을 유지하는 등 테넌트 키를 완전히 제어하기를 원할 수도 있습니다. 이 시나리오를 흔히 BYOK(Bring Your Own Key)라고 합니다. 이 옵션을 사용할 경우 다음과 같은 상황이 발생합니다.

1.  고객이 IT 정책에 따라 고객의 프레미스에서 테넌트 키를 생성합니다.

2.  고객 소유의 HSM(하드웨어 보안 모듈)에서 Microsoft가 소유하고 관리하는 HSM으로 테넌트 키를 안전하게 전송합니다. 이 프로세스 전체에서 테넌트 키는 하드웨어 보호 경계를 벗어나지 않습니다.

3.  테넌트 키를 Microsoft로 전송할 때 테넌트 키는 Thales HSM으로 보호됩니다. Microsoft는 Thales와 협력하여 고객의 테넌트 키가 Microsoft HSM에서 추출될 수 없도록 했습니다.

선택 사항이기는 하지만 테넌트 키가 언제, 어떻게 사용되는지를 정확하게 확인하기 위해 Azure RMS의 근 실시간 사용 현황 로그를 사용하기를 원할 수도 있습니다.

> [!NOTE]
> 추가 보호 조치로 Azure RMS에서는 북아메리카, EMEA(유럽, 중동 및 아시아) 및 아시아의 데이터 센터에 별도의 보안 권역을 사용합니다. 고객의 고유 테넌트 키를 관리할 때 이 키는 고객의 RMS 테넌트가 등록된 지역의 보안 권역에 연결됩니다. 예를 들어 유럽 고객의 테넌트 키를 북아메리카 또는 아시아의 데이터 센터에서 사용할 수 없습니다.

## 테넌트 키 수명 주기
고객이 Microsoft가 고객의 테넌트 키를 관리해야 한다고 결정한 경우 Microsoft는 대부분의 키 수명 주기 작업을 처리합니다. 그러나 고객이 직접 테넌트 키를 관리하기로 결정한 경우 키 수명 주기 작업의 많은 부분과 일부 추가 절차는 고객의 책임입니다.

다음 다이어그램은 이러한 두 옵션을 비교해서 보여줍니다. 첫 번째 다이어그램은 Microsoft가 테넌트 키를 관리하는 기본 구성을 사용할 경우 관리자 오버헤드가 얼마나 작은지 보여줍니다.

![Azure RMS 테넌트 키 수명 주기- Microsoft에서 관리, 기본값](../media/RMS_BYOK_cloud.png)

두 번째 다이어그램은 고객이 직접 테넌트 키를 관리할 경우 필요한 추가 단계를 보여줍니다.

![Azure RMS 테넌트 키 수명 주기 - 사용자가 직접 관리, BYOK](../media/RMS_BYOK_onprem.png)

고객이 Microsoft에서 테넌트 키를 관리하도록 결정할 경우 키를 생성하기 위해 수행해야 할 추가 작업이 없으므로 [다음 단계](plan-implement-tenant-key.md#next-steps)로 바로 이동하세요.

테넌트 키를 직접 관리하기로 결정한 경우 다음 섹션에서 자세한 내용을 확인하세요.

## Azure 권한 관리 테넌트 키 구현

직접 테넌트 키를 생성하고 관리하기로 결정한 경우(BYOK(Bring Your Own Key) 시나리오) 이 섹션의 정보 및 절차를 사용하세요.


> [!IMPORTANT]
> 이미 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]를 사용하기 시작(서비스가 활성화됨)했으며 Office 2010을 실행하는 사용자가 있는 경우 이러한 절차를 실행하기 전에 Microsoft CSS(고객 지원 서비스)에 문의하세요. 시나리오 및 요구 사항에 따라 계속해서 BYOK를 사용할 수 있지만 몇 가지 제한 사항이나 추가 단계가 수반될 수 있습니다.
> 
> 조직에 키 처리에 대한 특정 정책이 있는 경우에도 CSS에 문의하세요.

### BYOK 사전 요구 사항
BYOK(Bring Your Own Key) 사전 요구 사항 목록은 다음 표를 참조하세요.

|요구 사항|추가 정보|
|---------------|--------------------|
|Azure RMS를 지원하는 구독|사용 가능한 구독에 대한 자세한 내용은 [Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.|
|개인용 또는 Exchange Online용으로 RMS를 사용하지 않도록 합니다. 또는 Exchange Online을 사용하는 경우 이 구성에서 BYOK를 사용할 때의 제한 사항을 이해하고 받아들여야 합니다.|BYOK와 관련된 현재 제한 사항에 대한 자세한 내용은 [BYOK 가격 및 제한 사항](byok-price-restrictions.md)을 참조하세요.<br /><br />**중요**: 현재 BYOK는 Exchange Online과 호환되지 않습니다.|
|Thales HSM, 스마트 카드 및 지원 소프트웨어<br /><br />**참고**: 소프트웨어 키-하드웨어 키를 사용하여 AD RMS에서 Azure RMS로 마이그레이션하는 경우 11.62 버전 이상의 Thales 드라이버가 있어야 합니다.|Thales 하드웨어 보안 모듈에 대한 액세스 권한이 있어야 하며 Thales HSM의 기본적인 작동 지식이 있어야 합니다. 호환되는 모델 목록을 확인하거나 HSM이 없는 경우 구입하려면 [Thales 하드웨어 보안 모듈](http://www.thales-esecurity.com/msrms/buy) 을 참조하세요.|
|실제로 미국 Redmond에 가지 않고 인터넷을 통해 테넌트 키를 전송하려는 경우 다음 세 가지 요구 사항이 있습니다.<br /><br />1: 최소 Windows 운영 체제가 Windows 7이고 Thales nShield 소프트웨어 버전이 11.62 이상인 오프라인 x64 워크스테이션<br /><br />이 워크스테이션이 Windows 7을 실행하는 경우 [Microsoft .NET Framework 4.5를 설치](http://go.microsoft.com/fwlink/?LinkId=225702)해야 합니다.<br /><br />2: 인터넷에 연결되어 있고 최소 Windows 운영 체제가 Windows 7인 워크스테이션<br /><br />3: 사용 가능한 공간이 16MB 이상인 USB 드라이브 또는 기타 휴대용 저장 장치|이러한 사전 요구 사항은 Redmond로 가서 직접 테넌트 키를 전송하는 경우에는 불필요합니다.<br /><br />보안상의 이유로 첫 번째 워크스테이션은 네트워크에 연결하지 않는 것이 좋습니다. 그러나 이러한 사항이 프로그래밍 방식으로 강제 적용되지는 않습니다.<br /><br />참고: 뒤에 나오는 지침에서 이 첫 번째 워크스테이션을 **연결이 끊어진 워크스테이션**이라고 합니다.<br /><br />또한 테넌트 키가 프로덕션 네트워크용인 경우 도구 집합을 다운로드하고 테넌트 키를 업로드하는 데는 별도의 두 번째 워크스테이션을 사용하는 것이 좋습니다. 그러나 테스트 목적으로는 첫 번째 워크스테이션과 동일한 워크스테이션을 사용할 수 있습니다.<br /><br />참고: 뒤에 나오는 지침에서 이 두 번째 워크스테이션을 **인터넷에 연결된 워크스테이션**이라고 합니다.|

테넌트 키를 생성 및 사용하는 절차는 인터넷을 통해 할 것인지, 직접 할 것인지에 따라 다릅니다.

-   **인터넷을 통해 생성 및 사용하는 경우:** 이 경우에는 도구 집합 및 Windows PowerShell cmdlet 다운로드 및 사용과 같은 몇 가지 추가 구성 단계가 필요합니다. 그러나 테넌트 키를 전송하기 위해 실제로 Microsoft 본사에 갈 필요는 없습니다. 보안은 다음과 같은 방법으로 유지 관리됩니다.

    -   오프라인 워크스테이션에서 테넌트 키를 생성합니다. 그러면 공격에 대한 취약성이 감소합니다.

    -   테넌트 키가 KEK(키 교환 키)로 암호화됩니다. 그러면 테넌트 키가 Azure RMS HSM으로 전송될 때까지 암호화 상태를 유지합니다. 테넌트 키의 암호화된 버전만 원래 워크스테이션을 벗어납니다.

    -   도구 집합은 테넌트 키를 Azure RMS 보안 권역에 바인딩하는 속성을 테넌트 키에 설정합니다. 따라서 Azure RMS HSM에서 테넌트 키를 받아 암호를 해독한 후에만 이러한 HSM에서 테넌트 키를 사용할 수 있습니다. 테넌트 키를 내보낼 수 없습니다. 이 바인딩은 Thales HSM에서 강제 적용합니다.

    -   테넌트 키를 암호화하는 데 사용되는 KEK(키 교환 키)는 Azure RMS HSM 내부에서 생성되며 내보낼 수 없습니다. HSM은 HSM 외부에 KEK의 일반 버전이 있을 수 없도록 합니다. 또한 이 도구 집합에는 KEK를 내보내는 것이 불가능하고 KEK가 Thales에서 제조한 정품 HSM 내부에서 생성되었음을 나타내는 Thales로부터의 증명이 포함되어 있습니다.

    -   이 도구 집합에는 Azure RMS 보안 권역도 Thales에서 제조한 정품 HSM에서 생성되었음을 나타내는 Thales로부터의 증명이 포함되어 있습니다. 이는 Microsoft가 정품 하드웨어를 사용 중임을 고객에게 증명합니다.

    -   Microsoft에서는 각 지역에 별도의 보안 권역뿐만 아니라 별도의 KEK를 사용하여 테넌트 키가 암호화된 지역의 데이터 센터에서만 사용될 수 있도록 합니다. 예를 들어 유럽 고객의 테넌트 키를 북아메리카 또는 아시아의 데이터 센터에서 사용할 수 없습니다.

    > [!NOTE]
    > 테넌트 키는 암호화되고 액세스 제어 수준 권한(Azure RMS의 고객 HSM 및 Microsoft HSM 내에서만 사용 가능)으로 보호되기 때문에 신뢰할 수 없는 컴퓨터를 안전하게 이동할 수 있습니다. 도구 집합에 제공된 스크립트를 사용하여 보안 조치를 확인하고 Thales의 [RMS 클라우드의 하드웨어 키 관리](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud)에서 도구 집합이 작동하는 방식에 대한 자세한 내용을 살펴볼 수 있습니다.

-   **직접 생성 및 사용하는 경우:** 이 경우에는 Microsoft CSS(고객 지원 서비스)에 문의하여 Azure RMS의 키 전송 약속을 예약해야 합니다. 테넌트 키를 Azure RMS 보안 권역으로 전송하려면 미국 워싱턴주의 Redmond에 있는 Microsoft 본사로 가야 합니다.

방법 지침을 보려면 인터넷을 통해 테넌트 키를 생성 및 전송할지, 아니면 직접 생성 및 전송할지를 선택합니다. 

- [인터넷을 통해 생성 및 전송하는 경우](generate-tenant-key-internet.md)
- [직접 생성 및 전송하는 경우](generate-tenant-key-in-person.md)


## 다음 단계

이제 테넌트 키를 계획하고 필요한 경우 생성했으므로 다음을 수행합니다.

1.  테넌트 키 사용을 시작합니다.

    -   아직 Rights Management를 활성화하지 않은 경우 조직에서 RMS 사용을 시작할 수 있도록 Rights Management를 활성화해야 합니다. 사용자는 즉시 테넌트 키(Microsoft에서 관리하거나 고객이 직접 관리함) 사용을 시작합니다.

        활성화에 대한 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.

    -   이미 Rights Management를 활성화한 후 직접 테넌트 키를 관리하기로 결정한 경우 사용자는 점진적으로 이전 테넌트 키에서 새 테넌트 키로 전환하며, 시차를 두고 진행되는 이 전환이 완료되기까지 몇 주가 걸릴 수 있습니다. 권한 있는 사용자는 이전 테넌트 키로 보호된 문서와 파일에 계속 액세스할 수 있습니다.

2.  RMS가 수행하는 모든 트랜잭션을 기록하는 사용 현황 로깅을 사용하는 것이 좋습니다.

    직접 테넌트 키를 관리하기로 결정한 경우 로깅에는 테넌트 키 사용에 대한 정보가 포함됩니다. Excel에 표시된 다음과 같은 로그 파일 예를 참조하세요. 여기서 **Decrypt** 및 **SignDigest** 요청 유형은 테넌트 키가 사용되고 있음을 보여줍니다.

    ![테넌트 키가 사용되는 위치의 로그 파일](../media/RMS_Logging.gif)

    사용 현황 로깅에 대한 자세한 내용은 [Azure 권한 관리 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.

3.  테넌트 키를 유지 관리합니다.

    자세한 내용은 [Azure 권한 관리 테넌트 키에 대한 작업](../deploy-use/operations-tenant-key.md)을 참조하세요.



<!--HONumber=May16_HO3-->


