---
# required metadata

title: Azure 권한 관리 배포 로드맵 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리 배포 로드맵
다음 단계에 따라 조직에 대해 Azure RMS(Azure 권한 관리)를 준비, 구현 및 관리합니다.

그러나 프로덕션 환경에서 롤아웃하지 않고 직접Azure RMS를 빠르게 시도하려는 경우 [Azure 권한 관리에 대한 빠른 시작 자습서](../get-started/quick-start-tutorial.md)를 참조하세요.

> [!IMPORTANT]
> 다음 단계를 수행하기 전에 [Azure 권한 관리 요구 사항](../get-started/requirements-azure-rms.md)을 검토해야 합니다.

## 1단계: Azure 권한 관리를 포함하는 구독이 있는지 확인
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]가 포함된 둘 이상의 구독 형식이 있습니다. [Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하고, [RMS(권한 관리 서비스) 제공 서비스 비교](https://technet.microsoft.com/dn858608)의 표를 참조하여 조직에서 사용하려는 기능이 구독에 포함되어 있는지 확인하세요. Azure RMS를 사용하여 파일과 메일을 보호할 조직의 각 사용자에게 이 구독의 라이선스를 할당해야 합니다.

## 2단계: 권한 관리를 사용하도록 테넌트 계정 준비
[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 사용을 시작하기 전에 다음 준비를 수행합니다.

1.  Azure 또는 Office 365 테넌트에 조직의 사용자 인증을 위해 Azure RMS에서 사용하는 사용자 계정 및 그룹이 포함되어 있는지 확인합니다. 필요한 경우 이러한 계정 및 그룹을 만들거나 온-프레미스 디렉터리에서 동기화합니다. 자세한 내용은 [Azure 권한 관리 준비](prepare.md)를 참조하세요.

2.  테넌트 키를 Microsoft에서 관리하도록 할지(기본값) 아니면 직접 생성하고 관리할지(BYOK, Bring Your Own Key라고도 함)를 결정합니다. 현재는 Exchange Online을 사용하는 경우 BYOK를 사용할 수 없습니다. 자세한 내용은 [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)을 참조하세요.

3.  인터넷에 연결된 한 대 이상의 컴퓨터에 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]용 Windows PowerShell 모듈을 설치합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure 권한 관리용 Windows PowerShell 설치](../deploy-use/install-powershell.md)를 참조하세요.

4.  온-프레미스 권한 관리 서비스를 사용 중인 경우: 마이그레이션을 수행하여 키, 템플릿 및 URL을 클라우드로 이동합니다. 자세한 내용은 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.

5.  서비스 사용을 시작할 수 있도록 권한 관리를 활성화합니다. 단계별 배포가 필요한 경우 특정 사용자로 사용을 제한하도록 사용자 온보딩 컨트롤을 구성합니다. 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.

원하는 경우 다음 항목을 구성할 수 있습니다.

-   조직에서 기본 권한 정책 템플릿만으로는 부족한 경우 사용자 지정 템플릿을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

-   조직에서 권한 관리를 사용하는 방식을 모니터링할 수 있도록 사용 현황 로깅을 구성합니다. 이 단계는 지금 수행해도 되고 나중에 수행해도 됩니다. 자세한 내용은 [Azure 권한 관리 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.

## 3단계: 권한 관리용 응용 프로그램 및 서비스 구성
응용 프로그램 및 서비스 구성 과정에는 Rights Management 공유 응용 프로그램을 설치하고 SharePoint Online 또는 Exchange Online에서 IRM(정보 권한 관리) 기능을 지원하도록 설정하는 작업이 포함될 수 있습니다. 자세한 내용은 [Azure 권한 관리에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)을 참조하세요.

Azure RMS가 보호하는 파일을 검사해야 하는 기존 IT 서비스(DLP(데이터 손실 방지) 솔루션, CEG(콘텐츠 암호화 게이트웨이) 및 맬웨어 방지 제품)가 있는 경우 Azure RMS에 대한 슈퍼 사용자가 되도록 서비스 계정을 구성합니다. 자세한 내용은 [Azure 권한 관리 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)을 참조하세요.

Azure 권한 관리에 사용하려는 온-프레미스 서비스가 있으면 Rights Management 커넥터를 설치 및 구성합니다. 자세한 내용은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

## 4단계: 권한으로 보호된 콘텐츠 게시 및 사용
이제 보호된 콘텐츠를 게시하고 사용할 준비가 되었으며 회사에서 권한 관리를 사용하는 방법을 기록합니다. 자세한 내용은 [사용자가 Azure 권한 관리를 사용하여 파일을 보호할 수 있도록 지원](../deploy-use/help-users.md) 및 [Azure 권한 관리 사용 현황 로깅 및 분석](../deploy-use/log-analyze-usage.md)을 참조하세요.

## 5단계: 필요에 따라 테넌트 계정의 권한 관리 관리
[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 사용을 시작하면 Windows PowerShell용 [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] 모듈을 통해 관리 변경 작업을 스크립트로 작성하거나 자동화할 수 있습니다. 자세한 내용은 [Windows PowerShell을 사용하여 Azure 권한 관리](../deploy-use/administer-powershell.md)를 참조하세요.




<!--HONumber=Apr16_HO3-->


