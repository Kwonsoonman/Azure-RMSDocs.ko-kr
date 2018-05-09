# <a name="class-mipconsent"></a>클래스 mip::Consent 
동작 허용에 대한 사용자의 수락/거부를 나타냅니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const mip::ConsentResult& Result() const  |  동의 요청의 결과를 가져옵니다.
public void Result(const ConsentResult& value)  |  동의 요청의 결과를 설정합니다.
public mip::ConsentType Type() const  |  동의 유형을 가져옵니다.
public const std::vector<std::string> Urls() const  |  동의 요청에 포함된 URL을 가져옵니다.
public const std::string User() const  |  동의를 요청한 사용자(메일 주소)를 가져옵니다.
public const std::string Domain() const  |  동의를 요청한 사용자와 연결된 도메인을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="mipconsentresult"></a>mip::ConsentResult
동의 요청의 결과를 가져옵니다.
  
#### <a name="returns"></a>Returns
동의 요청의 결과
  
### <a name="result"></a>결과
동의 요청의 결과를 설정합니다.
  
#### <a name="parameters"></a>매개 변수
* value 동의 요청의 결과
  
### <a name="mipconsenttype"></a>mip::ConsentType
동의 유형을 가져옵니다.
  
#### <a name="returns"></a>Returns
동의 유형
  
### <a name="urls"></a>Urls
동의 요청에 포함된 URL을 가져옵니다.
  
#### <a name="returns"></a>Returns
동의 요청에 포함된 URL
  
### <a name="user"></a>사용자
동의를 요청한 사용자(메일 주소)를 가져옵니다.
  
#### <a name="returns"></a>Returns
동의를 요청한 사용자
  
### <a name="domain"></a>도메인
동의를 요청한 사용자와 연결된 도메인을 가져옵니다.
  
#### <a name="returns"></a>Returns
동의를 요청한 사용자와 연결된 도메인