# <a name="class-mipfilehandlerobserver"></a>클래스 mip::FileHandler::Observer 
클라이언트가 파일 처리기 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_filehandler_observer.md) 인터페이스입니다.
*오류 이벤트가 발생하면 오류 개체는 [mip::Error](class_mip_error.md) 클래스 내부에 포함됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public virtual ~Observer()  | _아직 문서화되지 않았습니다._
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& context)  |  처리기가 성공적으로 생성될 때 호출됩니다.
public virtual void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 처리기 생성이 실패한 경우 호출됩니다.
public virtual void OnGetLabelSuccess(const std::shared_ptr<ContentLabel>& label, const std::shared_ptr<void>& context)  |  레이블이 파일에서 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetLabelFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 레이블을 파일에서 검색할 때 호출됩니다.
public virtual void OnGetProtectionSuccess(const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& context)  |  보호 정책이 파일에서 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetProtectionFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 보호 정책을 파일에서 검색할 때 호출됩니다.
public virtual void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context)  |  파일에 대한 변경 내용이 성공적으로 커밋되었을 때 호출됩니다.
public virtual void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 파일에 대한 변경 내용을 커밋할 때 호출됩니다.
 protected Observer()  | _아직 문서화되지 않았습니다._
  
## <a name="members"></a>멤버
  
### <a name="observer"></a>~Observer
_아직 문서화되지 않았습니다._

  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
처리기가 성공적으로 생성될 때 호출됩니다.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
오류로 인해 처리기 생성이 실패한 경우 호출됩니다.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
레이블이 파일에서 성공적으로 검색될 때 호출됩니다.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
오류로 인해 실패한 레이블을 파일에서 검색할 때 호출됩니다.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
보호 정책이 파일에서 성공적으로 검색될 때 호출됩니다.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
오류로 인해 실패한 보호 정책을 파일에서 검색할 때 호출됩니다.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
파일에 대한 변경 내용이 성공적으로 커밋되었을 때 호출됩니다.
  
### <a name="oncommitfailure"></a>OnCommitFailure
오류로 인해 실패한 파일에 대한 변경 내용을 커밋할 때 호출됩니다.
  
### <a name="observer"></a>관찰자
_아직 문서화되지 않았습니다._
