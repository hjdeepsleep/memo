# cc 3주차

---

# TDD 쉽게 진행하기
* 구현 중간 부분을 자르는 연습을 한다 (기능을 작은단위로 분리)
* 구현 중간 부분을 자른다는것은 구현에 필요한 메서드를 찾는 과정
* 기능 안쪽의 작은 단위부터 시작 하면 TDD가 쉬워짐
* input,output이 있는 메서드가 test하기가 쉽다


# 레거시 코드 리팩토링
1. 메서드를 분리 한다.
1. indent를 1로 줄인다.
    * indent를 줄이기 힘들다면 그 class의 역할을 다시 생각해본다.
1. 이름을 rename한다.
1. 원시값과 문자열을 포장한다.
1. 일급 콜렉션을 사용한다.(멤버변수가 1개)
1. 메서드의 인자는 반드시 4개 미만 이어야 한다.(생성자 제외)
    * 인자가 3개 이상일때는 관련인자 끼리 묶어서 새로운 class를 생성해 본다.

# 상속(is-a)과 조합(has-a) 관계
1. is-a관게
    * 아래와 같이 구현하면 ArrayList<>()의 모든 api(메서드)를 이용한다는 의미 이다(우리는 일부만 필요하다.)
    ```
    public class Lottos extends ArrayList<Lotto> {

    }   
    ```
1. 상속(is-a)은 재사용성에서 장점이 있지만 유연성이 떨어지는 단점이 있다.
    * 부모에 변경이 발생하면 모든 자식에게 영향이 간다.
    * 변화에 빠르게 대응하는것이 중요함 -> 유연성의 장점을 살리는것이 좋다.

# 추가 리팩토링
1. 생성자 대싱 정적 팩토리 메서드 패턴을 이용한다.
    * 2개 이상의 생성자를 구현한다면, 정적 팩토리 메서드 패턴을 고민해봐라
    * 이름을 가짐으로써 의도를 표현 할 수 있다.
    ```
    static LottoNumber of(String value){}
    static LottoNumber of(int value){}
    static Lotto ofComma(String value){} // 컴마로 구문하는 팩토리
    static Lotto of(Integer... numbers){} //다양한 방법을 제시할수 있다
    ```
1. 객체는 immutable 하게 구현한다.
    * set 메서드를 제공하지 않는다
    * 클래스를 확장할 수 없도록 한다(public final class)
    * 모든 필드를 fincl로 선언한다.
    * 모든 필드를 private로 선언한다.
1. immutable object이 성능이 떨어지는건 아닐까?
    * instance가 너무 많이 생성되어 성능이 떨어질 수 있다.
        * 캐싱을 적용해 instance 생성을 최소화 할 수 있는 방법을 생각해 본다. (Map을 이용해 본다(key-value))
        * static 초기화 블럭을 이용해 테이터를 초기화 한다.
        ```
        private static final Map<Integer, LottoNumber> num = new HashMap<>;

        static{
            //값 범위 초기화
        }
        ```

# interface

## 객체지향 생활 체조 원칙
* 규칙4: 한줄에 점을 하나만 찍는다.
    * Clean Code 가이드의 디미터 법치을 지키는 것을 의미한다.
* 규칙6: 모든 엔티티를 작게 유지한다.
* 규칙7: 3개 이상의 인스턴스 변수를 가진 클래스를 쓰지 않는다.
* 규칙9: getter/setter/property를 쓰지 않는다.

# 함수형 프로그래밍
* 


