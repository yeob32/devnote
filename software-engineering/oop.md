# OOP

## 객체지향

### 객체
- 필드, 메서드로 이루어진 논리적인 구현체

### 특징
- 캡슐화
- 추상화
- 상속
- 다형성

## SOLID

- 단일 책임 원칙 (Single Responsibility, SRP)
  - 모든 클래스는 하나의 책임만 가진다.
  - 그 책임을 완전히 캡슐화 한다.
- 개방 폐쇄 원칙 (Open Close, OCP)
  - 변경에는 닫혀있고, 확장에는 열려있다.
  - 기존의 코드는 변경하지 않고, 기능을 추가한다. (DIP 밀접)
- 리스코프 치환 원칙 (Liskov Substitution, LSP)
  - 자식 클래스는 언제나 부모를 대체할 수 있다.
  - 다형성의 원리
- 인터페이스 분리 원칙 (Interface Segregation, ISP)
  - 목적과 용도에 맞게 적합한 인터페이스를 제공하는 것
  - 인터페이스의 단일 책임원칙이랄까,,
- 의존 역전 원칙 (Dependency Inversion, DIP)
  - 상위 수준에서 하위 수준의 구현을 의존해서는 안된다.
  - 인터페이스로 연결해야 확장이 유연함 → OCP 지켜짐

> 아마 모든 핵심은 추상화에서 시작되나 보다.
