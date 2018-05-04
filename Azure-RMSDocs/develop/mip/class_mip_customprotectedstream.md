# <a name="class-mipcustomprotectedstream"></a>클래스 mip::CustomProtectedStream 
스트림을 래핑하여 읽기 및 쓰기에 대한 투명한 암호화 및 암호 해독을 제공합니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public std::shared_future< int64_t > ReadAsync | 스트림에서 데이터 블록을 비동기적으로 읽습니다.
public std::shared_future< int64_t > WriteAsync | 데이터 블록을 스트림에 비동기적으로 씁니다.
public std::future< bool > FlushAsync | 출력 스트림 버퍼를 비동기적으로 플러시합니다.
public int64_t Read | 스트림에서 데이터 블록을 동기적으로 읽습니다.
public inline virtual std::vector< uint8_t > Read | 스트림에서 데이터 블록을 동기적으로 읽습니다.
public int64_t Write | 데이터 블록을 스트림에 동기적으로 씁니다.
public bool Flush | 출력 스트림 버퍼를 동기적으로 플러시합니다.
public SharedStream Clone | 스트림을 복제합니다.
public void Seek | 스트림 내의 위치를 검색합니다.
public bool CanRead | 스트림을 읽을 수 있는지 여부를 가져옵니다.
public bool CanWrite | 스트림을 쓸 수 있는지 여부를 가져옵니다.
public uint64_t Position | 시작부터 스트림의 현재 위치를 가져옵니다(바이트).
public uint64_t Size | 스트림의 크기(바이트)를 가져옵니다.
public void Size | 스트림의 크기(바이트)를 설정합니다.
## <a name="members"></a>멤버
### <a name="readasync"></a>ReadAsync
스트림에서 데이터 블록을 비동기적으로 읽습니다.
#### <a name="parameters"></a>매개 변수
* pbBuffer 스트림을 읽어야 하는 버퍼 
* cbBuffer 버퍼 크기 
* cbOffset 읽기가 시작되어야 하는 입력 스트림의 시작부터 오프셋 
* launchType 비동기 시작 유형
#### <a name="returns"></a>Returns
실제 읽은 바이트 수를 포함하는 비동기 미래, std::future에서 결과가 검색될 때까지 버퍼가 있는지 확인
### <a name="writeasync"></a>WriteAsync
데이터 블록을 스트림에 비동기적으로 씁니다.
#### <a name="parameters"></a>매개 변수
* cpbBuffer 쓰려는 데이터의 버퍼 
* cbBuffer 버퍼 크기 
* cbOffset 쓰기가 시작되어야 하는 출력 스트림의 시작부터 오프셋 
* launchType 비동기 시작 유형
#### <a name="returns"></a>Returns
실제 쓴 바이트 수를 포함하는 비동기 미래, std::future에서 결과가 검색될 때까지 버퍼가 있는지 확인
### <a name="flushasync"></a>FlushAsync
출력 스트림 버퍼를 비동기적으로 플러시합니다.
#### <a name="parameters"></a>매개 변수
* launchType 비동기 시작 유형
#### <a name="returns"></a>Returns
플러시가 성공했는지 여부를 포함하는 비동기 미래
### <a name="read"></a>읽기
스트림에서 데이터 블록을 동기적으로 읽습니다.
#### <a name="parameters"></a>매개 변수
* pbBuffer 스트림을 읽어야 하는 버퍼 
* cbBuffer 버퍼 크기
#### <a name="returns"></a>Returns
실제 읽은 바이트 수
### <a name="read"></a>읽기
스트림에서 데이터 블록을 동기적으로 읽습니다.
#### <a name="parameters"></a>매개 변수
* u64size 읽을 데이터의 크기(바이트)
#### <a name="returns"></a>Returns
실제 읽기 데이터의 벡터
### <a name="write"></a>쓰기
데이터 블록을 스트림에 동기적으로 씁니다.
#### <a name="parameters"></a>매개 변수
* cpbBuffer 쓰려는 데이터의 버퍼 
* cbBuffer 버퍼 크기
#### <a name="returns"></a>Returns
실제 쓴 바이트 수
### <a name="flush"></a>플러시
출력 스트림 버퍼를 동기적으로 플러시합니다.
#### <a name="returns"></a>Returns
플러시가 성공했는지 여부
### <a name="sharedstream"></a>SharedStream
스트림을 복제합니다.
#### <a name="returns"></a>Returns
복제된 스트림
### <a name="seek"></a>Seek
스트림 내의 위치를 검색합니다.
#### <a name="parameters"></a>매개 변수
* u64Position 스트림의 시작부터 바이트 오프셋
### <a name="canread"></a>CanRead
스트림을 읽을 수 있는지 여부를 가져옵니다.
#### <a name="returns"></a>Returns
스트림을 읽을 수 있는지 여부
### <a name="canwrite"></a>CanWrite
스트림을 쓸 수 있는지 여부를 가져옵니다.
#### <a name="returns"></a>Returns
스트림을 쓸 수 있는지 여부
### <a name="position"></a>위치
시작부터 스트림의 현재 위치를 가져옵니다(바이트).
#### <a name="returns"></a>Returns
시작부터 스트림의 현재 위치(바이트)
### <a name="size"></a>Size
스트림의 크기(바이트)를 가져옵니다.
#### <a name="returns"></a>Returns
스트림의 크기(바이트)
### <a name="size"></a>Size
스트림의 크기(바이트)를 설정합니다.
#### <a name="parameters"></a>매개 변수
* u64Value 스트림의 크기(바이트)