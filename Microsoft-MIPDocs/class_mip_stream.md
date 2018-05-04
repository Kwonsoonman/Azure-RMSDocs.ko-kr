# <a name="class-mipstream"></a>클래스 mip::Stream 
MIP SDK와 스트림 기반 콘텐츠 간에 인터페이스를 정의하는 클래스입니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public int64_t Read | 스트림에서 버퍼로 읽습니다.
public int64_t Write | 버퍼에서 스트림으로 씁니다.
public bool Flush | 스트림을 플러시합니다.
public void Seek | 스트림 내에서 특정 위치를 검색합니다.
public bool CanRead | 스트림을 읽을 수 있는지 확인합니다.
public bool CanWrite | 스트림이 쓰기 가능한지 확인합니다.
public uint64_t Position | 스트림 내의 현재 위치를 가져옵니다.
public uint64_t Size | 스트림 내의 콘텐츠 크기를 가져옵니다.
public void Size | 스트림 크기를 설정합니다.
public std::shared_ptr< Stream > Clone | 스트림을 복제합니다.
## <a name="members"></a>멤버
### <a name="read"></a>읽기
스트림에서 버퍼로 읽습니다.
#### <a name="parameters"></a>매개 변수
* buffer 버퍼에 대한 포인터 
* bufferLength 버퍼 크기. 
#### <a name="returns"></a>Returns
실제로 읽은 바이트 수.
### <a name="write"></a>쓰기
버퍼에서 스트림으로 씁니다.
#### <a name="parameters"></a>매개 변수
* buffer 버퍼에 대한 포인터 
* bufferLength 버퍼 크기. 
#### <a name="returns"></a>Returns
실제로 읽은 바이트 수.
### <a name="flush"></a>플러시
스트림을 플러시합니다.
#### <a name="returns"></a>Returns
성공하면 true, 그렇지 않으면 false.
### <a name="seek"></a>Seek
스트림 내에서 특정 위치를 검색합니다.
#### <a name="parameters"></a>매개 변수
* 스트림에서 검색할 위치입니다.
### <a name="canread"></a>CanRead
스트림을 읽을 수 있는지 확인합니다.
#### <a name="returns"></a>Returns
읽을 수 있는 경우 true, 그렇지 않으면 false.
### <a name="canwrite"></a>CanWrite
스트림이 쓰기 가능한지 확인합니다.
#### <a name="returns"></a>Returns
쓰기 가능한 경우 true, 그렇지 않으면 false.
### <a name="position"></a>위치
스트림 내의 현재 위치를 가져옵니다.
#### <a name="returns"></a>Returns
스트림 내의 위치.
### <a name="size"></a>Size
스트림 내의 콘텐츠 크기를 가져옵니다.
#### <a name="returns"></a>Returns
스트림 크기.
### <a name="size"></a>Size
스트림 크기를 설정합니다.
#### <a name="parameters"></a>매개 변수
* 스트림 크기입니다.
### <a name="stream"></a>스트림
스트림을 복제합니다.
#### <a name="returns"></a>Returns
새 스트림.