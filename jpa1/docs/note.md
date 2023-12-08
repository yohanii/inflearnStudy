- Cascade
  - persist를 따로 해주지 않아도, 상위에 cascade가 걸려있으면 자동으로 persist를 해줌.
  - @OneToX에 붙여줘야한다.
  - 대신 지워질때, 같이 지워짐.
  - 그래서, 여러 곳에서 쓰이는 경우가 아니고, 해당 클래스에서만 상대 클래스를 사용하는 경우만 사용할 것.
  

- @NoArgsConstructor(access = AccessLevel.PROTECTED)
  - 함부로 생성자를 통해, 객체를 생성하지 못하게 함.

  
- 모델 패턴
  - 도메인 모델 패턴
    - 엔티티에 비즈니스 로직을 두는 패턴
    - 객체 지향의 특성을 적극 활용
    - 이 강의에서 하는 방식이다.
    - 단위 테스트를 작성하기에 유리하다.
  - 트랜잭션 스크립트 패턴
    - 서비스 계층에 비즈니스 로직을 두는 패턴
    - 원래 하던 방식
  - 한 프로젝트 내에서도 여러 패턴을 사용하기 때문에, 그때그때 더 문맥에 맞는 패턴을 사용하면 된다고 한다.


- JPA에서 동적쿼리 작성하는 법
  - jpql String 조합
    - 알아보기 힘들고, 유지보수 힘들다. 코드도 길어짐.
  - criteria 쓰기
    - 마찬가지로 알아보기 힘들고, 유지보수 힘듬.
    - String 조합하는 것보단 조금 나음.
  - Querydsl 사용
    - 실무에서 사용
    - 훨씬 편함.


- Thymeleaf
  - include style
    - ex) `th:replace="fragments/bodyHeader :: bodyHeader"`
    - 자주 쓰는 html을 저장해두고 사용할 수 있음
    - 중복 제거 가능
  - object, field
    - object로 객체 넣고, field로 각 field 매핑
    - ex) th:object="${memberForm}"
    - th:field="*{name}"


- Error message 보여주기
  - 원하는 객체에 @NotEmpty @NotBlank 등 입력 + message 추가
  - Controller에서 해당 객체에 @Valid 붙이기
  - @BindingResult로 error 발생 시 원하는 html로 연결
  - html에서 `th:if"${#fields.hasErrors('name')}" th:errors="*{name}"`으로 에러메세지 보여주기


- 변경 감지와 병합
  - 준영속 객체
    - JPA가 식별할 id를 가지고 있지만, JPA가 관리하지 않는 엔티티
    - ex) Book 수정할 때, BookForm에서 새로운 Book을 만드는데 이 새로운 Book이 준영속 엔티티
  - 준영속 엔티티 수정 2가지 방법
    - 변경 감지 기능 사용 (더 나은 방법)
      - JPA가 관리하는 객체를 가져와서 수정하기
    - 병합(merge) 사용
      - 위랑 똑같은 방법인데, JPA가 알아서 찾아서 바꿔줌
      - 차이점 : 변경감지는 원하는 속성만 바꾸고, 병합은 모든 속성을 바꾸기 때문에, 병합은 위험하다.
      - ex) em.merge(item)
    - merge 대신 변경 감지 기능 쓰자!!!