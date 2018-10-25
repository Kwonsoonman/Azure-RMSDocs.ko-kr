---
title: 클래스 mip FileHandler Observer
description: 클래스 mip FileHandler Observer에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a587107afc2b8963d64c31ad47af81761bf2b9f8
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446183"
---
# <a name="class-mipfilehandlerobserver"></a>클래스 mip::FileHandler::Observer 
클라이언트가 파일 처리기 관련 알림 이벤트를 가져오기 위한 [Observer](class_mip_filehandler_observer.md) 인터페이스입니다.
모든 오류는 [mip::Error](class_mip_error.md)에서 상속됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& context)  |  처리기가 성공적으로 생성될 때 호출됩니다.
public virtual void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  처리기를 만들지 못했을 때 호출됩니다.
public virtual void OnGetLabelSuccess(const std::shared_ptr<ContentLabel>& label, const std::shared_ptr<void>& context)  |  레이블을 성공적으로 검색했을 때 호출됩니다.
public virtual void OnGetLabelFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  레이블을 검색하지 못했을 때 호출됩니다.
public virtual void OnGetProtectionSuccess(const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& context)  |  보호 정책을 성공적으로 검색했을 때 호출됩니다.
public virtual void OnGetProtectionFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  보호 정책을 검색하지 못했을 때 호출됩니다.
public virtual void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context)  |  파일에 대한 변경 내용이 성공적으로 커밋되었을 때 호출됩니다.
public virtual void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  변경 내용을 파일에 커밋하지 못했을 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
처리기가 성공적으로 생성될 때 호출됩니다.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
처리기를 만들지 못했을 때 호출됩니다.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
레이블을 성공적으로 검색했을 때 호출됩니다.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
레이블을 검색하지 못했을 때 호출됩니다.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
보호 정책을 성공적으로 검색했을 때 호출됩니다.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
보호 정책을 검색하지 못했을 때 호출됩니다.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
파일에 대한 변경 내용이 성공적으로 커밋되었을 때 호출됩니다.
  
### <a name="oncommitfailure"></a>OnCommitFailure
변경 내용을 파일에 커밋하지 못했을 때 호출됩니다.