---
title: 클래스 mip ProtectionEngine
description: 클래스 mip ProtectionEngine에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ddc8cfd58acb2a80d024978084b625f3d3728c87
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446739"
---
# <a name="class-mipprotectionengine"></a>class mip::ProtectionEngine 
특정 ID와 관련된 보호 관련 작업을 관리합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  엔진 설정을 가져옵니다.
public void GetTemplatesAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.
public std::vector<std::string> GetTemplates(const std::shared_ptr<void>& context)  |  사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.
public void GetRightsForLabelIdAsync(const std::string& documentId, const std::string& labelId, const std::string& ownerEmail, const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  레이블 ID에 대해 사용자가 사용할 수 있는 권한 컬렉션을 가져옵니다.
public std::vector<std::string> GetRightsForLabelId(const std::string& documentId, const std::string& labelId, const std::string& ownerEmail, const std::shared_ptr<void>& context)  |  labelId에 대해 사용자가 사용할 수 있는 권한 컬렉션을 가져옵니다.
public void GetGrantingLabelIdsAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  사용자가 사용할 수 있는 레이블 ID 컬렉션을 가져옵니다.
public std::vector<std::string> GetGrantingLabelIds(const std::shared_ptr<void>& context)  |  사용자가 사용할 수 있는 레이블 ID 컬렉션을 가져옵니다.
public void CreateProtectionHandlerFromDescriptorAsync(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromDescriptor(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.
public void CreateProtectionHandlerFromPublishingLicenseAsync(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  직렬화된 게시 라이선스에서 보호 처리기를 만듭니다.
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicense(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  직렬화된 게시 라이선스에서 보호 처리기를 만듭니다.
public void CreateProtectionHandlerFromPublishingLicenseContextAsync(const PublishingLicenseContext& publishingLicenseContext, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  게시 라이선스 컨텍스트에서 보호 처리기를 만듭니다.
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicenseContext(const PublishingLicenseContext& publishingLicenseContext, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  게시 라이선스 컨텍스트에서 보호 처리기를 만듭니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
엔진 설정을 가져옵니다.

  
**반환**: 엔진 설정
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.

매개 변수:  
* **observer**: [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 관찰자 및 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="gettemplates"></a>GetTemplates
사용자가 사용할 수 있는 템플릿 컬렉션을 가져옵니다.

매개 변수:  
* **context**: 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 불투명하게 전달될 클라이언트 컨텍스트



  
**반환**: 템플릿 ID 목록
  
### <a name="getrightsforlabelidasync"></a>GetRightsForLabelIdAsync
레이블 ID에 대해 사용자가 사용할 수 있는 권한 컬렉션을 가져옵니다.

매개 변수:  
* **documentId**: 문서 메타데이터와 연관된 문서 ID 


* **labelId**: 문서 생성에 사용된 문서 메타데이터와 연관된 [레이블](class_mip_label.md) ID 


* **ownerEmail**: 문서 소유자 


* **observer**: [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 이 동일한 컨텍스트가 [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) 또는 [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)에 전달됨


  
### <a name="getrightsforlabelid"></a>GetRightsForLabelId
labelId에 대해 사용자가 사용할 수 있는 권한 컬렉션을 가져옵니다.

매개 변수:  
* **documentId**: 문서 메타데이터와 연관된 문서 ID 


* **labelId**: 문서 생성에 사용된 문서 메타데이터와 연관된 [레이블](class_mip_label.md) ID 


* **ownerEmail**: 문서 소유자 


* **context**: 이 동일한 컨텍스트가 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 전달됨



  
**반환**: 권한 목록
  
### <a name="getgrantinglabelidsasync"></a>GetGrantingLabelIdsAsync
사용자가 사용할 수 있는 레이블 ID 컬렉션을 가져옵니다.

매개 변수:  
* **observer**: [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 이 동일한 컨텍스트가 [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) 또는 ProtectionEngine::Observer::OnGrantingLabelIdsFailure에 전달됨


  
### <a name="getgrantinglabelids"></a>GetGrantingLabelIds
사용자가 사용할 수 있는 레이블 ID 컬렉션을 가져옵니다.

매개 변수:  
* **context**: 이 동일한 컨텍스트가 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 전달됨



  
**반환**: 레이블 ID 목록
  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.

매개 변수:  
* **descriptor**: 보호 구성을 설명하는 [ProtectionDescriptor](class_mip_protectiondescriptor.md) 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 관찰자 및 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="protectionhandler"></a>ProtectionHandler
권한/역할이 특정 사용자에게 할당되는 보호 처리기를 생성합니다.

매개 변수:  
* **descriptor**: 보호 구성을 설명하는 [ProtectionDescriptor](class_mip_protectiondescriptor.md) 


* **options**: 생성 옵션 


* **context**: 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트



  
**반환**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
직렬화된 게시 라이선스에서 보호 처리기를 만듭니다.

매개 변수:  
* **serializedPublishingLicense**: 직렬화된 게시 라이선스 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 관찰자 및 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="protectionhandler"></a>ProtectionHandler
직렬화된 게시 라이선스에서 보호 처리기를 만듭니다.

매개 변수:  
* **serializedPublishingLicense**: 직렬화된 게시 라이선스 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트



  
**반환**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync"></a>CreateProtectionHandlerFromPublishingLicenseContextAsync
게시 라이선스 컨텍스트에서 보호 처리기를 만듭니다.

매개 변수:  
* **publishingLicenseContext**: 직렬화된 게시 라이선스의 미리 처리된 양식 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 관찰자 및 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="protectionhandler"></a>ProtectionHandler
게시 라이선스 컨텍스트에서 보호 처리기를 만듭니다.

매개 변수:  
* **publishingLicenseContext**: 직렬화된 게시 라이선스의 미리 처리된 양식 


* **options**: 생성 옵션 


* **observer**: [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) 인터페이스를 구현하는 클래스 


* **context**: 선택적인 [HttpDelegate](class_mip_httpdelegate.md)에 다시 불투명하게 전달될 클라이언트 컨텍스트



  
**반환**: [ProtectionHandler](class_mip_protectionhandler.md)