---
title: AIP 클라이언트로 보호된 문서 보기 및 사용
description: Azure Information Protection 클라이언트를 설치해야 하는 보호된 문서를 보고 사용하기 위한 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: article
ms.service: information-protection
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 518fd44053f6a6ee0c4b45024d5be0ac0122ec22
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808224"
---
# <a name="user-guide-view-and-use-files-that-have-been-protected-by-rights-management"></a>사용자 가이드: Rights Management로 보호된 파일 보기 및 사용

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

보호된 문서를 그냥 열어서 볼 수 있는 경우도 있습니다. 예를 들어 전자 메일 메시지의 첨부 파일을 두 번 클릭하거나 파일 탐색기에서 파일을 두 번 클릭할 수도 있고 파일의 링크를 클릭할 수도 있습니다.

파일이 바로 열리지 않으면 **Azure Information Protection 뷰어**에서 열 수 있습니다. 이 뷰어에서는 보호된 텍스트 파일, 보호된 이미지 파일, 보호된 PDF 파일 및 파일 이름 확장명이 **.pfile**인 모든 파일을 열 수 있습니다.

이 뷰어는 Azure Information Protection 클라이언트의 일부로 자동으로 설치되거나 별도로 설치할 수 있습니다. Microsoft 웹 사이트의 [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) 페이지에서 클라이언트와 뷰어를 둘 다 설치할 수 있습니다. 클라이언트를 설치하는 방법에 대한 자세한 내용은 [Azure Information Protection 클라이언트 다운로드 및 설치](install-client-app.md)를 참조하세요.

> [!NOTE]
> 클라이언트를 설치하면 더 많은 기능을 사용할 수 있지만 로컬 관리자 권한이 필요하며 전체 기능을 사용하려면 조직에 대한 해당 서비스가 있어야 합니다.
> 
>-Azure Information Protection
> 
>-Azure Rights Management
> 
>-Active Directory Rights Management Services 
> 
> 다른 조직의 누군가로부터 보호된 문서를 받았거나 PC에 대해 로컬 관리자 권한이 없으면 뷰어를 설치합니다.

보호된 문서를 열 수 있으려면 응용 프로그램이 "RMS 지원" 프로그램이어야 합니다. Office 앱 및 Azure Information Protection 뷰어가 RMS 지원 응용 프로그램의 예입니다. 유형 및 지원되는 장치별로 응용 프로그램 목록을 보려면 [RMS 지원 응용 프로그램](../requirements-applications.md#rms-enlightened-applications) 표를 참조하세요.  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg를 메일 첨부 파일로 사용

**message.rpmsg**를 메일 첨부 파일로 보는 경우 보호된 문서가 아니며 첨부 파일로 표시되는 보호된 메일 메시지입니다. Windows PC에서 이 보호된 메일 메시지를 보기 위해 Windows용 Azure Information Protection 뷰어를 사용할 수는 없습니다. 대신 Office Outlook과 같은 Rights Management 보호를 지원하는 Windows용 전자 메일 응용 프로그램이 필요합니다. 또는 웹용 Outlook을 사용할 수 있습니다.

그러나 iOS 또는 Android 장치에서는 Azure Information Protection 앱을 사용하여 이러한 보호된 메일 메시지를 열 수 있습니다. 이러한 모바일 장치용 앱은 Microsoft 웹 사이트의 [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) 페이지에서 다운로드할 수 있습니다.

## <a name="prompts-for-authentication"></a>인증 프롬프트

보호된 파일을 볼 수 있으려면 파일을 보호하는 데 사용한 Rights Management 서비스가 사용자에게 파일을 볼 수 있는 권한이 있는지 확인해야 합니다. 서비스는 이 확인 작업을 위해 사용자 이름 및 암호를 확인합니다. 이러한 자격 증명은 어떤 경우에 캐시될 수도 있고 로그인을 요청하는 메시지가 표시되지 않습니다. 다른 경우 자격 증명을 제공하라는 메시지가 표시됩니다.

조직에 사용할 수 있는 클라우드 기반 계정이 없고(Office 365 또는 Azure) 해당 온-프레미스 버전(AD RMS)을 사용하지 않는 경우, 두 가지 옵션이 있습니다.

- 보호된 전자 메일이 전송된 경우 지침에 따라 소셜 ID 공급자(예: Gmail 계정용 Google)에 로그인하거나 일회성 암호를 신청하십시오.

- Rights Management에 의해 보호되는 문서를 열 수 있도록 자격 증명을 수락할 무료 계정을 신청할 수 있습니다. 이 계정을 신청하려면 링크를 클릭하여 [개인용 RMS](http://go.microsoft.com/fwlink/?LinkId=309469)를 신청하고 개인 이메일 주소 대신 회사 이메일 주소를 사용하십시오. 

## <a name="to-view-and-use-a-protected-document"></a>보호된 문서를 보고 사용하려면

1. 보호된 파일을 엽니다. 예를 들어 파일이나 첨부 파일을 두 번 클릭하거나 파일의 링크를 클릭합니다. 앱을 선택하라는 메시지가 나타나면 **Azure Information Protection 뷰어**를 선택합니다. 

2. **로그인** 또는 **등록** 페이지가 표시되면 **로그인**을 클릭하고 자격 증명을 입력합니다. 보호된 파일이 첨부 파일로 전송된 경우에는 파일을 전송하는 데 사용된 것과 같은 전자 메일 주소를 지정해야 합니다.
    
    허용되는 계정이 없는 경우 이 페이지에서 [인증 프롬프트](#prompts-for-authentication) 섹션을 참조하세요.

3. 읽기 전용 버전의 파일이 **Azure Information Protection 뷰어**에서 열립니다. 권한이 있으면 파일을 인쇄하고 편집할 수 있습니다. 

    **권한**을 클릭하면 파일에 대한 권한을 확인할 수 있습니다. **권한** 대화 상자에서는 추가 권한과 함께 새 파일 버전을 요청하려는 경우 연락할 수 있는 파일 소유자도 확인할 수 있습니다.
    
    권한 및 각 권한에 포함되는 사용 권한에 대한 자세한 내용은 [권한 수준에 포함된 권한](../configure-usage-rights.md#rights-included-in-permissions-levels)을 참조하세요.

4. 파일을 편집하려면 **다른 이름으로 저장**을 클릭합니다. 이렇게 하면 보호되지 않은 파일을 레이블 없이 원본 파일 이름 확장명으로 저장할 수 있습니다. 그런 다음 해당 파일 형식과 연결된 응용 프로그램을 사용하여 파일을 편집할 수 있습니다. 
    
    파일 편집을 마치면 파일 탐색기에서 파일을 마우스 오른쪽 단추로 클릭하여 레이블을 다시 적용합니다. 그러면 보호가 다시 적용됩니다.

5. 보호된 파일을 추가로 열려는 경우 **열기** 옵션을 사용하여 뷰어에서 해당 파일을 직접 찾아볼 수 있습니다. 그러면 뷰어에서 원본 파일 대신 선택한 파일이 표시됩니다. 

> [!TIP]
> 보호된 파일이 열리지 않고 전체 Azure Information Protection 클라이언트를 설치한 경우 **설정 재설정** 옵션을 시도해 봅니다. Office 앱에서 이 옵션에 액세스하려면 **보호** 단추 > **도움말 및 피드백** > **설정 재설정**을 선택합니다. 
> 
> [설정 재설정 옵션에 대한 자세한 내용](client-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>기타 지침
Azure Information Protection 사용자 가이드의 사용 방법 지침:

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

