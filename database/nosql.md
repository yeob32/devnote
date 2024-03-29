# NoSQL

## NoSQL

- Not Only SQL
- 특징
    - 수평 확장 가능한 분산 시스템
    - Schema-less
    - 완화된 ACID
        - 분산 트랜잭션 지원함

### RDBMS vs NoSQL

| RDBMS   | 	RDBMS                    | 	NoSQL                         |
|---------|---------------------------|--------------------------------|
| 적합한 사용례 | 	데이터 정합성이 보장되어야 하는 은행 시스템 | 	낮은 지연 시간, 가용성이 중요한 SNS 시스템    |
| 데이터 모델  | 	정규화와 참조 무결성이 보장된 스키마     | 	스키마가 없는 자유로운 데이터 모델           |
| 트랜젝션    | 	강력한 ACID 지원              | 	완화된 ACID(Base)                |
| 확장      | 	하드웨어 강화(Scale up)        | 	수평 확장이 가능한 분산 아키텍처(Scale out) |
| API     | 	SQL 쿼리                   | 	객체 기반 API 제공                  |