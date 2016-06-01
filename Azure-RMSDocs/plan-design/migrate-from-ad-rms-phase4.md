---
# required metadata

title: AD RMS에서 Azure 권한 관리로 마이그레이션 - 4단계 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 마이그레이션 4단계 - 사후 마이그레이션 작업

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*


AD RMS에서 Azure 권한 관리(Azure RMS)로 마이그레이션 4단계에는 다음 정보를 사용합니다. 이러한 절차에서는 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 8-9단계를 설명합니다..


## 8단계: AD RMS 서비스 해제

선택 사항: 온-프레미스 권한 관리 인프라에서 컴퓨터를 검색하지 못하게 하려면 Active Directory에서 SCP(서비스 연결 지점)를 제거합니다. 이는 레지스트리에서 마이그레이션 스크립트를 실행하는 등의 방법으로 구성한 리디렉션이므로 선택 사항입니다. 서비스 연결 지점을 제거하려면 [Rights Management Services 관리 도구 키트](http://www.microsoft.com/download/details.aspx?id=1479)의 AD SCP 레지스터 도구를 사용합니다..

[시스템 상태 보고서의 요청](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [ServiceRequest 테이블](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx), [보호된 콘텐츠에 대한 사용자 액세스 감사](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx) 등을 확인하여 AD RMS 서버에서 활동을 모니터링합니다. RMS 클라이언트가 이러한 서버와 더 이상 통신하지 않으며 클라이언트가 Azure RMS를 성공적으로 사용하고 있는지 확인한 다음, 이러한 서버에서 AD RMS 서버 역할을 제거할 수 있습니다. 전용 서버를 사용하는 경우, 일정 기간 동안 서버를 종료한 후 이러한 서버를 다시 시작해야 하는 문제가 보고되지 않았는지 확인하는 준비 단계를 거쳐 클라이언트가 Azure RMS를 사용하지 않는 이유를 조사할 때 서비스가 중단되지 않도록 할 수 있습니다.

AD RMS 서버를 서비스 해제한 후에는 Azure 클래식 포털에서 템플릿을 검토하고 통합하여 사용자가 보다 적은 수의 템플릿 중에서 선택하거나, 템플릿을 다시 구성하거나, 새 템플릿을 추가할 기회를 제공할 수 있습니다. 이때 기본 템플릿을 게시하는 것도 좋습니다. 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md) 항목을 참조하세요..

## 9단계: Azure RMS 테넌트 키 다시 입력
이 단계는 AD RMS 배포에서 RMS 암호화 모드 1을 사용한 경우 마이그레이션이 완료되었을 때 필요합니다. 키를 다시 입력하면 RMS 암호화 모드 2를 사용하는 새 테넌트 키가 생성되기 때문입니다. 암호화 모드 1에서 Azure RMS를 사용하는 방식은 마이그레이션 프로세스 중에만 지원됩니다.

이 단계는 선택 사항이지만, RMS 암호화 모드 2에서 실행한 경우 마이그레이션이 완료되었을 때 권장됩니다. 잠재적인 보안 위반으로부터 Azure RMS 테넌트 키를 보호하는 데 도움이 되기 때문입니다. Azure RMS 테넌트 키를 다시 입력하면("키 롤링"이라고도 함) 새 키가 만들어지고 원래 키는 보관됩니다. 하지만 한 키에서 다른 키로 바로 이동되지 않고 몇 주 이상이 걸립니다. 따라서 원래 키에 대해 의심스러운 위반이 발생할 때까지 기다리지 말고, 마이그레이션이 완료되는 즉시 RMS 테넌트 키를 다시 입력합니다.

Azure RMS 테넌트 키를 다시 입력하려면

-   RMS 테넌트 키를 Microsoft에서 관리하는 경우: Microsoft CSS(고객 지원 서비스)에 전화하여 본인이 RMS 테넌트 관리자임을 입증합니다.

-   RMS 테넌트 키를 사용자가 직접 관리하는 경우(BYOK): BYOK 절차를 반복하여 인터넷을 통해 또는 직접 새 키를 생성하고 만듭니다.

RMS 테넌트 키 관리에 대한 자세한 내용은 [Azure 권한 관리 테넌트 키에 대한 작업](../deploy-use/operations-tenant-key.md) 항목을 참조하세요..

## 다음 단계

이제는 마이그레이션을 완료했으므로 [배포 로드맵](deployment-roadmap.md)을 검토하여 필요할 수 있는 다른 배포 작업을 확인합니다.



<!--HONumber=Apr16_HO4-->


