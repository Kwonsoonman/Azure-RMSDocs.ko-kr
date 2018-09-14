---
title: 방법&#58; 기본 제공 권한 사용 | Azure RMS
description: RMS SDK 4.2에서 제공하는 기본 제공 권한 및 앱이 이러한 제한에 따라 적용해야 하는 사용 제한에 대해 간략하게 설명합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 0d88cec3e0f6be56843a57db352785b4896bd045
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44148106"
---
# <a name="how-to-use-built-in-rights"></a>방법: 기본 제공 권한 사용

이 항목에서는 Microsoft Rights Management SDK 4.2에서 제공하는 기본 제공 권한 및 앱이 이러한 제한에 따라 적용해야 하는 사용 제한에 대해 간략하게 설명합니다. 다음은 기본 제공 권한, 일반적인 권한, 편집 가능한 문서 권한 및 메일 권한과 설명 및 운영 체제별 값을 보여 줍니다.

**참고** - Linux SDK에 대한 자세한 내용은 *rights.h* 소스 파일을 참조하세요.

## <a name="common-rights"></a>일반적인 권한

**모두** - 모든 일반적인 권한 컬렉션입니다.
- Android: [CommonRights.All](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS 및 OS X: [MSCommonRights](https://msdn.microsoft.com/library/dn758314.aspx) - 사용자 소유자 및 보기로 **모두** 구현
- Windows 스토어 및 Windows Phone: [CommonRights.All</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.all.aspx)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**소유자** - 소유자 권한은 보호된 콘텐츠에 대한 모든 권한을 부여합니다.
- Android: [<strong>CommonRights.Owner](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS 및 OS X: [MSCommonRights owner](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows 스토어 및 Windows Phone: [CommonRights.Owner](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.owner.aspx)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**보기** - 보호된 콘텐츠를 볼 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 응용 프로그램을 통해 사용자가 보호된 콘텐츠를 열어서 볼 수 있지만 콘텐츠를 수정, 추출, 전달 또는 저장하려면 추가 권한이 필요합니다.

- Android: [CommonRights.View](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS 및 OS X: [MSCommonRights view](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows 스토어 및 Windows Phone: [CommonRights.View](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.view.aspx)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>편집할 수 있는 문서 권한
**모두** - 편집할 수 있는 문서 권한이 모두 포함된 컬렉션입니다.
- Android: [EditableDocumentRights.All](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights all](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.all.aspx)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**주석** - 문서에 주석을 만들 수 있는 권한입니다.
- Android: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights comment](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.comment.aspx)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**편집** - 보호된 콘텐츠를 편집하고 동일한 보호된 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 변경하고 동일한 파일에 저장할 수 있습니다.
- Android: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights edit](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.edit.aspx)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**내보내기** - 보호된 형식에서 콘텐츠를 추출하여 다른 AD RMS 보호된 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 다른 AD RMS 보호된 형식으로 저장할 수 있습니다. 예를 들어 응용 프로그램에서 *다른 이름으로 저장* 기능을 구현하는 경우입니다.

- Android: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights exportable](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.export.aspx)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**추출** - 보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠에서 정보를 복사하고 붙여넣을 수 있습니다. 앱에서 <em>다른 이름으로 저장</em> 기능을 구현하는 경우 응용 프로그램을 통해 사용자가 보호된 콘텐츠를 보호되지 않는 형식이나 다른 보호된 형식으로 저장할 수도 있습니다. 이 권한은 메일에 대한 추출 권한과 동일한 값을 갖습니다.

- Android: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights extract](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.extract.aspx)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**인쇄** - 보호된 콘텐츠를 인쇄할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 사용자가 보호된 콘텐츠를 인쇄할 수 있습니다. 이 권한은 메일에 대한 인쇄 권한과 동일한 값을 갖습니다.

- Android: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS 및 OS X: [MSEditableDocumentRights print](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows 스토어 및 Windows Phone: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.print.aspx)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>메일 권한

**모두** - 메일 권한이 모두 포함된 컬렉션입니다.
- Android: [EmailRights.All](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS X: [MSEmailRights all](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.all.aspx)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**추출** - 보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지에서 정보를 복사하고 붙여넣을 수 있습니다. 앱에서 <em>다른 이름으로 저장</em> 기능을 구현하는 경우 응용 프로그램을 통해 받는 사람이 보호된 콘텐츠를 보호되지 않는 형식이나 다른 보호된 형식으로 저장할 수도 있습니다. 이 권한은 편집할 수 있는 문서에 대한 추출 권한과 동일한 값을 갖습니다.

- Android: [EmailRights.Extract](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS X: [MSEmailRights extract](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.Extract</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.extract.aspx)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**전달** - 보호된 메시지를 전달할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지를 전달할 수 있습니다.
- Android: [<strong>EmailRights.Forward</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS X: [MSEmailRights forward](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.Forward](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.forward.aspx)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**인쇄** - 보호된 콘텐츠를 인쇄할 수 있는 권한입니다. 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지를 인쇄할 수 있습니다. 이 권한은 편집할 수 있는 문서에 대한 인쇄 권한과 동일한 값을 갖습니다.

- Android: [EmailRights.Print](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS X: [MSEmailRights print](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.print.aspx)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**회신** - 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지에 회신하고 원본 메시지의 복사본을 포함할 수 있습니다.

- Android: [EmailRights.Reply](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS X: [MSEmailRights reply](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.Reply](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.reply.aspx)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**전체 회신** - 일반적으로 이 권한이 부여되면 앱을 통해 메일 받는 사람이 보호된 메시지의 모든 받는 사람에게 회신하고 원본 메시지의 복사본을 포함할 수 있습니다.

- Android: [EmailRights.ReplyAll</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS 및 OS x: [MSEmailRights replyAll](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows 스토어 및 Windows Phone: [EmailRights.ReplyAll](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.replyall.aspx)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)
