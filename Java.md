# 1. 자바(Java Programming Language)

  * 객체지향언어 : 객체지향 프로그래밍언어로써 상속, 캡슐화, 다형성이 잘 적용된 언어이다.
   
  * 자동 메모리 관리 : Garbage Collection이 자동으로 메모리를 관리해주기 때문에 프로그래머는 따로 메모리 관리를 할 필요가 없다. (프로그래밍에 집중할 수 있는 환경을 제공받을 수 있다.)
     
  * 유용한 기능 지원 : 멀티쓰레드와 동적 로딩을 지원하며, 특히 필요한 시점에 클래스를 로딩하여 사용할 수 있다는 장점이 있다.

  * JRE : Java Runtime Enviroment (JVM + 클래스라이브러리 Java API) / JDK : Java Development Kit (JRE + 개발에 필요한 실행파일)
  
  
  ------
  
# 2. 변수(Variable)
 
  * Naming : 클래스 이름의 첫 글자는 항상 대문자로 하며, 변수와 메소드는 소문자로 한다. 여러 단어로 이루어진 이름은 카멜 표기법을 따른다.
  
  * Primitive type : 실제 값을 저장한다. (boolean, char, byte, short, int, long, float, double - 총 8개)
  
  * Reference type : 어떤 값이 저장되어 있는 주소를 값으로 가진다. (새로운 클래스를 작성하여 새로운 참조형변수를 만들어 낼 수 있다.)
  
  * Casting : 다른 타입으로의 변수로 변환한다. (연산은 기본적으로 같은 타입의 변수 간 동작한다.)

------

# 3. 객체지향(Object-Oriented)

  * Class/Object : 클래스에 정의된 대로 객체가 생성되며, 만들어진 객체는 그 클래스의 인스턴스라고 한다. (그리고 인스턴스는 참조변수를 통해서만 다룰 수 있다.)
  
  * Instance : 인스턴스 변수와 메소드는 인스턴스를 생성한 후 사용가능하며 인스턴스마다 서로 다른 값을 가질 수 있다. 클래스 변수와 메소드는 static 키워드를 활용해 사용할 수 있고, 모든 인스턴스들이 공통적인 값을 유지할 때 사용한다. (모든 인스턴스가 하나의 저장공간을 공유)
  
  * Overloading : 메소드의 이름이 같고 파라미터 갯수나 리턴 값 타입이 달라야한다. (ex : println함수)
  
  * Inheritance : 클래스 간의 관계는 포함(has-a)와 상속(is-a)로 구분할 수 있으며, 상황에 따라 클래스 자체가 변수로 쓰일 수도 있다.
  
  * OVerriding : 조상클래스로부터 상속받은 메소드의 내용을 상황에 맞게 변경할 수도 있다. 단, 선언부(이름, 리턴타입, 매개변수 등)는 같아야 한다.

  * Polymorphism : 조상클래스 타입의 참조변수로 자손클래스의 인스턴스를 참조할 수 있다. (상위 클래스변수는 하위 객체로 생성이 가능하다. ex: parent p = new child());
  
----
 
# 4. 예외처리(Exception handling)

  * 컴파일에러 : 컴파일 시 발생하는 에러
  
  * 런타임에러 : 프로그램 실행 도중에 발생하는 에러(에러와 예외)
    
  * 에러 : 메모리 부족이나 스택오버플로우처럼 일단 발생하면 복구할 수 없는 심각한 오류
  
  * 예외 : 발생하더라도 적절한 코드를 활용해 비정상적인 종료를 막을 수 있는 오류
  
  
  ---

# 5. 메모리
  
  * 특징 : 자바 응용프로그램은 운영체제나 하드웨어가 아닌 JVM하고만 통신하고, JVM이 자바 응용프로그램으로 전달받은 명령을 해당 운영체제가 이해할 수 있도록 변환하여 전달한다. 즉, 자바로 작성된 프로그램은 운영체제나 하드웨어와 관계없이 실행 가능하다.
  
  * 자바프로그램 실행과정 : 소스코드(.java) => 컴파일러 실행(javac) => 자바 바이트 코드 생성(.class) => OS별 JVM에서 실행
  
  * Static area : 메소드 내에서 정의하는 지역변수 및 데이터 값이 저장되는 영역
  
        public class StackAreaEx 
        {
	         public static void main(String[] args) 
          {
		          int a = 5;	a = 4;	a = 3;	a = 2;
		          System.out.println(a);

        //		System.out.println(i); 컴파일 에러
	       }

  * Heap area : 객체, 배열 등 참조형 데이터 타입을 저장하는 영역(new 연산자로 생성된 인스턴스 영역의 참조값을 )
  
           public class HeapAreaEx01
           {
	           public static void main(String[] args)
            {
		            int[] a = null; // int형 배열 선언 및 Stack 영역 공간 할당
		            System.out.println(a); // 결과 : null
		            a = new int[5]; // Heap 영역에 5개의 연속된 공간 할당 및 변수 a에 참조값 할당
		            System.out.println(a); // 결과 : @15db9742 (참조값)
	           }
           }
           
  * Static(Method, Class) area : 모든 객체가 다같이 공유하고 완벽하게 똑같이 공유하는 변수와 메소드에 활용되며, 코드가 JVM 메모리 상에 로딩될 때 딱 한 번만 올라간다.
