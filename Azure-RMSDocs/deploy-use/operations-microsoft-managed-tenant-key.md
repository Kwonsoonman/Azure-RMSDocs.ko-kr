---
title: "Microsoft 관리 - AIP 테넌트 키 수명 주기 작업"
description: "Microsoft에서 Azure Information Protection용 테넌트 키를 관리하는 경우(기본값)와 관련하여 수명 주기 작업에 대한 정보를 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0b4e9cd5350f942203129979b05bc1344fb37aa5
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="microsoft-managed-tenant-key-lifecycle-operations"></a>Microsoft 관리: 테넌트 키 수명 주기 작업

>*적용 대상: Azure Information Protection, Office 365*

Microsoft에서 Azure Information Protection용 테넌트 키를 관리하는 경우(기본값) 다음 섹션에서 이 토폴로지와 관련된 수명 주기 작업에 대한 자세한 내용을 확인하세요.

## <a name="revoke-your-tenant-key"></a>테넌트 키 해지
Azure Information Protection에 대한 구독을 취소하면, Azure Information Protection에서 테넌트 키 사용이 중지되므로 별도의 조치가 필요하지 않습니다.

## <a name="re-key-your-tenant-key"></a>테넌트 키 다시 입력
키 다시 입력을 키 롤링이라고도 합니다. 반드시 필요한 경우가 아니면 테넌트 키를 다시 입력하지 마세요. Office 2010 등의 이전 클라이언트는 키 변경 내용을 정상적으로 처리하지 못합니다. 이러한 경우에는 그룹 정책 또는 해당하는 메커니즘을 사용하여 컴퓨터에서 Rights Management 상태를 지워야 합니다. 그러나 테넌트 키를 다시 입력해야 하는 몇 가지 상황도 있습니다. 예를 들면 다음과 같습니다.

-   회사가 둘 이상으로 분할된 경우. 테넌트 키를 다시 입력하면 새 회사에서는 직원이 게시하는 새 콘텐츠에 액세스할 수 없습니다. 이전 테넌트 키의 복사본이 있으면 이전 콘텐츠에는 액세스할 수 있습니다.

-   테넌트 키의 마스터 복사본(현재 소유 중인 복사본)이 노출되었다고 판단되는 경우.

