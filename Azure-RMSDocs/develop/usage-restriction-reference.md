---
# required metadata

title: 사용 제한 참조 | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5c1b0de6-e6d6-4ec9-b810-017fd606866e

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿# 사용 제한 참조

사용 제한은 이 항목에 나열된 상수에 의해 정의됩니다.



AD RMS 권한 열에 나열된 각 사용자 권한에는 설명, 적용 지점 및 제안된 적용 방법이 있습니다.

| AD RMS 권한 | 설명 | 일반적인 적용 지점 | 적용 방법 |
|--------------|-------------|---------------------------|----------------|
|IPC_GENERIC_ALL |사용자에게 모든 권한을 부여합니다.| 없음 |이 권한은 시스템에서 사용되며 일반적으로 직접 검사하면 안 됩니다. <br><br> 이 예제와 같이 [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)는 이 권한을 사용하여 사용자에게 다른 권한을 부여할지 여부를 결정합니다.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`
|IPC_GENERIC_READ |문서 내용을 읽을 수 있는 권한입니다.|문서 로드|문서 내용을 로드하거나 표시하지 않습니다.|
|IPC_GENERIC_WRITE|문서 내용을 편집할 수 있는 권한입니다.|문서 수정|문서 내용을 수정하는 데 사용할 수 있는 UI 컨트롤을 편집할 수 없도록 설정합니다. <br><br> 문서 변경을 트리거하는 메뉴 항목을 모두 사용하지 않도록 설정합니다. 일반적인 예로 **편집** > **잘라내기**, **편집** > **붙여넣기**, **삽입** 등이 있습니다. <br><br>문서 변경을 트리거하는 바로 가기 메뉴 항목을 모두 사용하지 않도록 설정합니다.|
|AD RMS 권한 없음|호출자에게 AD RMS 권한이 없습니다.|저장|**파일** > **저장** 메뉴를 사용하지 않도록 설정합니다. <br><br> **참고** 이 권한은 원본 문서의 변경을 나타내지 않으므로 **파일** > **다른 이름으로 저장**을 제어하지 않습니다.<br><br> 저장을 트리거하는 데 사용할 수 있는 바로 가기 키(예: Ctrl+S)를 모두 사용하지 않도록 설정합니다.<br><br> **팁** 사용자에게 이 권한이 없을 경우 실패하도록 핵심 **파일** > **저장** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 저장을 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다.
|IPC_GENERIC_EXTRACT|보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다.|클립보드에 복사|**편집** > **복사** 메뉴를 사용하지 않도록 설정합니다. **편집** > **잘라내기** 메뉴를 사용하지 않도록 설정합니다. <br><br>바로 가기 메뉴에서 **복사** 및 **잘라내기**를 사용하지 않도록 설정합니다.<br><br>복사를 트리거할 수 있는 바로 가기 키(예: Ctrl+C 또는 Ctrl+X)를 모두 사용하지 않도록 설정합니다.<br><br>사용자에게 이 권한이 없을 경우 데이터 복사를 거부하도록 [**WM_CUT**](https://msdn.microsoft.com/library/windows/desktop/ms649023)에 대한 창 메시지 처리기를 업데이트합니다. 창에서 기본 Windows 제공 메시지 처리기를 사용하는 경우 이 창을 서브클래스하고 **WM_COPY** 및 **WM_CUT**에 대한 고유의 처리기를 제공합니다.
|AD RMS 권한 없음|호출자에게 AD RMS 권한이 없습니다.|다른 이름으로 저장|**다른 이름으로 저장** 대화 상자에서 RMS 보호 없이 문서가 저장되게 하는 파일 형식을 모두 사용하지 않도록 설정합니다.|
|AD RMS 권한 없음|호출자에게 AD RMS 권한이 없습니다.|Alt+PrtScn|문서 내용을 렌더링하는 창에서 [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow)를 호출합니다.|
|IPC_GENERIC_EXPORT|보호된 형식에서 콘텐츠를 추출하여 다른 AD RMS 보호된 형식으로 저장할 수 있는 권한입니다.|다른 이름으로 저장|**다른 이름으로 저장** 대화 상자에서 다른 파일 형식으로 저장하는 기능을 사용하지 않도록 설정합니다.<br><br>**팁** 사용자가 이 파일을 다른 형식으로 저장하려고 하며 이 권한이 없을 경우 실패하도록 핵심 **파일** > **다른 이름으로 저장** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 다른 이름으로 저장을 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다.|
|IPC_GENERIC_PRINT|문서 내용을 인쇄할 수 있는 권한입니다.|인쇄|**파일** > **인쇄** 메뉴를 사용하지 않도록 설정합니다.<br><br>인쇄를 트리거하는 데 사용할 수 있는 바로 가기 키(예: Ctrl+P)를 모두 사용하지 않도록 설정합니다.<br><br>인쇄를 트리거하는 데 사용할 수 있는 바로 가기 메뉴 항목을 사용하지 않도록 설정합니다.<br><br>**팁** 사용자에게 이 권한이 없을 경우 실패하도록 핵심 **파일** > **인쇄** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 인쇄를 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다.|
|IPC_GENERIC_COMMENT|일부 응용 프로그램은 핵심 문서 내용을 업데이트하지 않고 문서에 주석을 추가하는 기능을 지원합니다.<br><br>이 권한은 이 기능에 대한 액세스 권한을 사용자에게 부여합니다.|검토 > 주석 삽입 <br><br> 검토 > 주석 삭제 | 문서 설명이나 주석을 수정하는 데 사용할 수 있는 메뉴 항목을 모두 사용하지 않도록 설정합니다. 예를 들어 **검토** > **주석 삽입**, **검토** > **주석 삭제** 등이 있습니다. <br><br>문서 주석 수정을 트리거할 수 있는 바로 가기 키를 모두 사용하지 않도록 설정합니다.<br><br>**참고** 새 주석을 파일에 저장하려면 기본 구현에 **IPC_GENERIC_COMMENT** 및 **IPC_GENERIC_WRITE**가 둘 다 필요합니다. 응용 프로그램에서 **IPC_GENERIC_COMMENT** 권한이 부여되고 **IPC_GENERIC_WRITE** 권한이 부여되지 않은 경우에 대한 지원을 추가할 수도 있습니다. 이 경우 문서 수정이 주석으로만 제한되면 저장할 수 있습니다.|
|IPC_VIEW_RIGHTS||해당 없음|시스템에 의해 적용됩니다. 이 권한이 부여되지 않은 경우 시스템에서 개발자가 라이선스에서 [**사용자 권한 목록**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_user_rights_list)을 쿼리하도록 허용하지 않습니다.
|IPC_EDIT_RIGHTS|일부 응용 프로그램은 사용자가 AD RMS 보호된 콘텐츠에 대한 사용자 및 권한 집합을 수정할 수 있도록 허용합니다.<br><br>이 권한은 이 기능에 대한 액세스 권한을 사용자에게 부여합니다.|응용 프로그램 권한 편집 UI 컨트롤|문서에 대한 RMS 정책을 편집하는 데 사용할 수 있는 UI에 사용자가 액세스할 수 없도록 설정합니다.|

 

 

 


<!--HONumber=Apr16_HO3-->

