---
title: Azure Rights Management에 대한 사용 권한 구성 - AIP
description: Azure Information Protection의 Azure Rights Management 서비스를 사용하여 파일이나 전자 메일을 보호할 때 사용되는 특정 권한을 소개하고 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ab94d732144613d810c959f7fad0f34a842da9c7
ms.sourcegitcommit: 76e1b7c0255700813590be62d94b19338bf6c201
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48866189"
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Azure Rights Management에 대한 사용 권한 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection의 Azure Rights Management 서비스를 사용하여 파일 또는 메일에 보호를 설정하고 템플릿을 사용하지 않는 경우 직접 사용 권한을 구성해야 합니다. 또한 Azure Rights Management 보호에 대한 템플릿 또는 레이블을 구성할 때 선택한 사용 권한은 사용자, 관리자 또는 구성된 서비스에서 해당 템플릿 또는 레이블을 선택할 경우 자동으로 적용됩니다. 예를 들어 Azure 포털에서 사용 권한의 논리적 그룹화를 구성하는 역할을 선택하거나 개별 권한을 구성할 수 있습니다.

이 문서는 사용 중인 응용 프로그램에 대해 원하는 사용 권한을 구성하고 이러한 권한이 응용 프로그램에서 해석되는 방법을 이해하는데 도움이 됩니다.

> [!NOTE] 
> 완성도를 위해 이 아티클은 2018년 1월 8일에 사용이 중지된 Azure 클래식 포털의 값을 포함합니다.
>
> 새 포털로 마이그레이션하려면 [Azure 클래식 포털과 관련된 작업](migrate-portal.md)을 참조하세요.

## <a name="usage-rights-and-descriptions"></a>사용 권한 및 설명
다음 테이블은 Rights Management가 지원하는 사용 권한 및 사용하고 해석되는 방식에 대해 나열하고 설명합니다. 일반적으로 코드에 사용되는 단일 단어 값(**정책에서 인코딩** 값)의 더 친숙한 버전으로 표시되거나 참조된 사용 권한을 확인하는 방식인 **일반 이름**을 기준으로 나열됩니다. 

**API 상수 또는 값**은 MSIPC API 호출에 대한 SDK 이름이며 사용 권한을 확인하거나 사용 권한을 정책에 추가하는 RMS 지원 응용 프로그램을 작성할 때 사용됩니다.


