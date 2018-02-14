---
title: "Azure Rights Management에 대한 사용 권한 구성 - AIP"
description: "Azure Information Protection에서 Azure Rights Management 서비스를 사용하여 파일 또는 이메일을 보호할 때 사용되는 특정 권한을 이해하고 식별합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ceada043abfa1bee18c6407b3804815d95e89453
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Azure Rights Management에 대한 사용 권한 구성

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection에서 Azure Rights Management 서비스를 사용하여 파일 또는 이메일에 대한 보호를 설정하지만 템플릿을 사용하지 않는 경우에는 사용 권한을 직접 구성해야 합니다. 또한 Azure Rights Management 보호에 대한 템플릿이나 레이블을 구성하는 경우에는 사용자, 관리자 또는 구성된 서비스에서 템플릿이나 레이블을 선택할 때 자동으로 적용되는 사용 권한을 선택합니다. 예를 들어 Azure Portal에서 사용 권한의 논리적 그룹을 구성하는 역할을 선택하거나 개별 권한을 구성할 수 있습니다.

이 문서를 사용하면 사용하는 응용 프로그램에 대해 원하는 사용 권한을 구성하고, 이러한 권한이 응용 프로그램에서 해석되는 방식을 이해할 수 있습니다.

> [!NOTE] 
> 완성도를 높이기 위해 이 문서에는 2018년 1월 8일에 사용이 중지된 Azure 클래식 포털의 값이 포함되어 있습니다.
>
> 새 포털로 마이그레이션하는 데 도움이 되도록 [Azure 클래식 포털과 관련된 작업](migrate-portal.md)을 참조하세요.

## <a name="usage-rights-and-descriptions"></a>사용 권한 및 설명
다음 표에서는 Rights Management에서 지원하는 사용 권한 및 이를 사용하고 해석하는 방법을 나열하고 설명합니다. **일반 이름**으로 나열되며, 이는 일반적으로 코드에서 사용되는 단일 단어 값(**정책의 인코딩** 값)에 대한 친숙한 버전으로 사용 권한이 표시되거나 참조되는 방식입니다. 

**API 상수 또는 값**은 사용 권한을 확인하거나 정책에 추가하는 RMS 지원 응용 프로그램을 작성할 때 사용되는 MSIPC API 호출에 대한 SDK 이름입니다.


