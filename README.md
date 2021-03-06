# Swift-Coordinate

다형성에 대해 공부한 프로젝트이다.

앞으로의 요구사항이 추가될 때 코드는 어떤 식으로 변화하는가?

**변경사항을 줄일 수 있나?** 를 공부했다.

**로버트.C.마틴 - 클린코드**에서 객체와 자료구조 장을 보면 
책을 느끼며 둘의 차이는 이러했다.

**자료구조**는 **데이터(프로퍼티)를 공개**해둔다.
데이터에 대한 연산(메소드)는 별도의 객체로 분리한다.
데이터를 처리하는 객체는 자료구조의 타입이 많아지면 **스위치문**은 커지지만 **처리하는 연산이 하나의 객체**에 밀집되어있다.

**객체**는 **데이터를 비공개**하고, **연산을 공개**한다.
객체들간의 **약속(프로토콜,인터페이스)** 가 있고 그것을 객체 각각이 다른 방법으로 구현한다 **(다형메소드)**. 

모두 각각의 장단점이 있기에 상황에 따른 선택이 필요하다.

- #### 자료구조
 미래의 변화에서 **메소드(연산) 추가**가 우려될 때는 **자료구조**가 좋은 선택지일 수 있다. 
 
 **자료구조를 처리하는 메소드(switch)** 가 하나 추가될 뿐 기존 타입들에게 영향을 미치지 않는다.
 
 대신 자료구조의 타입이 추가되게 된다면? 
 
 아마 여태까지의 `switch`모두에 `case`가 추가되야 한다.
 
 OCP가 잘 지켜지지 않는다.


- #### 객체
 **객체는 타입의 추가에는 유연하다**.
 **타입이 추가되면** 그 타입에서 필요한 연산을 **인터페이스를 순응하는 형태로 다형메소드를 구현**하면된다. 기존 코드들의 변화는 없다.
 
 반면 많은 객체를 구현한 **인터페이스에 추가 요구사항이 생기게되면 (필요한 연산이 하나 추가되게 된다면)** 
 
 이전 객체들은 연산의 구현 전 까지는 자격을 가지지 못하게된다. (프로토콜,인터페이스를 순응하지 못하기 때문에)
 
 그런데 객체의 타입의 너무 많다면?
 
 아마 엄청난 수정이 발생할 것이다. (각각의 인터페이스를 순응하는 타입에게 모두 메소드를 구현해야 한다)

 타입의 추가와 인터페이스의 추가 어떤 것이 자주 일어나는 지에 따른 객체 설계가 필요할 것 같다.

객체로 구현하게되면 타입추가에 용이하다 - 특정 인터페이스에 의존하게 된다면
특정인터페이스의 조건을 만족하면 객체가 될 수 있었다.

---

- ### 느낀점 및 회고

좌표계산기에서 `[Point]`의  가지고 있다면 `Figure`(도형)의 조건을 만족하게되고,

그 결과적을 저 조건을 만족하는 객체들을 모두 유연하게 수용할 수 있었다.

`OOP`에서 다형성을 충분히 맛볼 수 있는 주제였다.

하지만 객체를 정말 잘 활용했는 지는 아직은 의문이 있다.

객체의 데이터를 자기 자신이 연산으로 사용해야 응집도가 높은 객체가 될텐데 아직 미흡한 것 같다.


## 좌표계산기 실행 영상

![ezgif com-video-to-gif](https://user-images.githubusercontent.com/39197978/61314630-05c5e100-a838-11e9-8fd4-34d578f1ae1a.gif)
