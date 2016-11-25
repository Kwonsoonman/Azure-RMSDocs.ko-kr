---
title: "Azure Rights Management 커넥터 모니터링 | Azure Information Protection"
description: "조직의 Azure Information Protection의 Azure Rights Management 서비스 사용과 커넥터를 모니터링하는 데 도움이 되는 정보를 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 65d9e0bb46238d9fda31b8fb47e8e4368d96e1b2


---

# <a name="monitor-the-azure-rights-management-connector"></a>Azure Rights Management 커넥터 모니터링

>*적용 대상: Azure Information Protection, Windows Server 2012, Windows Server 2012 R2*

RMS 커넥터를 설치하고 구성한 후에 다음과 같은 방법과 정보를 사용하여 커넥터와 조직의 Azure Information Protection의 Azure Rights Management 사용을 모니터링할 수 있습니다.

## <a name="application-event-log-entries"></a>응용 프로그램 이벤트 로그 항목

RMS 커넥터에서는 응용 프로그램 이벤트 로그를 사용하여 **Microsoft RMS 커넥터**의 항목을 기록합니다. 

예를 들어, 커넥터 서비스가 시작된 것을 확인하는 ID 1000, 서버가 RMS 커넥터에 연결된 것을 나타내는 ID 1002, 권한이 있는 계정의 목록(각 계정 나열)이 커넥터에 다운로드된 것을 나타내는 ID 1004와 같은 정보 이벤트가 있습니다. 

커넥터에서 HTTPS를 사용하도록 구성하지 않은 경우에는 클라이언트에서 비보안(HTTP) 연결을 사용하고 있음을 나타내는 경고 ID 2002가 표시될 수 있습니다.

커넥터에서 Azure Rights Management 서비스에 연결하지 못하면 오류 3001이 표시될 가능성이 큽니다. 예를 들어, 이러한 표시는 RMS 커넥터를 실행하는 하나 이상의 서버에 DNS 문제가 있거나 인터넷에 액세스할 수 없는 경우에 나타날 수 있습니다. 

> [!TIP]
> RMS 커넥터 서버에서 Azure Rights Management 서비스에 연결할 수 없는 경우는 웹 프록시 구성에 원인이 있을 가능성이 큽니다.

모든 이벤트 로그 항목이 그렇듯이, 자세한 내용을 보려면 메시지를 상세히 검색합니다.

커넥터를 처음 배포할 때 이벤트 로그를 확인하는 것 외에도, 지속적으로 경고와 오류를 확인합니다. 예를 들어, 처음에는 커넥터가 정상적으로 작동했는데 다른 관리자가 종속 구성을 변경할 수도 있습니다. 예를 들어, 다른 관리자가 RMS 커넥터 서버에서 더 이상 인터넷에 연결할 수 없도록 웹 프록시 서버 구성을 변경하거나(오류 3001) 커넥터 사용이 승인된 것으로 지정한 그룹에서 컴퓨터 계정을 제거할 수도 있습니다(경고 2001).

### <a name="event-log-ids-and-descriptions"></a>이벤트 로그 ID 및 설명

가능한 이벤트 ID, 설명 및 추가 정보를 식별하려면 다음 섹션을 사용하세요.

-----

정보 **1000**

**Microsoft RMS 커넥터 웹 서비스가 시작되었습니다.**

이 이벤트는 RMS 커넥터가 처음 시작되려 할 때 기록됩니다.

----

정보 **1001**

**Microsoft RMS 커넥터 웹 서비스가 중지되었습니다.**

이 이벤트는 RMS 커넥터가 정상적인 작업의 결과로 중지될 때 기록됩니다. 예를 들어 IIS가 다시 시작되거나 컴퓨터가 종료될 때입니다. 

----

정보 **1002**

**권한이 부여된 서버에 대해 Microsoft RMS 커넥터에 대한 액세스가 허용되었습니다.**

이 이벤트는 계정이 RMS 커넥터 관리자 도구에서 Azure RMS 관리자에 의해 권한이 부여된 후 온-프레미스 서버에서 이 계정이 처음 RMS 커넥터에 연결할 때 기록됩니다. SID, 계정 이름 및 연결을 수행하는 컴퓨터 이름은 이벤트 메시지에 포함되어 있습니다.

----

정보 **1003**

**아래 나열된 클라이언트에서의 연결은 비보안(HTTP) 연결에서 보안(HTTPS) 연결로 전환되었습니다.**

이 이벤트는 온-프레미스 서버가 RMS 커넥터에 대한 연결을 HTTP(낮은 보안 수준)에서 HTTPS(높은 보안 수준)로 변경할 때 기록됩니다. SID, 계정 이름 및 연결을 수행하는 컴퓨터 이름은 이벤트 메시지에 포함되어 있습니다.

