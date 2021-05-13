# design-pattern

### 빌더 패턴
    - 장점
        - 불변 객체를 만들 수 있음
        - 어떤 필드에 값을 넣고 있는지 알 수 있어서 실수를 면할 수 있음
    - 단점
        - 값을 안줬을 경우 null이 될 수 있어서 확인이 필요
        - Lombok 빌더를 사용한 경우 IDE에 있는 코드 변환을 사용했을때 같이 변환이 되지 않음
    - 구현
        - 해당 class에 static class로 Builder라는 class를 만들고 builder에 적용할 class에 필요한 필드 값 method를 지정하고 리턴형으로 this를 넘겨서 체인형태가 될 수 있게 한다.
        - 그리고 마지막 build 메소드를 만들어서 원하는 객체를 만들고 builder 객체를 넘겨서 값을 맵핑 해준다.
### 템플릿 메소드 패턴
    - 보통 abstract class(슈퍼클래스)에서 method를 이용해 기본적인 기능을 구현해두고, 하위 클래스에서 디테일 기능을 구현하면서 기능을 확장시킬 때 사용
        - 광고에서 사용한 곳은 delivery status의 값을 구하는 로직
            - Delivery status에 대해서 EnumSet을 구해오는 부분은 abstract로 적용해두고, 해당 delivery status를 이용해서 최종적으로 적용할 부분은 슈퍼클래스에 로직으로 처리
    - Spring Security에 AbstractAuthenticationProcessFilter에서 사용 중
### 컴포지션 패턴
    - 특정 인터페이스를 상속 받은 구현체들을 list로 갖고 있고 구현체들을 이용해 어떤 작업을 할 때 사용
    - Spring Security에서는 FilterChainProxy가 SecurityFilterChain을 list로 갖고 있으면서 matching이 되는 securityFilterChain에 적용되어 있는 filter를 가져와 준다.
    - 그 외에도 적용해본 부분은 validation 부분 validate 인터페이스를 만들고 해당 부분에 대해서 서로 다르게 검증해야 되는 부분을 구현하고 구현되어 있는 모든 validation이 통과되었다면 검증완료로 처리
### 스트레티지 패턴
    - 어떤 기능에 대해 인터페이스를 구현해 놓고 사용하는 쪽에서는 인터페이스만 알게하여 캡슐화 방식을 적용
    - 실제 인터페이스를 맞춰두었기에 필요시에 구현체를 바꿔서 기능 부분을 쉽게 변경할 수 있다.
    - 실제 적용 부분
        - Line live에서는 main stream, sub stream이 존재하는데 두 개의 스트림을 만드는 플로우는 동일하나 처리되는 부분은 달라서 스트레티지 패턴을 적용
            - Start, suspend, end 등 stream을 하기 위한 flow는 같지만 구현 부분이 달랐음
            - 예를들면 main에 stop은 방송 종료지만 sub의 경우 sub만 종료해야 하고 main은 남아 있어야 한다.
            - start할때 play url의 정보도 다르게 셋팅해줘야 한다.
### 데코레이터 패턴
    - 어떤 작업을 처리하는데 있어서 추가적인 작업을 진행해야 할때 사용하는 패턴
    - abstract로 method를 생성하여 하위에서 구현하게 하는 방식
    - Delegate 필드를 갖고 있고 해당 메소드를 처리할 때 delegate 작업 전 후로 추가작업을 설정하여 데코레이터를 할 수 있음
    - Spring webflux에 ServerWebExchange에 대해서는 ServerWebExchangeDecorator를 이용해서 추가기능을 심어서 사용
    - 하나씩 추가할때 마다 바깥쪽 겹이 쌓이고 실행은 안쪽에서부터 바깥쪽으로 겹을 벗겨 내듯이 실행된다.

