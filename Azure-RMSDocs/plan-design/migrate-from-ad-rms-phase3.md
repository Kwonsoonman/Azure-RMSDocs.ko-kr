---
title: "AD RMS에서 Azure 권한 관리로 마이그레이션 - 3단계 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 75cce1d0e5a1cff0d4f6609d0f084fda1af62951


---

# 마이그레이션 3단계 - 지원 서비스 구성

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*


AD RMS에서 Azure 권한 관리(Azure RMS)로 마이그레이션 3단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure 권한 관리로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 6-7단계를 설명합니다.


## 6단계. Exchange Online에 대한 IRM 통합 구성

이전에 AD RMS에서 Exchange Online으로 TDP를 가져온 경우 Azure RMS로 마이그레이션한 후에 템플릿 및 정책 충돌을 방지하기 위해 이 TDP를 제거해야 합니다. 이렇게 하려면 Exchange Online에서 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) cmdlet을 사용합니다.

Azure RMS 테넌트 키 토폴로지로 **Microsoft 관리**를 선택한 경우

-   [Office 365: 클라이언트 및 온라인 서비스 구성](../deploy-use/configure-office365.md) 문서에서 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration) 섹션을 참조하세요. 이 섹션에는 Exchange Online 서비스에 연결하고, Azure RMS에서 테넌트 키를 가져오고, Exchange Online에 대해 IRM 기능을 사용하도록 설정하는 일반적인 명령이 포함되어 있습니다. 이러한 단계를 완료한 후에 Exchange Online에서 전체 RMS 기능을 사용할 수 있게 됩니다.

Azure RMS 테넌트 키 토폴로지로 **고객 관리(BYOK)**를 선택한 경우

-   [BYOK 가격 및 제한 사항](byok-price-restrictions.md) 문서에 설명된 대로 Exchange Online에서 사용할 수 있는 RMS 기능이 줄어듭니다.

## 7단계. RMS 커넥터 배포
AD RMS에서 Exchange Server 또는 SharePoint Server의 IRM(정보 권한 관리) 기능을 사용한 경우 먼저 이러한 서버에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성을 제거해야 합니다. 그런 다음 온-프레미스 서버와 Azure RMS 간에 통신 인터페이스(릴레이) 역할을 하는 RMS(권한 관리) 커넥터를 배포합니다.

이 단계를 위해 마지막으로, 여러 TPD를 메일 메시지를 보호하는 데 사용된 Azure RMS로 가져온 경우 모든 TPD URL을 RMS 커넥터로 리디렉션하도록 Exchange Server 컴퓨터의 레지스트리를 수동으로 편집해야 합니다.

> [!NOTE]
> 시작하기 전에 [Azure RMS를 지원하는 온-프레미스 서버](../get-started/requirements-servers.md)에서 Azure RMS가 지원하는 온-프레미스 서버 버전을 확인합니다.

### Exchange Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  각 Exchange Server에서 다음 폴더를 찾아 해당 폴더의 항목을 모두 삭제합니다. \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Exchange Server 중 하나에서 Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) cmdlet를 사용하여 내부의 받는 사람에게 전송되는 메시지에 대한 IRM 기능을 사용하지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  그런 후 동일한 cmdlet를 사용하여 외부의 받는 사람에게 전송되는 메시지에 대해 IRM 기능이 사용되지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  다음에는 동일한 cmdlet를 사용하여 Microsoft Office Outlook Web App 및 Microsoft Exchange ActiveSync에서 IRM이 사용되지 않도록 설정합니다.

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  마지막으로 동일한 cmdlet를 사용하여 캐시된 모든 인증서를 지웁니다.

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  예를 들어 각 Exchange Server에서 관리자 권한으로 명령 프롬프트를 실행하고 **iisreset**을 입력하여 IIS를 초기화합니다.

### SharePoint Server에서 IRM을 사용하지 않도록 설정하고 AD RMS 구성 제거

1.  RMS로 보호된 라이브러리에서 체크 아웃된 문서가 없는지 확인합니다. 체크 아웃된 문서가 있는 경우 이 절차가 끝나면 액세스할 수 없게 됩니다.

2.  Sharepoint 중앙 관리 웹 사이트의 **빠른 실행** 섹션에서 **보안**을 클릭합니다.

3.  **보안** 페이지의 **정보 정책** 섹션에서 **정보 권한 관리 구성**을 클릭합니다.

4.  **정보 권한 관리** 페이지의 **정보 권한 관리** 섹션에서 **이 서버에서 IRM 사용 안 함**을 선택하고 **확인**을 클릭합니다.

5.  각 SharePoint Server 컴퓨터에서 SharePoint Server&gt;*를 실행하는 계정의 \ProgramData\Microsoft\MSIPC\Server\*&lt;SID 폴더의 내용을 삭제합니다.

#### RMS 커넥터 설치 및 구성

-   [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md) 문서의 지침을 따릅니다.

#### Exchange만 및 여러 TPD: 레지스트리 편집

-   각 Exchange Server에서 가져온 각 추가 TPD에 대해 다음 레지스트리 키를 수동으로 추가하여 TPD URL을 RMS 커넥터로 리디렉션합니다. 이러한 레지스트리 항목은 마이그레이션에만 관련되며 Microsoft RMS 커넥터용 서버 구성 도구를 통해 추가되지 않습니다.

    이와 같이 레지스트리를 편집할 때는 다음 지침을 따르세요.

    -   *ConnectorFQDN* 을 DNS에서 커넥터에 대해 정의한 이름으로 바꿉니다. **rmsconnector.contoso.com**을 예로 들 수 있습니다.

    -   온-프레미스 서버와 통신하는 데 HTTP 또는 HTTPS 중 어느 것을 사용하도록 커넥터를 구성했는지에 따라 커넥터 URL에 대해 HTTP 또는 HTTPS 접두사를 사용합니다.

Exchange 2013의 경우 - 레지스트리 편집 1:


**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**종류:**

Reg_SZ

**Value:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**데이터:**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Exchange 2013의 경우 - 레지스트리 편집 2:

**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 


**종류:**

Reg_SZ

**Value:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**데이터:**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

Exchange 2010의 경우 - 레지스트리 편집 1:



**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**종류:**

Reg_SZ

**Value:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**데이터:**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Exchange 2010의 경우 - 레지스트리 편집 2:


**레지스트리 경로:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection
 

**종류:**

Reg_SZ

**Value:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**데이터:**

Exchange Server에서 RMS 커넥터로의 연결에 HTTP와 HTTPS 중 어느 것을 사용하는지에 따라 다음 중 하나:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

이러한 절차를 완료했으면 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md) 문서에서 **다음 단계** 섹션을 읽을 준비가 되었습니다.

## 다음 단계
마이그레이션을 계속하려면 [4단계 - 사후 마이그레이션 작업](migrate-from-ad-rms-phase4.md)으로 이동합니다.


<!--HONumber=Jul16_HO3-->


