
## Java
### Generic
- 강력한 타입체크, 캐스팅 안해도됨, wildcard
- 컬렉션에서 많이 보이는 형태

### 박싱, 언박싱
- Primitive Class <-> Wrapper Class
- 묵시적
    - ex) Integer n = 0; --> int temp = n;
- 명시적
    - ex) 캐스팅

### Checked Exception, Unchecked Exception
- Checked Exception
    - 명시적 예외 처리
    - 컴파일 단계에서 체크 가능
    - `RuntimeException` 제외 `Exception` 의 하위 클래스
- Unchecked Exception
    - 명시적 예외 처리 x
    - 런타임 단계에서 확인
    - `RuntimeException` 의 하위 클래스

### Immutable
- 멀티스레드 환경에서 동기화 처리 없이 객체 공유 가능 (Thread-Safe)
- 객체가 가지는 값 마다 새로 할당 해야되기 때문에 성능 저하 발생
    - Heap 영역에서 변경이 불가능한 것이지 재할당이 불가능한 것은 아니다.
- String, Integer, Boolean, Float, Long

### final
- 상속, 오버라이드, 재할당 불가

### 동기화
- 하나의 공유자원을 하나의 스레드만 사용할 수 있도록 제어
    - synchronized 키워드 사용하여 레이스 컨디션 통제
    - List -> Vector, Map -> HashTable => 성능 별로
    - ~ Java 1.7 concurrent 패키지 제공

### ThreadLocal
- 쓰레드 사이에 간섭이 없어야하는 데이터에 사용
    - ex) 사용자 인증, 세션정보, 트랜잭션 컨텍스트
- 사용 후 반드시 해당 데이터를 삭제해줘야한다.

### 동기, 비동기
- 특정 작업의 결과를 기다릴지 말지

### 블로킹, 논블로킹
- 제어권이 해당 스레드에 없어 특정 작업이 끝나길 기다려야한다.

### 직렬화
- 네트워크 통신 시 스트림을 통해 객체를 byte 코드로 변환 필요

### 해시 충돌
- 서로 다른 키 값이 해쉬 함수를 통해 같은 해쉬 값이 나오는 상황
- 해결 방법
    - Chaining : value 를 연결리스트로 변환
        - Java : 연결리스트 -> 트리
    - Open Addressing : 비어있는 해시를 찾아서 저장
- HashMap
    - 동기화 필요 시 HashTable(성능 별로), ConcurrentHashMap

### Statement, PreparedStatement
- Statement
    - 단일로 사용 될 때 쓰면 좋다.
    - 쿼리 인자 부여 불가능
    - 매번 컴파일 수행
- PreparedStatement
    - 컴파일 수행 (캐싱)
    - 쿼리 인자 부여 가능

### 동일성, 동등성
- 동일성
    - 완전히 동일한(identical) 오브젝트
    - == 비교
- 동등성
    - 동일한 정보를 담고 있는(equivalent) 오브젝트
    - equals() 메소드 비교
        - equals() 메소드 따로 구현 하지 않았다면, 최상위 클래스인 Object 클래스의 equals() 사용
            - Object 의 equals() 메소드는 동일성 비교