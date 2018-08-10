---
title: Azure Information Protection 레이블에 대한 Exchange Online 메일 흐름 규칙 구성
description: Azure Information Protection 레이블에 대한 Exchange Online 메일 흐름 규칙을 구성하기 위한 지침 및 예제입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba4e4a4d-5280-4e97-8f5c-303907db1bf5
ms.reviewer: shakella
ms.suite: ems
ms.openlocfilehash: 546becbaa6cf7b20bb0daddc74a9cfa885f32d23
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39490176"
---
# <a name="configuring-exchange-online-mail-flow-rules-for-azure-information-protection-labels"></a>Azure Information Protection 레이블에 대한 Exchange Online 메일 흐름 규칙 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

다음 정보를 사용하여 Exchange Online의 메일 흐름 규칙을 구성함으로써 Azure Information Protection 레이블을 사용하고 특정 시나리오에 대해 추가 보호를 적용할 수 있습니다. 예를 들면 다음과 같습니다.

- 기본 레이블은 보호가 적용되지 않는 **일반**입니다. 이 레이블이 있으며 외부적으로 전송되는 메일의 경우 추가로 전달 금지 보호 작업을 적용합니다.

- **기밀 \ 파트너** 레이블이 있는 첨부 파일이 조직 외부의 사람에게 메일로 전송되고 이 메일이 보호되지 않는 경우 추가로 암호화 전용 보호 작업을 적용합니다.

메일이 이미 보호되고 있는 경우 작업으로 보호를 적용하는 메일 흐름 규칙은 무시됩니다. 예를 들어, 전달 금지로 보호된 메일 메시지는 Exchange 메일 흐름 규칙을 통해 암호화 전용 옵션을 사용하도록 변경할 수 없습니다.  

