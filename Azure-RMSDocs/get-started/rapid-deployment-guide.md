---
title: "Azure Information Protection 빠른 배포 가이드 | Azure Information Protection"
description: "조직 데이터를 보호하기 위해 Azure Information Protection을 보다 빠르게 배포하고 사용하는 방법을 설명하는 가이드입니다. 먼저 특정 시나리오 목록에서 구현할 시나리오를 선택합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: d1415913f4a76331088140555b0cfeaa88200871


---

# <a name="rapid-deployment-guide-for-azure-rights-management"></a>Azure 권한 관리 빠른 배포 가이드

>*적용 대상: Azure Information Protection, Office 365*

**배포 및 사용** 섹션의 구성 정보와 함께 이 가이드를 사용하면 특정 시나리오 목록에서 구현할 시나리오를 선택하여 Azure Information Protection을 보다 빠르게 배포하고 사용할 수 있습니다.

이러한 시나리오에는 관리자 지침과 함께 최종 사용자 문서가 포함되어 있습니다. 이 설명서(지침 또는 알림)를 최종 사용자에게 제공하기 전에 비즈니스 요구 사항 및 기존 워크플로에 맞게 이 설명서를 사용자 지정해야 합니다. 예제 지침 집합이나 알림을 통해 최종 사용자 문서가 어떻게 표시되는지 확인할 수 있습니다.

각 시나리오에는 이러한 솔루션을 순서에 상관없이 독립적으로 배포할 수 있도록 필요한 경우 추가 정보 링크가 포함된 요구 사항 목록이 있습니다.

여기에 나열된 시나리오는 가장 널리 사용되는 시나리오의 샘플입니다. Azure Information Protection을 사용하여 조직 내에서는 물론 조직 간에도 다양한 시나리오에서 정보를 보호할 수 있으므로 이 동일한 모델을 사용하여 고유한 시나리오를 정의하고 운영 환경과 사용자에게 배포할 수 있습니다. 특정 시나리오에 중점을 두면 Azure Information Protection 배포가 비즈니스 목표에 맞게 더욱 일치됩니다. 또한 경험상, 사용자는 "중요한 문서 보호"와 같은 일반적인 지침보다 더 자세하고 체계적으로 시나리오별 지침을 따르는 경향이 있습니다.

이러한 솔루션을 배포하기 전에 최종 사용자에게 광범위한 알림을 전송하여 회사 데이터를 보호하기 위해 일부 변경이 예정되어 있으며 그에 따라 최종 사용자도 변경해야 할 수 있음을 알리는 것이 좋습니다. 다음 표 뒤에 예제 통신이 포함되어 있습니다.

> [!NOTE]
> 이 가이드에 대한 질문과 의견이 있는 경우 이 페이지의 피드백 메커니즘을 사용하거나 [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback)으로 메일 메시지를 보내 주세요.

## <a name="scenarios-for-azure-information-protection"></a>Azure Information Protection에 대한 시나리오
Azure Information Protection을 신속하게 배포하여 특정 비즈니스 문제를 해결하려면 비즈니스 목표와 가장 일치하는 시나리오를 선택한 다음 필요에 따라 변경합니다.



**결과로 생성된 액세스를 추적하는 기능을 사용하여 다른 조직의 사용자에게 Office 파일을 안전하게 메일로 보내기(B2B 공동 작업)**

예:

- 고객에게 가격표, 로드맵 또는 릴리스 계획 보내기

- 공급업체에 작업 순서 또는 마케팅 사양 보내기

- 파트너에게 제안 또는 RFQ(견적 요청) 보내기

참조: [시나리오 - 다른 조직의 사용자와 Office 파일 공유](scenario-share-office-file-externally.md)

**SharePoint 라이브러리에 저장된 문서에 대한 제어 유지**

예:

- 부서별 스프레드시트 및 보고서

- 디자인 문서 또는 결과물에 대한 팀 간 공동 작업

참조: [시나리오 - SharePoint에 저장된 문서에 대한 제어 유지](scenario-sharepoint.md)

**임원이 권한이 제한된 정보를 안전하게 메일로 교환**

예:

- 인수 계획 공유

- 법적 문제 논의 또는 보급

- 잠재적 해고 또는 기타 민감한 주제에 대한 정보

참조: [시나리오 - 임원이 권한이 제한된 정보를 안전하게 교환](scenario-executives-email.md)

**파일 서버에 있는 모든 파일을 자동으로 보호**

예:

- 지적 재산의 손실을 방지하기 위해 사내에 보관해야 하는 CAD 문서