----

정보 **1004**

**권한 있는 계정 목록이 업데이트되었습니다.**

이 이벤트는 RMS 커넥터가 RMS 커넥터 사용 권한이 있는 최신 계정 목록(기존 계정 및 모든 변경 사항)을 다운로드했을 때 기록됩니다. 이 목록은 RMS 커넥터가 Azure Rights Management 서비스와 통신할 수 있을 경우 15분마다 다운로드됩니다.

----

경고 **2000**

**HTTP 컨텍스트에서의 사용자 계정이 누락되었거나 잘못되었습니다. Microsoft RMS 커넥터 웹 사이트에 IIS에서 사용하지 않도록 설정된 익명 인증이 있고 Windows 인증만 사용할 수 있도록 설정되어 있는지를 확인하세요.**

이 이벤트는 RMS 커넥터가 RMS 커넥터에 연결하려고 하는 계정을 고유하게 식별할 수 없는 경우에 기록됩니다. 이러한 경우는 IIS에 대해 잘못 구성된 익명 인증으로 인한 것일 수 있으며, 아니면 계정이 신뢰할 수 없는 포리스트에 속해 있습니다.

----

경고 **2001**

**Microsoft RMS 커넥터에 대한 무단 액세스 시도입니다.**

이 이벤트는 계정이 RMS 커넥터에 연결을 시도하지만 실패할 때 기록됩니다. 이에 대한 가장 일반적인 이유는 연결을 수행하는 계정이 RMS 커넥터가 Azure Rights Management 서비스에서 다운로드하는 권한 있는 계정 목록에 없기 때문입니다. 예를 들어 이 최신 목록이 아직 다운로드되지 않았거나(15분마다 다운로드) 해당 계정이 목록에 없는 것입니다. 

또 다른 이유는 RMS 커넥터를 사용하도록 구성된 서버와 동일한 서버에 이 RMS 커넥터를 설치한 경우일 수 있습니다. 예를 들어 Exchange Server를 실행하는 서버에 RMS 커넥터를 설치하고 커넥터를 사용하도록 Exchange 계정에 권한을 부여한 경우입니다. 연결을 시도할 때에는 RMS 커넥터에서 해당 계정을 올바로 식별할 수 없기 때문에 이러한 구성이 지원되지 않습니다.

이벤트 메시지에는 계정 및 RMS 커넥터에 연결하려고 시도하는 컴퓨터에 대한 정보가 들어 있습니다.

