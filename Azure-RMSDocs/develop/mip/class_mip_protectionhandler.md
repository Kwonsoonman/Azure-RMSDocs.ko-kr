# <a name="class-mipprotectionhandler"></a>class mip::ProtectionHandler 
특정 보호 구성(사용자, 권한, 역할 등)에 대한 보호 관련 동작을 수행합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public std::shared_ptr<Stream> CreateProtectedStream(const std::shared_ptr<Stream>& backingStream, uint64_t contentStartPosition, uint64_t contentSize)  |  콘텐츠의 암호화/암호 해독을 허용하는 보호된 스트림을 생성합니다.
 public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  버퍼를 암호화합니다.
 public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  버퍼를 암호 해독합니다.
 public uint64_t GetProtectedContentLength(uint64_t size)  |  이 [ProtectionHandler](class_mip_protectionhandler.md)로 암호화되는 경우 콘텐츠의 크기(바이트)를 계산합니다.
 public uint64_t GetBlockSize()  |  이 [ProtectionHandler](class_mip_protectionhandler.md)에서 사용하는 암호화 모드의 블록 크기(바이트)를 가져옵니다.
 public bool AccessCheck(const std::string& right) const  |  보호 처리기가 지정된 액세스 권한을 사용자에게 부여하는지 확인합니다.
 public const std::string GetIssuedTo()  |  보호 처리기와 연결된 사용자를 가져옵니다.
 public const std::string GetOwner()  |  콘텐츠 소유자의 메일 주소를 가져옵니다.
 public bool IsIssuedToOwner()  |  현재 사용자가 콘텐츠 소유자인지 여부를 가져옵니다.
public std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor()  |  보호 세부 정보를 가져옵니다.
 public const std::string GetContentId()  |  문서/콘텐츠에 대한 고유 식별자를 가져옵니다.
 public bool DoesUseDeprecatedAlgorithms()  |  보호 처리기에서 이전 버전과의 호환성을 위해 사용 중단된 암호화 알고리즘(ECB)을 사용하는지 여부를 가져옵니다.
 public bool IsAuditedExtractAllowed()  |  보호 처리기가 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부를 가져옵니다.
public const std::vector<uint8_t> GetSerializedPublishingLicense()  |  [ProtectionHandler](class_mip_protectionhandler.md)를 PL(게시 라이선스)로 직렬화합니다.
  
## <a name="members"></a>멤버
  
### <a name="stream"></a>스트림
콘텐츠의 암호화/암호 해독을 허용하는 보호된 스트림을 생성합니다.

매개 변수:  
* **backingStream**: 읽기/쓰기를 수행할 지원 스트림 


* **contentStartPosition**: 보호된 콘텐츠가 시작되는 지원 스트림 내의 시작 위치(바이트) 


* **contentSize**: 지원 스트림 내 보호된 콘텐츠의 크기(바이트)



  
**반환**: 보호된 스트림
  
### <a name="encryptbuffer"></a>EncryptBuffer
버퍼를 암호화합니다.

매개 변수:  
* **offsetFromStart**: 일반 텍스트 콘텐츠의 맨 처음을 기준으로 inputBuffer의 상대적인 위치 


* **inputBuffer**: 암호화될 일반 텍스트 콘텐츠의 버퍼 


* **inputBufferSize**: 입력 버퍼의 크기(바이트) 


* **outputBuffer**: 암호화된 콘텐츠가 복사될 버퍼 


* **outputBufferSize**: 출력 버퍼의 크기(바이트) 


* **isFinal**: 입력 버퍼에 마지막 일반 텍스트 바이트가 포함되는지 여부



  
**반환**: 암호화된 콘텐츠의 실제 크기(바이트)
  
### <a name="decryptbuffer"></a>DecryptBuffer
버퍼를 암호 해독합니다.

매개 변수:  
* **offsetFromStart**: 암호화된 콘텐츠의 맨 처음을 기준으로 inputBuffer의 상대적인 위치 


* **inputBuffer**: 암호 해독될 암호화된 콘텐츠의 버퍼 


* **inputBufferSize**: 입력 버퍼의 크기(바이트) 


* **outputBuffer**: 암호 해독된 콘텐츠가 복사될 버퍼 


* **outputBufferSize**: 출력 버퍼의 크기(바이트) 


* **isFinal**: 입력 버퍼에 마지막 암호화된 바이트가 포함되는지 여부



  
**반환**: 암호 해독된 콘텐츠의 실제 크기(바이트)
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
이 [ProtectionHandler](class_mip_protectionhandler.md)로 암호화되는 경우 콘텐츠의 크기(바이트)를 계산합니다.

매개 변수:  
* **contentLength**: 보호되지 않은 콘텐츠의 크기(바이트)



  
**반환**: 보호된 콘텐츠의 크기(바이트)
  
### <a name="getblocksize"></a>GetBlockSize
이 [ProtectionHandler](class_mip_protectionhandler.md)에서 사용하는 암호화 모드의 블록 크기(바이트)를 가져옵니다.

  
**반환**: 블록 크기(바이트)
  
### <a name="accesscheck"></a>AccessCheck
보호 처리기가 지정된 액세스 권한을 사용자에게 부여하는지 확인합니다.

매개 변수:  
* **right**: 확인할 권한



  
**반환**: 보호 처리기가 지정된 액세스 권한을 사용자에게 부여하는지 여부
  
### <a name="getissuedto"></a>GetIssuedTo
보호 처리기와 연결된 사용자를 가져옵니다.

  
**반환**: 보호 처리기와 연결된 사용자
  
### <a name="getowner"></a>GetOwner
콘텐츠 소유자의 메일 주소를 가져옵니다.

  
**반환**: 콘텐츠 소유자의 메일 주소
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
현재 사용자가 콘텐츠 소유자인지 여부를 가져옵니다.

  
**반환**: 현재 사용자가 콘텐츠 소유자인지 여부
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
보호 세부 정보를 가져옵니다.

  
**반환**: 보호 세부 정보
  
### <a name="getcontentid"></a>GetContentId
문서/콘텐츠에 대한 고유 식별자를 가져옵니다.

  
**반환**: 고유한 콘텐츠 식별자
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
보호 처리기에서 이전 버전과의 호환성을 위해 사용 중단된 암호화 알고리즘(ECB)을 사용하는지 여부를 가져옵니다.

  
**반환**: 보호 처리기에서 사용 중단된 암호화 알고리즘을 사용하는지 여부
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
보호 처리기가 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부를 가져옵니다.

  
**반환**: 보호 처리기가 사용자에게 ‘감사된 추출’ 권한을 부여하는지 여부
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
[ProtectionHandler](class_mip_protectionhandler.md)를 PL(게시 라이선스)로 직렬화합니다.

  
**반환**: 직렬화된 게시 라이선스