- 경쟁 우위를 유지하기 위해 공개되지 않도록 비밀로 유지해야 하는 마케팅 홍보 계획서 및 날짜

참고: [시나리오 - 파일 서버 공유에 있는 파일 보호](scenario-fci.md)

**비즈니스에 미치는 영향이 큰 1급 기밀 문서 보호**

예:

- 회사의 고유한 조리법 또는 제조법 정보

- 기밀 인수 또는 합병 계획

- 천연 자연 탐사 데이터

참고: [시나리오 - 가장 중요한(소수) 파일 보호](scenario-secure-most-valuable-files.md)

**회사 기밀 메일 및 첨부 파일을 안전하게 보내기**

예:

- 회사 비전 선언문

- 조직도, 개편 뉴스 또는 승진 공고문

- 회사 정책 정보

참고: [시나리오 - 회사 기밀 메일 보내기](scenario-company-confidential-email.md)

**클라우드 폴더에 있는 Office 파일에 대해 지속적인 보호 적용**

예:

- 회사 기밀 프로젝트에 대한 로컬로 편집한 Word 문서

- 중요한 데이터나 비즈니스에 미치는 영향이 큰 데이터를 포함하는 로컬로 생성된 스프레드시트

- 최종 프레젠테이션이 완성될 때까지 누출되거나 실수로 조직 외부 사용자와 공유되면 안 되는 로컬에 저장된 작업 중인 PowerPoint 프레젠테이션

참고: [시나리오 - 클라우드 폴더에 대해 지속적인 보호 구성](scenario-work-folders.md)




## <a name="announcement-for-users-before-rollout"></a>출시 전의 사용자 알림
다음 예제 커뮤니케이션 메시지를 사용하여 Azure Information Protection을 배포하면 일부 사항이 변경된다는 사실을 사용자에게 알릴 수 있습니다. 조직의 임원 중 한 명(CEO 권장)이 모든 사용자에게 메일로 보내도록 다음 텍스트를 복사하여 붙여넣습니다. 사용자와 조직에 보다 적절한 메시지를 만들기 위해 이 텍스트를 변경하는 것이 좋습니다.

![Azure RMS 빠른 배포를 위한 예제 사용자용 설명 문서 배너](../media/AzRMS_ExampleBanner.png)

### <a name="changes-were-making-to-safeguard-our-data"></a>데이터를 보호하기 위한 변경 내용
실수로 파트너에게 보낸 문서에 대한 액세스를 차단하려고 한 적이 있나요? 보낸 최신 제품 뉴스를 어떤 고객이 읽었는지 알 수 있는 방법이 있는지 궁금했던 적이 있나요? 보지 않아야 하는 사람에게 전송되지 않을까 염려하지 않고 기밀 제품 정보를 공유할 수 있어야 하나요?

곧 이러한 작업을 수행할 수 있습니다. IT 부서에서 Microsoft Azure Information Protection을 엔터프라이즈 데이터 보호 솔루션으로 구현하는 시스템 변경 작업을 수행하고 있기 때문입니다. 이러한 솔루션은 대부분 특별한 작업을 수행하지 않아도 필요한 보호 기능을 자동으로 적용합니다. 그러나 일부 변경의 경우 특별한 작업을 수행해야 할 수 있으며, 이 경우 IT 부서에서 정보와 지침을 보내며 질문이나 문제가 있을 경우 지원 센터에서 지원합니다.

예를 들어 공유하는 문서를 추적(및 필요한 경우 해지)하려면 문서 추적 사이트를 사용합니다.

![Azure RMS 문서 추적 스크린샷](../media/AzRMS_Tutorial_5_Screenshots.png)

작동 방식을 미리 살펴보려면 이 2분 분량의 동영상 [Azure RMS 문서 추적 및 취소](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)를 시청하세요.

이 조직의 가장 중요한 자산 중 하나는 데이터, 즉 매일 생성, 저장 및 사용하는 데이터입니다. 데이터를 통해 경쟁 우위를 얻고 성공적으로 수행할 수 있습니다. 데이터에 대한 제어를 유지하고 액세스하면 안 되는 사람들이 액세스할 수 없도록 하는 것이 중요한 것은 이런 이유 때문입니다.

구현 중인 솔루션은 중요한 데이터를 보호하는 데 도움이 되며 해당 데이터에 대한 제어를 유지하는 도구를 제공합니다. 이러한 변경을 구현하는 동안 협조해 주셔서 감사합니다.




<!--HONumber=Nov16_HO2-->