이러한 예를 확장하고 수정할 수도 있습니다. 예를 들어 더 많은 조건을 추가할 수 있습니다. 메일 흐름 규칙 구성에 대한 자세한 내용은 Exchange Online 설명서의 [Exchange Online의 메일 흐름 규칙(전송 규칙)](https://technet.microsoft.com/library/jj919238(v=exchg.150\).aspx)을 참조하세요.

메일 메시지를 암호화하도록 메일 흐름 규칙을 구성하는 방법에 대한 자세한 내용은 Office 설명서의 [Office 365에서 메일 메시지를 암호화하도록 메일 흐름 규칙 정의](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8)를 참조하세요. 

## <a name="where-labels-are-stored-in-emails-and-documents"></a>메일 및 문서에서 레이블이 저장되는 위치

Azure Information Protection 레이블이 메타데이터에 저장되므로 Exchange Online의 메일 흐름 규칙은 메시지 및 문서 첨부 파일에 대한 이 정보를 읽을 수 있습니다.

- 전자 메일에서 이 정보는 x- 헤더(**msip_labels: MSIP_Label_\<GUID>_Enabled=True;**)에 저장됩니다. 

- Word 문서(.doc 및 .docx), Excel 스프레드시트(.xls 및 .xlsx), PowerPoint 프레젠테이션(.ppt 및 .pptx) 및 PDF 문서(.pdf)의 경우 이 메타데이터는 **MSIP_Label_\<GUID>_Enabled=True** 사용자 지정 속성에 저장됩니다.  

레이블에 대한 GUID를 확인하려면 Azure Portal에서 Azure Information Protection 정책을 보거나 구성할 때 **레이블** 블레이드에서 레이블 ID 값을 찾습니다. 레이블이 적용된 파일의 경우 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 실행하여 GUID(MainLabelId 또는 SubLabelId)를 확인할 수도 있습니다. 레이블에 하위 레이블이 있는 경우 항상 부모 레이블이 아니라 하위 레이블의 GUID만 지정합니다.

메일 흐름 규칙을 구성하기 전에 사용하려는 Azure Information Protection 레이블의 GUID를 알고 있어야 합니다.

## <a name="example-configurations"></a>예제 구성

다음 예제에서는 다음 단계를 사용하여 새 메일 흐름 규칙을 생성합니다.

1. 웹 브라우저에서, 전역 관리자 권한이 부여된 회사 또는 학교 계정을 사용하여 Office 365에 로그인합니다. 

2. **관리** 타일을 선택합니다.

3. Office 365 관리 센터에서 **관리 센터** > **Exchange**를 선택합니다.

4. Exchange 관리 센터에서: **메일 흐름** > **규칙** > **+** > **새 규칙 만들기**를 선택합니다. 

> [!TIP]
> 규칙을 구성할 때 사용자 인터페이스에 문제가 있는 경우 Internet Explorer와 같은 다른 브라우저를 사용해 보세요.

예제에는 메일이 조직 외부로 전송될 때 보호를 적용하는 단일 조건이 있습니다. 선택할 수 있는 다른 조건에 대한 자세한 내용은 [Exchange Online에서 메일 흐름 규칙 조건 및 예외(조건자)](https://technet.microsoft.com/library/jj919235(v=exchg.150\).aspx))를 참조하세요.


### <a name="example-1-rule-that-applies-the-do-not-forward-option-to-emails-that-are-labeled-general-when-they-are-sent-outside-the-organization"></a>예제 1: **일반** 레이블이 지정된 메일이 조직 외부로 전송될 때 이 메일에 전달 금지 옵션을 적용하는 규칙

이 예제에서 **일반** 레이블에는 0e421e6d-ea17-4fdb-8f01-93a3e71333b8의 GUID가 있습니다. 이 규칙에 사용하려는 고유 레이블 또는 하위 레이블 GUID를 대체하세요. 

Azure Information Protection 정책에서 이 레이블은 메일을 **일반**으로 분류하기 위한 기본 레이블로 구성되었으며, 이 레이블은 보호를 적용하지 않습니다. 

1. **이름**에 `Apply Do Not Forward for General emails sent externally`와 같이 규칙 이름을 입력합니다.
 
2. **다음의 경우 이 규칙 적용**에서 **The recipient is located**(수신자 위치)를 선택하고, **Outside the organization**(조직 외부), **확인**을 차례로 선택합니다.

3. **추가 옵션**을 선택한 후 **조건 추가**를 선택합니다.
 
4. **그리고**에서 **A message header**(메시지 헤더)를 선택한 후 **includes any of these words**(다음 단어 중 하나 포함)를 선택합니다.
     
    a. **텍스트 입력**을 선택하고 `msip_labels`를 입력합니다.
     
    b. **단어 입력**을 선택하고 `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;`를 입력합니다.
    
    c. **+** 를 선택한 후 **확인**을 선택합니다.

5. **다음 작업 실행**에서 **메시지 보안 수정** > **Apply Office 365 Message Encryption and rights protection** > **전달 금지**를 선택한 후 **확인**을 선택합니다.
    
    이제 규칙 구성이 다음과 유사하게 표시됩니다. ![Azure Information Protection 레이블에 대해 구성된 Exchange Online 메일 흐름 규칙 - 예제1](./media/aip-exo-rule-ex1.png)

7. **저장**을 선택합니다. 

전달 금지 옵션에 대한 자세한 내용은 [메일에 대한 전달 금지 옵션](configure-usage-rights.md#do-not-forward-option-for-emails)을 참조하세요.

### <a name="example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization"></a>예제 2: 메일에 **기밀 \ 파트너** 레이블이 지정된 첨부 파일이 있고 메일이 조직 외부로 전송되는 경우 이러한 메일에 암호화 전용 옵션을 적용하는 규칙

이 예제에서 **기밀 \ 파트너** 하위 레이블의 GUID는 5ab1c8a1-8241-72bc-3f22-304a0558362a입니다. 이 규칙에 사용하려는 고유 레이블 또는 하위 레이블 GUID를 대체하세요. 

이 레이블은 파트너 공동 작업에 사용하는 문서를 분류하고 보호하는 데 사용됩니다.   

1. **이름**에 `Apply Encrypt to emails sent externally if protected attachments`와 같이 규칙 이름을 입력합니다.
 
2. **다음의 경우 이 규칙 적용**에서 **The recipient is located**(수신자 위치)를 선택하고, **Outside the organization**(조직 외부), **확인**을 차례로 선택합니다.

3. **추가 옵션**을 선택한 후 **조건 추가**를 선택합니다.
 
4. **그리고**에서 **Any attachment**(임의 첨부 파일)를 선택한 후 **has these properties, including any of these words**(다음 단어 중 하나를 포함하여 이러한 속성이 있음)를 선택합니다.
     
    a. **+** > **Specify a custom attachment property**(사용자 지정 첨부 파일 속성 지정)를 선택합니다.
  
    b. **속성**에 `MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled`를 입력합니다.
    
    c. **값**에 `True`를 입력합니다.
    
    d. **저장**을 선택한 후 **확인**을 선택합니다.

5. **다음 작업 실행**에서 **메시지 보안 수정** > **Apply Office 365 Message Encryption and rights protection** > **암호화**를 선택한 후 **확인**을 선택합니다.
    
    이제 규칙 구성이 다음과 유사하게 표시됩니다. ![Azure Information Protection 레이블에 대해 구성된 Exchange Online 메일 흐름 규칙 - 예제1](./media/aip-exo-rule-ex2.png)

6. **저장**을 선택합니다. 

암호화 옵션에 대한 자세한 내용은 [메일에 대한 암호화 전용 옵션](configure-usage-rights.md#encrypt-only-option-for-emails)을 참조하세요.


## <a name="next-steps"></a>다음 단계

Exchange Online 메일 흐름 규칙에 사용할 레이블을 만들고 구성하는 방법에 대한 자세한 내용은 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.

또한 첨부 파일이 포함된 메일 메시지를 분류하려면 Azure Information Protection [정책 설정](configure-policy-settings.md): **첨부 파일이 있는 메일 메시지의 경우 해당 첨부 파일의 최상위 분류와 일치하는 레이블 적용**을 사용하는 것이 좋습니다.


