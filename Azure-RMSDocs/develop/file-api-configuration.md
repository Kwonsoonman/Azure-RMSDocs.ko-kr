---
title: "파일 API 구성 | Azure RMS"
description: "레지스트리 설정을 통해 파일 API의 동작을 구성할 수 있습니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 930878C2-D2B4-45F1-885F-64927CEBAC1D
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 56d0538243af49580f24c701ad5097b30f3059b0
ms.openlocfilehash: 46b1fe5a0c4f138db65072d14489a5d588015df7


---

# 파일 API 구성


레지스트리 설정을 통해 파일 API의 동작을 구성할 수 있습니다.

파일 API에서는 기본 보호와 PFile 보호라는 두 종류의 보호 기능을 제공합니다.

-   **기본 보호** - MIME 형식(파일 이름 확장명)을 기반으로 하는 AD RMS 형식으로 파일이 보호됩니다.
-   **PFile 보호** - AD RMS PFile(보호된 파일) 형식으로 파일이 보호됩니다.

지원되는 파일 형식에 대한 자세한 내용은 이 항목에서 **파일 API 파일 지원 세부 정보**를 참조하세요.

## 키/키 값 형식 및 설명

다음 섹션에서는 암호화를 제어하는 키와 키 값에 대해 설명합니다.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection

**형식**: 키

**설명**: 파일 API에 대한 일반 구성이 포함됩니다.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;

**형식**: 키

**설명**: 특정 파일 확장명(예: TXT, JPG 등)에 대한 구성 정보를 지정합니다.

- 와일드카드 문자 '*'가 허용되지만 특정 확장명에 대한 설정이 와일드카드 설정보다 우선합니다. 와일드카드 문자는 Microsoft Office 파일에 대한 설정에 영향을 주지 않습니다. 파일 형식별로 명시적으로 사용하지 않도록 설정해야 합니다.
- 확장명이 없는 파일을 지정하려면 '.'을 사용합니다.
- 특정 파일 확장명에 대한 키를 지정할 때는 '.' 문자를 지정하지 마세요. 예를 들어 `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT`를 사용하여 .txt 파일에 대한 설정을 지정합니다. `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`를 사용하지 마세요.

키의 **Encryption** 값을 설정하여 보호 동작을 지정합니다. **Encryption** 값을 설정하지 않으면 파일 형식에 대한 기본 동작을 따릅니다.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;\Encryption*

**형식**: REG_SZ

**설명**: 다음 세 가지 값 중 하나가 포함됩니다.

- **Off**: 암호화가 사용되지 않습니다.

> [!Note] 
> 이 설정은 암호 해독과 아무 관계도 없습니다. 기본 보호 또는 Pfile 보호를 통해 암호화되었는지와 관계없이, 사용자에게 **EXTRACT** 권한이 있는 한 암호화된 파일의 암호를 해독할 수 있습니다.

- **Native**: 기본 암호화가 사용됩니다. Office 파일의 경우 암호화된 파일의 확장명이 원본 파일과 같습니다. 예를 들어 .docx 파일 확장명을 가진 파일은 .docx 확장명을 가진 파일로 암호화됩니다. 기본 보호를 적용할 수 있는 기타 파일의 경우 p*zzz* 형식의 확장명을 가진 파일로 암호화됩니다. 여기서 *zzz*는 원래 파일 확장명입니다. 예를 들어 .txt 파일은 확장명이 .ptxt인 파일로 암호화됩니다. 아래에는 기본 보호를 적용할 수 있는 파일 확장명 목록이 나와 있습니다.

- **Pfile**: PFile 암호화가 사용됩니다. 암호화된 파일은 원래 확장명에 .pfile이 추가됩니다. 예를 들어 암호화 후에 .txt 파일은 .txt.pfile 확장명을 사용합니다.


> [!Note] 
> 이 설정은 Office 파일 형식과 아무 관계도 없습니다. 예를 들어 `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption` 값을 &quot;Pfile”로 설정할 경우 .docx 파일은 여전히 기본 보호를 사용하여 암호화되고 암호화된 파일이 계속 .docx 파일 확장명을 사용합니다.

다른 값을 설정하거나 값을 설정하지 않으면 기본 동작이 사용됩니다.

## 다양한 파일 형식에 대한 기본 동작

-   **Office 파일** 네이티브 암호화가 사용됩니다.
-   **txt, xml, jpg, jpeg, pdf, png, tiff, bmp, gif, giff, jpe, jfif, jif 파일** 네이티브 암호화가 사용됩니다(xxx가 pxxx로 바뀜).
-   **기타 모든 파일** 암호화 시 보호된 파일(pfile)을 사용할 수 있습니다(xxx가 xxx.pfile로 바뀜).

차단된 파일 형식에 대해 암호화를 시도하면 [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes) 오류가 발생합니다.

### 파일 API - 파일 지원 세부 정보

모든 파일 형식(확장)에 대해 기본 지원을 추가할 수 있습니다. 예를 들어 &lt;ext&gt; 확장명(비 Office)의 경우 해당 확장명에 대한 관리자 구성이 "NATIVE"이면 \*.p&lt;ext&gt;가 사용됩니다.

**Office 파일**

-   파일 확장명: doc, dot, xla, xls, xlt, pps, ppt, docm, docx, dotm, dotx, xlam, xlsb, xlsm, xlsx, xltm, xltx, xps, potm, potx, ppsx, ppsm, pptm, pptx, thmx
-   보호 유형 = 기본(기본값): sample.docx가 sample.docx로 암호화됩니다.
-   보호 유형 = Pfile: Office 파일의 경우 기본 보호와 동일한 효과가 있습니다.
-   Off: 암호화를 사용하지 않도록 설정합니다.

**PDF 파일**

-   보호 유형 = 기본: sample.pdf가 암호화되고 sample.ppdf로 이름이 바뀝니다.
-   보호 유형 = Pfile: sample.pdf가 암호화되고 sample.pdf.pfile로 이름이 바뀝니다.
-   Off: 암호화를 사용하지 않도록 설정합니다.

**기타 모든 파일 형식**

-   보호 유형 = Pfile: sample.*zzz*가 암호화되고 sample.*zzz*.pfile로 이름이 바뀝니다. 여기서 *zzz*는 원래 파일 확장명입니다.
-   Off: 암호화를 사용하지 않도록 설정합니다.

### 예

다음 설정은 txt 파일에 대해 PFile 암호화를 사용하도록 설정합니다. Office 파일의 경우 기본적으로 기본 보호가 적용되고, txt 파일의 경우 PFile 보호가 적용되고, 기타 모든 파일의 경우 기본적으로 보호가 차단됩니다.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               txt
                  Encryption = Pfile
```

다음 설정은 txt 파일을 제외한 모든 비-Office 파일에 대해 PFile 암호화를 사용하도록 설정합니다. Office 파일의 경우 기본적으로 기본 보호가 적용되고, txt 파일의 경우 보호가 차단되고, 기타 모든 파일의 경우 PFile 보호가 적용됩니다.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               *
                  Encryption = Pfile
               txt
                  Encryption = Off
```

다음 설정은 docx 파일에 대해 네이티브 암호화를 사용하지 않도록 설정합니다. docx 파일을 제외한 Office 파일의 경우 기본적으로 기본 보호가 적용되고, 기타 모든 파일의 경우 기본적으로 보호가 차단됩니다.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               docx
                  Encryption = Off
```

## 관련 항목

* [개발자 노트](developer-notes.md)
* [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes)
 

 



<!--HONumber=Jun16_HO4-->


