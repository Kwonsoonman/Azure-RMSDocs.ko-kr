---
title: "빠른 시작 자습서 5단계 | Azure Information Protection"
description: "조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 5단계로 약 30분 만에 완료해야 합니다."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1af9f3b3451bf8ceafbaf3cddd2b26c37fe9d597
ms.openlocfilehash: d607c19d37da6b6fb23513067e9e30f33f0260de


---


# 5단계: 작업에서 보호된 파일 공유 확인 및 문서 추적 

>*적용 대상: Azure Information Protection*

이 자습서의 마지막 단계에서는 이미 만들어 놓았고 파트너나 동료에게 보낼 Word 문서를 찾습니다. 이 자습서에서 실제로 포함되는 텍스트는 중요하지 않지만, 텍스트를 포함하면 권한이 있는 수신자가 읽었는지 더 쉽게 확인할 수 있습니다.

이제 이 문서를 메일로 안전하게 공유할 준비가 되었습니다. 

## 문서를 메일로 안전하게 공유하려면

1.  Word에서 문서를 엽니다. 기본 레이블 값이 **내부용**으로 다시 자동 적용됩니다. 

2.  **홈** 탭의 **RMS** 그룹에서 **보호된 항목 공유**를 클릭하고 메뉴에서 **보호된 항목 공유**를 클릭합니다.

    ![Azure Information Protection 빠른 시작 자습서 5단계 - 보호된 항목 공유](../media/share-protected-callout.png)

    다음 그림과 유사한 **보호된 항목 공유** 대화 상자가 표시됩니다.

    ![Azure Information Protection 빠른 시작 자습서 5단계 - 보호된 항목 공유 대화 상자](../media/example-share-protected-dialog.png)

3. 조직에서 업무를 같이 하는 사람에게 문서를 보낼 때와 마찬가지로 **사용자** 상자에 회사 메일 주소를 하나 이상 입력합니다. 또는 동료의 전자 메일 주소를 지정할 수 있습니다. 현재 Azure Information Protection에서는 개인용 전자 메일 주소를 지원하지 않으므로 **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같은 회사 메일 주소를 지정해야 합니다. 

    문서를 받는 사람에게 Azure Information Protection이 있는지 여부는 걱정할 필요가 없습니다.

4. **뷰어 – 보기 전용**을 선택합니다.

    이는 수신자가 문서를 볼 수 있지만 편집하거나 인쇄할 수는 없는 것을 의미합니다.

5. **누군가가 이 문서를 열려고 하면 내게 메일 보내기**를 선택합니다.

    수신자가 첨부 파일을 열려고 할 때마다, 그리고 수신자가 메일을 동료에게 전달한 등의 경우에 다른 사람이 첨부 파일을 열려고 할 때마다 메일로 알림을 받습니다. 문서가 전달되면 액세스가 거부된 것을 알 수 있고, 사용자 세부 정보에서 그 사람에게 열 수 있는 문서 복사본을 보낼 것인지 여부를 결정할 수 있습니다.

6. **이러한 문서에 대한 액세스를 즉시 취소할 수 있도록 허용**을 선택합니다.

    이 옵션을 사용하려면 수신자가 첨부 파일을 열 때마다 인터넷 연결이 필요하지만, 나중에 문서를 취소할 경우 그 뒤에는 열 수가 없다는 이점이 있습니다. 

4.  **보내기**를 클릭하면 기본 지침 텍스트와 함께 지정한 받는 사람에게 전송될 준비가 된 전자 메일 메시지를 확인합니다. 예를 들면 다음과 같습니다.

    ![보호된 항목을 공유하는 경우 전자 메일 메시지 예](../media/example-email-share-protected.png)
    
    **참고**: Azure Information Protection 클라이언트를 설치할 때 Outlook을 열면 이전 그림에 나타났던 Information Protection 표시줄이 표시되지 않습니다. 보호된 문서를 공유하는 방법을 보여 주는 이 단계에서 특별히 사용되지 않은 것이므로 자습서를 완료하기 위해 Outlook을 닫았다가 다시 열지 않아도 됩니다. Azure Information Protection 클라이언트를 설치한 이후 Outlook을 열면 Word 문서를 처음 열 때와 같이, Azure Information Protection 정책에서 이 전역 설정을 구성한 결과로 이 전자 메일 메시지에 **내부용** 레이블이 적용됩니다.
    
    원래의 Word 문서와 확장자가 **.ppdf**로 파일 이름이 동일한 파일 두 개의 첨부파일을 받게 됩니다. .ppdf 버전은 받는 사람에게 보호된 문서를 지원하는 Office 버전이 없을 경우 Rights Management 공유 응용 프로그램이 자동으로 생성하는 보호된 PDF 파일입니다. 이 추가 파일을 사용하면 받는 사람은 Rights Management 공유 응용 프로그램과 함께 설치된 뷰어를 사용하여 보호된 문서를 읽을 수 있습니다.

    전자 메일 메시지에서 **보내기**를 클릭합니다.

이제 보호된 문서를 보냈으니 수신자에게 도착하기를 기다렸다가 열어 보라고 요청하면 됩니다. 그러나 마지막 단계에서 공유 문서를 추적할 때 다시 사용해야 하므로 Word는 닫지 마세요.

