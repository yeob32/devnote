#### @ManyToOne
- optional > default true
    - true 일 경우 해당 객체에 null 삽입 가능
    - @JoinColumn(nullable = true) 같음
    - true 일 경우 `left join`, false 일 경우 `inner join`

#### @OneToMany
- mappedBy 연관 관계 주인 설정
    - 연관 관계의 주인은 FK 가 있는 곳으로 정한다.
    - 주인이 아닌 쪽은 읽기만 가능하다.

#### @DynamicUpdate
- 장점
  - 
- 단점
    - 하이버네이트는 애플리케이션 구동 시 엔티티 스캔 후 모든 필드에 대한 업데이트 쿼리를 캐싱하고 사용하는데
      해당 애노테이션 사용 시 업데이트 할 컬럼으로 구성된 새로운 쿼리를 생성을 위해 캐싱 된 쿼리를 사용하지 못하고
      업데이트 시 마다 새 동적쿼리 생성

- 결론
    - @DynamicUpdate는 업데이트 시 무의미한 필드들이 많아 오버헤드가 많이 발생하는 경우 사용한다.
    - JPA @Version 어노테이션으로 명시 해놓은 버전 필드가 있는 엔티티의 Optimistic Lock(낙관적 락)을 사용하고자 할 때는 @DynamicUpdate를 사용하는 것이 좋다.
      (@Version 필드만 업데이트 해야 하는 경우가 분명하기 때문에)