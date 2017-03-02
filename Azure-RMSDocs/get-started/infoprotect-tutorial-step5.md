---
title: "빠른 시작 자습서 5단계 - AIP"
description: "조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 20분 정도의 소개 자습서 5단계입니다."
keywords: 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 351ba4f71ac36194494ed315466522120a61692c
ms.lasthandoff: 02/24/2017


---


# <a name="step-5-see-sharing-of-protected-files-in-action-and-track-your-document"></a>5단계: 작업에서 보호된 파일 공유 확인 및 문서 추적 

>*적용 대상: Azure Information Protection*

이 자습서의 마지막 단계에서는 이미 만들어 놓았고 파트너나 동료에게 보낼 Word 문서 또는 Excel 스프레드시트를 찾습니다. 이 자습서에서 실제로 포함되는 텍스트는 중요하지 않지만, 텍스트를 포함하면 권한이 있는 수신자가 읽었는지 더 쉽게 확인할 수 있습니다.

이제 이 문서를 메일로 안전하게 공유할 준비가 되었습니다. 

## <a name="to-safely-share-your-document-by-email"></a>문서를 메일로 안전하게 공유하려면

1. 파일 탐색기에서 문서를 마우스 오른쪽 단추로 클릭하고 **분류 및 보호**를 선택합니다. **분류 및 보호 - Azure Information Protection** 대화 상자가 열립니다.

    ![Azure Information Protection 빠른 시작 자습서 5단계 - 마우스 오른쪽 단추로 분류 및 제거 클릭](../media/classify-protect-dialog.png)

2. **사용자 지정 권한으로 보호**를 선택합니다. 그러면 추가 옵션이 표시됩니다.

3. **사용 권한 선택**에 대해 기본값인 **뷰어 - 보기 전용**을 그대로 둡니다.

    이 설정을 사용하면 받는 사람은 문서를 볼 수 있지만 편집하거나 인쇄할 수는 없습니다.

4. 조직에서 업무를 같이 하는 사람에게 문서를 보낼 때와 마찬가지로 **사용자 선택**에 회사 메일 주소를 하나 이상 입력합니다. 현재 Azure Information Protection에서는 개인용 메일 주소를 지원하지 않으므로 **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같은 회사 메일 주소를 지정해야 합니다. 

    또는 주소록을 클릭하여 동료의 전자 메일 주소를 선택합니다.

    ![Azure Information Protection 빠른 시작 자습서 5단계 - 사용자 지정 권한으로 보호](../media/protect-custom-permissions.png)  
    
    주소를 지정한 후 이후 단계에서 사용할 것이므로 클립보드에 복사합니다.

5. **적용**을 클릭하고 **작업 완료** 메시지가 표시될 때까지 기다린 후 결과를 확인합니다. 그런 다음 **닫기**를 클릭합니다.

4. 파일 탐색기에서 파일을 다시 마우스 오른쪽 단추로 클릭하고, 이번에는 **보내기** > **전자 메일로**를 선택합니다. 이렇게 하면 일부 기본 텍스트가 변경된 전자 메일 메시지에 문서가 첨부됩니다.

5. 기본 텍스트를 변경하기 전에 앞서 지정한 전자 메일 주소를 **받는 사람** 상자에 붙여 넣습니다. 

6. 경우에 따라 **제목** 상자에 선택한 제목을 입력합니다(예: **보호된 문서 공유**). 

7. 받는 사람에게 적합하게 기본 메시지 설명을 수정합니다. 그렇지만 다음 텍스트를 추가합니다.

    **Microsoft Azure Information Protection로 이 파일을 보호했습니다. 처음 사용할 경우 https://aka.ms/rms-signup의 지침을 참조하세요.** 

    ![Azure Information Protection 빠른 시작 자습서 5단계 - 전자 메일로 보호된 문서 공유](../media/share-protected-email.png)

    **보내기**를 클릭합니다.

이제 보호된 문서를 보냈으니 수신자에게 도착하기를 기다렸다가 열어 보라고 요청하면 됩니다. 

## <a name="ask-your-recipients-to-open-the-emailed-document"></a>수신자에게 메일의 문서를 열라고 요청

보호된 문서가 메일 첨부 파일로 전송되면 수신자는 다양한 장치를 사용하여 읽을 수 있습니다. 이러한 장치에는 iPad, iPhone, Android 태블릿 및 전화, Mac 컴퓨터, Windows 컴퓨터 등이 포함됩니다.

전송된 메일 메시지를 읽도록 요청합니다. Rights Management를 통해 보호되는 첨부 파일을 처음으로 받은 경우라고 가정하면 받는 사람에게 지침 링크를 클릭할 것을 요청합니다. 그러면 Microsoft Azure Information Protection에 대한 **시작** 페이지가 표시되며 회사 전자 메일 주소를 입력하도록 요구됩니다.

**등록**을 클릭하면 Azure Information Protection은 조직에 Azure Rights Management 데이터 보호 서비스를 포함하는 구독이 있는지 여부를 확인합니다. 그렇지 않은 경우 무료 계정을 신청할 수 있습니다.

