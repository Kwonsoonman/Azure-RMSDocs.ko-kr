# <a name="class-mipconsentresult"></a>클래스 mip::ConsentResult 
사용자 조작 후에 동의 요청의 결과를 설명합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline ConsentResult(bool accepted, bool showAgain, const std::string& userId)  |  [ConsentResult](#classmip_1_1_consent_result) 생성자입니다.
public inline bool Accepted() const  |  사용자가 동작에 동의했는지 여부를 가져옵니다.
public inline bool ShowAgain() const  |  미래 요청에 명시적 동의가 필요한지 여부를 가져옵니다.
public inline const std::string& UserId() const  |  동의를 요청한 사용자(메일 주소)를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](#classmip_1_1_consent_result) 생성자입니다.
  
#### <a name="parameters"></a>매개 변수
* accepted 사용자가 동작에 동의했는지 여부 
* showAgain 미래 동작 요청에 명시적 동의가 필요한지 여부 
* userId 동의를 요청한 사용자(메일 주소)
  
### <a name="accepted"></a>Accepted
사용자가 동작에 동의했는지 여부를 가져옵니다.
  
#### <a name="returns"></a>Returns
사용자가 동작에 동의했는지 여부
  
### <a name="showagain"></a>ShowAgain
미래 요청에 명시적 동의가 필요한지 여부를 가져옵니다.
  
#### <a name="returns"></a>Returns
미래 요청에 명시적 동의가 필요한지 여부, true인 경우 SDK는 이 동의 결과를 기억하고 나중에 동의를 묻는 메시지를 클라이언트 응용 프로그램에 표시하지 않습니다.
  
### <a name="userid"></a>UserId
동의를 요청한 사용자(메일 주소)를 가져옵니다.
  
#### <a name="returns"></a>Returns
동의를 요청한 사용자