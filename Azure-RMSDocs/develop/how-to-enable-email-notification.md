---
title: "메일 알림 사용 | Azure RMS"
description: "메일 알림을 사용하면 누군가가 보호된 콘텐츠에 액세스할 경우 보호된 콘텐츠 소유자가 알림을 받을 수 있습니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5FB975EE-E4E5-4089-B8E1-CAFD5B9B34EC
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 5da480834485d58028b366c8fbb9a53412cd7c6a


---

# <a name="howto-enable-email-notification"></a>방법: 메일 알림 사용

메일 알림을 사용하면 누군가가 보호된 콘텐츠에 액세스할 경우 보호된 콘텐츠 소유자가 알림을 받을 수 있습니다.

지정된 라이선스에 대해 메일 알림을 설정하려면 속성 형식 매개 변수 *dwPropID*를 [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx)로 지정하고 응용 프로그램 데이터 필드를 [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx) 형식으로 지정하여 [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)를 사용합니다.

    C++

    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {"MS.Conetent.Name", 0, "FinancialReport.docx"};
    propertyValuePairs[1] = {"MS.Notify.Enabled",0 , "true"};
    propertyValuePairs[2] = {"MS.Notify.Culture",0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);


다음 표에는 RMS 메일 알림에 대한 응용 프로그램 데이터 필드, 속성 이름 및 값 쌍이 포함되어 있습니다.


|속성 이름 | 데이터 형식 | 예제 값 | 참고 |
|--------------|-----------|---------------|-------|
|MS.Content.Name|문자열|“FinancialReport.docx”|보호된 콘텐츠와 연결된 식별자입니다.<br><br> 보호된 파일의 경우 이 값은 경로 정보를 제외한 파일 이름이어야 합니다.<br><br> 메일 메시지와 같은 다른 콘텐츠 유형의 경우 메일 제목이거나 비어 있을 수 있습니다.|
|MS.Notify.Enabled|문자열|“true” &#124; “false”|이 값을 "true"로 설정하면 누군가가 게시 라이선스를 사용하여 최종 사용자 라이선스를 얻으려고 시도할 경우 게시 라이선스 소유자에게 알림 메일이 전송됩니다.|
|MS.Notify.Culture|문자열|“en-US”| **원본:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>이 값은 알림 메일의 지역화된 언어와 메일 메시지에 사용해야 하는 날짜/시간 및 숫자 형식을 확인하는 데 사용됩니다.<br><br>게시 라이선스가 생성된 컴퓨터의 사용자 설정이나 게시 라이선스 소유자의 기본 문화권에 따라 설정해야 합니다.|
|MS.Notify.TZID|문자열|“태평양 표준시”|**원본:** TimeZoneInfo.Local.Id - Windows 표준 시간대 ID입니다.<br><br>이 값은 특정 표준 시간대와 해당 특성을 설명하는 Microsoft Windows OS 표준 시간대 식별자입니다.|
|MS.Notify.TZO|문자열|“-480”|UTC 시간을 기준으로 분 단위로 지정된 게시 라이선스 소유자의 표준 시간대 오프셋입니다.<br><br>유효한 TZID 값을 제공하면 해당 값으로 지정된 표준 시간대 오프셋이 사용되고 이 값은 무시됩니다.<br><br>이 값은 Windows OS 표준 시간대 ID 값 목록에 액세스할 수 없는 비 Windows 기반 게시 플랫폼에서 사용될 가능성이 큽니다.<br><br>TZID 값을 제공하지 않으면 이 값을 사용하여 알림 메시지의 시간 오프셋을 계산하고, 표준 시간대 값에 관계없이 TZSN을 사용하여 표준 시간대 이름을 표시합니다. 이렇게 하면 표준 시간대가 고정되고, 일광 절약 시간제가 적용되는 경우에도 적절하게 업데이트되지 않습니다.<br><br>예를 들면 다음과 같습니다.<br><br>TXID를 비워 두고 TZ0을 "-420", TZSN을 "태평양 일광 절약 시간"으로 설정하면 알림 메일에 표시된 모든 값이 "태평양 일광 절약 시간"으로 조정되며 일광 절약 시간제가 현재 적용되지 않는 경우에도 이렇게 표시됩니다.<br><br>반면, TZSN 및 TZDN과 함께 TZID를 제공하면 알림 메일에 지정된 시간이 날짜 및 시간을 일광 절약 모드 또는 표준 모드로 표시해야 하는지에 따라 조정 및 표시됩니다.|
|MS.Notify.TZSN|문자열|“태평양 표준시”|**원본:** TimeZoneInfo.Local.StandardName - 표준 시간대 이름입니다.<br><br>표준 시간대 이름의 지역화된 이름이어야 합니다.|
|MS.Notify.TZDN|문자열|"태평양 일광 절약 시간"|**원본:** TimeZoneInfo.Local.DaylightName - 표준 시간대 일광 절약 시간 이름입니다.<br><br>표준 시간대 일광 절약 시간 이름의 지역화된 이름이어야 합니다. 표준 시간대가 일광 절약 시간제를 지원하지 않는 경우 표준 이름과 같을 수 있습니다.|

## <a name="related-topics"></a>관련 항목

- [IpcSetLicenseProperty](https://msdn.microsoft.com/library/hh535271.aspx)
- [IPC\_LI\_APP\_SPECIFIC\_DATA](https://msdn.microsoft.com/library/hh535287.aspx)
- [IPC\_NAME\_VALUE\_LIST](https://msdn.microsoft.com/library/hh535277.aspx).
 

 



<!--HONumber=Nov16_HO2-->


