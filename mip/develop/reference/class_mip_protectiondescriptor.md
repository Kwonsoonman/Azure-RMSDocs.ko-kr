---
title: 클래스 mip ProtectionDescriptor
description: 클래스 mip ProtectionDescriptor에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e723041af1eec7be7a839bf36f6d3db67b32447f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446552"
---
# <a name="class-mipprotectiondescriptor"></a>class mip::ProtectionDescriptor 
콘텐츠와 연관된 보호에 대한 설명입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public ProtectionType GetProtectionType() const  |  보호 SDK 템플릿에서 비롯되었는지 여부와 관계없이 보호 유형을 가져옵니다.
 public std::string GetOwner() const  |  보호의 소유자를 가져옵니다.
 public std::string GetName() const  |  보호 이름을 가져옵니다.
 public std::string GetDescription() const  |  보호 설명을 가져옵니다.
 public std::string GetTemplateId() const  |  보호 템플릿 ID(있는 경우)를 가져옵니다.
 public std::string GetLabelId() const  |  레이블 ID(있는 경우)를 가져옵니다.
public std::vector<UserRights> GetUserRights() const  |  사용자-권한 매핑의 컬렉션을 가져옵니다.
public std::vector<UserRoles> GetUserRoles() const  |  사용자-역할 매핑의 컬렉션을 가져옵니다.
public std::chrono::time_point<std::chrono::system_clock> GetContentValidUntil() const  |  보호 정책 만료 시간을 설정합니다.
 public bool DoesAllowOfflineAccess() const  |  보호에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.
 public std::string GetReferrer() const  |  보호 참조 주소를 설정합니다.
public std::map<std::string, std::string> GetEncryptedAppData() const  |  암호화된 앱별 데이터를 가져옵니다.
public std::map<std::string, std::string> GetSignedAppData() const  |  서명된 앱별 데이터를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="protectiontype"></a>ProtectionType
보호 SDK 템플릿에서 비롯되었는지 여부와 관계없이 보호 유형을 가져옵니다.

  
**반환**: 보호 유형
  
### <a name="getowner"></a>GetOwner
보호의 소유자를 가져옵니다.

  
**반환**: 보호의 소유자
  
### <a name="getname"></a>GetName
보호 이름을 가져옵니다.

  
**반환**: 보호 이름
  
### <a name="getdescription"></a>GetDescription
보호 설명을 가져옵니다.

  
**반환**: 보호 설명
  
### <a name="gettemplateid"></a>GetTemplateId
보호 템플릿 ID(있는 경우)를 가져옵니다.

  
**반환**: 템플릿 ID
  
### <a name="getlabelid"></a>GetLabelId
레이블 ID(있는 경우)를 가져옵니다.

  
**반환**: [레이블](class_mip_label.md) ID. 이 속성은 기존의 보호된 콘텐츠에 대한 ProtectionDescriptors에만 채워집니다. 보호된 콘텐츠가 사용되자마자 서버가 채우는 필드입니다.
  
### <a name="userrights"></a>UserRights
사용자-권한 매핑의 컬렉션을 가져옵니다.

  
**반환**: 사용자-권한 매핑 컬렉션. 현재 사용자에게 이 정보에 대한 액세스 권한이 없는 경우(다시 말해서 사용자는 정보 소유자가 아니며 VIEWRIGHTSDATA 권한이 없음) [UserRights](class_mip_userrights.md) 속성 값이 비어 있습니다.
  
### <a name="userroles"></a>UserRoles
사용자-역할 매핑의 컬렉션을 가져옵니다.

  
**반환**: 사용자-역할 매핑의 컬렉션
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
보호 정책 만료 시간을 설정합니다.

  
**반환**: 보호 만료 시간
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
보호에서 오프라인 콘텐츠 액세스를 허용하는지 여부를 가져옵니다.

  
**반환**: 보호에서 오프라인 콘텐츠 액세스를 허용하는지 여부(기본값 = true)
  
### <a name="getreferrer"></a>GetReferrer
보호 참조 주소를 설정합니다.

  
**반환**: 보호 참조 주소. 참조 주소는 사용자가 콘텐츠 보호를 해제할 수 없는 경우 사용자에게 표시할 수 있는 URI입니다. 사용자가 콘텐츠 액세스 권한을 얻을 수 있는 방법에 대한 정보가 포함되어 있습니다.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
암호화된 앱별 데이터를 가져옵니다.

  
**반환**: 앱별 데이터. [ProtectionHandler](class_mip_protectionhandler.md)에는 보호 서비스에 의해 암호화된 앱별 데이터 사전이 포함될 수 있습니다. 이 암호화된 데이터는 [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata)를 통해 액세스할 수 있는 서명된 데이터와 관련이 없습니다.
  
### <a name="getsignedappdata"></a>GetSignedAppData
서명된 앱별 데이터를 가져옵니다.

  
**반환**: 앱별 데이터. [ProtectionHandler](class_mip_protectionhandler.md)에는 보호 서비스에 의해 서명된 앱별 데이터 사전이 포함될 수 있습니다. 이 서명된 데이터는 [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)를 통해 액세스할 수 있는 암호화된 데이터와 관련이 없습니다.