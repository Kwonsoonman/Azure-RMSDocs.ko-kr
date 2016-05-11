---
# required metadata

title: Azure RMS 빠른 시작 자습서 - 3단계 | Azure RMS
description: 15분 이내에 완료할 수 있는 5단계를 통해 조직에서 Microsoft Azure 권한 관리 사용을 빠르게 시작하는 방법을 확인할 수 있는 자습서의 세 번째 단계입니다.
keywords:
author: Cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.assetid: c604e749-8918-40e8-8148-6bd000cb2be2

# optional metadata

ROBOTS: 
audience:
ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
ms.tgt_pltfrm:
ms.technology:
ms.custom:

---


# Azure RMS 빠른 시작 3단계: 보호할 문서를 메일로 보내기

다음으로 이동합니다. 
> [!div class="op_single_selector"]
- [소개](quick-start-tutorial.md)
- [1단계: Azure RMS 활성화](tutorial-step1.md)
- [2단계: RMS 공유 앱 설치](tutorial-step2.md)
- [3단계: 기밀 문서를 메일로 보내기](tutorial-step3.md)
- [4단계: 받는 사람이 문서 읽기](tutorial-step4.md)
- [5단계: 문서 추적](tutorial-step5.md)


이 단계에서는 먼저 Word를 사용하여 보호할 문서를 나타내는 문서를 저장하고 **Confidential.docx**라는 이름을 지정합니다. 이 자습서에서 실제로 포함되는 텍스트는 중요하지 않지만, 텍스트를 포함하면 권한이 있는 수신자가 읽었는지 더 쉽게 확인할 수 있습니다. 예를 들어, 다음과 같이 입력할 수 있습니다. **메일의 첨부 파일에서 이 내용을 읽고 있다면 발신자가 Azure RMS로 보호된 파일을 성공적으로 공유한 것입니다.**

이제 이 문서를 메일로 안전하게 공유할 준비가 되었습니다.

![](../media/AzRMS_Tutorial_3_Screenshots.png)

### 문서를 메일로 안전하게 공유하려면

1.  Outlook을 사용하여 메시지를 새로 작성하고 방금 만든 파일을 첨부합니다.

2.  **받는 사람** 상자에 비즈니스 메일 주소를 하나 이상 입력합니다. 현재 Azure 권한 관리에서는 인터넷 공급자로부터 받아 집에서 사용할 수 있는 개인용 메일 주소를 지원하지 않으므로 **janetm@contoso.com** 또는 **p.dover@fabrikam.com**과 같은 비즈니스 메일 주소를 지정해야 합니다. 문서를 받는 사람에게 Azure Rights Management가 있는지 여부는 걱정할 필요가 없습니다.

3.    **기밀 문서** 와 같은 제목을 입력한 다음 메일에 **이 기밀 문서를 읽고, 다른 사람과는 결코 공유하지 마십시오**와 같은 짧은 메시지를 입력합니다.

4.  그런 다음 **메시지** 탭의 **RMS** 그룹에서 **보호된 항목 공유** 를 클릭하고 **보호된 항목 공유** 를 다시 클릭합니다.

5.  **보호된 항목 공유** 대화 상자에서:

    1.  **뷰어 – 보기 전용**을 선택합니다.

        이는 수신자가 문서를 볼 수 있지만 편집하거나 인쇄할 수는 없는 것을 의미합니다.

    2.  **누군가가 이 문서를 열려고 하면 내게 메일 보내기**를 선택합니다.

        수신자가 첨부 파일을 열려고 할 때마다, 그리고 수신자가 메일을 동료에게 전달한 등의 경우에 다른 사람이 첨부 파일을 열려고 할 때마다 메일로 알림을 받습니다. 마지막 시나리오에서는 액세스가 거부된 것을 알 수 있고, 사용자 세부 정보에서 그 사람에게 열 수 있는 문서 복사본을 보낼 것인지 여부를 결정할 수 있습니다.

    3.  **이러한 문서에 대한 액세스를 즉시 취소할 수 있도록 허용**을 선택합니다.

        이 옵션을 사용하려면 수신자가 첨부 파일을 열 때마다 인터넷 연결이 필요하지만, 나중에 문서를 취소할 경우 그 뒤에는 열 수가 없다는 이점이 있습니다. 이 옵션을 선택하지 않으면 인터넷에 연결되어 있지 않은 동안에도 수신자가 문서를 열 수 있지만, 나중에 문서를 취소해도 실제로 적용될 때까지 지연이 생긴다는 단점이 있습니다.

    4.  **지금 보내기**를 클릭합니다.

        첨부 파일이 있는 메일이 지정된 메일 주소로 전송됩니다. 메일 메시지 외에도 Azure Rights Management로 보호된 첨부 문서를 읽는 방법에 대한 지침이 수신자에게 표시됩니다.

이제 보호된 문서를 보냈으니 수신자에게 도착하기를 기다렸다가 열어 보라고 요청하면 됩니다. 그러나 마지막 단계에서 첨부 파일을 추적할 때 다시 사용해야 하므로 Outlook은 닫지 마세요.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|메일로 공유하는 파일의 보호 방법에 대한 전체 지침과 대체 방법|[Rights Management 공유 응용 프로그램을 사용하여 메일로 공유하는 파일 보호](../rms-client/sharing-app-protect-by-email.md)|
|**보호된 항목 공유** 대화 상자의 옵션 정보|[Rights Management 공유 응용 프로그램에 대한 대화 상자 옵션](../rms-client/sharing-app-dialog-box.md)|


>[!div class="step-by-step"]
[« 2단계](tutorial-step2.md)
[4단계 »](tutorial-step4.md)

<!--HONumber=Apr16_HO3-->


