---
title: Azure Information Protection이 중앙 보고
description: 중앙 보고 기능을 사용하여 Azure Information Protection 레이블의 도입을 추적하고 중요한 정보를 포함하는 파일을 식별하는 방법
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/27/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: cf951bba3cc74a82e31841986dde9e75ec34a630
ms.sourcegitcommit: e70bb1a02e96d701fd5ae2a25536fa485bbf2e87
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48862127"
---
# <a name="central-reporting-for-azure-information-protection"></a>Azure Information Protection이 중앙 보고

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> 이 기능은 현재 미리 보기 상태이며 변경될 예정입니다. 이 미리 보기 동안 수집한 데이터는 기능을 일반 공급으로 전환하는 동안 지원되지 않을 수 있습니다.


Azure Information Protection 분석을 사용하여 중앙 보고 기능에서 레이블이 지정된 문서 및 메일에 대한 사용자 액세스와 분류 변경 내용을 모니터링할 수 있을 뿐만 아니라 Azure Information Protection 레이블 도입을 추적할 수 있습니다. 또한 보호해야 하는 중요한 정보를 포함하는 문서를 식별할 수 있습니다.

사용자에게 표시되는 데이터는 Azure Information Protection 클라이언트, Azure Information Protection 검사기 및 [통합 레이블 지정을 지원하는 클라이언트](configure-policy-migrate-labels.md#clients-that-support-unified-labeling)에서 집계됩니다.

예를 들어 다음을 볼 수 있습니다.

- 기간을 선택할 수 있는 **사용 현황 보고서**:
    
    - 적용할 레이블
    
    - 레이블을 지정할 문서 및 메일 수
    
    - 보호할 문서 및 메일 수
    
    - 문서 및 메일에 레이블을 지정하는 사용자 및 장치 수
    
    - 레이블 지정에 사용할 응용 프로그램

- **데이터 검색** 보고서:

    - 검사한 데이터 리포지토리에 있는 파일
    
    - 레이블이 지정되고 보호되는 파일 및 레이블별 파일 위치
    
    - 알려진 범주의 중요한 정보(예: 재무 데이터 및 개인 정보)를 포함하는 파일과 이러한 범주별 파일 위치
    
보고서는 [Azure Log Analytics](/azure/log-analytics/log-analytics-overview)를 사용하여 사용자가 소유하는 작업 영역에 데이터를 저장합니다. 쿼리 언어에 익숙한 경우 해당 쿼리를 수정할 수 있으며 새 보고서와 Power BI 대시보드를 만들 수 있습니다. 자습서 [분석 포털 시작](https://docs.loganalytics.io/docs/Learn/Getting-Started/Getting-started-with-the-Analytics-portal)은 쿼리 언어를 이해하는 데 도움이 될 수 있습니다. 

자세한 내용은 블로그 게시물 [Data discovery, reporting and analytics for all your data with Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)(Microsoft Information Protection을 사용한 모든 데이터의 데이터 검색, 보고 및 분석)을 참조하세요.

### <a name="information-collected-and-sent-to-microsoft"></a>수집되어 Microsoft로 전송된 정보

이러한 보고서를 생성하기 위해 엔드포인트는 다음 유형의 정보를 Microsoft로 보냅니다.

- 레이블 작업. 예를 들어 레이블을 설정하거나, 레이블을 변경하거나, 보호, 자동 및 권장 레이블을 추가 또는 제거합니다.

- 조직의 테넌트 ID

- 사용자 ID(메일 주소 또는 UPN)

- 레이블이 지정된 문서의 파일 경로 및 파일 이름

- Azure Information Protection 클라이언트의 버전

- 클라이언트 운영 체제 버전

이 정보는 사용자가 소유한 Azure Log Analytics 작업 영역에 저장됩니다.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Azure Information Protection 분석의 필수 구성 요소
Azure Information Protection 보고서를 보고 직접 만들려면 다음 요구 사항이 충족되어야 합니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|Log Analytics를 포함하는 Azure 구독|[Azure Log Analytics 가격 책정](https://azure.microsoft.com/pricing/details/log-analytics) 페이지를 참조하세요.<br /><br />Azure 구독이 없거나 현재, Azure Log Analytics를 사용하지 않는 경우 가격 책정 페이지에 평가판에 대한 링크를 포함됩니다.|
|Azure Information Protection 클라이언트의 현재 미리 보기 버전|현재 미리 보기 버전의 클라이언트를 아직 설치하지 않은 경우 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=53018)에서 다운로드한 후 설치할 수 있습니다.|
|**검색 및 위험** 보고서: <br /><br />- 둘 이상의 Azure Information Protection 검사기(현재 미리 보기 버전) 인스턴스 배포|자세한 내용은 [Azure Information Protection 검사기를 배포하여 파일을 자동으로 분류 및 보호](deploy-aip-scanner.md)를 참조하세요. <br /><br />이전 버전의 검사 기능에서 업그레이드하는 경우 [Azure Information Protection 검사기 업그레이드](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner)를 참조하세요.|


## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>보고서의 Log Analytics 작업 영역 구성

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.
    
2. **관리** 메뉴 옵션을 찾고 **분석 구성(미리 보기)** 을 선택합니다.

3. **Azure Information Protection Log Analytics** 블레이드에서 테넌트가 소유한 모든 Log Analytics 작업 영역 목록을 확인합니다. 다음 중 하나를 수행합니다.
    
    - 새 Log Analytics 작업 영역 만들기: **새 작업 영역 만들기**를 선택하고 **Log Analytics 작업 영역** 블레이드에서 요청된 정보를 제공합니다.
    
    - 기존 Log Analytics 작업 영역 사용: 목록에서 해당 작업 영역을 선택합니다.

Log Analytics 작업 영역을 만드는 데 도움이 필요한 경우 [Azure Portal에서 Log Analytics 작업 영역 만들기](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace)를 참조하세요.

작업 영역이 구성되면 보고서를 볼 준비가 된 것입니다.

## <a name="how-to-view-the-reports"></a>보고서 확인 방법

Azure Information Protection 블레이드에서 **대시보드(미리 보기)** 메뉴 옵션을 찾은 후 다음 옵션 중 하나를 선택합니다.

- **사용 현황 보고서**: 레이블이 사용되는 방식을 확인하려면 이 보고서를 사용합니다. 

- **데이터 검색**: 검사 기능이 찾은 파일에 대한 정보를 보려면 이 보고서를 사용합니다.

## <a name="how-to-modify-the-reports"></a>보고서 수정 방법

대시보드의 쿼리 아이콘을 선택하여 **로그 검색** 블레이드를 엽니다. 

![Azure Information Protection 보고서를 사용자 지정하기 위한 Log Analytics 아이콘](./media/log-analytics-icon.png)


## <a name="next-steps"></a>다음 단계
보고서의 정보를 검토한 후에 Azure Information Protection 정책을 변경할지 결정할 수 있습니다. 지침에 대해서는 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.