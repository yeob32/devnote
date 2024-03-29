# Kafka

### 카프카 특징
- 영속성
    - 메세지를 하드디스크에 저장
    - 데이터 유실 방지
- 확장성 및 고가용성
    - 카프카는 클러스터로 구성되어 있음
    - Fault-tolerant 한 고가용성 서비스 제공 및 분산 처리를 통해 빠른 데이터 처리 가능
    - 서버를 수평적으로 늘려 안정성 및 성능을 향상시키는 Scale-out 가능
- 고성능
    - Pub/Sub 모델의 단점 존재
        - 중간에 카프카라는 메시징 시스템에 보내고 컨슈머들이 받는다는 구조적 단점으로 속도가 느리다는 점
        - 직접 연결해서 전달하는 과정이 아니다보니 컨슈머가 제대로 데이터를 전달 받았는지 확인하는 방법이 어렵다는 점
    - 그래서 카프카는 내부적으로 분산처리, 배치 처리 등 다양한 기법을 사용하여 대규모, 고성능을 유지하는 메시징 시스템이 가능하도록 함

### 카프카 사용 이유
- 병렬처에 의한 처리율 향상
- 데이터 유실 방지
- 클러스터링에 의한 고가용성

## Why is Kafka so fast

### Sequential IO
- 디스크가 순차적으로 저장되어 있으므로 디스크 I/O 가 줄어들어 성능이 빨라짐
- 디스크의 읽기 속도는 실제 데이터를 읽는 속도가 아니라, 데이타의 위치를 찾는 시간(Seek Time) 에 의해 디스크 읽기 속도가 지연됨
- Kafka 는 데이터를 순차적으로 저장하기에, Seek Time 을 최소화 할 수 있습니다.
- 
### Zero-copy
- 일반적인 애플리케이션은 데이터를 메모리에 올린 후 전송
- Kafka 는 애플리케이션에 데이터를 올리는 대신, 디스크에서 데이터를 읽음과 동시에 네트워크에 전송
- 구현 방법
  - 커널 명령어 중 sendfile() 함수를 이용
    - 애플리케이션이 사용하는 메모리에 데이터를 올리지 않고 즉시 네트워크에 데이터 전송
### Page Cache
- 한번 읽은 파일의 내용을 페이지 캐시라는 영역에 저장해두고, 동일한 접근이 있을 시 페이지 캐시에서 읽음으로써 상대적으로 속도가 느린 디스크로의 접근을 최소화
- OS 는 물리적 메모리에서 카프카 애플리케이션이 사용하는 부분을 제외한 잔여 메모리를 이용해 페이지 캐시로 이용
  - 때문에 하나의 시스템에 카프카를 제외한 다른 애플리케이션을 구동하는 것을 권장하지 않음
### Protocol
  - 부하를 최소화하고 메세지 전송 외 불필요한 블로킹/핸드쉐이크 등의 요소를 최대한으로 배제하여 최대한의 처리율을 보장
  - 특징
    - 컨슈머당 단일 TCP 연결 유지
      - 하나의 메세지에 하나의 TCP 연결이 아닌, 컨슈머에 단일 TCP 연결을 사용하여 전송
      - 이를 통해 TCP handshaking 등의 부하도 없앨 수 있음
    - Binary
      - Serialize/Deserialize 과정 없이 그대로의 데이터를 전송하여 부하 최소화
    - Non-blocking I/O
      - 응답을 대기하지 않고서도 계속해서 메세지를 송신 할 수 있음
### Data Batch & Compression
  - 카프카는 데이터 배치와 압축을 지원하여 네트워킹 횟수를 대폭 줄여 성능을 향상 시킴