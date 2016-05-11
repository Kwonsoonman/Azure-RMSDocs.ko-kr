---
# required metadata

title: 방법&#58; 문서 추적 사용 | Azure RMS
description: 문서 추적 기능을 사용하려면 관련 메타데이터 및 서비스 등록 관리에 대한 몇 가지 간단한 사항을 이해해야 합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d193afec-6dc5-477d-8e67-f820a97480ff

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# 방법: 문서 추적 사용

문서 추적 기능을 사용하려면 관련 메타데이터 및 서비스 등록 관리에 대한 몇 가지 간단한 사항을 이해해야 합니다.

## 문서 추적 메타데이터 관리

문서 추적을 지원하는 각 운영 체제는 유사한 구현을 사용합니다. 여기에는 메타데이터를 나타내는 속성 집합, 사용자 정책 생성 메서드에 추가된 새 매개 변수, 문서 추적 서비스를 사용하여 추적할 정책을 등록하기 위한 메서드가 포함됩니다.

운영 측면에서 **콘텐츠 이름** 및 **알림 유형** 속성만 문서 추적에 필요합니다.

지정된 콘텐츠에 대해 문서 추적을 설정하는 데 사용할 단계 순서는 다음과 같습니다.

-   **라이선스 메타데이터** 개체를 만듭니다.

    자세한 내용은 [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) 또는 [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc)를 참조하세요.

-   **콘텐츠 이름** 및 **알림 유형**을 설정합니다. 두 속성만 필수 속성입니다.

    자세한 내용은 플랫폼에 해당하는 라이선스 메타데이터 클래스([**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) 또는 [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc))의 속성 액세스 방법을 참조하세요.

-   정책 유형별로는 템플릿 또는 임시입니다.

    -   템플릿 기반 문서 추적의 경우 라이선스 메타데이터를 매개 변수로 전달하여 **사용자 정책** 개체를 만듭니다.

        자세한 내용은 [**UserPolicy.create**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_class_java) 및 [**MSUserPolicy.userPolicyWithTemplateDescriptor**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_templatedescriptor_property_objc)를 참조하세요.

    -   임시 기반 문서 추적의 경우 **정책 설명자** 개체의 **라이선스 메타데이터** 속성을 설정합니다.

        자세한 내용은 [**PolicyDescriptor.getLicenseMetadata**](https://stage.docs.microsoft.com/en-us/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java), [**PolicyDescriptor.setLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_setlicensemetadata_java) 및 [**MSPolicyDescriptor.licenseMetadata**](/rights-management/sdk/4.2/api/iOS/mspolicydescriptor#msipcthin2_mspolicydescriptor_licensemetadata_property_objc)를 참조하세요.

    **참고** 라이선스 메타데이터 개체는 지정된 사용자 정책에 대해 문서 추적을 설정하는 중에만 직접 액세스할 수 있습니다. 사용자 정책 개체를 만든 후에는 관련된 라이선스 메타데이터에 액세스할 수 없습니다. 즉, 라이선스 메타데이터의 값을 변경해도 효과가 없습니다.

     

-   문서 추적에 대한 플랫폼 등록 메서드를 호출합니다.

    [**MSUserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc) 또는 [**UserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc)을 참조하세요.

 

 





<!--HONumber=Apr16_HO3-->

