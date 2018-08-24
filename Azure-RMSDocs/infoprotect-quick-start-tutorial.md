---
title: Azure Information Protection 빠른 시작 자습서
description: 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 20분 정도의 소개 자습서입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/08/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
ms.openlocfilehash: 4989b0feb9bb355fac1813b8730f436295e8beab
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804391"
---
# <a name="quick-start-tutorial-for-azure-information-protection"></a>Azure Information Protection 빠른 시작 자습서 

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 자습서를 사용하여 20분 정도에 완료할 수 있는 5단계를 통해 Azure Information Protection을 빠르게 사용해 보세요. 이 자습서는 Azure Information Protection에서 제공하는 기능 중 일부 경우를 빠르게 보여 주는 자가 주도형 데모로 만들어졌습니다. 사용 가능한 모든 기능이 포함되어 있지는 않으므로 조직에 대한 배포 가이드 목적이 아닙니다. 조직에 대한 Azure Information Protection을 배포하려면 [배포 로드맵 설명서](deployment-roadmap.md)를 참조하세요. 

이 자습서는 IT 관리자 및 컨설턴트를 대상으로 하며, 목표는 조직의 엔터프라이즈 정보 보호 솔루션으로 Azure Information Protection을 평가하는 데 도움이 되는 것입니다. 프로덕션 환경에서 Information Protection 정책을 구성하며 사용자용 클라이언트를 설치하는 단계는 관리자가 수행합니다. 문서 레이블을 지정하고 메일을 통해 문서를 안전하게 공유하고 최종 사용자가 수행하는 작업을 추적하는 단계입니다. 이 자습서에는 조직의 데이터를 분류하고 레이블을 지정하며 보호하는 일반적인 종단 간 시나리오를 설명하기 위해 모든 단계가 포함되어 있습니다. 

Azure Information Protection을 사용하여 이 자습서를 완료하는 데 문제가 있거나 이에 대한 다른 사용자의 의견을 확인하려면 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)를 참조하세요.

## <a name="prerequisites"></a>전제 조건 
이 자습서를 완료하려면 다음이 필요합니다.

- 분류, 레이블 지정 및 보호를 위해 Azure Information Protection이 포함된 구독. 이 자습서에는 사용자 권장 사항으로 자동화된 데이터 분류 및 문서 추적 사이트와 같은 고급 기능이 포함되어 있습니다. 이 자습서를 진행하려면 이러한 기능을 지원하는 구독이 있는지 확인해야 합니다. 자세한 내용은 [Azure Information Protection 가격 책정](https://azure.microsoft.com/pricing/details/information-protection) 페이지에서 기능 목록을 참조하세요.
    
    이러한 기능에 대한 구독이 없는 경우 [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)에 대한 무료 평가판에 등록할 수 있습니다.
    
  > [!TIP] 
  > 이 프로세스를 완료하려면 시간이 오래 걸릴 수도 있으므로 구독을 신청해야 할 경우에는 미리 준비해야 합니다.

- Azure Portal에 로그인하여 보호를 활성화하고 Azure Information Protection 정책을 구성할 수 있는 전역 관리자 계정. 또는 [Information Protection 관리자 또는 보안 관리자](/azure/active-directory/active-directory-assign-admin-roles-azure-portal)와 같은 다음 관리 역할을 가진 계정을 사용할 수 있습니다. 이 계정에 메일 주소와 제대로 작동하는 메일 서비스(예: Exchange Online)가 있어야 합니다.

- Windows(Windows 7 서비스 팩 1 이상)를 실행하며 Office 365 ProPlus(2016 앱 또는 2013 앱 포함), Office Professional Plus 2016, Office Professional Plus 2013 서비스 팩 1 또는 Office Professional Plus 2010 서비스 팩 2가 설치된 컴퓨터. 
    
    Azure Information Protection에서 이러한 응용 프로그램을 사용하려면 [Azure Rights Management 서비스 사용을 포함하는 Office 365 구독](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)이 있어야 합니다. 예: Office 365 E3 또는 Office 365 E5 구독. 이 구독의 라이선스를 사용하여 Office 앱에 로그인해야 합니다.

이제 시작하겠습니다.

>[!div class="step-by-step"]
[&#187; 1단계](infoprotect-tutorial-step1.md)