- RMS 커넥터에 연결을 시도하는 계정이 올바른 계정인 경우에는 RMS 커넥터 관리자 도구를 사용하여 계정을 권한이 있는 계정 목록에 추가합니다. 권한이 있어야 하는 계정에 대한 자세한 내용은 [허용된 서버 목록에 서버를 추가하려면](install-configure-rms-connector.md#add-a-server-to-the-list-of-allowed-servers)을 참조하세요. 

- RMS 커넥터에 연결을 시도하는 계정이 RMS 커넥터 서버와 동일한 컴퓨터에 속하는 경우에는 커넥터를 별도의 서버에 설치하세요. 커넥터에 대한 필수 구성 요소에 대한 자세한 내용은 [RMS 커넥터의 사전 요구 사항]( deploy-rms-connector.md#prerequisites-for-the-rms-connector)을 참조하세요.

----

경고 **2002**

**아래에 나열된 클라이언트에서의 연결은 비보안(HTTP) 연결을 사용하고 있습니다.**

이 이벤트는 온-프레미스 서버에서 RMS 커넥터에 성공적으로 연결하지만 연결에서는 HTTPS(높은 보안 수준) 대신 HTTP(낮은 보안 수준)를 사용할 때 기록됩니다. 하나의 이벤트는 연결이 아닌 계정에 대해 기록됩니다. 이 이벤트는 계정이 HTTPS를 사용하도록 전환되었지만 HTTP로 되돌아가는 경우 다시 발생합니다.

이벤트 메시지는 계정 SID, 계정 이름 및 RMS 커넥터에 연결하는 컴퓨터의 이름을 포함합니다.

HTTPS 연결을 위해 RMS 커넥터를 구성하는 방법에 대해서는 [HTTPS를 사용하도록 RMS 커넥터 구성](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)을 참조하세요.

----

경고 **2003**

**권한 부여 목록이 비어 있습니다. 커넥터에 대한 권한이 있는 사용자 및 그룹의 목록이 채워질 때까지는 이 서비스를 사용할 수 없습니다.**

이 이벤트는 RMS 커넥터에 권한이 있는 계정 목록이 없고, 그래서 온-프레미스 서버가 커넥터에 연결할 수 없는 경우 기록됩니다. RMS 커넥터는 15분마다 Azure RMS에서 목록을 다운로드합니다. 

계정을 지정하려면 RMS 커넥터 관리자 도구를 사용하세요. 자세한 내용은 [RMS 커넥터를 사용하도록 서버에 권한 부여]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)를 참조하세요. 

----

오류 **3000**

**Microsoft RMS 커넥터에서 처리되지 않은 예외가 발생했습니다.**

이 이벤트는 RMS 커넥터에 예기치 않은 오류가 발생할 때마다 기록되며, 이벤트 메시지에는 오류에 대한 세부 정보가 포함됩니다.

한 가지 가능한 원인은 이벤트 메시지의 **빈 응답과 함께 요청이 실패했습니다** 텍스트로 확인할 수 있습니다. 이 텍스트가 표시되는 경우 온-프레미스 서버와 RMS 커넥터 서버 간의 패킷에 대한 SSL 검사를 수행하는 네트워크 장치가 있는 것일 수 있습니다. 이는 지원되지 않으며 사용할 경우 통신이 실패하고 이 이벤트 로그 메시지가 표시됩니다.

----

오류 **3001**

**권한 부여 정보를 다운로드하는 동안 예외가 발생했습니다.**

이 이벤트는 RMS 커넥터가 RMS 커넥터를 사용할 권한이 있는 최신 계정 목록을 다운로드할 수 없을 경우 기록됩니다. 이벤트 메시지에는 오류에 대한 세부 정보가 포함됩니다.



----

## <a name="performance-counters"></a>성능 카운터

RMS 커넥터를 설치하면 **Microsoft Rights Management 커넥터** 성능 카운터가 자동으로 생성되며, 이 카운터는 커넥터를 통해 Azure Rights Management 서비스의 사용 성능을 모니터링하는 데 유용합니다. 예를 들어, 문서나 메일을 보호하거나 보호된 문서 또는 메일을 열 때 정기적으로 지연이 발생하는 경우는 성능 카운터를 사용하여 지연의 원인이 커넥터의 처리 시간, Azure Rights Management 서비스의 처리 시간, 네트워크 지연 중 어느 것에 있는지 확인할 수 있습니다. 지연이 발생하는 위치를 쉽게 찾을 수 있도록 **커넥터 처리 시간**, **서비스 응답 시간**, **커넥터 응답 시간**의 평균 수를 포함하는 카운터를 확인합니다. 예: **라이선싱 성공 일괄 처리 요청 평균 커넥터 응답 시간**.

최근에 커넥터를 사용할 새 서버 계정을 추가한 경우에 **마지막 권한 부여 정책 업데이트 이후 시간** 카운터를 확인하여 커넥터를 업데이트한 후 목록을 다운로드했는지, 아니면 조금 더 기다려야 하는지(최대 15분) 확인할 수 있습니다.

## <a name="rms-analyzer"></a>RMS 분석기

Rights Management 서비스 분석기 도구를 사용하면 커넥터의 상태를 모니터링하고 구성 문제를 식별하는 데 유용합니다.

이 도구를 아직 다운로드하지 않은 경우에는 [다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=46437)에서 다운로드한 다음 인터넷에 연결할 수 있으며 RMS 커넥터에 연결된 컴퓨터에 설치할 수 있습니다. 도구를 실행하고 **시작** 페이지에서 **Azure RMS 커넥터** 옵션을 선택합니다.

추가 정보 및 지침은 다운로드 페이지의 **세부 정보** 및 **설치 지침**을 참조하세요.

## <a name="logging"></a>로깅

사용 현황 로깅은 메일과 문서가 보호되고 사용되는 경우를 식별할 때 유용합니다. 여기에 RMS 커넥터를 사용하는 경우, 로그의 사용자 ID 필드에는 RMS 커넥터에 대해 자동으로 생성되는 **Aadrm_S-1-7-0**이라는 서비스 사용자 이름이 포함됩니다.

사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management Service 사용 현황 로깅 및 분석](log-analyze-usage.md)을 참조하세요.

진단을 위해 더 자세한 로깅이 필요한 경우는 Windows Sysinternals에서 [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277)를 사용하고 IIS의 기본 사이트에서 web.config 파일을 구성하여 RMS 커넥터에 대한 추적을 사용하도록 설정할 수 있습니다. 이렇게 하려면 다음을 수행합니다.

1. **%programfiles%\Microsoft Rights Management connector\Web Service**에서 web.config 파일을 찾습니다.

2. 다음 줄을 찾습니다.

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. 이 줄을 다음으로 바꿉니다.

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  IIS를 중지했다가 시작하여 추적을 활성화합니다. 

5.  필요한 추적을 캡처한 경우에는 3단계에서 해당 줄을 되돌리고 IIS를 중지했다가 다시 시작합니다.




<!--HONumber=Nov16_HO2-->