|사용 권한|Description|구현|
|-------------------------------|---------------------------|-----------------|
|일반 이름: **콘텐츠 편집, 편집** <br /><br />정책의 인코딩: **DOCEDIT**|사용자가 응용 프로그램 내에서 콘텐츠 수정, 다시 정렬, 형식 지정 또는 필터링할 수 있습니다. 편집한 복사본을 저장할 수 있는 권한은 부여되지 않습니다.|Office 사용자 지정 권한: **변경** 및 **모든 권한** 옵션의 일부입니다. <br /><br />Azure 클래식 포털의 이름: **콘텐츠 편집**<br /><br />Azure Portal의 이름: **콘텐츠 편집, 편집(DOCEDIT)**<br /><br />AD RMS 템플릿의 이름: **편집** <br /><br />API 상수 또는 값: 해당 없음|
|일반 이름: **저장** <br /><br />정책의 인코딩: **EDIT**|사용자가 현재 위치에 문서를 저장할 수 있습니다.<br /><br />Office 응용 프로그램에서 이 권한을 사용하면 사용자가 문서를 수정할 수 있습니다.|Office 사용자 지정 권한: **변경** 및 **모든 권한** 옵션의 일부입니다. <br /><br />Azure 클래식 포털의 이름: **파일 저장**<br /><br />Azure Portal의 이름: **저장(EDIT)**<br /><br />AD RMS 템플릿의 이름: **저장** <br /><br />API 상수 또는 값: `IPC_GENERIC_WRITE L"EDIT"`|
|일반 이름: **주석** <br /><br />정책의 인코딩: **COMMENT**|콘텐츠에 주석 또는 메모를 추가하는 옵션을 사용하도록 설정합니다.<br /><br />이 권한은 SDK에서 사용할 수 있으며, Windows PowerShell용 AzureInformationProtection 및 RMS 보호 모듈의 임시 정책으로 사용할 수 있고, 일부 소프트웨어 공급업체 응용 프로그램에서 구현되었습니다. 그러나 널리 사용되지 않으며, 현재 Office 응용 프로그램에서 지원되지 않습니다.|Office 사용자 지정 권한: 구현되지 않음 <br /><br />Azure 클래식 포털의 이름: 구현되지 않음<br /><br />Azure Portal의 이름: 구현되지 않음<br /><br />AD RMS 템플릿의 이름: 구현되지 않음 <br /><br />API 상수 또는 값: `IPC_GENERIC_COMMENT L"COMMENT`|
|일반 이름: **다른 이름으로 저장, 내보내기** <br /><br />정책의 인코딩: **EXPORT**|콘텐츠를 다른 파일 이름으로 저장하는 옵션(다른 이름으로 저장)을 사용하도록 설정합니다. Office 문서 및 Azure Information Protection 클라이언트의 경우 파일을 보호하지 않고 저장할 수 있습니다.<br /><br />사용자는 이 권한을 통해 응용 프로그램에서 **OneNote로 보내기**와 같은 다른 내보내기 옵션도 수행할 수 있습니다.<br /><br /> 참고: 이 권한이 부여되지 않은 경우, 선택한 파일 형식에서 기본적으로 Rights Management 보호를 지원하면 사용자가 Office 응용 프로그램에서 문서를 새 이름으로 저장할 수 있습니다.|Office 사용자 지정 권한: **변경** 및 **모든 권한** 옵션의 일부입니다. <br /><br />Azure 클래식 포털의 이름: **콘텐츠 내보내기(다른 이름으로 저장)** <br /><br />Azure Portal의 이름: **다른 이름으로 저장, 내보내기(EXPORT)**<br /><br />AD RMS 템플릿의 이름: **내보내기(다른 이름으로 저장)** <br /><br />API 상수 또는 값: `IPC_GENERIC_EXPORT L"EXPORT"`|
|일반 이름: **전달** <br /><br />정책의 인코딩: **FORWARD**|이메일 메시지를 전달하고 **받는 사람** 및 **참조** 줄에 받는 사람을 추가하는 옵션을 사용하도록 설정합니다. 이 권한은 문서에 적용되지 않고, 이메일 메시지에만 적용됩니다.<br /><br />전달자는 전달 작업의 일부로 다른 사용자에게 권한을 부여할 수 없습니다. <br /><br />이 권한을 부여할 때 원본 이메일이 첨부 파일이 아니라 전달된 이메일 메시지의 일부로 포함되도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여합니다. 또한 이 권한은 Outlook 클라이언트 또는 Outlook 웹앱을 사용하는 다른 조직으로 이메일을 보내는 경우에도 필요합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스를 사용하지 않는 조직의 사용자에게 적합합니다.|Office 사용자 지정 권한: **전달 금지** 표준 정책을 사용하는 경우 거부됩니다.<br /><br />Azure 클래식 포털의 이름: **전달**<br /><br />Azure Portal의 이름: **전달(FORWARD)**<br /><br />AD RMS 템플릿의 이름: **전달** <br /><br />API 상수 또는 값: `IPC_EMAIL_FORWARD L"FORWARD"`|
|일반 이름: **모든 권한** <br /><br />정책의 인코딩: **OWNER**|문서에 대한 모든 권한을 부여하고, 사용 가능한 모든 작업을 수행할 수 있습니다.<br /><br />보호를 제거하고 문서를 다시 보호하는 기능이 포함됩니다. <br /><br />이 사용 권한은 [Rights Management 소유자](#rights-management-issuer-and-rights-management-owner)와 다릅니다.|Office 사용자 지정 권한: **모든 권한** 사용자 지정 옵션입니다.<br /><br />Azure 클래식 포털의 이름: **모든 권한**<br /><br />Azure Portal의 이름: **모든 권한(OWNER)**<br /><br />AD RMS 템플릿의 이름: **모든 권한** <br /><br />API 상수 또는 값: `IPC_GENERIC_ALL L"OWNER"`|
|일반 이름: **인쇄** <br /><br />정책의 인코딩: **PRINT**|콘텐츠를 인쇄하는 옵션을 사용하도록 설정합니다.|Office 사용자 지정 권한: 사용자 지정 권한의 **콘텐츠 인쇄** 옵션입니다. 받는 사람별 설정이 아닙니다.<br /><br />Azure 클래식 포털의 이름: **인쇄**<br /><br />Azure Portal의 이름: **인쇄(PRINT)**<br /><br />AD RMS 템플릿의 이름: **인쇄** <br /><br />API 상수 또는 값: `IPC_GENERIC_PRINT L"PRINT"`|
|일반 이름: **회신** <br /><br />정책의 인코딩: **REPLY**|**받는 사람** 또는 **참조** 줄을 변경할 수 없고 이메일 클라이언트에서 **회신** 옵션을 사용하도록 설정합니다.<br /><br />이 권한을 부여할 때 원본 이메일이 첨부 파일이 아니라 전달된 이메일 메시지의 일부로 포함되도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여합니다. 또한 이 권한은 Outlook 클라이언트 또는 Outlook 웹앱을 사용하는 다른 조직으로 이메일을 보내는 경우에도 필요합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스를 사용하지 않는 조직의 사용자에게 적합합니다.|Office 사용자 지정 권한: 해당 없음<br /><br />Azure 클래식 포털의 이름: **회신**<br /><br />Azure 클래식 포털의 이름: **회신(REPLY)**<br /><br />AD RMS 템플릿의 이름: **회신** <br /><br />API 상수 또는 값: `IPC_EMAIL_REPLY`|
|일반 이름: **전체 회신** <br /><br />정책의 인코딩: **REPLYALL**|이메일 클라이언트에서 **전체 회신** 옵션을 사용하도록 설정하지만, 사용자가 **받는 사람** 또는 **참조** 줄에 받는 사람을 추가할 수 있습니다.<br /><br />이 권한을 부여할 때 원본 이메일이 첨부 파일이 아니라 전달된 이메일 메시지의 일부로 포함되도록 **콘텐츠 편집, 편집** 권한(일반 이름)도 부여합니다. 또한 이 권한은 Outlook 클라이언트 또는 Outlook 웹앱을 사용하는 다른 조직으로 이메일을 보내는 경우에도 필요합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스를 사용하지 않는 조직의 사용자에게 적합합니다.|Office 사용자 지정 권한: 해당 없음<br /><br />Azure 클래식 포털의 이름: **전체 회신**<br /><br />Azure Portal의 이름: **전체 회신(REPLY ALL)**<br /><br />AD RMS 템플릿의 이름: **전체 회신** <br /><br />API 상수 또는 값: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|일반 이름: **보기, 열기, 읽기** <br /><br />정책의 인코딩: **VIEW**|사용자가 문서를 열고 콘텐츠를 볼 수 있습니다.|Office 사용자 지정 권한: **읽기** 사용자 지정 정책, **보기** 옵션입니다.<br /><br />Azure 클래식 포털의 이름: **보기**<br /><br />Azure Portal의 이름: **보기, 열기, 읽기(VIEW)**<br /><br />AD RMS 템플릿의 이름: **전체 회신** <br /><br />API 상수 또는 값: `IPC_GENERIC_READ L"VIEW"`|
|일반 이름: **복사** <br /><br />정책의 인코딩: **EXTRACT**|문서의 데이터(화면 캡처 포함)를 같거나 다른 문서에 복사하는 옵션을 사용하도록 설정합니다.<br /><br />일부 응용 프로그램에서는 전체 문서를 보호되지 않은 형식으로 저장할 수도 있습니다.|Office 사용자 지정 권한: **읽기 권한이 있는 사용자에게 콘텐츠 복사 허용** 사용자 지정 정책 옵션입니다.<br /><br />Azure 클래식 포털의 이름: **콘텐츠 복사 및 추출**<br /><br />Azure Portal의 이름: **복사(EXTRACT)**<br /><br />AD RMS 템플릿의 이름: **추출** <br /><br />API 상수 또는 값: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|일반 이름: **권한 보기** <br /><br />정책의 인코딩: **VIEWRIGHTSDATA**|사용자가 문서에 적용된 정책을 볼 수 있습니다.|Office 사용자 지정 권한: 구현되지 않음<br /><br />Azure 클래식 포털의 이름: **할당된 권한 보기**<br /><br />Azure Portal의 이름: **권한 보기(VIEWRIGHTSDATA)**<br /><br />AD RMS 템플릿의 이름: **권한 보기** <br /><br />API 상수 또는 값: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|일반 이름: **권한 변경** <br /><br />정책의 인코딩: **EDITRIGHTSDATA**|사용자가 문서에 적용된 정책을 변경할 수 있습니다. 보호 제거 포함이 포함됩니다.|Office 사용자 지정 권한: 구현되지 않음<br /><br />Azure 클래식 포털의 이름: **권한 변경**<br /><br />Azure Portal의 이름: **권한 편집(EDITRIGHTSDATA)**.<br /><br />AD RMS 템플릿의 이름: **권한 편집** <br /><br />API 상수 또는 값: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|일반 이름: **매크로 허용** <br /><br />정책의 인코딩: **OBJMODEL**|매크로를 실행하거나 문서의 콘텐츠를 다른 프로그래밍 방식 또는 원격으로 액세스하는 옵션을 사용하도록 설정합니다.|Office 사용자 지정 권한: **프로그래밍 방식 액세스 허용** 사용자 지정 정책 옵션입니다. 받는 사람별 설정이 아닙니다.<br /><br />Azure 클래식 포털의 이름: **매크로 허용**<br /><br />Azure Portal의 이름: **매크로 허용(OBJMODEL)**<br /><br />AD RMS 템플릿의 이름: **매크로 허용** <br /><br />API 상수 또는 값: 구현되지 않음|

## <a name="rights-included-in-permissions-levels"></a>권한 수준에 포함된 권한

일부 응용 프로그램은 사용 권한을 권한 수준으로 그룹화하여 일반적으로 함께 사용되는 사용 권한을 더 쉽게 선택할 수 있도록 합니다. 이러한 권한 수준은 사용자의 복잡성 수준을 추상화하는 데 도움이 되므로 역할 기반 옵션을 선택할 수 있습니다.  예를 들어 **검토자**와 **공동 작성자**가 있습니다. 이러한 옵션은 종종 사용자에게 권한 요약을 표시하지만 앞의 표에서 나열된 모든 권한을 포함하지 않을 수도 있습니다.

이러한 사용 권한 수준의 목록과 해당 사용 권한의 전체 목록은 다음 표를 참조하세요. 사용 권한은 [일반 이름](#usage-rights-and-descriptions)으로 나열됩니다.

|권한 수준|응용 프로그램|포함된 사용 권한|
|---------------------|----------------|---------------------------------|
|뷰어|Azure 클래식 포털 <br /><br />Azure 포털<br /><br /> Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 권한 보기; 회신 [[1]](#footnote-1); 전체 회신 [[1]](#footnote-1); 매크로 허용 [[2]](#footnote-2)<br /><br />참고: 이메일의 경우 이메일 회신을 첨부 파일이 아닌 이메일 메시지로 받도록 하려면 이 권한 수준 대신 검토자를 사용합니다. 또한 검토자는 Outlook 클라이언트 또는 Outlook 웹앱을 사용하는 다른 조직으로 이메일을 보내는 경우에도 필요합니다. 또는 [온보딩 컨트롤](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy)을 구현했으므로 Azure Rights Management 서비스를 사용하지 않는 조직의 사용자에게 적합합니다.|
|검토자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 권한 보기; 회신: 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3); 매크로 허용 [[2]](#footnote-2)|
|공동 작성자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 복사; 권한 보기; 매크로 허용; 다른 이름으로 저장, 내보내기 [[4]](#footnote-4); 회신 [[3]](#footnote-3); 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3)|
|공동 소유자|Azure 클래식 포털 <br /><br />Azure 포털<br /><br />Windows용 Rights Management 공유 응용 프로그램<br /><br />Windows용 Azure Information Protection 클라이언트|보기, 열기, 읽기; 저장; 콘텐츠 편집, 편집; 복사; 권한 보기; 권한 변경; 매크로 허용; 다른 이름으로 저장, 내보내기; 회신 [[3]](#footnote-3); 전체 회신 [[3]](#footnote-3); 전달 [[3]](#footnote-3); 모든 권한|

----

###### <a name="footnote-1"></a>각주 1

Azure Portal에는 포함되지 않습니다.

###### <a name="footnote-2"></a>각주 2

Windows용 Azure Information Protection 클라이언트의 경우 이 권한은 현재 Office 앱의 Information Protection 표시줄에 필요합니다.

###### <a name="footnote-3"></a>각주 3
Windows용 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 응용 프로그램에는 적용되지 않습니다.

###### <a name="footnote-4"></a>각주 4
Azure Portal 또는 Windows용 Azure Information Protection 클라이언트에는 포함되지 않습니다.

## <a name="rights-included-in-the-default-templates"></a>기본 템플릿에 포함된 권한
다음 표에서는 기본 템플릿을 만들 때 포함되는 사용 권한을 나열하고 있습니다. 사용 권한은 [일반 이름](#usage-rights-and-descriptions)으로 나열됩니다.

이러한 기본 템플릿은 구독을 구매할 때 만들어지며, Azure Portal에서 해당 이름과 사용 권한을 [변경](configure-policy-templates.md)할 수 있습니다. 

|템플릿의 표시 이름|2017년 10월 6일부터 현재 날짜까지의 사용 권한|2017년 10월 6일 이전의 사용 권한|
|----------------|--------------------|----------|
|\<*조직 이름> - 기밀 보기 전용* <br /><br />로 구분하거나 여러<br /><br /> *극비 \ 모든 직원*|보기, 열기, 읽기; 복사; 권한 보기; 매크로 허용; 전달; 회신; 전체 회신; 저장; 콘텐츠 편집, 편집|보기, 열기, 읽기|
|\<*조직 이름> - 기밀* <br /><br />로 구분하거나 여러 <br /><br />*기밀 \ 모든 직원*|보기, 열기, 읽기; 다른 이름으로 저장, 내보내기; 복사; 권한 보기; 권한 변경; 매크로 허용; 전달; 회신; 전체 회신; 저장; 콘텐츠 편집, 편집; 모든 권한|보기, 열기, 읽기; 다른 이름으로 저장, 내보내기; 콘텐츠 편집, 편집; 권한 보기; 매크로 허용; 전달; 회신; 전체 회신|

## <a name="do-not-forward-option-for-emails"></a>이메일에 대한 전달 금지 옵션

Exchange 클라이언트 및 서비스(예: Outlook 클라이언트, Outlook Web Access 앱 및 Exchange 전송 규칙)에는 이메일에 대한 추가 정보 권한 보호 옵션인 **전달 금지**가 있습니다. 

이 옵션은 사용자(및 Exchange 관리자)에게 기본 Rights Management 템플릿인 것처럼 표시되지만 **전달 금지**는 템플릿이 아닙니다. 따라서 이는 Azure Portal에서 Azure Rights Management에 대한 템플릿을 보고 관리할 때 표시되지 않습니다. 대신, **전달 금지** 옵션은 사용자가 이메일을 받는 사람에게 동적으로 적용하는 권한 집합입니다.

이메일에 **전달 금지** 옵션이 적용되는 경우 받는 사람은 이메일을 전달하거나, 인쇄하거나, 복사하거나, 첨부 파일을 저장하거나, 다른 이름으로 저장할 수 없습니다. 예를 들어 Outlook 클라이언트에서 [전달] 단추를 사용할 수 없고, **다른 이름으로 저장**, **첨부 파일 저장** 및 **인쇄** 메뉴 옵션을 사용할 수 없으며, **받는 사람**, **참조** 또는 **숨은 참조** 상자에 받는 사람을 추가하거나 변경할 수 없습니다.

**전달 금지** 옵션을 적용하는 것과 이메일에 전달 권한을 부여하지 않는 템플릿을 적용하는 것 사이에는 중요한 차이가 있습니다. **전달 금지** 옵션은 사용자가 원래 이메일의 받는 사람을 기반으로 하는 권한 있는 사용자에 대한 동적 목록을 사용하는 반면, 템플릿의 권한에는 관리자가 이전에 지정한 권한이 부여된 사용자에 대한 정적 목록이 포함됩니다. 차이점은 무엇일까요? 예를 들어 보겠습니다. 

사용자는 마케팅 부서의 특정 사람에게 다른 사람과 공유할 수 없는 일부 정보를 이메일로 보내려고 합니다. 마케팅 부서의 권한(보기, 회신 및 저장)을 제한하는 템플릿으로 이메일을 보호해야 할까요?  아니면 **전달 금지** 옵션을 선택해야 할까요? 어떤 방법이든 받는 사람은 이메일을 전달할 수 없습니다. 

- 템플릿을 적용한 경우 받는 사람은 마케팅 부서의 다른 사람들과 정보를 공유할 수 있습니다. 예를 들어 받는 사람은 탐색기를 사용하여 이메일을 공유 위치 또는 USB 드라이브에 끌어서 놓을 수 있습니다. 그러면 이 위치에 액세스할 수 있는 마케팅 부서(및 이메일 소유자)의 모든 사람이 이메일의 정보를 볼 수 있습니다.
 
- **전달 금지** 옵션을 적용한 경우 받는 사람은 이메일을 다른 위치로 이동함으로써 마케팅 부서의 다른 사람과 정보를 공유할 수 없습니다. 이 시나리오에서는 원래의 받는 사람(및 이메일 소유자)만 이메일의 정보를 볼 수 있습니다.

> [!NOTE] 
> 보낸 사람이 선택한 받는 사람에게만 이메일의 정보를 표시해야 하는 경우에는 **전달 금지**를 사용합니다. 보낸 사람이 선택한 받는 사람과는 별도로, 관리자가 미리 지정한 사람의 그룹에 대한 권한을 제한하려면 이메일에 대한 템플릿을 사용합니다.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Rights Management 발급자 및 Rights Management 소유자

Azure Rights Management 서비스를 사용하여 문서 또는 이메일을 보호하면 해당 콘텐츠를 보호하는 계정이 자동으로 해당 콘텐츠에 대한 Rights Management 발급자가 됩니다. 이 계정은 [사용 현황 로그](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs)에 **발급자** 필드로 기록됩니다. 

Rights Management 발급자는 항상 문서 또는 이메일에 대한 [모든 권한] 사용 권한뿐만 아니라 다음 권한도 추가로 부여받습니다.

- 보호 설정에 만료 날짜가 포함되면 Rights Management 발급자는 해당 날짜 이후에도 문서 또는 이메일을 열고 편집할 수 있습니다.

- Rights Management 발급자는 항상 문서 또는 이메일을 오프라인으로 액세스할 수 있습니다.

- Rights Management 발급자는 철회된 문서도 열 수 있습니다. 

기본적으로 이 계정은 해당 콘텐츠에 대한 **Rights Management 소유자**이기도 합니다. 이 경우 문서 또는 이메일을 만든 사용자가 보호를 시작합니다. 그러나 관리자 또는 서비스가 사용자를 대신하여 콘텐츠를 보호할 수 있는 몇 가지 시나리오가 있습니다. 예를 들어 다음과 같이 사용할 수 있습니다.

- 관리자가 파일 공유의 파일을 대량 보호: Azure AD의 관리자 계정이 사용자의 문서를 보호합니다.

- Rights Management 커넥터를 통해 Windows Server 폴더의 Office 문서를 보호: Azure AD에서 RMS 커넥터에 대해 만든 서비스 사용자 계정이 사용자의 문서를 보호합니다.

이러한 시나리오에서 Rights Management 발급자는 Azure Information Protection SDK 또는 PowerShell을 사용하여 Rights Management 소유자를 다른 계정에 할당할 수 있습니다. 예를 들어 Azure Information Protection 클라이언트에서 [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) PowerShell cmdlet을 사용하는 경우, **OwnerEmail** 매개 변수를 지정하여 Rights Management 소유자를 다른 계정에 할당할 수 있습니다. 

Rights Management 발급자가 사용자를 대신하여 보호할 때 Rights Management 소유자를 할당하면, 원래의 문서 또는 이메일 소유자는 보호를 직접 시작한 것처럼 보호된 콘텐츠에 대해 동일한 수준의 제어 권한을 갖습니다. 

예를 들어 문서를 만든 사용자는 [인쇄] 사용 권한이 포함되지 않은 템플릿으로 보호되고 있더라도 인쇄할 수 있습니다. 동일한 사용자는 해당 템플릿에 구성되었을 수도 있는 오프라인 액세스 설정 또는 만료 날짜에 관계없이 항상 자신의 문서에 액세스할 수 있습니다. 또한 Rights Management 소유자에게는 [모든 권한] 사용 권한이 있으므로 이 사용자는 문서를 다시 보호하여 추가 사용자 액세스 권한을 부여할 수 있고(이 시점에서 사용자는 Rights Management 발급자인 동시에 Rights Management 소유자임), 보호를 제거할 수도 있습니다. 그러나 Rights Management 발급자만 문서를 추적하고 철회할 수 있습니다.

문서 또는 이메일의 Rights Management 소유자는 [사용 현황 로그](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs)에 **소유자 이메일** 필드로 기록됩니다.

Rights Management 소유자는 Windows 파일 시스템 소유자와 다릅니다. SDK 또는 PowerShell을 사용하지 않는 경우에도 종종 동일하지만 다를 수 있습니다.

## <a name="rights-management-use-license"></a>Rights Management 사용 라이선스

사용자가 Azure Rights Management로 보호되는 문서 또는 이메일을 열면 해당 콘텐츠에 대한 Rights Management 사용 라이선스가 사용자에게 부여됩니다. 이 사용 라이선스는 문서 또는 이메일 메시지에 대한 사용자의 사용 권한 및 콘텐츠를 암호화하는 데 사용된 암호화 키가 포함된 인증서입니다. 또한 사용 라이선스에는 만료 날짜(설정되어 있는 경우) 및 해당 사용 라이선스의 유효 기간도 포함되어 있습니다.

사용 라이선스 기간 동안 사용자가 다시 인증되거나 권한이 다시 부여되지 않습니다. 이렇게 하면 사용자가 인터넷에 연결하지 않고도 보호된 문서 또는 이메일을 계속 열 수 있습니다. 사용 라이선스 유효 기간이 만료되면, 다음 번에 사용자가 보호된 문서 또는 이메일에 액세스할 때 사용자가 다시 인증되고 권한이 다시 부여되어야 합니다. 

보호 설정을 정의하는 레이블이나 템플릿을 사용하여 문서 및 이메일 메시지를 보호하는 경우, 콘텐츠를 다시 보호하지 않고도 레이블이나 템플릿에서 이러한 설정을 변경할 수 있습니다. 사용자가 이미 콘텐츠에 액세스한 경우 해당 사용 라이선스가 만료되어야 변경 내용이 적용됩니다. 그러나 사용자가 사용자 지정 권한(임시 권한 정책이라고도 함)을 적용하고 문서 또는 이메일을 보호한 후에 이러한 권한을 변경해야 하는 경우, 해당 콘텐츠는 새 권한으로 다시 보호해야 합니다. 이메일 메시지에 대한 사용자 지정 권한은 [전달 금지] 옵션으로 구현됩니다.

테넌트에 대한 기본 사용 라이선스 유효 기간은 30일이며, 이 값은 [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime) PowerShell cmdlet을 사용하여 구성할 수 있습니다. 레이블이나 템플릿을 사용하여 보호를 적용하는 경우 더 제한적인 설정을 구성할 수 있습니다.

- Azure Portal에서 레이블이나 템플릿을 구성하는 경우 사용 라이선스 유효 기간에는 **오프라인 액세스 허용 설정**의 값이 적용됩니다. 
    
    Azure Portal에서 이 설정을 구성하는 방법에 대한 자세한 내용과 지침은 [Rights Management 보호에 대해 레이블을 구성하는 방법](configure-policy-protection.md)의 9단계에 있는 표를 참조하세요.

- PowerShell을 사용하여 템플릿을 구성하는 경우 사용 라이선스 유효 기간에는 [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) 및 [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) cmdlet의 *LicenseValidityDuration* 매개 변수 값이 적용됩니다.
    
    PowerShell을 사용하여 이 설정을 구성하는 방법에 대한 자세한 내용과 지침은 각 cmdlet에 대한 도움말을 참조하세요.


## <a name="see-also"></a>참고 항목
[Azure Information Protection의 템플릿 구성 및 관리](configure-policy-templates.md)

[Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](configure-super-users.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

