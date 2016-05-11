---
# required metadata

title: 시나리오 - 다른 조직의 사용자와 Office 파일 공유 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 시나리오 - 다른 조직의 사용자와 Office 파일 공유
이 시나리오와 지원 사용자 문서에서는 사용자가 다른 조직의 사용자와 Office 파일을 안전하게 메일로 주고받을 수 있도록 Azure 권한 관리를 사용합니다. 예를 들어 Office 파일은 파트너를 위한 가격 목록 정보, 대리점을 위한 제품 목록 또는 배송 시간 표시줄과 잠재적 고객 목록이 포함된 Word 문서, Excel 스프레드시트 또는 PowerPoint 프레젠테이션일 수 있습니다. 사용자가 이러한 지침을 따르면 전자 메일 메시지에 첨부된 파일이 Azure 권한 관리를 통해 보호됩니다.

이 시나리오는 다음과 같은 상황에 적합합니다.

-   직원이 정보를 Office 문서 첨부 파일 형태로 메일을 통해 조직 외부에 보내야 하는 경우

-   공개 대상이 아닌 정보를 포함하는 문서가 내부 전용이 아닌 경우

-   받는 사람에게 이 정보를 다른 사람과 추가로 공유하거나 인쇄하거나 자체 문서의 일부로 사용해야 하는 요구 사항이 적용되지 않는 경우. 이러한 상황에 해당하지 않는 경우에는 보기 전용 권한을 선택하는 대신 받는 사람이 첨부 파일을 변경하도록 허용하는 다른 옵션을 선택하도록 사용자 지침을 변경할 수 있습니다.

-   직원이 외부 사용자가 이 문서를 연 시간을 확인하려는 경우

## 배포 지침
![](../media/AzRMS_AdminBanner.png)

사용자 문서를 진행하기 전에 다음 요구 사항이 충족되었는지 확인합니다.

## 이 시나리오의 요구 사항
이 시나리오의 사용자 지침이 작동하려면 다음 사항을 준비해야 합니다.

