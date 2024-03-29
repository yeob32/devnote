# Architecture Pattern

### API-Gateway Pattern

- 모든 클라이언트 요청의 단일점 역할
- 마이크로서비스 엑세스를 단순화하여 클라이언트와의 커뮤니케이션을 도와줌

### Service Discovery Pattern

- 마이크로서비스의 복잡한 설계를 쉽게 탐색하도록 한다.
- 서비스 간의 원활한 커뮤니케이션을 보장하고, 수동 컨피규레이션의 필요성을 줄여준다.

### Circuit Breaker Pattern

- 서비스 간의 장애 전파를 차단하여 전체 시스템의 붕괴를 막아준다.

### Load Balancing Pattern

- 트래픽이 발생하면 서비스 간 골고루 트래픽을 분산해준다.
- 특정 서비스에만 대부분의 트래픽을 감당하면 성능 저하 또는 운영 중단이 발생할 수 있음.

### Bulkhead Pattern

- 서비스와 리소스를 분리해서 특정 서비스에서 장애가 발생해도 전체 시스템이 다운되지 않도록 한다.
- 이 패턴 구현의 실제 예로는 AWS Lambda 함수 리소스 할당 및 데이터베이스의 커넥션 풀링(connection pooling)이 있다.

### CQRS Pattern

- Write 와 Read 작업을 구분하여 마이크로서비스의 성능과 확장성을 증가시켜준다.

### **Event-Driven Architecture Pattern**

- 이벤트를 발행하고 소비하는 형태의 서비스 구성으로 서비스 간의 느슨한 결합을 도와주고, 의존을 줄여 유연성 및 확장성 증가시켜준다.

### Saga Pattern

- 분산 트랜잭션을 처리할 수 있는 안정적인 솔루션을 제공하여 서비스의 자율성을 유지하면서 데이터의 일관성을 보장해준다.

### BFF (Backend For Front) Pattern

- 각 프론트엔드 당 전용 백엔드 서비스를 생성하여 각 플랫폼에 맞는 최적의 성능과 유저 경험을 보장해준다.

### Retry Pattern

- 장애의 완화 또는 극복을 위해 실패한 작업을 재시도 하는 패턴
- 재시도 횟수, 재시도 사이의 backoff 를 설정한다.

### Sidecar Pattern

- 자율성을 해치지 않고 마이크로서비스에 기능을 추가할 수 있는 패턴
- 서비스에 추가 구성 요소를 연결해서 핵심 서비스를 변경하지 않고 모듈식 기능을 제공한다.

### Strangler Pattern

- 모놀리식 아키텍처를 점차적으로 마이크로서비스로 리스크 없이 전환할 수 있는 패턴