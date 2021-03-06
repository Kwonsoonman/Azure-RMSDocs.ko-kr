---
title: Azure RMS 서비스의 사용 현황 로깅 및 분석 - AIP
description: Azure RMS(Azure Rights Management)에서 사용 현황 로깅을 사용하는 방법에 대한 정보와 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1deea1b4353e2d48c85ae24625ab29eca96a3968
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47211329"
---
# <a name="logging-and-analyzing-usage-of-the-azure-rights-management-service"></a>Azure Rights Management 서비스의 사용 현황 로깅 및 분석

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

이 정보를 통해 Azure Information Protection의 Azure Rights Management 서비스에 대한 사용 현황 로깅을 사용하는 방법을 파악할 수 있습니다. 이 서비스는 조직의 문서 및 메일에 대한 데이터 보호를 제공하고 모든 요청을 기록할 수 있습니다. 이러한 요청에는 사용자가 문서 및 메일을 보호하고 이 콘텐츠를 사용하는 시기, 이 서비스에 대해 관리자가 수행하는 작업, Azure Information Protection 배포를 지원하기 위해 Microsoft 운영자가 수행하는 작업이 포함됩니다. 

이러한 Azure Rights Management 서비스 로그를 사용하여 다음과 같은 비즈니스 시나리오를 지원할 수 있습니다.

-   **비즈니스 관련 정보 분석**

    Azure Rights Management 서비스에서 생성한 로그를 데이터베이스, OLAP(온라인 분석 처리) 시스템 또는 맵 감소 시스템과 같은 선택한 리포지토리로 가져와서 정보를 분석하고 보고서를 생성할 수 있습니다. 예를 들어 보호된 데이터에 액세스하는 사용자를 파악할 수 있습니다. 그리고 사용자들이 액세스하는 보호된 데이터 및 액세스에 사용하는 장치와 액세스 위치를 확인할 수 있습니다. 사용자들이 보호된 콘텐츠를 정상적으로 읽을 수 있는지 확인할 수 있으며, 보호된 중요 문서를 사용자들이 읽었는지도 파악할 수 있습니다.

-   **남용 모니터링**

    Azure Rights Management 로깅 정보는 거의 실시간으로 제공되므로 회사의 Rights Management 서비스 사용을 지속적으로 모니터링할 수 있습니다. 로그의 99.9%는 서비스 작업을 시작한 후 15분 이내에 사용 가능합니다.

    예를 들어 표준 업무 시간 이외의 시간에 보호된 데이터를 읽는 사용자 수가 갑자기 증가하면 알림을 받을 수 있습니다. 이러한 현상은 악의적인 사용자가 경쟁자에게 판매하기 위해 정보를 수집하는 것일 수 있기 때문입니다. 또한 같은 사용자가 짧은 시간 내에 서로 다른 두 IP 주소에서 데이터에 액세스하는 경우에는 해당 사용자의 계정이 노출된 것일 수 있습니다.

-   **법정 분석 수행**

    정보가 유출된 경우 최근 특정 문서에 액세스한 사용자와 유출이 의심되는 사용자가 최근 액세스한 정보를 확인해야 할 가능성이 높습니다. 이 로깅을 사용하는 경우 관련 질문에 답할 수 있습니다. 보호된 콘텐츠의 사용자가 Azure Rights Management 서비스로 보호되는 문서와 사진을 열려면 항상 Rights Management 라이선스를 받아야 하기 때문입니다. 이는 메일을 통해 이러한 파일을 이동하거나 USB 드라이브 또는 기타 저장소 장치에 복사하는 경우에도 마찬가지입니다. 즉, Azure Rights Management 서비스를 사용하여 데이터를 보호하는 경우 이 로그를 법정 분석용의 최종 정보 출처로 사용할 수 있습니다.

이 사용 현황 로깅 외에도 다음 로깅 옵션도 있습니다.

