---
title: '방법: 문서 추적 사용 | Azure RMS'
description: 문서 추적 기능을 사용하려면 관련 메타데이터 및 서비스 등록 관리에 대한 몇 가지 간단한 사항을 이해해야 합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 1caac2301fd41930856e13b634ead28f7335728f
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
ms.locfileid: "27764601"
---
# <a name="how-to-use-document-tracking"></a>방법: 문서 추적 사용

문서 추적 기능을 사용하려면 관련 메타데이터 및 서비스 등록 관리에 대한 몇 가지 간단한 사항을 이해해야 합니다.

## <a name="managing-document-tracking-metadata"></a>문서 추적 메타데이터 관리

문서 추적을 지원하는 각 운영 체제는 유사한 구현을 사용합니다. 여기에는 메타데이터를 나타내는 속성 집합, 사용자 정책 생성 메서드에 추가된 새 매개 변수, 문서 추적 서비스를 사용하여 추적할 정책을 등록하기 위한 메서드가 포함됩니다.

운영 측면에서 **콘텐츠 이름** 및 **알림 유형** 속성만 문서 추적에 필요합니다.

지정된 콘텐츠에 대해 문서 추적을 설정하는 데 사용할 단계 순서는 다음과 같습니다.

-   **라이선스 메타데이터** 개체를 만든 다음 **콘텐츠 이름** 및 **알림 유형**을 설정합니다. 두 속성만 필수 속성입니다.
   - Android - [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx)
   -  iOS - [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx)

정책 유형을 템플릿 또는 임시로 선택합니다.
- 템플릿 기반 문서 추적의 경우 라이선스 메타데이터를 매개 변수로 전달하여 **사용자 정책** 개체를 만듭니다.
  - Android - [UserPolicy.create](https://msdn.microsoft.com/library/dn790887.aspx)
  - iOS - [MSUserPolicy.userPolicyWithTemplateDescriptor](https://msdn.microsoft.com/library/dn790808.aspx)

- 임시 기반 문서 추적의 경우 **정책 설명자** 개체의 **라이선스 메타데이터** 속성을 설정합니다.
  - Android -  [PolicyDescriptor.setLicenseMetadata](https://msdn.microsoft.com/library/mt573698.aspx)
  - iOS -  [MSPolicyDescriptor.licenseMetadata](https://msdn.microsoft.com/library/mt573693.aspx).

    **참고** 라이선스 메타데이터 개체는 지정된 사용자 정책에 대해 문서 추적을 설정하는 중에만 직접 액세스할 수 있습니다. 사용자 정책 개체를 만든 후에는 관련된 라이선스 메타데이터에 액세스할 수 없습니다. 즉, 라이선스 메타데이터의 값을 변경해도 효과가 없습니다.

     

-   마지막으로 문서 추적에 대한 플랫폼 등록 메서드를 호출합니다.
  - Android - [UserPolicy.registerForDocTracking asynchronous](https://msdn.microsoft.com/library/mt573699.aspx) 또는 [UserPolicy.registerForDocTracking synchronous](https://msdn.microsoft.com/library/mt631387.aspx)
  - iOS - [MSUserPolicy.registerForDocTracking](https://msdn.microsoft.com/library/mt573694.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]