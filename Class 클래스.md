## Class 클래스
- reflection 프로그래밍 : Class 클래스를 이용하여 클래스의 정보(생성자, 멤버변수, 매서드)를 가져오고 이를 활용하여 인스턴스를 생성하고,   
  매서드를 호출하는 등의 프로그래밍 방식.
- 로컬 메모리에 객체가 없어서 객체의 데이터 타입을 직접 알 수 없는 경우(원격에 객체가 있는 경우 등) 객체 정보만을 이용하여 프로그래밍 할 수 있음.
- Constructor, Method, Filed 등 java.lang.reflect 패키지에 있는 클래스들을 활용하여 프로그래밍.
- 일반적으로 자료 형을 알 수 있는 경우에는 사용하지 않음.


1. Object 클래스의 getClass() 매서드
2. 클래스 파일 이름을 Class 변수에 직접 대입
3. Class.forNmae("클래스 이름") 매서드 

<code>
  <pre>
  
  package classEx;

public class ClassTest {

	public static void main(String[] args) throws ClassNotFoundException {

		Person person = new Person();
		
		Class pClass1 = person.getClass();
		
		System.out.println(pClass1.getName());
		
		Class pClass2 =  Person.class;
	
		System.out.println(pClass2.getName());

		//위의 두 개는 Person이란 클래스가 컴파일 되어있어야 사용 가능함.
		//static 로딩. 데이터 타입이 다 맞아떨어져야지 로딩이 되는 것.

		Class pClass3 = Class.forName("classEx.Person");
		
		System.out.println(pClass3.getName());
		
		//forName은 " "안에 문자열을 써서 그 이름의 클래스가 있으면 그것을 메모리에 로딩을 시킴.
		//있는지 없는지 모르는데 문자열이 실행이 되는 순간 그 이름을 가진 클래스가 있으면 가져옴.
		//파일 찾기랑 같구만. run을 해봐야지만 찾는게 있는지 없는지를 알 수 있는거.
		//동적 로딩.
		
	}
}

</code>
  </pre>
  
  # 동적 로딩
  - 동적 로딩이란?   
    컴파일 시에 데이터 타입이 모두 biding 되어 자료형이 로딩되는 것(static loading)이 아니라 실행 중에 데이터 타입을 알고 binding되는 방식.
  - 프로그래밍 할 떄는 어떤 클래스를 사용할지 모를 때 변수로 처리하고 실행될 때   
    해당 변수에 대입된 값의 클래스가 실행될 수 있도록 Class 클래스에서 제공하는 static 매서드.
  - 실행 시에 로딩되므로 경우에 따라 다른 클래스가 사용될 수 있어 유용함.
  - 컴파일 타임에 체크 할 수 없으므로 해당 문자열에 대한 클래스가 없는 경우 예외(ClassNotFoundException)이 발생할 수 있음.
