# <a name="class-mipfilehandlerobserver"></a>클래스 mip::FileHandler::Observer 
클라이언트가 파일 처리기 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](#classmip_1_1_file_handler_1_1_observer) 인터페이스입니다.
*오류 이벤트가 발생하면 오류 개체는 [mip::Error](#classmip_1_1_error) 클래스 내부에 포함됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline virtual ~Observer()  |  
public void OnGetLabelSuccess(const std::shared_ptr<ContentLabel>& label, const std::shared_ptr<void>& context)  |  레이블이 파일에서 성공적으로 검색될 때 호출됩니다.
public void OnGetLabelFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 레이블을 파일에서 검색할 때 호출됩니다.
public void OnGetProtectionSuccess(const std::shared_ptr<UserPolicy>& userPolicy, const std::shared_ptr<void>& context)  |  보호 정책이 파일에서 성공적으로 검색될 때 호출됩니다.
public void OnGetProtectionFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 보호 정책을 파일에서 검색할 때 호출됩니다.
public void OnCommitSuccess(bool commited, const std::shared_ptr<void>& context)  |  파일에 대한 변경 내용이 성공적으로 커밋되었을 때 호출됩니다.
public void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  오류로 인해 실패한 파일에 대한 변경 내용을 커밋할 때 호출됩니다.
protected inline Observer()  |  
  
## <a name="members"></a>멤버
  
### <a name="observer"></a>~Observer
  
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