---
title: 클래스 mip ProtectionDescriptorBuilder
description: 클래스 mip ProtectionDescriptorBuilder에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 42e44cfaf269a43d0210c0c040ea70ccc1fb192e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446637"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>class mip::ProtectionDescriptorBuilder 
콘텐츠 부분과 관련된 보호를 설명하는 [ProtectionDescriptor](class_mip_protectiondescriptor.md)를 생성합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public MIP_API std::shared_ptr<ProtectionDescriptor> Build()  |  이 [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) 인스턴스에 의해 액세스 권한이 정의된 [ProtectionDescriptor](class_mip_protectiondescriptor.md)를 만듭니다.
 public void SetName(const std::string& value)  |  보호 정책 이름을 설정합니다.
 public void SetDescription(const std::string& value)  |  보호 정책 설명을 설정합니다.
public void SetContentValidUntil(const std::chrono::time_point<std::chrono::system_clock>& value)  |  보호 정책 만기 시간을 설정합니다.
 public void SetAllowOfflineAccess(bool value)  |  보호 정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 설정합니다.
 public void SetReferrer(const std::string& uri)  |  보호 정책 참조 주소를 설정합니다.
public void SetEncryptedAppData(const std::map<std::string, std::string>& value)  |  암호화해야 하는 앱별 데이터를 설정합니다.
public void SetSignedAppData(const std::map<std::string, std::string>& value)  |  서명해야 하는 앱별 데이터를 설정합니다.
 public virtual ~ProtectionDescriptorBuilder()  | _아직 문서화되지 않았습니다._
  
## <a name="members"></a>멤버
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
이 [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md) 인스턴스에 의해 액세스 권한이 정의된 [ProtectionDescriptor](class_mip_protectiondescriptor.md)를 만듭니다.

  
**반환**: 새 [ProtectionDescriptor](class_mip_protectiondescriptor.md) 인스턴스
  
### <a name="setname"></a>SetName
보호 정책 이름을 설정합니다.

매개 변수:  
* **value**: 보호 정책 이름


  
### <a name="setdescription"></a>SetDescription
보호 정책 설명을 설정합니다.

매개 변수:  
* **value**: 정책 설명


  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
보호 정책 만기 시간을 설정합니다.

매개 변수:  
* **value**: 정책 만료 시간


  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
보호 정책에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 설정합니다.

매개 변수:  
* **value**: 보호 정책이 오프라인 콘텐츠 액세스를 허용하는지 여부


  
### <a name="setreferrer"></a>SetReferrer
보호 정책 참조 주소를 설정합니다.

매개 변수:  
* **uri**: 정책 참조 주소


참조는 사용자가 콘텐츠에 액세스할 권한을 얻는 방법에 대한 정보가 포함된 보호 정책 취득 실패 시 사용자에게 표시될 수 있는 URI입니다.
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
암호화해야 하는 앱별 데이터를 설정합니다.

매개 변수:  
* **value**: 앱별 데이터


애플리케이션이 보호 서비스에서 암호화되는 앱별 데이터의 사전을 지정할 수 있습니다. 이 암호화된 데이터는 SetSignedAppData를 통해 설정된 서명된 데이터와 관련이 없습니다.
  
### <a name="setsignedappdata"></a>SetSignedAppData
서명해야 하는 앱별 데이터를 설정합니다.

매개 변수:  
* **value**: 앱별 데이터


애플리케이션이 보호 서비스에서 서명되는 앱별 데이터의 사전을 지정할 수 있습니다. 이 서명된 데이터는 SetEncryptedAppData를 통해 설정된 암호화된 데이터와 관련이 없습니다.
  
### <a name="protectiondescriptorbuilder"></a>~ProtectionDescriptorBuilder
_아직 문서화되지 않았습니다._
