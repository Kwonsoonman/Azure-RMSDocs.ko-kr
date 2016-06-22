---
# required metadata

title: 명시적 소유자 권한 추가 방법 | Azure RMS
description: 라이선스를 처음부터 만드는 경우 응용 프로그램에서 "소유자" 권한을 명시적으로 추가해야 합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EF43FAC4-ABB4-459D-B173-972B5716F816
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 방법: 명시적 소유자 권한 추가

라이선스를 처음부터 만드는 경우([**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)) 응용 프로그램에서 "소유자" 권한을 명시적으로 추가해야 합니다.

## 필수 구성 요소

응용 프로그램이 [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)를 사용하여 라이선스 핸들을 만드는 경우 소유자에게 모든 권한을 명시적으로 부여해야 합니다.

>[!NOTE] **IPC\_LI\_OWNER** 속성과 함께 [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)를 사용하여 사용자를 "소유자"로 설정하는 경우에는 소유자에게 모든 권한이 부여되지 않습니다.

다음 예제 코드에서는 특정 권한을 만들고 특정 라이선스에 추가하는 작업과 관련된 단계만 보여 줍니다.

## 지침
 
## 1단계: 예제 시나리오

이 예제에서는 [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)를 사용하여 만든 라이선스에 필요한 권한이 추가되었습니다. 예제에서는 권한을 만들고 권한 목록을 통해 라이선스에 권한을 할당하는 작업을 보여 줍니다.

해당 사용자에게 다음 두 가지 권한이 추가되었습니다.

-   *읽기* 권한이 joe@contoso.com에 할당됨
-   *모든* 권한이 mary\_kay@contoso.com에 할당됨

        // Create User Rights structure
        IPC_USER_RIGHTS ownerRightForOwner = {0};

        // Create rights
        LPCWSTR rgwszOwnerRights[1] = {IPC_GENERIC_ALL};

        // Assign values to members of Rights structure
        ownerRightForOwner.User.dwType = IPC_USER_TYPE_IPC;
        ownerRightForOwner.User.wszID = IPC_USER_ID_OWNER;
        ownerRightForOwner.rgwszRights = rgwszOwnerRights;
        ownerRightForOwner.cRights = 1;

        // Create User Rights structure for Joe with Read permissions
        IPC_USER_RIGHTS joeReadRight = {0};
        LPCWSTR rgwszReadRights[1] = {IPC_GENERIC_READ};

        // Assign values to members of Rights structure for Joe
        joeReadRight.User.dwType = IPC_USER_TYPE_EMAIL;
        joeReadRight.User.wszID = "joe@contoso.com";
        joeReadRight.rgwszRights = rgwszReadRights;
        joeReadRight.cRights = 1;

        // Create User Rights structure for Mary Kay with Full permissions
        IPC_USER_RIGHTS mary_kayFullRight = {0};
        LPCWSTR rgwszFullRights[1] = {IPC_GENERIC_ALL};

        // Assign values to members of Rights structure for Mary Kay
        mary_kayFullRight.User.dwType = IPC_USER_TYPE_EMAIL;
        mary_kayFullRight.User.wszID = L"mary_kay@contoso.com";
        mary_kayFullRight.rgwszRights = rgwszFullRights;
        mary_kayFullRight.cRights = 1;

        // Create User Rights List and assign the above rights
        size_t uNoOfUserRights = 3;
        PIPC_USER_RIGHTS_LIST pUserRightsList = NULL;
        pUserRightsList = reinterpret_cast<PIPC_USER_RIGHTS_LIST>
        (new BYTE[ sizeof(IPC_USER_RIGHTS_LIST) + uNoOfUserRights * sizeof(IPC_USER_RIGHTS)]);

        if(pUserRightsList == NULL)
        {
          // Handle error
        }

        // Assign values to members of Rights List structure for Joe and Mary Kay
        (*pUserRightsList).cbSize = sizeof(IPC_USER_RIGHTS_LIST);
        (*pUserRightsList).cUserRights = uNoOfUserRights;
        (*pUserRightsList).rgUserRights[0] = ownerRightForOwner;
        (*pUserRightsList).rgUserRights[1] = joeReadRight;
        (*pUserRightsList).rgUserRights[2] = mary_kayFullRight;

        // Set the Rights List property on the license via its handle
        // hLicense is a license handle created with IpcCreateLicenseFromScratch
        hr = IpcSetLicenseProperty(hLicense, FALSE, IPC_LI_USER_RIGHTS_LIST, pUserRightsList);

        if(FAILED(hr))
        {
          // Handle the error
        }



## 관련 항목

* [개발자 노트](developer-notes.md)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)
 

 


<!--HONumber=Jun16_HO2-->


