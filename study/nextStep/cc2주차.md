* 생성자를 만들 때는 parm이 적은 쪽에서 많은쪽을 호출한다.
* given when then 을 엔터로 구분해 준다.
* 도메인에 default 접근제한자를 이용하여 자신의 기능을 표현한다.
* 테스트 코드를 하나 작성후에 PC를 계속해서 만족할때까지 리팩토링 한다.
* 상태를 가지는 일급컬렉션을 생성 한다
	이것을 테스트 할때는 객체 생성자를 이용해 비교 하여 같은지를 테스트 한다.
	ex) assertThat(new Postion(3)).isEqual(new Postion(3));
* DTO는 get/setter를 사용 가능
* VO는 get/setter를 만들지 않는다 > immutable
* VO의 접근제어자를 default로 선언하여 외부 aggregate에서 참조 불가능으로 만든다
* 일급컬렉션 : 객체를 primitive타입과 동일하다고 생각하고 값을 객체로 포장한것
* Collections.unmodifiableList(cars) 와 같이 collection을 변경 불가능하게 선언하고 VO의 생성자에서 초기화 한다.