---
# required metadata

title: 콘텐츠 추적 | Azure RMS
description: 문서 추적을 구현하기 위한 기본 지침
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** 이 SDK 콘텐츠는 현재 버전이 아닙니다. 잠시 MSDN에서 [현재 버전](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx)의 설명서를 확인해 주세요. **
# 콘텐츠 추적

이 항목에서는 권한 관리 서비스 SDK 2.1을 통해 보호된 콘텐츠의 문서 추적을 구현하기 위한 기본 지침을 제공합니다.

문서 추적은 권한 관리 시스템의 기능입니다. 문서 보호 프로세스 중 특정 메타데이터를 추가하면 문서를 추적 서비스 포털에 등록할 수 있으며, 이 서비스에서 여러 가지 추적 옵션을 제공합니다.

이러한 API를 사용하여 문서 추적 메타데이터로 콘텐츠 라이선스를 추가/업데이트할 수 있습니다.

-   [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
-   [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

    모든 메타데이터 속성을 설정합니다. 해당 속성은 아래에 유형별로 나열되어 있습니다.

    자세한 내용은 [**라이선스 메타데이터 속성 형식**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)을 참조하세요.

    -   **IPC\_MD\_CONTENT\_PATH**

        추적된 문서를 식별하는 데 사용합니다. 전체 경로를 사용할 수 없는 경우 파일 이름만 제공합니다.

    -   **IPC\_MD\_CONTENT\_NAME**

        추적된 문서 이름을 식별하는 데 사용합니다.

    -   **IPC\_MD\_NOTIFICATION\_TYPE**

        알림이 전송되는 시기를 지정하는 데 사용합니다. 자세한 내용은 [**알림 유형**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)을 참조하세요.

    -   **IPC\_MD\_NOTIFICATION\_PREFERENCE**

        알림 유형을 지정하는 데 사용합니다. 자세한 내용은 [**알림 기본 설정**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)을 참조하세요.

    -   **IPC\_MD\_DATE\_MODIFIED**

        사용자가 **저장**을 클릭할 때마다 이 날짜를 설정하는 것이 좋습니다.

    -   **IPC\_MD\_DATE\_CREATED**

        파일의 원래 날짜입니다.

-   [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

다음 중 해당 API를 사용하여 파일이나 스트림에 메타데이터를 추가합니다.

-   [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
-   [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

마지막으로, 다음 API를 사용하여 추적된 문서를 추적 시스템에 등록합니다.

-   [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

다음은 문서 추적 메타데이터와 추적 시스템에 등록 호출을 설정하는 예제를 보여 주는 코드 조각입니다.



    HRESULT hr = S_OK;
    LPCWSTR wszOutputFile = NULL;
    wstring wszWorkingFile;
    IPC_LICENSE_METADATA md = {0};

    md.cbSize = sizeof(IPC_LICENSE_METADATA);
    md.dwNotificationType = IPCD_CT_NOTIFICATION_TYPE_ENABLED;
    md.dwNotificationPreference = IPCD_CT_NOTIFICATION_PREF_DIGEST;
    //file origination date, current time for this example
    md.ftDateCreated = GetCurrentTime();
    md.ftDateModified = GetCurrentTime();

    LOGSTATUS_EX(L&quot;Encrypt file with official template...&quot;);

    hr =IpcfEncryptFileWithMetadata(  wszWorkingFile.c_str(),
                                       m_wszTestTemplateID.c_str(),
                                       IPCF_EF_TEMPLATE_ID,
                                       0,
                                       NULL,
                                       NULL,
                                       &amp;md,
                                       &amp;wszOutputFile);

    /* This will contain the serialized license */
    PIPC_BUFFER pSerializedLicense;

    /* the context to use for the call */
    PCIPC_PROMPT_CTX pContext;

    wstring wstrContentName(“MyDocument.txt”);
    bool sendLicenseRegistrationNotificationEmail = FALSE;

    hr = IpcRegisterLicense( pSerializedLicense,
                              0,
                              pContext,
                              wstrContentName.c_str(),
                              sendLicenseRegistrationNotificationEmail);


## 관련 항목


* [**라이선스 메타데이터 속성 형식**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)
* [**알림 기본 설정**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [**알림 유형**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)
* [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)
 

 


<!--HONumber=Jun16_HO1-->


