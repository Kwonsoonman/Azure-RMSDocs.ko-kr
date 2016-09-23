---
title: "방법&#58; 기본 제공 권한 사용 | Azure RMS"
description: "RMS SDK 4.2에서 제공하는 기본 제공 권한 및 앱이 이러한 제한에 따라 적용해야 하는 사용 제한에 대해 간략하게 설명합니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: 9d99bc0589d3dbbc1669d08941d991363f224221
ms.openlocfilehash: a8c01039898a527c8e4c8edea7a2730c2ee7ee3a


---

# 방법: 기본 제공 권한 사용

이 항목에서는 Microsoft Rights Management SDK 4.2에서 제공하는 기본 제공 권한 및 앱이 이러한 제한에 따라 적용해야 하는 사용 제한에 대해 간략하게 설명합니다. 다음은 기본 제공 권한, 일반적인 권한, 편집 가능한 문서 권한 및 메일 권한과 설명 및 운영 체제별 값을 보여 줍니다.

**참고** - Linux SDK에 대한 자세한 내용은 *rights.h* 소스 파일을 참조하세요.

## 일반적인 권한 ##

**모두** - 모든 일반적인 권한 컬렉션입니다.
- Android: [CommonRights.All](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL)
- iOS 및 OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows 스토어 및 Windows Phone: [CommonRights.All</strong>](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

** 소유자** - 소유자 권한은 보호된 콘텐츠에 대한 모든 권한을 부여합니다.
- Android: [<strong>CommonRights.Owner](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner)
- iOS 및 OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows 스토어 및 Windows Phone: [CommonRights.Owner](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**보기** - 보호된 콘텐츠를 볼 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 응용 프로그램을 통해 사용자가 보호된 콘텐츠를 열어서 볼 수 있지만 콘텐츠를 수정, 추출, 전달 또는 저장하려면 추가 권한이 필요합니다.

- Android: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- iOS 및 OS X: [MSCommonRights view](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows 스토어 및 Windows Phone: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## 편집할 수 있는 문서 권한 ##
**모두** - 편집할 수 있는 문서 권한이 모두 포함된 컬렉션입니다.
- Android: [EditableDocumentRights.All](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL)
- iOS 및 OS X: [MSEditableDocumentRights all](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.All](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**주석** - 문서에 주석을 만들 수 있는 권한입니다.
- Android: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)
- iOS 및 OS X: [MSEditableDocumentRights comment](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**편집** - 보호된 콘텐츠를 편집하고 동일한 보호된 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 변경하고 동일한 파일에 저장할 수 있습니다.
- Android: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit)
- iOS 및 OS X: [MSEditableDocumentRights edit](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**내보내기** - 보호된 형식에서 콘텐츠를 추출하여 다른 AD RMS 보호된 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 다른 AD RMS 보호된 형식으로 저장할 수 있습니다. 예를 들어 응용 프로그램에서 *다른 이름으로 저장* 기능을 구현하는 경우입니다.

- Android: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export)
- iOS 및 OS X: [MSEditableDocumentRights exportable](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**추출** - 보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠에서 정보를 복사하고 붙여넣을 수 있습니다. 앱에서 <em>다른 이름으로 저장</em> 기능을 구현하는 경우 응용 프로그램을 통해 사용자가 보호된 콘텐츠를 보호되지 않는 형식이나 다른 보호된 형식으로 저장할 수도 있습니다. 이 권한은 메일에 대한 추출 권한과 동일한 값을 갖습니다.

- Android: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract)
- iOS 및 OS X: [MSEditableDocumentRights extract](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**인쇄** - 보호된 콘텐츠를 인쇄할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 인쇄할 수 있습니다. 이 권한은 메일에 대한 인쇄 권한과 동일한 값을 갖습니다.

- Android: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print)
- iOS 및 OS X: [MSEditableDocumentRights print](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## 메일 권한 ##

**모두** - 메일 권한이 모두 포함된 컬렉션입니다.
- Android: [EmailRights.All](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL)
- iOS 및 OS X: [MSEmailRights all](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.All](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**추출** - 보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지에서 정보를 복사하고 붙여넣을 수 있습니다. 앱에서 <em>다른 이름으로 저장</em> 기능을 구현하는 경우 응용 프로그램을 통해 받는 사람이 보호된 콘텐츠를 보호되지 않는 형식이나 다른 보호된 형식으로 저장할 수도 있습니다. 이 권한은 편집할 수 있는 문서에 대한 추출 권한과 동일한 값을 갖습니다.

- Android: [EmailRights.Extract](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract)
- iOS 및 OS X: [MSEmailRights extract](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.Extract</strong>](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**전달** - 보호된 메시지를 전달할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지를 전달할 수 있습니다.
- Android: [<strong>EmailRights.Forward</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward)
- iOS 및 OS X: [MSEmailRights forward](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.Forward](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**인쇄** - 보호된 콘텐츠를 인쇄할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지를 인쇄할 수 있습니다. 이 권한은 편집할 수 있는 문서에 대한 인쇄 권한과 동일한 값을 갖습니다.

- Android: [EmailRights.Print](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print)
- iOS 및 OS X: [MSEmailRights print](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.Print](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**회신** - 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지에 회신하고 원본 메시지의 복사본을 포함할 수 있습니다.

- Android: [EmailRights.Reply](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply)
- iOS 및 OS X: [MSEmailRights reply](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.Reply](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**전체 회신** - 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지의 모든 받는 사람에게 회신하고 원본 메시지의 복사본을 포함할 수 있습니다.

- Android: [EmailRights.ReplyAll</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll)
- iOS 및 OS x: [MSEmailRights replyAll](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows 스토어 및 Windows Phone: [EmailRights.ReplyAll](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

 

 

 



<!--HONumber=Sep16_HO3-->


