# <a name="functions"></a>함수

 함수(범위)                        | 설명                                
--------------------------------|---------------------------------------------
public const std::string& GetCustomSettingExportPolicyFileName()       |  SCC 정책 데이터를 내보낼 파일 경로를 명시적으로 지정하는 설정의 이름입니다.
public const std::string& GetCustomSettingPolicyDataFile()       |  정책 데이터 파일 경로를 명시적으로 지정하는 설정의 이름입니다.
public const std::string& GetCustomSettingPolicyDataName()       |  정책 데이터를 명시적으로 지정하는 설정의 이름입니다.
**mip 함수** |
public std::shared_ptr<mip::Stream> CreateStreamFromBuffer(uint8_t* buffer, const int64_t size)       |  버퍼에서 [스트림](class_mip_stream.md)을 만듭니다.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::iostream>& stdIOStream)       |  std::iostream에서 [스트림](class_mip_stream.md)을 만듭니다.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::istream>& stdIStream)       |  std::istream에서 [스트림](class_mip_stream.md)을 만듭니다.
public std::shared_ptr<mip::Stream> CreateStreamFromStdStream(const std::shared_ptr<std::ostream>& stdOStream)       |  std::ostream에서 [스트림](class_mip_stream.md)을 만듭니다.
**mip::Rights 함수**|
public std::string AuditedExtract()       |  ‘감사된 추출’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Comment()       |  ‘주석’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::vector<std::string> CommonRights()       |  모든 시나리오에 적용되는 권한 목록을 가져옵니다.
public std::string Edit()       |  ‘편집’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::vector<std::string> EditableDocumentRights()       |  문서에 적용되는 권한 목록을 가져옵니다.
public std::vector<std::string> EmailRights()       |  메일에 적용되는 권한 목록을 가져옵니다.
public std::string Export()       |  ‘내보내기’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Extract()       |  ‘추출’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Forward()       |  ‘전달’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Owner()       |  ‘소유자’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Print()       |  ‘인쇄’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string Reply()       |  ‘회신’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string ReplyAll()       |  ‘전체 회신’ 권한에 대한 문자열 식별자를 가져옵니다.
public std::string View()       |  ‘보기’ 권한에 대한 문자열 식별자를 가져옵니다.
**mip::Roles 함수**|
public std::string Author()       |  ‘작성자’ 역할의 문자열 식별자를 가져옵니다.
public std::string CoOwner()       |  ‘공동 소유자’ 역할에 대한 문자열 식별자를 가져옵니다.
public std::string Reviewer()       |  ‘검토자’ 역할에 대한 문자열 식별자를 가져옵니다.
public std::string Viewer()       |  ‘보기 권한자’ 역할에 대한 문자열 식별자를 가져옵니다.

  
## <a name="enumeration-details"></a>열거 세부 정보
  
## <a name="functions-common"></a>함수(일반)

### <a name="getcustomsettingpolicydataname"></a>GetCustomSettingPolicyDataName
정책 데이터를 명시적으로 지정하는 설정의 이름입니다.

  
**반환**: 사용자 지정 설정 키입니다.
  
### <a name="getcustomsettingexportpolicyfilename"></a>GetCustomSettingExportPolicyFileName
SCC 정책 데이터를 내보낼 파일 경로를 명시적으로 지정하는 설정의 이름입니다.

  
**반환**: 사용자 지정 설정 키입니다.
  
### <a name="getcustomsettingpolicydatafile"></a>GetCustomSettingPolicyDataFile
정책 데이터 파일 경로를 명시적으로 지정하는 설정의 이름입니다.

  
**반환**: 사용자 지정 설정 키입니다.

## <a name="functions-mip"></a>함수(mip)

### <a name="mipstream-istream"></a>mip::Stream (istream)

std::istream에서 [스트림](class_mip_stream.md)을 만듭니다.

매개 변수:  

* **stdIStream**: std::istream 지원
  
**반환**: std::istream을 래핑하는 [스트림](class_mip_stream.md) 입니다.
  
### <a name="mipstream-ostream"></a>mip::Stream (ostream)