[Microsoft 지원에 문의](../get-started/information-support.md#to-contact-microsoft-support)하여 **Azure Information Protection 테넌트 키 다시 입력 요청에 관한 Azure Information Protection 지원 케이스**를 열면 테넌트 키를 다시 입력할 수 있습니다. 자신이 Azure Information Protection 테넌트의 관리자임을 증명해야 하고, 이 프로세스를 확인하는 데 며칠이 걸린다는 것을 이해해야 합니다. 표준 지원 요금이 적용됩니다. 테넌트 키 다시 입력은 무료 지원 서비스가 아닙니다.

테넌트 키를 다시 입력하면 새 테넌트 키를 사용하여 새 콘텐츠를 보호합니다. 이 과정은 단계별로 진행되므로 일정 시간 동안에는 일부 새 콘텐츠가 계속해서 이전 테넌트 키로 보호됩니다. 이전에 보호되었던 콘텐츠도 이전 테넌트 키로 계속 보호됩니다. 이 시나리오를 지원하기 위해 Azure Information Protection에서는 이전 콘텐츠용 라이선스를 발급할 수 있도록 이전 테넌트 키를 보존합니다.

## <a name="backup-and-recover-your-tenant-key"></a>테넌트 키 백업/복구
Microsoft에서 테넌트 키를 백업하며 사용자는 아무런 작업을 수행할 필요가 없습니다.

## <a name="export-your-tenant-key"></a>테넌트 키 내보내기
다음&3;단계의 지침에 따라 Azure Information Protection 구성 및 테넌트 키를 내보낼 수 있습니다.

### <a name="step-1-initiate-export"></a>1단계: 내보내기 시작

-   그러려면, [Microsoft 지원에 문의](../get-started/information-support.md#to-contact-microsoft-support)하여 **Azure Information Protection 키 내보내기 요청에 관한 Azure Information Protection 지원 케이스**를 엽니다. 자신이 Azure Information Protection 테넌트의 관리자임을 증명해야 하고, 이 프로세스를 확인하는 데 며칠이 걸린다는 것을 이해해야 합니다. 표준 지원 요금이 적용됩니다. 테넌트 키 내보내기는 무료 지원 서비스가 아닙니다.

### <a name="step-2-wait-for-verification"></a>2단계: 확인 대기

-   Microsoft는 Azure Information Protection 테넌트 키 해제 요청이 합법적인지 확인합니다. 이 프로세스는 최대 3주까지 걸릴 수 있습니다.

### <a name="step-3-receive-key-instructions-from-css"></a>3단계: CSS에서 키 관련 지침 받기

-   Microsoft CSS(고객 지원 서비스)에서 Azure Information Protection 구성 및 테넌트 키를 파일 이름 확장명이 .tpd인 암호로 보호된 파일에 암호화된 상태로 포함하여 전송합니다. 이를 위해 CSS는 먼저 내보내기를 시작한 사용자에게 전자 메일로 도구를 보냅니다. 다음과 같이 명령 프롬프트에서 해당 도구를 실행해야 합니다.

    ```
    AadrmTpd.exe -createkey
    ```
    그러면 RSA 키 쌍이 생성되며 공용 및 개인 키가 현재 폴더에 파일로 저장됩니다. 예를 들어 **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** 및 **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**입니다.

    이름이 **PublicKey**로 시작하는 파일을 첨부하여 CSS의 메일에 회신합니다. 그러면 CSS에서 RSA 키를 사용하여 암호화된 .xml 파일 형태로 TPD 파일을 보냅니다. 원래 AadrmTpd 도구를 실행한 것과 같은 폴더에 이 파일을 복사하고 **PrivateKey**로 시작하는 파일과 CSS의 파일을 사용하여 도구를 다시 실행합니다. 예를 들면 다음과 같습니다.

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    이 명령을 실행하면 암호로 보호된 TPD의 일반 텍스트 암호가 포함된 파일, 암호로 보호된 TPD 자체 등 두 개의 파일이 출력됩니다. 상호 참조를 위해 두 파일의 GUID는 AadrmTpd.exe -createkey 명령을 실행할 때의 공용 키 및 개인 키 파일과 같아야 합니다.

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    이 테넌트 키로 보호되는 콘텐츠를 해독할 수 있게 이 파일을 백업하여 안전하게 보관합니다. 또한 AD RMS로 마이그레이션하는 경우에는 이 TPD 파일(**ExportedTDP**로 시작하는 파일)을 AD RMS 서버로 가져올 수 있습니다.

### <a name="step-4-ongoing-protect-your-tenant-key"></a>4단계: 지속적인 테넌트 키 보호

-   테넌트 키를 받은 후에는 지속적으로 보호해야 합니다. 테넌트 키에 액세스할 수 있으면 보호되는 모든 문서의 암호를 해당 키를 사용하여 해독할 수 있기 때문입니다.

    Azure Information Protection을 더 이상 사용하기 않기 위해 테넌트 키를 내보낼 경우 Azure Information Protection 테넌트에서 Azure Rights Management 서비스를 비활성화하는 것이 가장 좋습니다. 테넌트 키를 받을 때까지 기다렸다가 테넌트를 비활성화하지 마세요. 이러한 예방 조치를 취해야 권한이 없는 사람이 테넌트 키에 액세스하는 경우의 영향을 최소화할 수 있습니다. 지침은 [Azure 권한 관리 서비스 해제 및 비활성화](decommission-deactivate.md)를 참조하세요.

## <a name="respond-to-a-breach"></a>위반 사항에 대응
아무리 강력한 보안 시스템이라도 위반 대응 프로세스가 없다면 완벽하다고 할 수 없습니다. 테넌트 키는 노출되거나 도용될 수 있습니다. 테넌트 키를 효율적으로 보호한다고 하더라도 현재 생성 HSM 기술 또는 현재 키 길이/알고리즘에 취약점이 있을 수도 있습니다.

Microsoft에서는 전담 팀이 제품 및 서비스의 보안 문제에 대응하고 있습니다. 이 팀은 신뢰할 만한 문제 보고서가 확인되는 즉시 해당 범위, 근본 원인 및 완화 방법을 조사합니다. 이 문제가 사용자의 자산에 영향을 주는 경우 Microsoft는 구독 시 사용자가 제공한 주소를 사용해 전자 메일로 Azure Information Protection 테넌트 관리자에게 문제를 알립니다.

보안 위반이 발생한 경우 사용자나 Microsoft에서 수행할 수 있는 최선의 작업은 위반 범위에 따라 다르며, Microsoft는 사용자와 협의하여 이 프로세스를 진행합니다. 다음 표에는 몇 가지 일반적인 상황과 가능한 대응 방법이 나와 있습니다. 정확한 대응 방법은 조사 중에 확인되는 모든 정보에 따라 달라집니다.

|문제 설명|가능한 대응 방법|
|------------------------|-------------------|
|테넌트 키가 유출되었습니다.|테넌트 키를 다시 입력합니다. 이 문서에서 [테넌트 키 다시 입력](operations-microsoft-managed-tenant-key.md#re-key-your-tenant-key) 섹션을 참조하세요.|
|권한이 없는 개인이나 맬웨어가 테넌트 키 사용 권한을 확보했으나 키 자체가 유출되지는 않았습니다.|이 경우에는 테넌트 키를 다시 입력해도 도움이 되지 않으며 근본 원인을 분석해야 합니다. 프로세스 또는 소프트웨어 버그로 인해 권한이 없는 개인이 액세스 권한을 얻은 경우에는 해당 상황을 해결해야 합니다.|
|RSA 알고리즘이나 키 길이에 취약점이 있거나 전산상 무차별 암호 대입 공격(brute force attack)이 가능합니다.|Microsoft에서 복원 가능한 더 긴 키 길이와 새 알고리즘을 지원하도록 Azure Information Protection을 업데이트하고 모든 고객에게 테넌트 키를 갱신하도록 지시해야 합니다.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

