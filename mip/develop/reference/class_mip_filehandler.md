---
title: 클래스 mip FileHandler
description: 클래스 mip FileHandler에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: efae18bdc10f8878f255f35c608a50482a29887b
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446127"
---
# <a name="class-mipfilehandler"></a>클래스 mip::FileHandler 
모든 파일 처리 함수에 대한 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public void GetLabelAsync(const std::shared_ptr<void>& context)  |  파일에서 민감도 레이블 검색을 시작합니다.
public void GetProtectionAsync(const std::shared_ptr<void>& context)  |  파일에서 보호 정책 검색을 시작합니다.
 public void SetLabel(const std::string& labelId, const LabelingOptions& labelingOptions)  |  파일에 대한 민감도 레이블을 설정합니다.
 public void DeleteLabel(const LabelingOptions& labelingOptions)  |  파일에서 민감도 레이블을 삭제합니다.
public void SetProtection(const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  파일에 대한 사용자 지정 또는 템플릿 기반 권한을 설정합니다(protectionDescriptor->GetProtectionType에 따라).
 public void RemoveProtection()  |  파일에서 보호를 제거합니다. 파일에 레이블이 지정된 경우 레이블이 유실됩니다.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr<void>& context) | \|outputFilePath\로 지정된 파일에 변경 내용을 씁니다. |  매개 변수로 전달할 수 있습니다.
public void CommitAsync(const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& context) | \|outputStream\로 지정된 스트림에 변경 내용을 씁니다. |  매개 변수로 전달할 수 있습니다.
 public void NotifyCommitSuccessful(const std::string& contentIdentifier)  |  변경 내용이 디스크에 커밋된 경우 호출됩니다.
 public std::string GetOutputFileName()  |  원래 파일 이름 및 누적된 변경 내용을 기반으로 출력 파일 이름 및 확장명을 계산합니다.
  
## <a name="members"></a>멤버
  
### <a name="getlabelasync"></a>GetLabelAsync
파일에서 민감도 레이블 검색을 시작합니다.
[FileHandler::Observer](class_mip_filehandler_observer.md)는 성공 또는 실패 시 호출됩니다.

매개 변수:  
* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="getprotectionasync"></a>GetProtectionAsync
파일에서 보호 정책 검색을 시작합니다.
[FileHandler::Observer](class_mip_filehandler_observer.md)는 성공 또는 실패 시 호출됩니다.

매개 변수:  
* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


  
### <a name="setlabel"></a>SetLabel
파일에 대한 민감도 레이블을 설정합니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다. Privileged and Auto 메서드를 사용하면 API가 기존 레이블을 재정의할 수 있습니다. 레이블을 설정할 때 [JustificationRequiredError](class_mip_justificationrequirederror.md)를 throw하려면 labelingOptions 매개 변수를 통해 작업의 근거가 제공되어야 합니다.
  
### <a name="deletelabel"></a>DeleteLabel
파일에서 민감도 레이블을 삭제합니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다. Privileged and Auto 메서드를 사용하면 API가 기존 레이블을 재정의할 수 있습니다. 레이블을 설정할 때 [JustificationRequiredError](class_mip_justificationrequirederror.md)를 throw하려면 labelingOptions 매개 변수를 통해 작업의 근거가 제공되어야 합니다.
  
### <a name="setprotection"></a>SetProtection
파일에 대한 사용자 지정 또는 템플릿 기반 권한을 설정합니다(protectionDescriptor->GetProtectionType에 따라).
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다.
  
### <a name="removeprotection"></a>RemoveProtection
파일에서 보호를 제거합니다. 파일에 레이블이 지정된 경우 레이블이 유실됩니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다.
  
### <a name="commitasync"></a>CommitAsync
| outputFilePath | 매개 변수로 지정된 파일에 변경 내용을 씁니다.
[FileHandler::Observer](class_mip_filehandler_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="commitasync"></a>CommitAsync
| outputStream | 매개 변수로 지정된 스트림에 변경 내용을 씁니다.
[FileHandler::Observer](class_mip_filehandler_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="notifycommitsuccessful"></a>NotifyCommitSuccessful
변경 내용이 디스크에 커밋된 경우 호출됩니다.

매개 변수:  
* **contentIdentifier**: 파일의 예: "C:\mip-sdk-for-cpp\files\audit.docx" [path] 메일의 예: "RE: Audit design:user1@contoso.com" [Subject:Sender] 


감사 이벤트를 발생합니다.
  
### <a name="getoutputfilename"></a>GetOutputFileName
원래 파일 이름 및 누적된 변경 내용을 기반으로 출력 파일 이름 및 확장명을 계산합니다.