### <a name="instructions-for-recipient-to-view-the-protected-document-attachment"></a>받는 사람에 대한 지침: 보호된 문서 첨부 파일을 보호하려면

1. Office가 설치된 PC 또는 모바일 장치에서 첨부 파일을 열고 문서를 읽습니다.  

2.  사용자 이름과 암호를 묻는 메시지가 표시되면 메일과 첨부 파일을 보내는 데 사용된 것과 같은 메일 주소 형식을 사용하여 사용자 이름을 입력합니다. 예를 들면 **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같습니다. 암호로는 개인용 RMS에 가입할 때 입력했던 암호를 입력합니다. 또는 조직에 Office 365와 같은 클라우드 서비스가 있거나 Azure를 사용하는 경우에는 실제 작업 암호를 입력합니다.

3. 열리면 문서 내용을 읽습니다. 읽기 전용이므로 내용을 변경할 수는 없습니다.

선택적 단계로, 수신자는 원래 메일에서 지정하지 않은 다른 사람에게 메일을 전달할 수 있습니다. 이러한 사용자는 첨부 파일을 열 수 없습니다. 사용자 이름에 대한 승격을 처리할 때 문서에 대한 액세스가 거부됩니다.

이제 받는 사람이 첨부 파일을 열었고, 선택적으로 해당 파일을 다른 사람에게 전달하기도 했으므로 문서를 추적할 준비가 되었습니다.

## <a name="to-track-your-protected-document"></a>보호된 문서를 추적하려면

1.  보호 및 공유한 문서를 엽니다. 정보 배너에는 사용자가 지정한 사용자 지정 보호 설정이 표시됩니다.

    ![사용자 지정 보호에 대한 정보 배너](../media/information-banner-custom-protection.png)

2.  **홈** 탭에서 **보호** > **추적 및 해지**를 클릭합니다.

    ![추적 사용 옵션](../media/track-usage-callout.png)

    이렇게 하면 문서 추적 사이트가 열립니다.

2.  **보호와 공유를 원하는 대로** 페이지가 보이면 **로그인**을 클릭하고 사용자 이름과 암호를 다시 입력합니다.

3.  **공유 문서** 페이지에 공유한 문서 이름이 표시됩니다. 이 시점에서는 이 파일이 유일하게 표시된 파일이지만, 보호된 문서를 더 공유하면 목록도 커집니다.

    이 페이지에는 문서를 공유한 시기(보호된 첨부 파일이 있는 메일을 보낸 시기), 마지막 활동 날짜, 메일을 받는 수신자가 표시됩니다. 추가 세부 정보를 확인하려면 문서 이름을 클릭합니다.

4.  클릭한 파일의 이름이 표시된 새 페이지에서는 해당 문서만의 요약 세부 정보와 문서에 사용할 수 있는 다른 옵션(**목록**, **타임라인**, **지도**, **설정**)의 목록을 확인할 수 있습니다.

    각 옵션을 클릭하며 보호된 문서를 추적하는 여러 가지 방법을 탐색합니다. 또는 **요약** 페이지에 있는 동안 **Excel에서 열기** 를 클릭하여 정보를 스프레드시트로 내보내거나 **액세스 취소** 를 클릭하여 문서 공유를 중지할 수도 있습니다.

필요한 경우 이 사이트로 돌아와 보호된 문서에 대한 추가 활동을 추적하거나 액세스를 취소할 수 있습니다. 모바일 장치나 태블릿에서 브라우저를 사용하여 [문서 추적](http://go.microsoft.com/fwlink/?LinkId=529562)링크로 사이트에 액세스할 수도 있습니다.



|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|안전하게 공유할 수 있는 파일 보호에 대한 전체 지침|[파일 또는 전자 메일 분류 및 보호](../rms-client/client-classify-protect.md)|
|다른 사용자가 등록할 수 있는 무료 계정 정보|[개인용 RMS 및 Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|문서 추적 사이트 사용 정보|[문서 추적 및 취소](../rms-client/client-track-revoke.md)


## <a name="next-steps"></a>다음 단계

이제 기본 Azure Information Protection 정책, 이러한 정책의 사용자 지정 방법 및 Word 문서에 대해 레이블 지정이 작동하는 방식을 확인했으므로, 다른 설정을 사용해 보고 Azure Information Protection을 지원하는 다른 Office 프로그램(Excel, PowerPoint, Outlook)에서 이러한 설정이 작동하는 방식을 확인해 보세요. Azure Information Protection 클라이언트를 설치할 때 이러한 응용 프로그램이 열려 있었던 경우에는 이러한 응용 프로그램을 닫았다가 다시 연 후 Azure Information Protection에서 이러한 응용 프로그램을 사용해 보세요.

더 많은 문서를 공유해 보고 사용되는 방식을 추적하고, 문서 취소 작업 방법을 확인합니다.

Azure Information Protection [질문과 대답](faqs.md)에서 일부 내용을 읽어보고 다른 설명서 문서의 내용도 살펴보는 것이 도움이 될 수 있습니다. 그러나 조직에 대해 Azure Information Protection 배포를 시작할 준비가 되면 그다음 단계로 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)을 확인해야 합니다. 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
