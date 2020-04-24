# cc 5주차

---

## out-in, in-out 방식

### out-in
* main > service > domain 순으로 개발

### in-out
* domain > service > main 순으로 개발
* 도메인에 대한 지식이 충분 할때 유리
* tdd로 개발하기 쉽다

### 어떻게 진행 해야 할까?
* out-in이 좋을 수도, in-out이 좋을수도 있다
* 어느 한쪽이 정답이라고 할 수 없음
* out-in, in-out 방식을 섞어서 개발을 진행 하는것이 좋다

> tdd를 충분히 연습 후에 책임 주도 설계 연습을 진행해 보자

### 책임 주도 설계의 interface
* interface를 통해 DI를 활용 할 수 있다
    * service layer는 인터페이스가 필요해지는 순간에 interface로 구현
    * dao, repository를 인터페이스로
* 패키지 간의 dependency는 단방향 관계로 설계 해야 한다
    * 단방향으로 개발할 경우, 각각의 패키지를 별도로 jar로 배포 가능 하다
    * cycle이 걸려 있을때는 MSA 아키텍처 적용이 어려워 진다
    > sonarqube를 이용하여 cycle이 걸린 패키지를 찾을 수 있다

## MVC의 비즈니스 로직
* service에 비즈니스 로직이 있으면 테스트 하기 어려워진다
* service layer에 있는 비즈니스 로직을 도메인으로 이동시켜 보자
* Mock을 이용하면 서비스를 테스트 할 수 있다
* life cycle을 공유하는 도메인끼리 묶어보자

### db 스키마와 domain의 갭
* DB와 domain이 1:1 매핑이 안되는것이 올바르게 개발하고 있는 것이다
* model mapper, assembler, dto등을 이용해 어느 layer에서 데이터와 domain을 매핑시켜줄지 고민해 보자

