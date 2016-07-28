---
title: "Azure Information Protection 빠른 시작 자습서 | Azure 권한 관리"
description: "15분 이내에 완료할 수 있는 4단계를 통해 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서입니다."
author: cabailey
manager: mbaldwin
ms.date: 07/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
translationtype: Human Translation
ms.sourcegitcommit: cac95dec84f99d2e6caa3458dc8284defe2324bc
ms.openlocfilehash: 7dc988365c1fa86827d1a7edc33c0a2eb6180f0e


---

# Azure Information Protection 빠른 시작 자습서 

*적용 대상: Azure Information Protection 미리 보기*

이 자습서를 사용하여 15분 이내에 완료할 수 있는 4단계를 통해 조직에서 Azure Information Protection 미리 보기 사용을 빠르게 시작하는 방법을 확인할 수 있습니다. 선택적으로, Azure 권한 관리 서비스를 활성화하고 기본 Azure Information Protection 정책을 확인하고 수정하며 Azure Information Protection 클라이언트를 설치한 다음 Word 문서를 사용하여 실제 분류, 레이블 지정 및 보호 작동 방식을 확인합니다.

이 자습서는 IT 관리자 및 컨설턴트를 대상으로 하며, 목표는 조직의 엔터프라이즈 정보 보호 솔루션으로 Azure Information Protection을 평가하는 데 도움이 되는 것입니다. 프로덕션 환경에서 이 서비스를 활성화하고 Information Protection 정책을 구성하며 사용자용 클라이언트를 설치하는 지침은 관리자가 수행합니다. 문서에 레이블을 지정하는 지침은 최종 사용자가 수행합니다. 조직의 데이터를 분류하고 레이블을 지정하며 보호하는 종단 간 시나리오를 설명하기 위해, 이 자습서에는 두 가지 지침이 모두 포함되어 있습니다. 

Azure Information Protection의 미리 보기 릴리스를 사용하여 이 자습서를 완료하는 데 문제가 있거나 이에 대한 다른 사용자의 의견을 확인하려면 [Azure Information Protection Yammer 사이트](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)를 참조하세요.

## 필수 구성 요소 
이 자습서를 완료하려면 다음이 필요합니다.

- Azure Information Protection의 미리 보기 릴리스에 대한 액세스 권한을 제공하는, Azure 권한 관리를 포함하는 모든 구독. Azure Information Protection은 Azure 권한 관리를 지원하는 모든 지역에서 사용할 수 있습니다. 사용 가능한 구독에 대한 자세한 내용과 무료 평가판 링크는 [Azure RMS 요구 사항: Azure RMS를 지원하는 클라우드 구독](../get-started/requirements-subscriptions.md)을 참조하세요.

- Azure 포털에 액세스하여 Azure Information Protection 정책을 구성할 수 있는 Azure 구독. 조직에서 아직 Azure를 구독하지 않은 경우 무료 평가판을 신청하여 사용해 볼 수 있습니다. [Azure 시작](https://account.windowsazure.com/organization) 페이지로 이동하여 지침을 따르세요.

  > [!TIP] 
  > 이 프로세스를 완료하려면 시간이 오래 걸릴 수도 있으므로 이러한 구독 중 하나 또는 둘 다가 필요한 경우에는 미리 준비해야 합니다.

- 권한 관리 서비스를 활성화해야 하는 경우 Office 365 관리 센터 또는 Azure 클래식 포털에 로그인하는 데 사용할 전역 관리자 계정. 이 계정에 메일 주소와 제대로 작동하는 메일 서비스(예, Exchange Online 또는 Exchange Server)가 있어야 합니다.

- Windows(Windows 7 서비스 팩 1 이상)를 실행하며 Office 2016, Office 2013 서비스 팩 1 또는 Office 2010이 설치된 컴퓨터. 

- 조직에 AD RMS(Active Directory Rights Management Services)를 배포한 경우: 컴퓨터는 이전에 AD RMS를 사용하지 않은 작업 그룹 컴퓨터여야 합니다. 이 요구 사항은 문서를 보호하려는 경우 필요하며, 컴퓨터가 Azure 권한 관리에서만 템플릿을 다운로드하도록 합니다. 컴퓨터를 AD RMS와 Azure RMS에 동시에 연결하는 것은 지원되지 않습니다. 마이그레이션 정보에 관심이 있는 경우 [AD RMS에서 Azure 권한 관리로 마이그레이션](../plan-design/migrate-from-ad-rms-to-azure-rms.md)을 참조하세요.   

이제 시작하겠습니다.

>[!div class="step-by-step"]
[&#187; 1단계](infoprotect-tutorial-step1.md)





<!--HONumber=Jul16_HO3-->


