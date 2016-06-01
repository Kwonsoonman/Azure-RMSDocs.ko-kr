---
# required metadata

title: Azure 권한 관리용 사용자 지정 템플릿 구성 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure 권한 관리용 사용자 지정 템플릿 구성

*적용 대상: Azure 권한 관리, Office 365*

[Azure 권한 관리(Azure RMS)를 활성화](activate-service.md)하면 액세스 권한이 조직의 권한 있는 사용자로 제한되는 정책을 중요한 파일에 쉽게 적용할 수 있도록 두 가지 기본 템플릿을 자동으로 사용할 수 있습니다. 이 두 개의 템플릿에는 다음의 권한 정책 제한이 있습니다.

-   보호된 콘텐츠의 읽기 전용 보기

    -   표시 이름: **&lt;조직 이름&gt; - 기밀 보기 전용**

    -   권한 지정: 콘텐츠 보기

-   보호된 콘텐츠의 사용 권한을 읽거나 수정하기

    -   표시 이름: **&lt;조직 이름&gt; - 기밀**

    -   권한 지정: 콘텐츠 보기, 파일 저장하기, 콘텐츠 편집하기, 할당된 권한 보기, 매크로 허용하기, 전달하기, 회신하기, 전체 회신하기

또한 [RMS 공유 응용 프로그램](../rms-client/sharing-app-windows.md)에서는 사용자가 원하는 권한 설정을 정의할 수 있습니다. 그리고 Outlook 클라이언트와 Outlook Web Access의 경우 전자 메일 메시지에 대해 **전달 금지** 옵션을 선택할 수 있습니다.

많은 조직에서는 기본 템플릿만으로도 충분할 수 있습니다. 그러나 원하는 경우 사용자 지정 권한 정책 템플릿을 만들 수 있습니다. 사용자 지정 템플릿을 만드는 이유는 다음과 같습니다.

-   모든 사용자가 아닌 조직의 하위 사용자 집합에 권한을 부여하는 템플릿을 원하는 경우

-   조직의 모든 사용자가 템플릿을 보고 선택할 수 있는 것이 아니라 일부 사용자만 응용 프로그램에서 템플릿(부서별 템플릿)을 보고 선택할 수 있도록 하려는 경우

-   보기와 편집은 허용하나 복사나 인쇄는 금지하는 것과 같이 템플릿에 사용자 지정 권한을 설정하고 싶을 경우

-   템플릿에 인터넷 연결 없이 해당 콘텐츠에 액세스할 수 있는지와 만료 날짜를 포함한 추가 옵션을 구성하고자 하는 경우

이러한 설정을 포함한 사용자 지정 템플릿을 선택하려면 우선 사용자 지정 템플릿을 만들고 구성한 후 이를 게시해야 합니다. 대체로 몇 개의 템플릿만 필요하지만 Azure에는 최대 500개의 사용자 지정 템플릿이 저장되어 있을 수 있습니다. 

다음 정보를 참조하여 사용자 지정 템플릿을 구성하고 사용할 수 있습니다.

-   [사용자 지정 템플릿을 작성, 구성 및 게시하는 방법](create-template.md)

-   [템플릿 복사 방법](copy-template.md)

-   [템플릿 제거(보관) 방법](remove-template.md)

-   [사용자를 위해 템플릿을 새로 고치는 방법](refresh-templates.md)

-   [PowerShell을 사용하여 템플릿 관리](configure-templates-with-powershell.md)




<!--HONumber=Apr16_HO4-->