|로깅 옵션|설명|
|----------------|---------------|
|관리자 로그|Azure Rights Management 서비스에 대한 관리 작업을 로그합니다. 예를 들면 서비스가 비활성화된 경우 슈퍼 사용자 기능이 활성화될 때와 사용자가 서비스에 관리자 권한을 위임할 때입니다. <br /><br />자세한 내용은 PowerShell cmdlet [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog)를 참조하세요.|
|문서 추적|사용자가 Azure Information Protection 클라이언트 또는 RMS 공유 앱으로 추적한 문서를 추적하고 취소할 수 있습니다. 전역 관리자가 사용자를 대신하여 이러한 문서를 추적할 수도 있습니다. <br /><br />자세한 내용은 [Azure Information Protection에 대한 문서 추적 구성 및 사용](./rms-client/client-admin-guide-document-tracking.md)을 참조하세요.|
|클라이언트 이벤트 로그|로컬 Windows **응용 프로그램 및 서비스** 이벤트 로그(**Azure Information Protection**)에 기록된 Azure Information Protection 클라이언트에 대한 사용 활동입니다. <br /><br />자세한 내용은 [Azure Information Protection 클라이언트에 대한 사용 현황 로깅](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)을 참조하세요.|
|클라이언트 로그 파일|**%localappdata%\Microsoft\MSIP**에 있는 Azure Information Protection 클라이언트에 대한 문제 해결 로그입니다. <br /><br />이러한 파일은 Microsoft 지원용으로 설계되었습니다.|

또한 Azure Information Protection 클라이언트 사용 현황 로그 및 Azure Information Protection 검사기의 정보가 수집 및 집계된 후 Azure Portal에서 보고서가 생성됩니다. 자세한 내용은 [Azure Information Protection의 보고](reports-aip.md)를 참조하세요.

Azure Rights Management 서비스에 대한 사용 현황 로깅에 대한 자세한 내용은 다음 섹션에서 확인할 수 있습니다. 

## <a name="how-to-enable-azure-rights-management-usage-logging"></a>Azure 권한 관리 사용 현황 로깅을 사용하도록 설정하는 방법
2016년 2월부터 모든 고객에 대해 Azure 권한 관리 사용 현황 로깅이 기본적으로 사용됩니다. 이 내용은 2016년 2월 이전에 Azure Rights Management 서비스를 활성화한 고객과 2016년 2월 이후에 서비스를 활성화하는 고객에게 적용됩니다. 

> [!NOTE]
> 로그 저장소 또는 로깅 기능에 대한 무료로 제공됩니다.
> 
> 2016년 2월 이전에 Azure Rights Management에 대한 사용 현황 로깅을 사용한 경우 Azure 구독이 필요하며 Azure에 충분한 저장소가 있어야 했지만 지금은 그렇지 않습니다.

