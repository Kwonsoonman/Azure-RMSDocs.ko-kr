---
title: "방법: RMS 서버 설치, 구성 및 테스트 | Azure RMS"
description: "권한 사용 응용 프로그램 테스트에 사용할 RMS 서버를 설치 및 구성합니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7ee098ceaa8ac6b1e0d5d6cbe090042510aa89b
ms.openlocfilehash: ac7dd8592d6e11905744c4f4e0171fd5b5945c51


---

# 방법: RMS 서버 설치, 구성 및 테스트

이 항목에서는 권한 사용 응용 프로그램 테스트에 사용할 RMS 서버 또는 Azure RMS에 연결하는 단계를 설명합니다.
 
## 지침

### 1단계: RMS 서버 설정

다음 단계에서는 RMS 서버 설정 과정을 안내하며 다음 작업을 포함합니다.

-   서버 설치
-   서버 등록

1.  **서버 설치**

    AD RMS(Active Directory Rights Management Services)는 개별 클라이언트 및 서버 구성 요소로 이루어져 있습니다. 서버 구성 요소는 RMS 인프라를 관리하고, 콘텐츠 소비자 및 게시자에게 라이선스를 발급하고, 컴퓨터 및 사용자에게 인증서를 발급하는 데 사용할 수 있는 웹 서비스 집합으로 구현됩니다.

    Windows Server 2008 이상에서는 클라이언트 및 서버 구성 요소가 운영 체제에 포함되어 있습니다. 이전 운영 체제에 대한 서버 구성 요소는 다음 위치에서 다운로드할 수 있습니다.

    -   [RMS 서버 v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    Windows Server 2008에서 서버 구성 요소를 구성하려면 AD RMS 역할을 설치해야 합니다. 이전 서버 운영 체제를 기반으로 하여 응용 프로그램을 개발하는 경우 RMS 서버 v1.0 SP2를 설치한 후 RMS 서비스를 프로비전하기 전에 레지스트리를 구성합니다.

2.  **서버 등록**

    RMS(Rights Management Services) 서버를 등록하여 사전 프로덕션 또는 프로덕션 계층 구조에서 식별해야 합니다. 등록 프로세스를 수행하면 서버 컴퓨터에 서버 사용 허가자 인증서가 남습니다. 이 인증서는 Microsoft의 신뢰할 수 있는 루트에 다시 연결됩니다. 서버를 등록하는 방법은 사용 중인 RMS 버전에 따라 달라집니다.

    -   **자체 등록**

        Windows Server 2008 이상에서는 Microsoft에 정보를 보내지 않고 적절한 계층 구조에 RMS 서버를 등록할 수 있습니다. RMS 역할을 설치할 때 자체 등록 인증서와 개인 키도 설치됩니다. 이러한 인증서와 키는 서버 사용 허가자 인증서를 자동으로 만드는 데 사용됩니다. Microsoft와 정보를 교환하지 않습니다.

    -   **온라인 등록**

        AD RMS v1.0 SP2를 사용하는 경우 온라인에서 서버를 등록할 수 있습니다. 등록은 프로비전 프로세스 중에 백그라운드에서 발생하지만 인터넷에 연결되어 있어야 합니다.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

3. **RMS 서버에서 테스트**

    RMS 서버에서 테스트하기 위해 Rights Management Service Client 2.1이 RMS 서버를 검색하고 통신할 수 있도록 서버 쪽 검색 또는 클라이언트 쪽 검색을 구성합니다.

    > [!Note]
    > Azure RMS에서 테스트하려는 경우 검색 구성은 필요하지 않습니다.

  - 서버 쪽 검색에서는 관리자가 RMS 루트 클러스터에 대한 SCP(서비스 연결 지점)를 Active Directory에 등록하며 클라이언트는 Active Directory를 쿼리하여 SCP를 검색하고 서버와의 연결을 설정합니다.
  - 클라이언트 쪽 검색에서는 RMS Client 2.1을 실행 중인 컴퓨터의 레지스트리에서 RMS 서비스 검색 설정을 구성합니다. 이러한 설정을 통해 RMS Client 2.1이 사용할 RMS 서버를 확인합니다. 설정이 있으면 서버 쪽 검색이 수행되지 않습니다.

  클라이언트 쪽 검색을 구성하기 위해 RMS 서버를 가리키도록 다음 레지스트리 키를 설정할 수 있습니다. 서비스 쪽 검색을 구성하는 방법에 대한 자세한 내용은 [RMS Client 2.0 배포 참고 사항](https://technet.microsoft.com/library/jj159267(WS.10).aspx) 항목을 참조하세요.

1. **EnterpriseCertification**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterpriseCertification

   **값**: (기본값): [**http|https**]: //RMSClusterName/**_wmcs/Certification**

2. **EnterprisePublishing**

        HKEY_LOCAL_MACHINE
          SOFTWARE
            Microsoft
              MSIPC
                ServiceLocation
                  EnterprisePublishing
                  
   **값**: (기본값): [**http|https**]://RMSClusterName/**_wmcs/Licensing**

>[!NOTE] 
> 기본적으로 이러한 키는 레지스트리에 없으며 만들어야 합니다.

>[!IMPORTANT] 
> 64비트 버전의 Windows에서 32비트 응용 프로그램을 실행하는 경우 다음 키 위치에서 이러한 키를 설정해야 합니다.<p>
  ```    
  HKEY_LOCAL_MACHINE
    SOFTWARE
      Wow6432Node
        Microsoft
          MSIPC
            ```

 

 



<!--HONumber=Oct16_HO3-->


