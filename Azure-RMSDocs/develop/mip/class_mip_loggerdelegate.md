# <a name="class-miploggerdelegate"></a>class mip::LoggerDelegate 
mip sdk 로거에 대한 인터페이스를 정의하는 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public void Init(const std::string& storagePath)  |  로거를 초기화합니다.
 public void Flush()  |  로거를 플러시합니다.
 public void WriteToLog(const LogLevel level, const std::string& message, const std::string& function, const std::string& file, const uint64_t line)  |  로그 파일에 로그 문을 작성합니다.
  
## <a name="members"></a>멤버
  
### <a name="init"></a>Init
로거를 초기화합니다.

매개 변수:  
* **storagePath**: 로그를 포함하여 영구 상태가 저장될 수 있는 위치에 대한 경로입니다.


  
### <a name="flush"></a>플러시
로거를 플러시합니다.
  
### <a name="writetolog"></a>WriteToLog
로그 파일에 로그 문을 작성합니다.

매개 변수:  
* **level**: 로그 문의 로그 수준입니다. 


* **message**: 로그 문의 메시지입니다. 


* **function**: 로그 문의 함수 이름입니다. 


* **file**: 로그 문이 생성된 파일 이름입니다. 


* **line**: 로그 문이 생성된 줄 번호입니다.