## <a name="how-to-access-and-use-your-azure-rights-management-usage-logs"></a>Azure 권한 관리 사용 현황 로그에 액세스 및 사용 방법
Azure Rights Management 서비스는 로그를 일련의 Blob으로 Azure 저장소 계정에 기록합니다. 각 Blob에는 W3C 확장 로그 형식의 로그 레코드가 하나 이상 포함됩니다. Blob 이름은 숫자이며 작성된 순서를 나타냅니다. 이 문서의 뒷부분에 있는 [Azure 권한 관리 사용 현황 로그를 해석하는 방법](#how-to-interpret-your-azure-rights-management-usage-logs) 섹션에 로그 콘텐츠 및 콘텐츠 생성에 대한 자세한 내용이 나와 있습니다.

Azure 권한 관리 작업 이후 저장소 계정에 로그가 표시될 때까지 다소 시간이 걸릴 수 있습니다. 대부분의 로그는 15분 이내에 표시됩니다. 로컬 폴더, 데이터베이스 또는 맵 감소 리포지토리와 같은 로컬 저장소에 로그를 다운로드하는 것이 좋습니다.

사용 현황 로그를 다운로드하려면 Windows PowerShell에 대한 Azure Rights Management 관리 모듈을 사용합니다. 설치 지침은 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요. 이전에 이 Windows PowerShell 모듈을 다운로드한 경우 다음 명령을 실행하여 버전 번호가 **2.4.0.0** 이상인지 확인합니다. `(Get-Module aadrm -ListAvailable).Version` 

### <a name="to-download-your-usage-logs-by-using-powershell"></a>PowerShell을 사용하여 사용 현황 로그를 다운로드하려면

1.  **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작하고 [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 Azure 권한 관리 서비스에 연결합니다.

    ```
    Connect-AadrmService
    ```
    
2.  특정 날짜에 대한 로그를 다운로드하려면 다음 명령을 실행합니다. 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    예를 들면 E: 드라이브에 Logs라는 폴더를 만든 후에
    
    * 특정 날짜(예: 2016년 2월 1일)에 대한 로그를 다운로드하려면 다음 명령을 실행합니다. `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * 날짜 범위(예: 2016년 2월 1일부터 2016년 2월 14일까지)에 대한 로그를 다운로드하려면 다음 명령을 실행합니다. `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

하루만 지정하는 경우 예제와 같이 시간이 현지 시간의 00:00:00으로 간주되고 UTC로 변환됩니다. -fromdate 또는 -todate 매개 변수로 시간을 지정하는 경우(예: -fordate "2/1/2016 15:00:00") 날짜 및 시간이 UTC로 변환됩니다. Get-AadrmUserLog 명령은 해당 UTC 기간에 대한 로그를 가져옵니다.

하루 이내로 다운로드를 지정할 수 없습니다.

기본적으로 이 cmdlet은 세 개의 스레드를 사용하여 로그를 다운로드합니다. 네트워크 대역폭이 충분하고 로그를 다운로드하는 데 필요한 시간을 줄이려는 경우 1부터 32까지의 값을 지원하는 -NumberOfThreads 매개 변수를 사용합니다. 예를 들어 다음 명령을 실행하는 경우 cmdlet은 로그를 다운로드하기 위해 10개 스레드를 생성합니다. `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> 잘 알려진 여러 로그 형식 간의 변환 도구인 [Microsoft 로그 파서](https://www.microsoft.com/download/details.aspx?id=24659)를 사용하면 다운로드한 모든 로그 파일을 CSV 형식으로 집계할 수 있습니다. 이 도구를 사용하여 데이터를 SYSLOG 형식으로 변환하거나 데이터베이스로 가져올 수도 있습니다. 도구를 설치한 후 `LogParser.exe /?`를 실행하면 이 도구 사용을 위한 정보와 도움말을 확인할 수 있습니다. 
>
> 예를 들어 모든 정보를 .log 파일 형식으로 가져오려면 다음 명령을 실행합니다. `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### <a name="if-you-manually-enabled-azure-rights-management-usage-logging-before-the-logging-change-february-22-2016"></a>2016년 2월 22일 로깅 변경 전에 Azure Rights Management 사용 현황 로깅을 수동으로 활성화한 경우


로깅 변경 전에 사용 현황 로깅을 사용한 경우 구성된 Azure 저장소 계정에 사용 현황 로그가 제공됩니다. Microsoft는 이러한 로깅 변경의 일부로 사용자 저장소 계정에 있는 이러한 로그를 새로운 Azure Rights Management 관리 저장소 계정에 복사하지 않습니다. 이전에 생성된 로그의 수명 주기를 관리해야 하며 [Get-AadrmUsageLog](/powershell/aadrm/vlatest/get-aadrmusagelog) cmdlet을 사용하여 기존 로그를 다운로드할 수 있습니다. 예를 들면 다음과 같습니다.

- 사용 가능한 모든 로그를 E:\logs 폴더에 다운로드하려면 다음 cmdlet을 실행합니다. `Get-AadrmUsageLog -Path "E:\Logs"`
    
- 특정 Blob 범위를 다운로드하려면 다음 cmdlet을 실행합니다. `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

다음 중 한 가지가 적용되는 경우 Get-AadrmUsageLog cmdlet을 사용하여 로그를 다운로드하지 않아도 됩니다.

-  2016년 2월 22일 이전에 Azure Rights Management 서비스를 활성화했지만 사용 현황 로깅 기능을 활성화하지 않았습니다.

- 2016년 2월 22일 이후에 Azure Rights Management 서비스를 활성화했습니다.

## <a name="how-to-interpret-your-azure-rights-management-usage-logs"></a>Azure 권한 관리 사용 현황 로그를 해석하는 방법
다음 정보를 참조하여 Azure 권한 관리 사용 현황 로그를 해석할 수 있습니다.

### <a name="the-log-sequence"></a>로그 순서
Azure Rights Management 서비스는 일련의 Blob으로 로그를 기록합니다. 

로그의 각 항목에 UTC 타임스탬프가 있습니다. Azure Rights Management 서비스가 여러 데이터 센터의 여러 서버에서 실행되므로 로그가 타임스탬프순으로 정렬되었어도 순서가 올바르지 않은 것처럼 보일 수 있습니다. 그러나 시간 차이는 크지 않으며 보통 1분 이내입니다. 대부분의 경우에는 이러한 시간 차이로 인해 로그 분석 시 문제가 발생하지 않습니다.

### <a name="the-blob-format"></a>Blob 형식
각 Blob은 W3C 확장 로그 형식으로 되어 있으며 다음의 두 줄로 시작됩니다.

**#Software: RMS**

**#Version: 1.1**

첫 번째 줄은 이러한 로그가 Azure 권한 관리 로그임을 나타냅니다. 두 번째 줄은 Blob의 나머지 부분이 버전 1.1 사양을 따름을 나타냅니다. 이러한 로그를 구문 분석하는 응용 프로그램에서 이 두 줄을 먼저 확인한 후에 Blob의 나머지 부분 구문 분석을 계속하도록 하는 것이 좋습니다.

세 번째 줄에는 탭으로 구분된 필드 이름 목록이 열거됩니다.

**#Fields: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip            admin-action            acting-as-user**

그 다음의 각 줄이 로그 레코드입니다. 필드의 값은 위 줄과 같은 순서로 되어 있으며 탭으로 구분됩니다. 다음 표를 참조하여 필드를 해석할 수 있습니다.

|필드 이름|W3C 데이터 형식|설명|예제 값|
|--------------|-----------------|---------------|-----------------|
|date|날짜|요청이 처리된 UTC 날짜입니다.<br /><br />원본은 요청을 처리한 서버의 로컬 시계입니다.|2013-06-25|
|time|시간|요청이 처리된 UTC 시간(24시간 형식)입니다.<br /><br />원본은 요청을 처리한 서버의 로컬 시계입니다.|21:59:28|
|row-id|텍스트|이 로그 레코드의 고유 GUID입니다. 값이 없으면 상관 관계 ID 값을 사용하여 항목을 식별합니다.<br /><br />로그를 집계하거나 다른 형식으로 복사할 때 이 값을 활용하면 유용합니다.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|이름|요청한 RMS API의 이름입니다.|AcquireLicense|
|user-id|문자열|요청을 한 사용자입니다.<br /><br />값은 작은따옴표로 묶입니다. 본인이 관리하는 테넌트 키(BYOK)로부터의 호출에는 **"** 라는 값이 있으며, 이것은 요청 종류가 익명일 경우에도 적용됩니다.|‘joe@contoso.com’|
|result|문자열|요청이 정상적으로 처리된 경우 'Success'입니다.<br /><br />요청이 실패한 경우에는 작은따옴표로 묶인 오류 유형이 표시됩니다.|'성공'|
|correlation-id|텍스트|지정된 요청에 대해 RMS 클라이언트 로그와 서버 로그 간에 공통적으로 사용되는 GUID입니다.<br /><br />이 값은 클라이언트 문제 해결 시 유용할 수 있습니다.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|텍스트|문서 등의 보호된 콘텐츠를 식별하는 중괄호로 묶인 GUID입니다.<br /><br />request-type이 AcquireLicense인 경우에만 이 필드에 값이 포함되며 기타 모든 요청 유형의 경우 이 필드는 비어 있습니다.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|문자열|문서 소유자의 전자 메일 주소입니다.<br /><br /> 요청 형식이 RevokeAccess이면 이 필드는 비어 있습니다.|alice@contoso.com|
|issuer|문자열|문서 발급자의 전자 메일 주소입니다. <br /><br /> 요청 형식이 RevokeAccess이면 이 필드는 비어 있습니다.|alice@contoso.com (또는) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|template-id|문자열|문서를 보호하는 데 사용된 템플릿의 ID입니다. <br /><br /> 요청 형식이 RevokeAccess이면 이 필드는 비어 있습니다.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|file-name|문자열|Windows용 Azure Information Protection 클라이언트 또는 Windows용 Rights Management 공유 응용 프로그램을 사용하여 추적되는 보호된 문서의 파일 이름입니다. <br /><br />현재 일부 파일(예: Office 문서)은 실제 파일 이름을 아닌 GUID로 표시됩니다.<br /><br /> 요청 형식이 RevokeAccess이면 이 필드는 비어 있습니다.|TopSecretDocument.docx|
|date-published|날짜|문서를 보호한 날짜입니다.<br /><br /> 요청 형식이 RevokeAccess이면 이 필드는 비어 있습니다.|2015-10-15T21:37:00|
|c-info|문자열|요청을 수행하는 클라이언트 플랫폼에 대한 정보입니다.<br /><br />구체적인 문자열은 운영 체제, 브라우저 등의 응용 프로그램에 따라 다릅니다.|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|주소|요청을 수행하는 클라이언트의 IP 주소입니다.|64.51.202.144|
|admin-action|Bool|관리자가 관리자 모드에서 문서 추적 사이트를 액세스했는지 여부입니다.|True|
|acting-as-user|문자열|관리자가 해당 문서 추적 사이트에 액세스하는 사용자의 전자 메일 주소입니다. |'joe@contoso.com'|


#### <a name="exceptions-for-the-user-id-field"></a>use-id 필드에 대한 예외
user-id 필드는 보통 요청을 수행한 사용자를 나타내지만 해당 값이 실제 사용자에 매핑되지 않는 두 가지 예외가 있습니다.

-   **'microsoftrmsonline@&lt;테넌트 ID&gt;.rms.&lt;지역&gt;.aadrm.com'** 값

    이 값은 Exchange Online 또는 SharePoint Online과 같은 Office 365 서비스에서 요청을 수행함을 나타냅니다. 위 문자열에서 *&lt;테넌트 ID&gt;* 는 테넌트의 GUID이고, *&lt;지역&gt;* 은 테넌트가 등록된 지역입니다. 예를 들어 **na** 는 북미, **eu** 는 유럽, **ap** 는 아시아를 나타냅니다.

-   RMS 커넥터를 사용하는 경우

    이 커넥터로부터의 요청은 RMS 커넥터 설치 시 자동으로 생성되는 **Aadrm_S-1-7-0**라는 서비스 사용자 이름으로 기록됩니다.

#### <a name="typical-request-types"></a>일반적인 요청 형식
Azure Rights Management 서비스에는 다양한 요청 형식이 있습니다. 아래 표에는 가장 일반적으로 사용되는 몇 가지 요청 형식이 나와 있습니다.

|요청 형식|설명|
|----------------|---------------|
|AcquireLicense|클라이언트가 Windows 기반 컴퓨터에서 RMS로 보호된 콘텐츠용 라이선스를 요청합니다.|
|AcquirePreLicense|사용자 대신 클라이언트가 RMS로 보호된 콘텐츠에 대한 라이선스를 요청합니다.|
|AcquireTemplates|템플릿 ID에 따라 템플릿을 얻도록 호출했습니다.|
|AcquireTemplateInformation|서비스에서 템플릿 ID를 가져오도록 호출했습니다.|
|AddTemplate|Azure 포털에서 템플릿을 추가하도록 호출합니다.|
|AllDocsCsv|**모든 문서** 페이지에서 CSV 파일을 다운로드하도록 문서 추적 사이트에서 호출합니다.|
|BECreateEndUserLicenseV1|모바일 장치에서 최종 사용자 라이선스를 만들도록 호출합니다.|
|BEGetAllTemplatesV1|모바일 장치(백 엔드)에서 모든 템플릿을 가져오도록 호출합니다.|
|Certify|클라이언트가 보호할 콘텐츠를 인증합니다.|
|DeleteTemplateById|Azure 포털에서 템플릿 ID별로 템플릿을 삭제하도록 호출합니다.|
|DocumentEventsCsv|단일 문서에 대한 .CSV 파일을 다운로드하도록 문서 추적 사이트에서 호출합니다.|
|ExportTemplateById|Azure 포털에서 템플릿 ID에 따라 템플릿을 내보내도록 호출합니다.|
|FECreateEndUserLicenseV1|AcquireLicense 요청과 비슷하지만 모바일 장치에서 수행하는 요청입니다.|
|FECreatePublishingLicenseV1|Certify 및 GetClientLicensorCert가 결합된 형태의 요청으로, 모바일 클라이언트에서 사용됩니다.|
|FEGetAllTemplates|모바일 장치(프런트 엔드)에서 템플릿을 가져오도록 호출합니다.|
|FindServiceLocationsForUser|Certify 또는 AcquireLicense를 호출하는 데 사용되는 Url을 쿼리하도록 호출합니다.|
|GetAllDocs|사용자에 대한 **모든 문서** 페이지를 로드하거나 테넌트에 대한 모든 문서를 검색하도록 문서 추적 사이트에서 호출합니다. 관리 작업 및 관리자 권한으로 실행 필드와 함께 이 값을 사용합니다.<br /><br />- 관리 작업이 비어 있는 경우: 사용자에게 해당 문서에 대한 **모든 문서** 페이지가 표시됩니다.<br /><br />- 관리 작업이 true이고 사용자 권한으로 실행이 비어 있는 경우: 관리자에게 해당 테넌트에 대한 모든 문서가 표시됩니다.<br /><br />- 관리 작업이 true이고 사용자 권한으로 실행이 비어 있지 않은 경우: 관리자에게 사용자에 대한 **모든 문서**가 표시됩니다.|
|GetAllTemplates|Azure 포털에서 모든 템플릿을 가져오도록 호출합니다.|
|GetClientLicensorCert|클라이언트가 Windows 기반 컴퓨터에서 게시 인증서(나중에 콘텐츠를 보호하는 데 사용됨)를 요청합니다.|
|GetConfiguration|Azure PowerShell cmdlet은 Azure RMS 테넌트의 구성을 가져오도록 호출됩니다.|
|GetConnectorAuthorizations|RMS 커넥터에서 클라우드로부터 해당 구성을 가져오도록 호출합니다.|
|GetRecipients|단일 문서에 대한 목록 보기로 이동하도록 문서 추적 사이트에서 호출합니다.|
|GetSingle|**단일 문서**이동하도록 문서 추적 사이트에서 호출합니다.|
|GetTenantFunctionalState|Azure 포털에서 Azure Rights Management 서비스 활성화 여부를 확인합니다.|
|GetTemplateById|Azure 포털에서 템플릿 ID를 지정하여 템플릿을 가져오도록 호출합니다.|
|KeyVaultDecryptRequest|클라이언트가 RMS로 보호된 콘텐츠의 암호 해독을 시도합니다. Azure 주요 자격 증명 모음에서 고객이 관리하는 테넌트 키(BYOK)에 대해서만 적용할 수 있습니다.|
|KeyVaultGetKeyInfoRequest|Azure Key Vault에서 Azure Information Protection 테넌트 키에 대해 사용되도록 지정된 키가 액세스 가능하며 이미 사용되지 않는지 확인하기 위해 호출합니다.|
|KeyVaultSignDigest|서명 용도로 Azure 주요 자격 증명 모음의 고객 관리 키(BYOK)를 사용할 때 호출합니다. 대개 AcquireLicence(또는 FECreateEndUserLicenseV1), Certify 및 GetClientLicensorCert(또는 FECreatePublishingLicenseV1)당 한 번씩만 호출합니다.|
|KMSPDecrypt|클라이언트가 RMS로 보호된 콘텐츠의 암호 해독을 시도합니다. 레거시 고객 관리 테넌트 키(BYOK)에 대해서만 적용할 수 있습니다.|
|KMSPSignDigest|서명 용도로 레거시 고객 관리 키(BYOK)를 사용할 때 호출합니다. 대개 AcquireLicence(또는 FECreateEndUserLicenseV1), Certify 및 GetClientLicensorCert(또는 FECreatePublishingLicenseV1)당 한 번씩만 호출합니다.|
|LoadEventsForMap|단일 문서에 대한 맵 보기로 이동하도록 문서 추적 사이트에서 호출합니다.|
|LoadEventsForSummary|단일 문서에 대한 타임라인 보기로 이동하도록 문서 추적 사이트에서 호출합니다.|
|LoadEventsForTimeline|단일 문서에 대한 맵 보기로 이동하도록 문서 추적 사이트에서 호출합니다.|
|ImportTemplate|Azure 포털에서 템플릿을 가져오도록 호출합니다.|
|RevokeAccess|문서를 취소하도록 문서 추적 사이트에서 호출합니다.|
|SearchUsers |테넌트의 모든 사용자를 검색하도록 문서 추적 사이트에서 호출합니다.|
|ServerCertify|RMS 사용 클라이언트(예: SharePoint)에서 서버를 인증하도록 호출합니다.|
|SetUsageLogFeatureState|사용 현황 로깅을 사용하도록 호출합니다.|
|SetUsageLogStorageAccount|Azure Rights Management 서비스 로그의 위치를 지정하도록 호출합니다.|
|UpdateNotificationSettings|단일 문서에 대한 알림 설정을 변경하도록 문서 추적 사이트에서 호출합니다.|
|UpdateTemplate|Azure 포털에서 기존 템플릿을 업데이트하도록 호출합니다.|


## <a name="windows-powershell-reference"></a>Windows PowerShell 참조
2016년 2월부터 Azure Rights Management 사용 현황 로깅에 필요한 Windows PowerShell cmdlet은 [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog)뿐입니다. 

이러한 변경 전에는 Azure Rights Management 사용 현황 로그에 다음 cmdlet이 필요했으며,현재는 사용되지 않습니다.  

-   [Disable-AadrmUsageLogFeature](/powershell/module/aadrm/disable-aadrmusagelogfeature)

-   [Enable-AadrmUsageLogFeature](/powershell/module/aadrm/enable-aadrmusagelogfeature)

-   [Get-AadrmUsageLog](/powershell/module/aadrm/get-aadrmusagelog)

-   [Get-AadrmUsageLogFeature](/powershell/module/aadrm/get-aadrmusagelogfeature)

-   [Get-AadrmUsageLogLastCounterValue](/powershell/module/aadrm/get-aadrmusageloglastcountervalue)

-   [Get-AadrmUsageLogStorageAccount](/powershell/module/aadrm/get-aadrmusagelogstorageaccount)

-   [Set-AadrmUsageLogStorageAccount](/powershell/module/aadrm/set-aadrmusagelogstorageaccount)

Azure Rights Management 로깅 변경 전에 Azure 저장소에 로그가 있는 경우 전과 마찬가지로 Get-AadrmUsageLog 및 Get-AadrmUsageLogLastCounterValue를 사용하여 이러한 기존 cmdlet과 함께 로그를 다운로드할 수 있습니다. 하지만 새 사용 현황 로그 모두 새 Azure RMS 저장소에 기록되므로 Get-AadrmUserLog와 함께 다운로드해야 합니다.

Azure Rights Management 서비스용 Windows PowerShell 사용에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Azure Rights Management 서비스 관리](administer-powershell.md)를 참조하세요.



