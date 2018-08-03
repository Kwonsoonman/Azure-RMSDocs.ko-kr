---
title: RMS 공유 앱에 대한 기술 개요 - AIP
description: Windows용 RMS 공유 응용 프로그램 배포를 담당하는 기업 네트워크의 관리자와 관련된 기술 세부 정보를 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/02/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f7b13fa4-4f8e-489a-ba46-713d7a79f901
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9aa69746786100df389997a7dca674a159edcb26
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39373807"
---
# <a name="technical-overview-and-protection-details-for-the-microsoft-rights-management-sharing-application"></a>Microsoft Rights Management 공유 응용 프로그램 기술 개요 및 보호 세부 정보

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*


Microsoft Rights Management 공유 응용 프로그램은 선택적으로 다운로드 가능하며 다음 기능을 제공하는 Microsoft Windows 및 기타 플랫폼용 응용 프로그램입니다.

-   단일 파일을 보호하거나 여러 파일 또는 선택한 폴더 내의 모든 파일을 대량으로 보호합니다.

-   일반적으로 사용되는 텍스트 및 이미지 파일 형식용 기본 제공 뷰어와 모든 파일 형식에 대한 보호를 완벽히 지원합니다.

-   RMS 보호를 지원하지 않는 파일에 대한 일반 보호 기능을 제공합니다.

-   Office IRM(정보 권한 관리)을 사용하여 보호된 파일과의 완벽한 상호 운용성을 제공합니다.

-   FCI(파일 분류 인프라) 및 지원되는 PDF 작성 도구를 사용하여 보호된 PDF 파일과의 완벽한 상호 운용성을 제공합니다.

