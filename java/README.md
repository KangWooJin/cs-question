# java

### 추상클래스와 인터페이스 차이
- https://yaboong.github.io/java/2018/09/25/interface-vs-abstract-in-java8/
  
  interface	Abstract class
  인스턴스화	불가능	불가능
  접근 제어자	변수 - Public static final         메소드 - public abstract 	가능
  메소드 구현	default로 가능	일반 메소드로 구현 가능
  사용되는 곳	여러 곳에 사용	security에 UsernamePasswordAuthentication
  상속	다중상속 허용	단일
  관련성은 없지만 인터페이스를 통일할 때	관련성이 높은 클래스 간에 코드를 공유할때
  상속을 통해 슈퍼클래스의 기능을 확장할 때 사용하는 가장 대표적인 방법.
  변하지 않는 기능은 슈퍼클래스에 만들어두고 자주 변경되며 확장할 기능은 서브클래스에서 만들도록 한다. 

### GC
- https://johngrib.github.io/wiki/jvm-memory/
- 공식
  - https://docs.oracle.com/en/java/javase/11/gctuning/introduction-garbage-collection-tuning.html#GUID-326EB4CF-8C8C-4267-8355-21AB04F0D304

### for, stream 차이
