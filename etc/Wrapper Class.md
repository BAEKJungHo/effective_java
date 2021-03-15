# Wrapper Class

InstrumentedSet 은 HashSet 의 모든 기능을 정의한 Set 인터페이스를 활용해서 설계된 클래스이며, 구체적으로는 Set 인터페이스를 구현했고, 임의의 Set 에 계측 기능을 덧씌워 새로운 Set 으로
만드는 것이 이 클래스의 핵심이다. 상속 방식은 구체 클래스 각각을 따로 확장해야 하며, 지원하고 싶은 상위 클래스의 생성자 각각에 대응하는 생성자를 별도로 정의해줘야 한다.

InstrumentedSet 같은 클래스를 `래퍼 클래스(Wrapper Class)`라 하며, 다른 Set 에 계측 기능을 덧씌운다는 뜻에서 `데코레이터 패턴(Decorator pattern)`이라고 한다. 컴포지션과 전달의 조합은 넓은 의미로
위임(delegation)이라 한다. 단, 엄밀히 따지면 래퍼 객체가 내부 객체에 자기 자신의 참조를 넘기는 경우만 위임에 해당한다.

래퍼 클래스는 단점이 거의 없다. 한 가지, 래퍼 클래스가 `콜백(callback) 프레임워크`와는 어울리지 않는다. 내부 객체는 자신을 감싸고 있는 래퍼의 존재를 모르니 래퍼 대신 자기 자신(this)의 참조를 넘기고,
콜백 때는 래퍼가 아닌 내부 객체를 호출하게 된다. 이를 `SELF 문제`라고 한다.

> https://stackoverflow.com/questions/28254116/wrapper-classes-are-not-suited-for-callback-frameworks