|사용 권한|설명|구현|
|-------------------------------|---------------------------|-----------------|
|일반 이름: **콘텐츠 편집, 편집** <br /><br />정책에서 인코딩: **DOCEDIT**|사용자가 응용 프로그램 내에서 콘텐츠를 수정, 다시 정렬, 형식 지정 또는 정렬할 수 있게 합니다. 편집된 복사본을 저장할 수 있는 권한은 부여하지 않습니다.<br /><br />Word에서 최소 [1807](https://docs.microsoft.com/officeupdates/monthly-channel-2018#version-1807-july-25) 버전의 Office 365 ProPlus가 설치되지 않은 경우 이 권한으로는 **변경 내용 추적**을 켜거나 끄고 검토자로 일부 변경 내용 추적 기능을 사용할 수 없습니다. 대신, 모든 변경 내용 추적 옵션을 사용하려면 **모든 권한**이 필요합니다. |Office 사용자 지정 권한: **변경** 및 **모든 권한** 옵션의 일부로 제공됩니다. <br /><br />Azure 클래식 포털의 이름: **콘텐츠 편집**<br /><br />Azure Portal의 이름: **콘텐츠 편집, 편집(DOCEDIT)**<br /><br />AD RMS 템플릿의 이름: **편집** <br /><br />API 상수 또는 값: 해당 사항 없음|
|일반 이름: **저장** <br /><br />정책에서 인코딩: **EDIT**|사용자가 현재 위치에 문서를 저장할 수 있게 합니다.<br /><br />Office 응용 프로그램에서 사용자가 이 권한을 사용하면 선택한 파일 형식이 Rights Management 보호를 기본적으로 지원하는 경우 문서를 수정하고 새 위치에 저장하고 새 이름을 저장할 수 있습니다. 파일 형식 제한은 원본 보호를 파일에서 제거할 수 없도록 합니다.|Office 사용자 지정 권한: **변경** 및 **모든 권한** 옵션의 일부로 제공됩니다. <br /><br />Azure 클래식 포털의 이름: **파일 저장**<br /><br />Azure Portal의 이름: **저장(EDIT)**<br /><br />AD RMS 템플릿의 이름: **저장** <br /><br />API 상수 또는 값: `IPC_GENERIC_WRITE L"EDIT"`|
|일반 이름: **주석** <br /><br />정책에서 인코딩: **COMMENT**|옵션을 사용하여 메모를 추가하거나 콘텐츠에 주석을 추가할 수 있습니다.<br /><br />이 권한은 SDK에서 사용할 수 있으며 Windows PowerShell 용 AzureInformationProtection 및 RMS 보호 모듈에서 임시 정책으로 사용할 수 있고 일부 소프트웨어 공급업체 응용 프로그램에서 구현되었습니다. 그러나 널리 사용되지 않으며 현재 Office 응용 프로그램에서 지원되지 않습니다.|Office 사용자 지정 권한: 구현되지 않음 <br /><br />Azure 클래식 포털의 이름: 구현되지 않음<br /><br />Azure 포털의 이름: 구현되지 않음<br /><br />AD RMS 템플릿의 이름: 구현되지 않음 <br /><br />API 상수 또는 값: `IPC_GENERIC_COMMENT L"COMMENT`|
|일반 이름: **다른 이름으로 저장, 내보내기** <br /><br />정책에서 인코딩: **EXPORT**|콘텐츠를 다른 파일 이름에 저장하는 옵션(다른 이름으로 저장)을 사용할 수 있게 합니다. <br /><br />Office 문서와 Azure Information Protection 클라이언트의 경우에는 파일은 보호하지 않고 저장되어 새로운 설정과 사용 권한을 사용하여 다시 보호될 수 있습니다. 이러한 허용되는 동작은 권한이 있는 사용자가 보호된 문서 또는 이메일에서 Azure Information Protection 레이블을 변경하거나 제거할 수 있음을 의미합니다. <br /><br />이 권한이 부여된 사용자는 응용 프로그램에서 **OneNote로 보내기**등의 다른 내보내기 옵션도 수행할 수 있습니다.<br /><br /> 참고: 이 권한이 부여되면, 선택한 파일 형식이 기본적으로 Rights Management 보호를 지원하는 경우 사용자는 Office 응용 프로그램을 사용하여 문서를 새 이름으로 저장할 수 있습니다.|Office 사용자 지정 권한: **모든 권한** 옵션의 일부로 제공됩니다. <br /><br />Azure 클래식 포털의 이름: **콘텐츠 내보내기(다른 이름으로 저장)** <br /><br />Azure Portal의 이름: **다른 이름으로 저장, 내보내기(EXPORT)**<br /><br />AD RMS 템플릿의 이름: **내보내기(다른 이름으로 저장)** <br /><br />API 상수 또는 값: `IPC_GENERIC_EXPORT L"EXPORT"`|
|일반 이름: **전달** <br /><br />정책에서 인코딩: **FORWARD**|전자 메일 메시지를 전달하고 **받는 사람** 및 **참조** 줄에 받는 사람을 추가하는 옵션을 사용할 수 있게 합니다. 이 권한은 문서에 적용되지 않고 메일 메시지에만 적용됩니다.<br /><br />전달자가 전달 동작의 일부로 다른 사용자에게 권한을 부여할 수 없게 합니다. <br /><br />이 권한을 부여할 때 보호된 메일 메시지가 첨부 파일로 전달되지 않도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여하고 추가로 **저장** 권한(일반 이름)도 부여합니다. Outlook 클라이언트나 Outlook 웹앱을 사용하는 다른 조직에 이메일을 보낼 때에도 이러한 권한을 지정합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스 사용을 면제받는 조직의 사용자에게 필요합니다.|Office 사용자 지정 권한: **전달 금지** 표준 정책을 사용하는 경우 거부됩니다.<br /><br />Azure 클래식 포털의 이름: **전달**<br /><br />Azure Portal의 이름: **전달(FORWARD)**<br /><br />AD RMS 템플릿의 이름: **전달** <br /><br />API 상수 또는 값: `IPC_EMAIL_FORWARD L"FORWARD"`|
|일반 이름: **모든 권한** <br /><br />정책에서 인코딩: **OWNER**|문서에 대한 모든 권한을 부여하며 사용 가능한 모든 작업을 수행할 수 있습니다.<br /><br />보호를 제거하고 문서를 다시 보호하는 기능이 포함됩니다. <br /><br />이 사용 권한은 [Rights Management 소유자](#rights-management-issuer-and-rights-management-owner)와 다릅니다.|Office 사용자 지정 권한: **모든 권한** 사용자 지정 옵션의 일부로 제공됩니다.<br /><br />Azure 클래식 포털의 이름: **모든 권한**<br /><br />Azure Portal의 이름: **모든 권한(OWNER)**<br /><br />AD RMS 템플릿의 이름: **모든 권한** <br /><br />API 상수 또는 값: `IPC_GENERIC_ALL L"OWNER"`|
|일반 이름: **인쇄** <br /><br />정책에서 인코딩: **PRINT**|콘텐츠 인쇄 옵션을 사용할 수 있게 합니다.|Office 사용자 지정 권한: 사용자 지정 권한에서 **콘텐츠 인쇄** 옵션의 일부로 제공됩니다. 받는 사람별 설정이 아닙니다.<br /><br />Azure 클래식 포털의 이름: **인쇄**<br /><br />Azure Portal의 이름: **인쇄(PRINT)**<br /><br />AD RMS 템플릿의 이름: **인쇄** <br /><br />API 상수 또는 값: `IPC_GENERIC_PRINT L"PRINT"`|
|일반 이름: **회신** <br /><br />정책에서 인코딩: **REPLY**|**받는 사람** 또는 **참조** 줄의 변경을 허용하지 않고 메일 클라이언트에서 **회신** 옵션을 사용할 수 있게 합니다.<br /><br />이 권한을 부여할 때 보호된 메일 메시지가 첨부 파일로 전달되지 않도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여하고 추가로 **저장** 권한(일반 이름)도 부여합니다. Outlook 클라이언트나 Outlook 웹앱을 사용하는 다른 조직에 이메일을 보낼 때에도 이러한 권한을 지정합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스 사용을 면제받는 조직의 사용자에게 필요합니다.|Office 사용자 지정 권한: 해당 없음<br /><br />Azure 클래식 포털의 이름: **회신**<br /><br />Azure 클래식 포털의 이름: **회신(REPLY)**<br /><br />AD RMS 템플릿의 이름: **회신** <br /><br />API 상수 또는 값: `IPC_EMAIL_REPLY`|
|일반 이름: **전체 회신** <br /><br />정책에서 인코딩: **REPLYALL**|메일 클라이언트에서 **전체 회신** 옵션을 사용할 수 있게 하지만 사용자가 **받는 사람** 또는 **참조** 줄에 받는 사람을 추가할 수 없습니다.<br /><br />이 권한을 부여할 때 보호된 메일 메시지가 첨부 파일로 전달되지 않도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여하고 추가로 **저장** 권한(일반 이름)도 부여합니다. Outlook 클라이언트나 Outlook 웹앱을 사용하는 다른 조직에 이메일을 보낼 때에도 이러한 권한을 지정합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스 사용을 면제받는 조직의 사용자에게 필요합니다.|Office 사용자 지정 권한: 해당 없음<br /><br />Azure 클래식 포털의 이름: **전체 회신**<br /><br />Azure Portal의 이름: **전체 회신(REPLY ALL)**<br /><br />AD RMS 템플릿의 이름: **전체 회신** <br /><br />API 상수 또는 값: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|일반 이름: **보기, 열기, 읽기** <br /><br />정책에서 인코딩: **VIEW**|사용자가 문서를 열고 콘텐츠를 시각화할 수 있게 합니다.<br /><br /> Excel에서는 이 권한으로는 데이터를 정렬할 수 없습니다. **콘텐츠 편집, 편집** 권한이 필요합니다. Excel에서 데이터를 필터링하려면 **콘텐츠 편집, 편집** 및 **복사** 권한이 필요합니다.|Office 사용자 지정 권한: **읽기** 사용자 지정 정책의 **보기** 옵션으로 제공됩니다.<br /><br />Azure 클래식 포털의 이름: **보기**<br /><br />Azure Portal의 이름: **보기, 열기, 읽기(VIEW)**<br /><br />AD RMS 템플릿의 이름: **읽기** <br /><br />API 상수 또는 값: `IPC_GENERIC_READ L"VIEW"`|
|일반 이름: **복사** <br /><br />정책에서 인코딩: **EXTRACT**|문서의 데이터(화면 캡처 포함)를 동일한 문서나 다른 문서에 복사하는 옵션을 사용할 수 있게 합니다.<br /><br />일부 응용 프로그램에서는 전체 문서를 보호되지 않은 형태로 저장할 수도 있습니다.<br /><br />비즈니스용 Skype 및 이와 유사한 화면 공유 응용 프로그램에서 발표자는 이 권한이 있어야만 보호된 문서를 프레젠테이션할 수 있습니다. 발표자에게 이 권한이 없으면 참석자는 문서를 볼 수 없고 이 문서가 까맣게 표시됩니다.|Office 사용자 지정 권한: **읽기 권한이 있는 사용자에게 내용 복사 허용** 사용자 지정 정책 옵션으로 제공됩니다.<br /><br />Azure 클래식 포털의 이름: **콘텐츠 복사 및 추출**<br /><br />Azure Portal의 이름: **복사(EXTRACT)**<br /><br />AD RMS 템플릿의 이름: **추출** <br /><br />API 상수 또는 값: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|일반 이름: **권한 보기** <br /><br />정책에서 인코딩: **VIEWRIGHTSDATA**|사용자가 문서에 적용된 정책을 볼 수 있게 합니다.|Office 사용자 지정 권한: 구현되지 않음<br /><br />Azure 클래식 포털의 이름: **할당된 권한 보기**<br /><br />Azure Portal의 이름: **권한 보기(VIEWRIGHTSDATA)**<br /><br />AD RMS 템플릿의 이름: **권한 보기** <br /><br />API 상수 또는 값: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|일반 이름: **권한 변경** <br /><br />정책에서 인코딩: **EDITRIGHTSDATA**|사용자가 문서에 적용된 정책을 변경할 수 있게 합니다. 보호 제거 포함을 포함합니다.|Office 사용자 지정 권한: 구현되지 않음<br /><br />Azure 클래식 포털의 이름: **권한 변경**<br /><br />Azure Portal의 이름: **권한 편집 (EDITRIGHTSDATA)**<br /><br />AD RMS 템플릿의 이름: **권한 편집** <br /><br />API 상수 또는 값: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|일반 이름: **매크로 허용** <br /><br />정책에서 인코딩: **OBJMODEL**|매크로를 실행하거나 문서의 콘텐츠를 다른 프로그래밍 방식으로 또는 원격으로 액세스하는 옵션을 사용할 수 있게 합니다.|Office 사용자 지정 권한: **프로그래밍 방식 액세스 허용** 사용자 지정 정책 옵션으로 제공됩니다. 받는 사람별 설정이 아닙니다.<br /><br />Azure 클래식 포털의 이름: **매크로 허용**<br /><br />Azure Portal:의 이름: **매크로 허용(OBJMODEL)**<br /><br />AD RMS 템플릿의 이름: **매크로 허용** <br /><br />API 상수 또는 값: 구현되지 않음|

## <a name="rights-included-in-permissions-levels"></a>사용 권한 수준에 포함된 권한

일부 응용 프로그램은 사용 권한을 사용 권한 수준과 그룹화하여 일반적으로 함께 사용되는 사용 권한을 보다 수비게 선택할 수 있도록 합니다. 이러한 사용 권한 수준은 역할 기반의 옵션을 선택할 수 있는 보다 간단한 수준을 제시합니다.  예를 들어 **검토자** 및 **공동 작성자**가 있습니다. 이러한 옵션은 사용자에게 권한을 요약해서 표시하므로 앞에 나온 표에 제공된 모든 권한을 포함하지는 않을 수 있습니다.

이러한 사용 권한 수준의 목록과 포함된 사용 권한의 전체 목록을 보려면 다음 표를 참조하세요. 사용 권한은 해당 [일반 이름](#usage-rights-and-descriptions)으로 나열됩니다.

|사용 권한 수준|응용 프로그램|포함된 사용 권한|
|---------------------|----------------|---------------------------------|
|보기 권한자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br /> Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 권한 보기; 회신 [[1]](#footnote-1); 전체 회신 [[1]](#footnote-1); 매크로 허용 [[2]](#footnote-2)<br /><br />참고: 메일의 경우 메일의 회신이 첨부 파일이 아닌 메일 메시지로 수신되도록 이 권한 수준 대신 검토자 권한을 사용합니다. 검토자는 Outlook 클라이언트나 Outlook Web App을 사용하는 다른 조직에 메일을 보낼 때에도 필요합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스 사용을 면제받는 조직의 사용자에게 필요합니다.|
|검토자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 권한 보기; 회신: 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3); 매크로 허용 [[2]](#footnote-2)|
|공동 작성자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 복사; 권한 보기; 매크로 허용; 다른 이름으로 저장, 내보내기 [[4]](#footnote-4); 인쇄; 회신 [[3]](#footnote-3); 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3)|
|공동 소유자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 복사; 권한 보기; 권한 변경; 매크로 허용; 다른 이름으로 저장, 내보내기; 인쇄; 회신 [[3]](#footnote-3); 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3); 모든 권한|

----

###### <a name="footnote-1"></a>각주 1

Azure Portal에 포함되지 않습니다.

###### <a name="footnote-2"></a>각주 2

Windows용 Azure Information Protection 클라이언트의 경우 이 권한은 현재 Office 응용 프로그램에 있는 Information Protection 표시줄에 필요합니다.

###### <a name="footnote-3"></a>각주 3
Windows용 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 응용 프로그램에는 해당되지 않습니다.

###### <a name="footnote-4"></a>각주 4
Windows용 Azure Portal 또는 Azure Information Protection 클라이언트에는 포함되어 있지 않습니다.

## <a name="rights-included-in-the-default-templates"></a>기본 템플릿에 포함된 권한
다음 표에 기본 템플릿을 만들 때 포함된 사용 권한을 나열되어 있습니다. 사용 권한은 해당 [일반 이름](#usage-rights-and-descriptions)으로 나열됩니다.

이러한 기본 템플릿은 구독을 구매할 때 만들어지며, 이름 및 사용 권한은 Azure Portal에서 [변경](configure-policy-templates.md)할 수 있습니다. 

|템플릿의 표시 이름|2017년 10월 6일부터 현재 날짜까지의 사용 권한|2017년 10월 6일 이전의 사용 권한|
|----------------|--------------------|----------|
|\<*조직 이름> - 기밀 보기 전용* <br /><br />또는<br /><br /> *Highly Confidential \ All Employees*|보기, 열기, 읽기; 복사; 권한 보기; 매크로 허용; 인쇄; 전달; 회신; 전체 회신; 저장; 콘텐츠 편집, 편집|보기, 열기, 읽기|
|\<*조직 이름>- 기밀* <br /><br />또는 <br /><br />*Confidential \ All Employees*|보기, 열기, 읽기; 다른 이름으로 저장, 내보내기; 복사; 권한 보기; 권한 변경; 매크로 허용; 인쇄; 전달; 회신; 전체 회신; 저장; 콘텐츠 편집, 편집; 모든 권한|보기, 열기, 읽기; 다른 이름으로 저장, 내보내기; 콘텐츠 편집, 편집; 권한 보기; 매크로 허용; 전달; 회신; 전체 회신|

## <a name="do-not-forward-option-for-emails"></a>메일에 대한 전달 금지 옵션

Exchange 클라이언트 및 서비스(예: Outlook 클라이언트, 웹용 Outlook, Exchange 메일 흐름 규칙 및 Exchange에 대한 DLP 작업)에는 메일에 대한 추가 정보 권한 보호 옵션인 **전달 금지**가 있습니다. 

선택할 수 있는 기본 권한 관리 템플릿처럼 이 옵션이 사용자(및 Exchange 관리자)에게 표시되지만 **전달 금지**는 템플릿이 아닙니다. 이것이 바로 템플릿을 보고 관리할 때 Azure Portal에서 이 옵션을 볼 수 없는 이유입니다. 대신, **전달 금지** 옵션은 사용자가 이메일 수신자에게 동적으로 적용되는 사용 권한 집합입니다.

**전달 금지** 옵션이 이메일에 적용되면, 이메일이 암호화되고 받는 사람을 인증해야 합니다. 그러면 받는 사람이 전달하거나 인쇄하거나 복사할 수 없습니다. 예를 들어, Outlook 클라이언트에서 전달 단추를 사용할 수 없고, **다른 이름으로 저장** 및 **인쇄** 메뉴 옵션을 사용할 수 없으며, **받는 사람**, **참조** 또는 **숨은 참조** 상자에서 수신자를 추가하거나 변경할 수 없습니다.

보호되지 않은 이메일에 연결된 [Office 문서](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM)는 동일한 제한 사항을 자동으로 상속합니다. 이러한 문서에 적용되는 사용 권한은 **콘텐츠 편집, 편집**; **저장**; **보기, 열기, 읽기**; 및 **매크로 허용**입니다. 첨부 파일에 대해 다른 사용 권한을 원하거나 첨부 파일이 상속된 보호를 지원하는 Office 문서가 아닌 경우 이메일에 첨부하기 전에 파일을 보호합니다. 그런 다음, 파일에 필요한 특정 사용 권한을 할당할 수 있습니다. 

### <a name="difference-between-do-not-forward-and-not-granting-the-forward-usage-right"></a>전달 금지와 전달 사용 권한을 부여하지 않음의 차이점

**전달 금지** 옵션을 적용하는 경우와 이메일에 **전달** 사용 권한을 부여하지 않은 템플릿을 적용할 경우 간에는 중요한 차이가 있습니다. **전달 금지** 옵션은 사용자가 원래 메일에서 선택한 수신자를 기준으로 권한 있는 사용자의 동적 목록을 사용하는 반면, 템플릿의 권한에는 관리자가 이전에 지정한 권한 있는 사용자의 정적 목록이 포함됩니다. 차이점은 무엇인가요? 예를 들어 보겠습니다. 

다른 사용자와 공유해서는 안 되는 어떤 정보를 마케팅 부서 내의 특정 사용자에게 메일로 보내려고 합니다. 권한(보기, 회신 및 저장)을 제한하는 템플릿을 사용하여 마케팅 부서에 메일을 보호해야 할까요?  아니면 **전달 금지** 옵션을 선택해야 할까요? 어떤 선택을 하든, 수신자는 메일을 전달할 수 없습니다. 

- 템플릿을 적용한 경우 수신자는 마케팅 부서의 다른 사용자와 정보를 공유할 수 있습니다. 예를 들어, 수신자는 탐색기를 사용하여 공유 위치 또는 USB 드라이브에 메일을 끌어서 놓을 수 있습니다. 이제 이 위치에 액세스할 수 있는 마케팅 부서의 모든 사용자(및 메일 소유자)는 메일의 정보를 볼 수 있습니다.
 
- **전달 금지** 옵션을 적용한 경우 수신자는 메일을 다른 위치로 이동하여 마케팅 부서의 어떤 사용자와도 정보를 공유할 수 없습니다. 이 시나리오에서는 원래 수신자(및 메일 소유자)만 메일의 정보를 볼 수 있습니다.

> [!NOTE] 
> 보낸 사람이 선택하는 수신자만 메일의 정보를 볼 수 있어야 하는 것이 중요한 경우 **전달 금지**를 사용합니다. 메일의 템플릿을 사용하면 보낸 사람이 선택한 수신자와 상관없이 관리자가 사전에 지정하는 사용자의 그룹으로 권한을 제한할 수 있습니다.

## <a name="encrypt-only-option-for-emails"></a>이메일에 대한 암호화 전용 옵션

Exchange Online에서 Office 365 메시지 암호화의 새로운 기능을 사용하면 이메일 옵션인 **암호화 전용**이 가능해 집니다.

이 옵션은 Exchange Online을 사용하는 테넌트에서 사용할 수 있으며, 메일 흐름 규칙의 다른 권한 보호 옵션 및 Office 365 DLP 작업으로 웹용 Outlook에서 선택하거나 최소 버전이 [1804](/officeupdates/monthly-channel-2018#outlook-feature-updates-4)인 Office 365 ProPlus가 있는 경우 Outlook에서 선택할 수 있습니다. 자세한 내용은 Office 팀에서 [Office 365 메시지 암호화에서 롤아웃된 암호화](https://aka.ms/omefeb2018) 블로그 게시물 공지를 참조하세요.

이 옵션을 선택하면 이메일이 암호화되고 받는 사람을 인증해야 합니다. 그런 다음, 받는 사람은 **다른 이름으로 저장, 내보내기** 및 **모든 권한**을 제외한 모든 사용 권한을 가집니다. 이 사용 권한 조합은 받는 사람에게 보호를 제거할 수 없다는 것을 제외하고 제한이 없다는 것을 의미합니다. 예를 들어 받는 사람은 이메일에서 복사, 인쇄 및 전달할 수 있습니다. 

마찬가지로, 기본적으로 메일에 연결된 보호되지 않은 [Office 문서](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM)는 동일한 사용 권한을 상속합니다. 이러한 문서는 자동으로 보호되며, 다운로드되면 Office 응용 프로그램에서 받는 사람이 저장, 편집, 복사 및 인쇄할 수 있습니다. 받는 사람이 문서를 저장할 때 새 이름과 다른 형식으로 문서를 저장할 수 있습니다. 그러나 보호를 지원하는 파일 형식만 사용할 수 있으므로 원래 보호 기능 없이 문서를 저장할 수 없습니다. 첨부 파일에 대해 다른 사용 권한을 원하거나 첨부 파일이 상속된 보호를 지원하는 Office 문서가 아닌 경우 이메일에 첨부하기 전에 파일을 보호합니다. 그런 다음, 파일에 필요한 특정 사용 권한을 할당할 수 있습니다.

또는 [Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps) 명령 **Set-IRMConfiguration**으로 설정하는 다음 구성 매개 변수 하나를 사용하여 문서에 대한 이 보호 상속을 변경할 수 있습니다. 사용자가 인증된 후 문서에 대한 원래 보호를 유지할 필요가 없는 경우 이러한 옵션을 사용하세요.

- 모든 받는 사람에 대해 문서의 보호를 제거하려는 경우: `Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true`. 이러한 받는 사람이 메일 메시지를 열면 문서가 보호되지 않습니다.

- 브라우저에서 문서를 보는 받는 사람에 대해서만 문서의 보호를 제거하려는 경우(일반적으로 Gmail과 같은 소셜 공급자 주소로 전송되므로): `Set-IRMConfiguration -DecryptAttachmentFromPortal $true`. 이러한 받는 사람이 문서를 다운로드하면 보호가 제거됩니다.

브라우저에서 문서를 보는 받는 사람에 대해서만 보호를 제거하는 방법은 Office 블로그 게시물, [Admin control for attachments now available in Office 365 Message Encryption](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)(이제 Office 365 메시지 암호화에서 첨부 파일에 대한 관리자 제어 사용 가능)을 참조하세요. 첨부된 문서에서 원래 보호를 유지해야 하는 경우 [Secure document collaboration by using Azure Information Protection](secure-collaboration-documents.md)(Azure Information Protection을 사용하여 문서 공동 작업 보호)을 참조하세요.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Rights Management 발급자와 Rights Management 소유자

Azure Rights Management 서비스를 사용하여 문서 또는 메일을 보호할 때 해당 콘텐츠를 보호하는 계정이 자동으로 그 콘텐츠의 Rights Management 발급자가 됩니다. 이 계정은 [사용 현황 로그](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs)에 **issuer** 필드로 기록됩니다. 

Rights Management 발급자는 항상 문서 또는 메일에 대한 [모든 권한]을 사용 권한으로 받으며 추가로:

- 보호 설정에 만료 날짜가 포함된 경우 Rights Management 발급자는 만료 날짜가 지난 후에도 문서 또는 메일을 열고 편집할 수 있습니다.

- Rights Management 발급자는 문서 또는 메일에 항상 오프라인으로 액세스할 수 있습니다.

- Rights Management 발급자는 문서가 해지된 후에도 열 수 있습니다. 

기본적으로 이 계정은 해당 콘텐츠의 **Rights Management 소유자**이기도 하며, 이 경우 문서 또는 메일을 만든 사용자가 보호를 시작합니다. 그러나 관리자 또는 서비스가 사용자를 대신하여 콘텐츠를 보호할 수 있는 시나리오도 있습니다. 예를 들면 다음과 같습니다.

- 관리자가 파일 공유의 파일을 일괄 보호: Azure AD의 관리자 계정이 사용자의 문서를 보호합니다.

- Windows Server 폴더에서 Rights Management 커넥터가 Office 문서 보호: Azure AD에서 RMS 커넥터에 대해 만든 서비스 주체 계정이 사용자의 문서를 보호합니다.

이러한 시나리오에서는 Rights Management 발급자가 Azure Information Protection SDK 또는 PowerShell을 사용하여 다른 계정에 Rights Management 소유자를 할당할 수 있습니다. 예를 들어, Azure Information Protection 클라이언트에서 [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) PowerShell cmdlet을 사용할 때 **OwnerEmail** 매개 변수를 사용하여 다른 계정에 Rights Management 소유자를 할당할 수 있습니다. 

Rights Management 발급자가 사용자를 대신하여 보호할 때, Rights Management 소유자를 할당하면 원본 문서 또는 메일 소유자는 자신이 보호를 시작한 것처럼 보호된 콘텐츠에 대해 같은 수준의 권한을 가집니다. 

예를 들어, 문서를 만든 사용자는 [인쇄] 사용 권한이 포함되지 않은 템플릿으로 보호되고 있어도 문서를 인쇄할 수 있습니다. 그 사용자는 해당 템플릿에 구성된 오프라인 액세스 설정이나 만료 날짜에 관계 없이 항상 문서에 액세스할 수 있습니다. 또한, Rights Management 소유자에게 모든 권한 사용 권한이 있기 때문에 이 사용자는 문서를 다시 보호하여 추가 사용자 액세스를 부여할 수 있고(그 시점에서 사용자가 Rights Management 소유자인 동시에 Rights Management 발급자가 됨), 보호를 제거할 수도 있습니다. 그러나 문서를 추적하고 해지하는 일은 Rights Management 발급자만 할 수 있습니다.

문서 또는 메일의 Rights Management 소유자는 [사용 현황 로그](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs)에서 **owner-email** 필드로 기록됩니다.

Rights Management 소유자는 Windows 파일 시스템의 소유자와 독립적입니다. 동일할 때도 많지만, SDK나 PowerShell을 사용하지 않는 경우에도 다를 수 있습니다.

## <a name="rights-management-use-license"></a>Rights Management 사용 라이선스

사용자가 Azure Rights Management로 보호되는 문서 또는 전자 메일을 열면 해당 콘텐츠에 대한 Rights Management 사용 라이선스가 사용자에게 부여됩니다. 이 사용 라이선스는 문서 또는 전자 메일 메시지에 대한 사용자의 사용 권한 및 콘텐츠를 암호화하는 데 사용된 암호화 키를 포함하는 인증서입니다. 또한 사용 라이선스에는 설정된 경우 만료 날짜 및 사용 라이선스가 유효한 기간이 포함되어 있습니다.

사용자는 [사용자 환경이 초기화](how-does-it-work.md#initializing-the-user-environment)된 후 31일마다 갱신될 때 부여되는 인증서인 RAC(권한 계정 인증서) 외에 콘텐츠를 열기 위한 유효한 사용 라이선스가 있어야 합니다.

사용 라이선스의 기간에는 콘텐츠에 대해 사용자를 다시 인증하거나 다시 권한을 부여하지 않습니다. 이렇게 하면 사용자는 보호된 문서 또는 전자 메일을 인터넷 연결 없이 계속 열 수 있습니다. 사용 라이선스 유효 기간이 만료되면 다음에 사용자가 보호된 문서 또는 이메일에 액세스할 때 사용자를 다시 인증하고 다시 권한을 부여해야 합니다. 

문서 및 전자 메일 메시지가 보호 설정을 정의하는 레이블 또는 템플릿을 사용하여 보호되는 경우 콘텐츠를 다시 보호할 필요 없이 레이블 또는 템플릿에서 이러한 설정을 변경할 수 있습니다. 사용자가 이미 콘텐츠에 액세스한 경우 변경 내용은 해당 사용 라이선스 기간이 만료된 후에 적용됩니다. 그러나 사용자가 사용자 지정 권한(임시 권한 정책이라고도 함)을 적용하고 이러한 사용 권한을 문서 또는 전자 메일을 보호한 후 변경해야 하는 경우, 해당 콘텐츠는 새 사용 권한으로 다시 보호되어야 합니다. 전자 메일 메시지에 대한 사용자 지정 권한은 전달 금지 옵션으로 구현됩니다.

테넌트에 대한 기본 사용 라이선스 유효 기간은 30일이며, PowerShell cmdlet [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime)을 사용하여 이 값을 구성할 수 있습니다. 보호가 레이블 또는 템플릿을 사용하여 적용되는 경우 더 제한적인 설정을 구성할 수 있습니다.

- Azure Portal에서 레이블 또는 템플릿을 구성하는 경우 사용 라이선스 유효 기간은 **오프라인 액세스 허용 설정**에서 해당 값을 가져옵니다. 
    
    Azure Portal에서 이 설정을 구성하기 위한 자세한 내용 및 지침은 Rights Management 보호를 위한 레이블을 구성하는 방법 지침에서 [보호 설정 정보](configure-policy-protection.md#information-about-the-protection-settings) 표를 참조하세요.

- PowerShell을 사용하여 템플릿을 구성하는 경우 사용 라이선스 유효 기간은 [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) 및 [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) cmdlet의 *LicenseValidityDuration* 매개 변수에서 해당 값을 가져옵니다.
    
    PowerShell을 사용하여 이 설정을 구성하기 위한 자세한 내용 및 지침은 각 cmdlet에 대한 도움말을 참조하세요.

## <a name="see-also"></a>참고 항목
[Azure Information Protection의 템플릿 구성 및 관리](configure-policy-templates.md)

[Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](configure-super-users.md)
