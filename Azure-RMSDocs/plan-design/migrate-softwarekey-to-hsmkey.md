---
# required metadata

title: 2단계&colon; 소프트웨어 보호된 키-HSM 보호된 키 마이그레이션 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 2단계: 소프트웨어 보호된 키-HSM 보호된 키 마이그레이션

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*


이 지침은 [AD RMS에서 Azure 권한 관리로의 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS 키가 소프트웨어로 보호되고 HSM 보호된 테넌트 키를 사용하여 Azure 권한 관리로 마이그레이션하려는 경우에만 적용됩니다. 

선택한 구성 시나리오가 아닌 경우 [2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms)로 돌아가서 다른 구성을 선택합니다.

다음은 Azure RMS에 AD RMS 구성을 가져오기 위한 세 부분으로 구성된 절차로, 이 작업을 수행하면 사용자가 관리하는(BYOK) Azure RMS 테넌트 키를 만들 수 있습니다.

먼저 구성 데이터에서 SLC(서버 사용 허가자 인증서) 키를 추출하여 온-프레미스 Thales HSM에 전송하고, HSM 키를 패키지하고 Azure RMS로 전송한 다음 구성 데이터를 가져와야 합니다.

## 1부: 구성 데이터에서 SLC를 추출하고 온-프레미스 HSM으로 키 가져오기

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md) 항목의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#BKMK_ImplementBYOK) 섹션에 있는 다음 단계를 수행합니다.

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **인터넷에 연결된 워크스테이션 준비**

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **연결이 끊어진 워크스테이션 준비**

    내보낸 구성 데이터(.xml) 파일에 테넌트 키가 이미 있으므로, 테넌트 키를 생성하는 단계는 수행하지 않도록 합니다. 대신 파일에서 이 키를 추출한 후 온-프레미스 HSM으로 가져오는 명령을 실행합니다.

2.  연결이 끊어진 워크스테이션에서는 다음 명령을 실행합니다.

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    예를 들어 북아메리카의 경우: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    추가 정보:

    -   ImportRmsCentrallyManagedKey 매개 변수는 이 작업이 SLC 키를 가져오는 작업임을 나타냅니다.

    -   명령에 암호를 지정하지 않으면 지정하라는 메시지가 표시됩니다.

    -   KeyIdentifier 매개 변수는 키 파일 이름을 만드는 키 이름을 나타냅니다. ASCII 소문자만 사용해야 합니다.

    -   ExchangeKeyPackage 매개 변수는 이름이 BYOK-KEK-pkg-로 시작하는 지역별 KEK(키 교환 키) 패키지를 지정합니다.

    -   NewSecurityWorldPackage 매개 변수는 이름이 BYOK-SecurityWorld-pkg-로 시작하는 지역별 보안 권역 패키지를 지정합니다.

    이 명령을 수행하면 다음 결과가 발생합니다.

    -   HSM 키 파일: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   SLC가 제거된 RMS 구성 데이터 파일: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml

3.  둘 이상의 RMS 구성 데이터 파일이 있는 경우 나머지 파일에 대해 2단계를 반복합니다.

HSM 기반 키로 사용할 수 있도록 SLC를 추출했으므로, 이 키를 패키지한 후 Azure RMS에 전송할 수 있습니다.

## 2부: HSM 키를 패키지한 후 Azure RMS로 전송

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#BKMK_ImplementBYOK) 섹션에 있는 다음 단계를 수행합니다.

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **테넌트 키 전송 준비**

    -   **인터넷을 통해 테넌트 키 생성 및 전송**: **Azure RMS로 테넌트 키 전송**

HSM 키를 Azure RMS에 전송했으므로, 새로 전송된 테넌트 키에 대한 포인터만 포함된 AD RMS 구성 데이터를 가져올 준비가 된 것입니다.

## 3부: 구성 데이터를 Azure RMS로 가져오기

1.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 SLC가 제거된 RMS 구성 파일을 복사합니다(연결이 끊어진 워크스테이션의 경우 %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml).

2.  첫 번째 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure RMS에서 콘텐츠를 보호하는 데 사용할 HSM 키에 해당하는 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    예: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    이전에 지정한 암호를 입력하라는 메시지가 표시되면 입력한 후 이 작업을 수행할 것임을 확인합니다.

3.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 2단계를 반복합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다. 예: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet를 사용하여 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).




<!--HONumber=Apr16_HO4-->