## 수신자에게 메일의 문서를 열라고 요청

보호된 문서가 메일 첨부 파일로 전송되면 수신자는 다양한 장치를 사용하여 읽을 수 있습니다. 이러한 장치에는 iPad, iPhone, Android 태블릿 및 전화, Mac 컴퓨터, Windows 컴퓨터 등이 포함됩니다.

전송된 메일 메시지를 읽도록 요청합니다. Rights Management를 통해 보호되는 첨부 파일을 처음으로 받은 경우라고 가정하면 받는 사람에게 지침 링크를 클릭할 것을 요청합니다. 그렇게 하면 [Microsoft RMS 시작!](https://portal.azurerms.com/#/rmshelp) 페이지가 나타나며 RMS 공유 응용 프로그램을 설치하고 필요한 경우 무료 계정으로 가입하라는 지침이 제공됩니다. 그러면 보호된 첨부 파일을 읽을 준비가 완료됩니다.

### 받는 사람에 대한 지침: 보호된 문서 첨부 파일을 보호하려면

1. 첨부 파일을 하나 열어 문서를 읽습니다.
    
    - 장치에 Rights Management를 지원하는 Office 버전이 있는 경우:
    
        -  파일 이름 확장명이 **.docx**인 문서를 엽니다.
        
    - Rights Management를 지원하는 Office 버전이 없거나, 확실하지 않거나, 단순히 Rights Management 공유 응용 프로그램에서 뷰어를 시도하려는 경우: 
    
        - 파일 이름 확장명이 **.ppdf**인 문서를 엽니다.

2.  사용자 이름과 암호를 묻는 메시지가 표시되면 메일과 첨부 파일을 보내는 데 사용된 것과 같은 메일 주소 형식을 사용하여 사용자 이름을 입력합니다. 예를 들어 **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같이 입력합니다. 암호로는 개인용 RMS에 가입할 때 입력했던 암호를 입력합니다. 또는 조직에 Office 365와 같은 클라우드 서비스가 있거나 Azure를 사용하는 경우에는 실제 작업 암호를 입력합니다.

3. 열리면 문서 내용을 읽습니다. 읽기 전용이므로 내용을 변경할 수는 없습니다.

선택적 단계로, 수신자는 원래 메일에서 지정하지 않은 다른 사람에게 메일을 전달할 수 있습니다. 이러한 사용자는 첨부 파일을 열 수 없습니다. 사용자 이름에 대한 승격을 처리할 때 문서에 대한 액세스가 거부됩니다.

이제 수신자가 첨부 파일을 열었고, 선택적인 단계를 수행했다면 다른 사람에게 메일을 전달하기도 했으므로 이 활동에 대해 보고하는 메일 알림을 받습니다. 그러나 메일 메시지는 시간이 지나면 잃어버리기가 쉽기 때문에, 문서에 액세스하는 사람을 추적하기에 더 좋은 방법은 마지막 절차와 같이 문서 추적 사이트를 사용하는 것입니다.

## 보호된 문서를 추적하려면

1.  Word로 돌아가 **홈** 탭의 **RMS** 그룹에서 **보호된 항목 공유**를 클릭하고 메뉴에서 **사용량 추적**을 클릭합니다.

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
|메일로 공유하는 파일의 보호 방법에 대한 전체 지침과 대체 방법|[Rights Management 공유 응용 프로그램을 사용하여 메일로 공유하는 파일 보호](../rms-client/sharing-app-protect-by-email.md)|
|**보호된 항목 공유** 대화 상자의 옵션 정보|[Rights Management 공유 응용 프로그램에 대한 대화 상자 옵션](../rms-client/sharing-app-dialog-box.md)|
|다른 사용자가 등록할 수 있는 무료 계정 정보|[개인용 RMS 및 Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|문서 추적 사이트 사용 정보|[문서 추적 및 취소](../rms-client/sharing-app-track-revoke.md)


## 다음 단계

이제 기본 Azure Information Protection 정책, 이러한 정책의 사용자 지정 방법 및 Word 문서에 대해 레이블 지정이 작동하는 방식을 확인했으므로, 다른 설정을 사용해 보고 Azure Information Protection을 지원하는 다른 Office 프로그램(Excel, PowerPoint, Outlook)에서 이러한 설정이 작동하는 방식을 확인해 보세요. Azure Information Protection 클라이언트를 설치할 때 이러한 응용 프로그램이 열려 있었던 경우에는 이러한 응용 프로그램을 닫았다가 다시 연 후 Azure Information Protection에서 이러한 응용 프로그램을 사용해 보세요.

더 많은 문서를 공유해 보고 사용되는 방식을 추적하고, 문서 취소 작업 방법을 확인합니다.

Azure Information Protection [질문과 대답](faqs.md)에서 일부 내용을 읽어보고 다른 설명서 문서의 내용도 살펴보는 것이 도움이 될 수 있습니다. 그러나 조직에 대해 Azure Information Protection 배포를 시작할 준비가 되면 그다음 단계로 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)을 확인해야 합니다. 


<!--HONumber=Sep16_HO4-->