Microsoft Rights Management 공유 응용 프로그램은 [AD RMS 클라이언트 2.1 런타임](http://www.microsoft.com/download/details.aspx?id=38396)을 사용합니다. Microsoft Rights Management 공유 응용 프로그램은 AD RMS 2.1의 기능을 사용하여 최종 사용자에게 단순한 보호 및 사용 환경을 제공합니다.

RMS의 2013년 10월 릴리스를 설치하면 Office 2010을 사용해 문서를 기본적으로 보호할 수 있으며 다른 회사 직원에게 문서를 보낼 수 있습니다. 문서를 받은 사용자는 Azure Information Protection의 Azure Rights Management 서비스를 통해 문서를 사용할 수 있습니다. 또한 이 릴리스에서는 암호화 모드 2에서 AD RMS를 사용하는 경우 개별 사용자에 대해 RMS를 사용할 수 있으며 Azure Rights Management 서비스를 사용하는 다른 회사 직원의 콘텐츠도 사용할 수 있습니다. 암호화 모드 2에 대한 자세한 내용은 [AD RMS 암호화 모드](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx)를 참조하세요.

배포 정보는 [Microsoft Rights Management 공유 응용 프로그램 자동 배포](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)를 참조하세요.

## <a name="levels-of-protection--native-and-generic"></a>보호 수준 - 기본 및 일반
Microsoft Rights Management 공유 응용 프로그램은 다음 표에서 설명하는 것처럼 각기 다른 두 수준의 보호를 지원합니다.

|보호 유형|네이티브|제네릭|
|----------------------|----------|-----------|
|설명|텍스트, 이미지, Microsoft Office(Word, Excel, PowerPoint) 파일, .pdf 파일 및 Rights Management 서비스를 지원하는 기타 응용 프로그램 파일 형식의 경우 기본 보호는 권한 적용 및 암호화를 모두 포함하는 강력한 보호 수준을 제공합니다.|기타 모든 응용 프로그램 및 파일 형식의 경우 일반 보호는 사용자가 파일을 열 권한이 있는지를 확인하는 인증 및 .pfile 파일 형식을 사용하는 파일 캡슐화 기능이 모두 포함된 보호 수준을 제공합니다.|
|보호|파일은 다음과 같은 방식으로 완벽하게 암호화되며 보호가 적용됩니다.<br /><br />- 보호된 콘텐츠를 렌더링하기 전에 메일을 통해 파일을 받았거나 파일 또는 공유 권한을 통해 파일 액세스 권한을 부여받은 사용자가 정상적으로 인증을 해야 합니다.<br /><br />- 또한 IP 뷰어(보호된 텍스트, 이미지 파일의 경우)나 연결된 응용 프로그램(지원되는 기타 모든 파일 형식의 경우)에서 콘텐츠를 렌더링할 때는 파일 보호 시 콘텐츠 소유자가 설정한 사용 권한 및 정책이 완전하게 적용됩니다.|파일 보호는 다음과 같은 방식으로 적용됩니다.<br /><br />- 보호된 콘텐츠를 렌더링하기 전에 파일을 열 권한이 있으며 파일 액세스 권한을 부여받은 사용자가 정상적으로 인증해야 합니다. 권한 부여가 실패하면 파일이 열리지 않습니다.<br /><br />- 콘텐츠 소유자가 설정한 사용 권한 및 정책이 표시되어 해당하는 사용 정책의 권한 있는 사용자를 알려 줍니다.<br /><br />- 지원되지 않는 응용 프로그램의 경우 파일을 열고 액세스하는 권한 있는 사용자의 감사 로깅이 수행되기는 하지만 사용 권한은 적용되지 않습니다.|
|파일 형식에 대한 기본값|이 보호 수준은 다음 파일 형식에 대한 기본 보호 수준입니다.<br /><br />- 텍스트 및 이미지 파일<br /><br />- Microsoft Office(Word, Excel, PowerPoint) 파일<br /><br />- Portable Document Format(.pdf)<br /><br />자세한 내용은 [지원되는 파일 형식 및 파일 이름 확장명](#supported-file-types-and-file-name-extensions) 섹션을 참조하세요.|이 수준은 전체 보호를 통해 지원되지 않는 .vsdx, .rtf 등의 기타 모든 파일 형식에 대한 기본 보호 수준입니다.|
RMS 공유 응용 프로그램이 적용하는 기본 보호 수준을 변경할 수 있습니다. 기본 수준을 일반 수준으로 변경하거나 그 반대로 변경할 수 있으며, RMS 공유 응용 프로그램이 보호를 적용하지 않도록 차단할 수도 있습니다. 자세한 내용은 이 문서에서 [파일의 기본 보호 수준 변경](#changing-the-default-protection-level-of-files) 섹션을 참조하세요.

## <a name="supported-file-types-and-file-name-extensions"></a>지원되는 파일 형식 및 파일 이름 확장명
다음 표에는 Microsoft Rights Management 공유 응용 프로그램에서 기본적으로 지원하는 파일 형식이 나와 있습니다. 이러한 파일 형식의 경우 기본 보호를 적용하면 원래 파일 이름 확장명이 변경되며 해당 파일은 읽기 전용이 됩니다.

또한 사용자가 공유를 통해 보호하는 Word, Excel 또는 PowerPoint 파일을 RMS 공유 응용 프로그램이 기본적으로 보호하는 경우 이 작업을 수행하면 원본과 파일 이름은 같은 복사본이며 파일 이름 확장명은 **.ppdf** 인 두 번째 파일이 자동으로 만들어집니다. 이 파일 버전이 만들어지므로 RMS 공유 응용 프로그램을 설치하는 받는 사람은 기본 보호가 적용된 파일을 항상 열 수 있습니다.

일반 수준으로 보호되는 파일의 경우에는 원래 파일 이름 확장명이 항상 .pfile로 변경됩니다.

> [!WARNING]
> 파일 이름 확장명을 검사한 다음 그에 따라 작업을 수행하는 방화벽, 웹 프록시 또는 보안 소프트웨어를 사용하는 경우에는 이러한 새 파일 이름 확장명을 지원하도록 방화벽, 웹 프록시 또는 보안 소프트웨어를 다시 구성해야 할 수 있습니다.

|원래 파일 이름 확장명|RMS로 보호된 파일 이름 확장명|
|--------------------------------|-------------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.pjeg|
|.pdf|.ppdf|
|.png|.ppng|
|.tif|.ptif|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jt|.pjt|
¹ PDF 렌더링 기능은 Foxit에서 제공합니다. Copyright © 2003–2014 by Foxit C또는p또는ation.

다음 표에는 Microsoft Rights Management 공유 응용 프로그램이 Microsoft Office 2016, Office 2013 및 Office 2010에서 기본적으로 지원하는 파일 형식이 나와 있습니다. 이러한 파일의 경우에는 Rights Management 서비스를 통해 파일을 보호한 후에도 파일 이름 확장명이 동일하게 유지됩니다.

|Office에서 지원하는 파일 형식|Office에서 지원하는 파일 형식|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="changing-the-default-protection-level-of-files"></a>파일의 기본 보호 수준 변경
레지스트리를 편집하여 RMS 공유 응용 프로그램이 파일을 보호하는 방식을 변경할 수 있습니다. 예를 들어 기본 보호를 지원하는 파일을 RMS 공유 응용 프로그램에서 일반적으로 보호하도록 강제 지정할 수 있습니다.

이러한 작업을 수행해야 하는 이유는 다음과 같습니다.

-   모든 사용자가 자신의 모바일 장치에서 파일을 열 수 있도록 설정

-   기본 보호를 지원하는 응용 프로그램을 사용하지 않더라도 모든 사용자가 파일을 열 수 있도록 설정

-   파일 이름 확장명을 기준으로 하여 파일에 대해 작업을 수행하며, .pfile 파일 이름 확장명을 수용하도록 다시 구성할 수는 있지만 기본 보호를 위해 여러 파일 이름 확장명을 수용하도록 다시 구성할 수는 없는 보안 시스템 수용

마찬가지로 일반 보호가 기본적으로 적용되는 파일에 대해 RMS 공유 응용 프로그램이 기본 보호를 적용하도록 강제 지정할 수 있습니다. 부 개발자가 작성한 LOB(기간 업무) 응용 프로그램이나 ISV(Independent Software Vendor)에서 구매한 응용 프로그램 등 RMS API를 지원하는 응용 프로그램을 사용하는 경우 이러한 작업을 수행할 수 있습니다.

RMS 공유 응용 프로그램이 파일 보호를 차단하도록, 즉 기본 보호 또는 일반 보호를 적용하지 않도록 강제 지정할 수도 있습니다. 예를 들어 콘텐츠를 처리하려면 특정 파일을 열 수 있어야 하는 자동화된 응용 프로그램이나 서비스를 사용하는 경우 이러한 작업을 수행해야 할 수 있습니다. 특정 파일 형식에 대한 보호를 차단하면 사용자가 RMS 공유 응용 프로그램을 사용하여 해당 파일 형식의 파일을 보호할 수 없습니다. 이러한 파일을 보호하려고 하면 관리자가 보호를 차단했으므로 파일을 보호하기 위한 작업을 취소해야 한다는 메시지가 표시됩니다.

기본적으로 기본 보호가 적용되는 모든 파일에 대해 RMS 공유 응용 프로그램이 일반 보호를 적용하도록 구성하려면 다음 레지스트리를 편집합니다. RmsSharingApp 또는 FileProtection 키가 없으면 직접 만들어야 합니다.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: 이름이 *인 새 키를 만듭니다.

    이 설정은 임의의 파일 이름 확장명이 지정된 파일을 나타냅니다.

2.  새로 추가한 키 HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\\\*에서 데이터 값이 **Pfile**인 새 문자열 값(REG_SZ) **Encryption**을 만듭니다.

    이 설정을 사용하는 경우 RMS 공유 응용 프로그램이 일반 보호를 적용하게 됩니다.

이 두 설정을 사용하면 RMS 공유 응용 프로그램이 특정 파일 이름 확장명을 사용하는 모든 파일에 일반 보호를 적용합니다. 이러한 결과를 원하는 경우에는 추가 구성을 수행할 필요가 없습니다. 그러나 계속 기본적으로 보호되도록 특정 파일 형식에 대해 예외를 정의할 수 있습니다. 이렇게 하려면 각 파일 형식에 대해 추가로 3개 레지스트리를 편집해야 합니다.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: 파일 이름 확장명(앞의 마침표는 제외)이 이름으로 지정된 새 키를 추가합니다.

    예를 들어 파일 이름 확장명이 .docx인 파일의 경우 **DOCX**키를 만듭니다.

2.  새로 추가된 파일 형식 키(예: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**)에서 값이 **0**인 새 DWORD 값 **AllowPFILEEncryption**을 만듭니다.

3.  새로 추가된 파일 형식 키(예: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**)에서 값이 **Native**인 새 문자열 값 **Encryption**을 만듭니다.

이러한 설정을 사용하는 경우 파일 이름 확장명이 .doxc인 파일(RMS 공유 응용 프로그램에 의해 기본적으로 보호됨)을 제외한 모든 파일이 일반적으로 보호됩니다.

기본 보호를 지원하며 RMS 공유 응용 프로그램에서 일반적으로 보호하지 않도록 지정하기 위해 예외로 정의하려는 다른 파일 형식에 대해 이 3단계를 반복합니다.

다음 값을 지원하는 **Encryption** 문자열의 값을 변경하여 다른 시나리오에서도 비슷하게 레지스트리를 편집할 수 있습니다.

-   **Pfile**: 일반 보호

-   **Native**: 기본 보호

-   **Off**: 보호 차단

## <a name="see-also"></a>참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)

