---
# required metadata

title: "방법: 문서 추적 및 해지 사용 | Azure RMS"
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
<<<<<<< HEAD

# 콘텐츠 추적
=======
>>>>>>> 81ec5ddf5acf3de78d77c01ed95631e44d37fe6e

# 방법: 문서 추적 및 해지 사용

이 항목에서는 콘텐츠의 문서 추적과 메타데이터 업데이트에 대한 예제 코드를 구현하고, 앱에 대한 **사용 추적 단추**를 만들기 위한 기본 지침을 다룹니다.

## 문서 추적을 구현하는 단계

1 및 2단계에서 문서를 추적할 수 있습니다. 3단계에서 앱 사용자는 문서를 추적하고 해지하기 위해 문서 추적 사이트에 연결할 수 있습니다.

1. 문서 추적 메타데이터 추가
2. RMS 서비스에 문서 등록
3. 앱에 사용량 추적 단추 추가

이러한 단계에 대한 구현 세부 사항은 다음과 같습니다.

## 1. 문서 추적 메타데이터 추가

문서 추적은 권한 관리 시스템의 기능입니다. 문서 보호 프로세스 중 특정 메타데이터를 추가하면 문서를 추적 서비스 포털에 등록할 수 있으며, 이 서비스에서 여러 가지 추적 옵션을 제공합니다.

이러한 API를 사용하여 문서 추적 메타데이터로 콘텐츠 라이선스를 추가/업데이트할 수 있습니다.


운영 측면에서 **콘텐츠 이름** 및 **알림 유형** 속성만 문서 추적에 필요합니다.


- [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
- [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

  모든 메타데이터 속성을 설정합니다. 해당 속성은 아래에 유형별로 나열되어 있습니다.

  자세한 내용은 [라이선스 메타데이터 속성 형식](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types) 항목을 참조하세요.

  - **IPC_MD_CONTENT_PATH**

    추적된 문서를 식별하는 데 사용합니다. 전체 경로를 사용할 수 없는 경우 파일 이름만 제공합니다.

  - **IPC_MD_CONTENT_NAME**

    추적된 문서 이름을 식별하는 데 사용합니다.

  - **IPC_MD_NOTIFICATION_TYPE**

    알림이 전송되는 시기를 지정하는 데 사용합니다. 자세한 내용은 Notification type(알림 유형) 항목을 참조하세요.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    알림 유형을 지정하는 데 사용합니다. 자세한 내용은 Notification preference(알림 기본 설정) 항목을 참조하세요.

  - **IPC_MD_DATE_MODIFIED**

    사용자가 저장을 클릭할 때마다 이 날짜를 설정하는 것이 좋습니다.

  - **IPC_MD_DATE_CREATED**

    파일의 원래 날짜를 설정하는 데 사용합니다.

- [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

다음 중 해당 API를 사용하여 파일이나 스트림에 메타데이터를 추가합니다.

- [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
- [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

마지막으로, 다음 API를 사용하여 추적된 문서를 추적 시스템에 등록합니다.

- [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)


## 2. RMS 서비스에 문서 등록

다음은 문서 추적 메타데이터와 추적 시스템에 등록 호출을 설정하는 예제를 보여 주는 코드 조각입니다.

      C++
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

      LOGSTATUS_EX(L"Encrypt file with official template...");

      hr =IpcfEncryptFileWithMetadata( wszWorkingFile.c_str(),
                               m_wszTestTemplateID.c_str(),
                               IPCF_EF_TEMPLATE_ID,
                               0,
                               NULL,
                               NULL,
                               &md,
                               &wszOutputFile);

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

## 앱에 **사용량 추적** 단추 추가

앱에 **사용량 추적** UI 항목을 추가하는 작업은 다음 URL 형식 중 하나를 사용하는 작업만큼 간단합니다.

- 콘텐츠 ID 사용
  - 라이선스가 직렬화된 경우 [IpcGetLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetlicenseproperty) 또는 [IpcGetSerializedLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetserializedlicenseproperty)를 사용하여 콘텐츠 ID를 가져오고 라이선스 속성 **IPC_LI_CONTENT_ID**를 사용합니다. 자세한 내용은 [라이선스 속성 형식](/rights-management/sdk/2.1/api/win/constants#msipc_license_property_types) 항목을 참조하세요.
  - **ContentId** 및 **Issuer** 메타 데이터와 함께 다음 형식을 사용합니다. `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    예 - `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- 해당 메타 데이터에 액세스할 수 없는 경우(즉, 보호되지 않는 버전의 문서를 검사 중인 경우) 다음 형식에서 **Content_Name**을 사용할 수 있습니다. `https://track.azurerms.com/#/?q={ContentName}`

  예 - https://track.azurerms.com/#/?q=Secret!.txt

클라이언트에서는 브라우저로 적절한 URL을 열기만 하면 됩니다. RMS 문서 추적 포털은 인증 및 모든 필수 리디렉션을 처리합니다.

## 관련 항목

* [라이선스 메타데이터 속성 형식](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types)
* [알림 기본 설정](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [알림 유형](/rights-management/sdk/2.1/api/win/constants#msipc_notification_type)
* [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

 


<!--HONumber=Jun16_HO2-->


