---
# required metadata

title: 클라이언트 구성 | Azure RMS
description: Active Directory Rights Management Services 클라이언트 2.1을 구성하는 방법에 대한 지침입니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 74C342BF-0F79-486D-AED7-C53230DE5FA7
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
# 클라이언트 구성

이 항목에는 Active Directory Rights Management Services 클라이언트 2.1을 구성하는 방법에 대한 지침이 포함되어 있습니다.

**중요** 단일 시스템(1-box) RMS ISV 환경에서 응용 프로그램을 실행하여 테스트하는 경우에는 AD RMS 클라이언트 2.1을 구성할 필요가 없습니다. 자세한 내용은 [권한 사용 응용 프로그램 테스트](running-your-first-application.md)를 참조하세요.

 

### 필수 구성 요소

-   응용 프로그램을 테스트할 컴퓨터에 AD RMS 클라이언트 2.1이 설치되어 있어야 합니다.

    -   개발 컴퓨터에서 응용 프로그램을 테스트하는 경우 권한 관리 서비스 SDK 2.1을 이미 설치한 상태여야 합니다. 지금은 AD RMS 클라이언트 2.1이 자동으로 설치됩니다.

        RMS SDK 2.1을 설치하는 방법에 대한 자세한 내용은 [SDK 설치](create-your-first-rights-aware-application.md)를 참조하세요.

    -   개발 컴퓨터 이외의 컴퓨터에서 응용 프로그램을 테스트하는 경우 [AD RMS 클라이언트 2.1 다운로드 페이지](http://www.microsoft.com/en-us/download/details.aspx?id=38396)에서 해당 컴퓨터에 AD RMS 클라이언트 2.1을 설치할 수 있습니다.
        **참고** 응용 프로그램에서 서버 API 모드(**IPC\_API\_MODE\_SERVER**)를 사용하는 경우에는 응용 프로그램 매니페스트를 사용할 필요가 없습니다. 프로덕션 RMS 서버에서 응용 프로그램을 테스트할 수 있으며, 프로덕션 환경으로 전환할 때 프로덕션 라이선스를 얻지 않아도 됩니다. 서버 모드 응용 프로그램에 대한 자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

         

-   RMS 서버가 설치되어 있고 사전 프로덕션 환경에서 작동하도록 구성되어 있어야 합니다. 자세한 내용은 [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)을 참조하세요.

지침

### 1단계: 사전 프로덕션 인증서 계층 구조에 대해 RMS 클라이언트 2.1을 설정하는 방법

다음 단계에서는 개발자 런타임을 설치하고 ISV 인증서(사전 프로덕션) 계층 구조를 구성하고 클라이언트에서 서비스 검색을 설정하는 방법을 설명합니다.

1.  개발자 런타임인 Ipcsecproc\_isv.dll을 %MSIPCSDKDIR%\\bin\\x86(32비트 버전의 Windows) 또는 %MSIPCSDKDIR\\bin\\x64(64비트 버전의 Windows)에서 C:\\Program Files\\Active Directory Rights Management Services Client 2.1로 복사합니다.

    **중요** 64비트 버전의 Windows에서 32비트 응용 프로그램을 실행하는 경우 %MSIPCSDKDIR%\\bin\\x86 to C:\\Program Files(x86)\\Active Directory Rights Management Services Client 2.1에서 Ipcsecproc\_isv.dll을 복사해야 합니다.

     

2.  **Hierarchy** 레지스트리 키 값을 1로 설정하여 ISV 인증서(사전 프로덕션) 계층 구조를 사용하도록 AD RMS 클라이언트 2.1을 구성합니다.

    ```
    HKEY_LOCAL_MACHINE
       SOFTWARE
          Microsoft
             MSIPC
                Hierarchy DWORD = 00000001
                Data type
                DWORD
    ```

    **참고** **Hierarchy** 값이 레지스트리에 없으면 해당 값이 0으로 설정된 것과 기능이 같으므로 RMS SDK 2.1이 프로덕션 모드로 작동합니다. 키 및 인증서 체인에 대한 자세한 내용은 [인증서 체인 이해](understanding-certificate-chains.md)를 참조하세요.

    **중요**  
    64비트 버전의 Windows에서 32비트 응용 프로그램을 실행하는 경우 다음 키 위치에서 **Hierarchy** 값을 설정해야 합니다.

    ```
    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    ```
     

3.  AD RMS 클라이언트 2.1이 사전 프로덕션 RMS 서버를 검색하고 통신할 수 있도록 서버 쪽 검색 또는 클라이언트 쪽 검색을 구성합니다.

    -   서버 쪽 검색에서는 관리자가 사전 프로덕션 RMS 루트 클러스터에 대한 SCP(서비스 연결 지점)를 Active Directory에 등록하며 클라이언트는 Active Directory를 쿼리하여 SCP를 검색하고 서버와의 연결을 설정합니다.
    -   클라이언트 쪽 검색에서는 AD RMS 클라이언트 2.1을 실행 중인 컴퓨터의 레지스트리에서 RMS 서비스 검색 설정을 구성합니다. 이러한 설정을 통해 AD RMS 클라이언트 2.1이 사용할 RMS 서버를 확인합니다. 설정이 있으면 서버 쪽 검색이 수행되지 않습니다.

    클라이언트 쪽 검색을 구성하려면 사전 프로덕션 RMS 서버를 가리키도록 다음 레지스트리 키를 설정할 수 있습니다. 서비스 쪽 검색을 구성하는 방법에 대한 자세한 내용은 [RMS 클라이언트 2.0 배포 참고 사항](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)을 참조하세요.

|Key|값|
|---|-----|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterpriseCertification`|(기본값):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Certification**|
|`HKEY_LOCAL_MACHINE\`<br>`SOFTWARE\`<br>`Microsoft\`<br>`MSIPC\`<br>`ServiceLocation\`<br>`EnterprisePublishing`|(기본값):<br><br> [**http**&#124;**https**]**://** *RMSClusterName* **/_wmcs/Licensing**|


**참고** 기본적으로 이러한 키는 레지스트리에 없으며 만들어야 합니다.
     
**중요**  
    64비트 버전의 Windows에서 32비트 응용 프로그램을 실행하는 경우 다음 키 위치에서 이러한 키를 설정해야 합니다.


    HKEY_LOCAL_MACHINE
        SOFTWARE
           Wow6432Node
              Microsoft
                MSIPC
    

### 설명

이 항목의 지침은 일부에 불과합니다. AD RMS 클라이언트 2.1을 구성하는 방법에 대한 자세한 내용은 [RMS 클라이언트 2.0 배포 참고 사항](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)을 참조하세요.

## 관련 항목


* [사용 방법](how-to-use-msipc.md)
* [RMS 클라이언트 2.0 배포 참고 사항](https://TechNet.Microsoft.Com/en-us/library/jj159267(WS.10).aspx)
* [SDK 설치](create-your-first-rights-aware-application.md)
* [서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md)
* [권한 사용 응용 프로그램 테스트](running-your-first-application.md)
* [인증서 체인 이해](understanding-certificate-chains.md)
 

 


<!--HONumber=Jun16_HO1-->