std::ostream에서 [스트림](class_mip_stream.md)을 만듭니다.

매개 변수:  
* **stdOStream**: std::ostream 지원

  
**반환**: std::ostream을 래핑하는 [스트림](class_mip_stream.md)
  
### <a name="mipstream-iostream"></a>mip::Stream (iostream)

std::iostream에서 [스트림](class_mip_stream.md)을 만듭니다.

매개 변수:  
* **stdIOStream**: std::iostream 지원
  
**반환**: std::iostream을 래핑하는 [스트림](class_mip_stream.md)
  
### <a name="mipstream-buffer"></a>mip::Stream (buffer)

버퍼에서 [스트림](class_mip_stream.md)을 만듭니다.

매개 변수:  
* **buffer**: 버퍼에 대한 포인터

**리턴**: 버퍼의 크기
  
## <a name="functions-miprights"></a>함수(mip::rights)

### <a name="auditedextract"></a>AuditedExtract
‘감사된 추출’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘감사된 추출’ 권한에 대한 문자열 식별자
  
### <a name="comment"></a>설명
‘주석’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘주석’ 권한에 대한 문자열 식별자
  
### <a name="commonrights"></a>CommonRights
모든 시나리오에 적용되는 권한 목록을 가져옵니다.

  
**반환**: 모든 시나리오에 적용되는 권한 목록

### <a name="edit"></a>편집
‘편집’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘편집’ 권한에 대한 문자열 식별자
  
### <a name="editabledocumentrights"></a>EditableDocumentRights
문서에 적용되는 권한 목록을 가져옵니다.

  
**반환**: 문서에 적용되는 권한의 목록
  
### <a name="emailrights"></a>EmailRights
메일에 적용되는 권한 목록을 가져옵니다.

  
**반환**: 메일에 적용되는 권한의 목록
  
### <a name="export"></a>내보내기
‘내보내기’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘내보내기’ 권한에 대한 문자열 식별자
  
### <a name="extract"></a>추출
‘추출’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘추출’ 권한에 대한 문자열 식별자
  

### <a name="forward"></a>전달
‘전달’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘전달’ 권한에 대한 문자열 식별자
  
### <a name="owner"></a>Owner
‘소유자’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘소유자’ 권한에 대한 문자열 식별자
  
### <a name="print"></a>인쇄
‘인쇄’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘인쇄’ 권한에 대한 문자열 식별자
  
### <a name="reply"></a>회신
‘회신’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘회신’ 권한에 대한 문자열 식별자
  
### <a name="replyall"></a>전체 회신
‘전체 회신’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘전체 회신’ 권한에 대한 문자열 식별자
  
### <a name="view"></a>뷰
‘보기’ 권한에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘보기’ 권한에 대한 문자열 식별자
  
## <a name="functions-miproles"></a>함수(mip::roles)

### <a name="author"></a>Author
‘작성자’ 역할의 문자열 식별자를 가져옵니다.

  
**반환**: ‘작성자’ 역할에 대한 문자열 식별자. 작성자는 콘텐츠를 보고 편집하고 복사하고 인쇄할 수 있습니다.
  
### <a name="coowner"></a>CoOwner
‘공동 소유자’ 역할에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘공동 소유자’ 역할에 대한 문자열 식별자. 공동 소유자는 모든 권한을 가집니다.

### <a name="reviewer"></a>검토자
‘검토자’ 역할에 대한 문자열 식별자를 가져옵니다.

  
**반환**: ‘검토자’ 역할에 대한 문자열 식별자. 검토자는 콘텐츠를 보고 편집할 수 있습니다. 복사하거나 인쇄할 수는 없습니다.

### <a name="viewer"></a>보기 권한자
‘보기 권한자’ 역할에 대한 문자열 식별자를 가져옵니다.

  
**리턴**: ‘보기 권한자’ 역할에 대한 문자열 식별자. 보기 권한자는 콘텐츠를 볼 수만 있습니다. 편집하거나 복사하거나 인쇄할 수는 없습니다.
  
  
