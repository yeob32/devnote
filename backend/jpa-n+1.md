# JPA N+1

## 문제 발생

### @OneToMany 관계 매핑
- EAGER 로 설정 했을 때 orderRepository.findAll() 호출 시 N+1 쿼리 발생
- LAZY 로 설정 했을 때에도 List 의 프록시 객체 조회 수행 시 N+1 쿼리 발생

## 해결 방안
- Fetch Join
```
  select order
  from Order order
    inner join fetch order.member as member # @ManyToOne
    left join fetch order.orderItems as orderItem; # @OneToMany
```
- @EntityGraph(attributePaths = "orderItems")
    - outer join

### 위 해결 방안 모두 카테시안 곱 발생
- 위의 해결 방안 모두 카테시간 곱이 발생한다.

#### 해결 방안
- 자료 구조 Set 으로 변경
    - 순서 보장 시 LinkedHashSet
- distinct 쿼리

### 페이징 처리
- 실제 적용된 쿼리를 보면 limit, offset 조건이 없음
- 아래의 경고 문구 처럼 일단 모든 데이터 조회 후 메모리에 담은 후 애플리케이션 레벨에서 요청 페이지만큼의 데이터 반환
```
o.h.h.internal.ast.QueryTranslatorImpl   : HHH000104: firstResult/maxResults specified with collection fetch; applying in memory!
```