|요구 사항|추가 정보가 필요한 경우 확인 가능한 위치|
|---------------|--------------------------------|
|Office 365 또는 Azure Active Directory용 계정과 그룹을 준비했는지 여부|[Azure 권한 관리 준비](https://technet.microsoft.com/library/jj585029.aspx)|
|Azure 권한 관리가 활성화되었는지 여부|[Azure 권한 관리 활성화](https://technet.microsoft.com/library/jj658941.aspx)|
|Windows를 실행하는 사용자의 컴퓨터에 Rights Management 공유 응용 프로그램이 배포되었는지 여부|[Microsoft Rights Management 공유 응용 프로그램 자동 배포](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|사용자가 Office 2013의 Outlook을 사용 중인지 여부|사용자가 Office 2010을 사용 중인 경우에는 그림이 사용자에게 표시되는 화면과 일치하도록 스크린샷을 해당 버전의 그림으로 바꿉니다.|
|Azure RMS 구독에 문서 추적이 포함되는지 여부|Azure RMS 구독에 문서 추적 및 취소 기능이 포함되어 있지 않으면 사용자가 사용자 지침의 모든 단계를 완료할 수 없습니다. 이 경우에는 해당 기능을 지원하는 구독을 구입하거나 사용자 지침을 수정하여 이러한 기능을 사용하는 단계를 제거합니다.<br /><br />구독 지원을 확인하려면 [RMS(Rights Management Services) 제품 비교](https://technet.microsoft.com/dn858608)를 참조하세요.|

## 사용자 문서 지침
다음 템플릿을 사용하여 최종 사용자 통신에 사용자 지침을 복사해서 붙여넣고 사용자 환경에 맞게 다음과 같이 수정합니다.

1.  &lt;Office 문서 종류의 이름&gt;을 사용자가 보낼 문서 종류로 바꿉니다. 사용자의 워크플로에 대해 “Word 문서", “Excel 스프레드시트" 등이 아닌 “가격 목록", “배송 시간", “입찰 제안" 등 구체적이며 익숙한 용어를 사용합니다. 이처럼 보다 구체적인 단어를 사용하면 해당 문서를 사용할 때 지침을 따를 가능성이 증가합니다.

2.  &lt;연락처 세부 정보&gt;를 웹 사이트 링크, 메일 주소, 전화 번호 등 사용자가 지원 센터에 연락할 수 있는 방법에 대한 지침으로 바꿉니다.

3.  **그 외에 수정할 수 있는 사항은 다음과 같습니다.**

    -   2단계에서는 사용 권한으로 **뷰어 - 보기만 가능**을 선택하는 것이 좋습니다. 그러면 첨부된 문서가 받는 사람에 대해 읽기 전용으로 설정됩니다(원본 문서는 읽기 전용으로 설정되지 않음). 이 제한 사항이 비즈니스 요구 사항에 적합하지 않은 경우에는 **검토자 - 보기 및 편집** 등의 다른 사용 권한 집합을 사용하도록 이 옵션을 변경합니다.

    -   3단계에서는 사용자가 나중에 문서를 취소하는 경우 지연이 발생하지 않도록 **이러한 문서에 대해 액세스 취소 즉시 적용** 을 선택하는 것이 좋습니다. 그러나 이 옵션을 설정하는 경우 받는 사람이 첨부 파일을 열기 위해 항상 인터넷에 연결해야 합니다. 또한 이 단계를 수행하려면 문서 추적 및 취소를 지원하는 구독이 있어야 합니다. 이 단계가 사용자에게 적합하지 않은 경우 삭제하세요.

    -   4단계에서는 **다른 사람이 이 문서를 열려고 하면 전자 메일을 통해 알림**옵션을 선택하는 것이 좋습니다. 사용자가 문서 추적 포털을 사용하여 문서를 추적하는 경우 전자 메일 알림이 필요하지 않다고 판단되면 이 단계를 삭제할 수 있습니다.

    -   이 단계에서 만료 날짜를 설정하지는 않습니다. 특정 날짜 후에는 정보를 사용하면 안 되는 경우 메일 메시지를 보낸 날부터 90일과 같은 적절한 만료 시간을 설정하는 다른 단계를 추가합니다.

    > [!NOTE]
    > 사용자가 선택할 수 있는 각 옵션에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램의 대화 상자 옵션](https://technet.microsoft.com/library/dn574738.aspx)을 참조하세요.

4.  이 지침 집합을 원하는 대로 수정한 다음 해당 사용자에게 보냅니다.

예제 문서에서는 사용자 지정 후 이러한 지침이 사용자에게 표시되는 방식을 보여 줍니다.

![](../media/AzRMS_UsersBanner.png)

### &lt;Office 문서 종류 이름&gt; 공유 방법

1.  전자 메일 주소를 하나 이상 지정하고 메시지를 입력한 다음 &lt;Office 문서 종류 이름&gt; 을 전자 메일 메시지에 첨부하여 전자 메일 메시지를 작성합니다. 그런 다음 **메시지** 탭의 **RMS** 그룹에서 **보호된 항목 공유** 를 클릭하고 **보호된 항목 공유** 를 다시 클릭합니다.

    ![](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  
              **보호된 항목 공유** 대화 상자에서 **뷰어 – 보기만 가능**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  
              **이러한 문서에 대해 액세스 취소 즉시 적용**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  
              **다른 사람이 이러한 문서를 열려고 하면 전자 메일을 통해 알림**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  **지금 보내기**를 클릭합니다.


              **받는 사람**, **참조**또는 **숨은 참조** 줄의 사용자가 이 전자 메일을 받으면 첨부된 *&lt;Office 문서 종류 이름&gt;*을 읽는 방법에 대한 지침을 제공하는 메시지가 표시됩니다. iPad, iPhone, Android 태블릿/휴대폰, Mac 컴퓨터, Windows 컴퓨터 등의 여러 장치에서 문서를 읽을 수 있습니다.


              [문서 포털 추적](https://track.azurerms.com/) 을 사용하면 받는 사람이 첨부된 &lt;Office 문서 종류 이름&gt;을 열었는지 여부와 연 시간을 추적할 수 있습니다. 받는 사람이 &lt;Office 문서 종류 이름&gt;을 열었음을 확인한 직후에 추가로 전화 연락을 할 수 있습니다.

**도움이 필요하십니까?**

-   추가 정보를 확인하려면 다음 항목을 참조하세요.

    -   [전자 메일을 통해 공유하는 파일 보호](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [문서 추적 및 취소](https://technet.microsoft.com/library/dn986611.aspx)

-   지원 센터에 연락하려면 다음 정보를 참조하세요.

    -   *&lt;연락처 세부 정보&gt;*

### 예제 사용자 지정 사용자 문서
![](../media/AzRMS_ExampleBanner.png)

#### 고객과 가격 목록을 공유하는 방법

1.  고객의 전자 메일 주소를 하나 이상 지정하고 메시지를 입력한 다음 최신 가격 목록을 전자 메일 메시지에 첨부하여 전자 메일 메시지를 작성합니다. 그런 다음 **메시지** 탭의 **RMS** 그룹에서 **보호된 항목 공유** 를 클릭하고 **보호된 항목 공유** 를 다시 클릭합니다.

    ![](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  
              **보호된 항목 공유** 대화 상자에서 **뷰어 – 보기만 가능**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  
              **이러한 문서에 대해 액세스 취소 즉시 적용**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  
              **다른 사람이 이러한 문서를 열려고 하면 전자 메일을 통해 알림**을 선택합니다.

    ![](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  **지금 보내기**를 클릭합니다.


              **받는 사람**, **참조**또는 **숨은 참조** 줄의 사용자가 이 전자 메일을 받으면 첨부된 가격 목록을 읽는 방법에 대한 지침을 제공하는 메시지가 표시됩니다. iPad, iPhone, Android 태블릿/휴대폰, Mac 컴퓨터, Windows 컴퓨터 등의 여러 장치에서 문서를 읽을 수 있습니다.


              [문서 포털 추적](https://track.azurerms.com/) 을 사용하면 받는 사람이 첨부된 가격 목록을 열었는지 여부와 연 시간을 추적할 수 있습니다. 받는 사람이 가격 목록을 열었음을 확인한 직후에 추가로 전화 연락을 할 수 있습니다.

**도움이 필요하십니까?**

-   추가 정보를 확인하려면 다음 항목을 참조하세요.

    -   [전자 메일을 통해 공유하는 파일 보호](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [문서 추적 및 취소](https://technet.microsoft.com/library/dn986611.aspx)

-   지원 센터에 연락하려면 다음 정보를 참조하세요.

    -   전자 메일: helpdesk@vanarsdelltd.com



<!--HONumber=Apr16_HO4-->


