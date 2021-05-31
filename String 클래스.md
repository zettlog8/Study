## String 클래스로 문자열 연결
- 한번 생성된 String 값(문자열)은 불면(immutable)
- 두 개의 문자열을 연결하면 새로운 인스턴스가 생성 됨
- 문자열 연결을 계속하면 메모리에 gabage가 많이 생길 수 있음

<code>
  <pre>
  package hahaha;

public class StringTest {

	public static void main(String[] args) {

		String str1 = new String("abc");
		String str2 = new String("abc");
		
		System.out.println(str1 == str2);   //'=='의 의미는 같은 주소값인지를 확인한다.
		
		String str3 = "abc";		//문자열 상수를 직접 가리키게 되면 두 개는 동일한 메모리를 가리킨다. 
		String str4 = "abc";
		System.out.println(str3 == str4);
		
---------------출력---------------
false
true

		
	}
}
</code>
  </pre>
  
<code>
  <pre>
package hahaha;

public class StringTest {

	public static void main(String[] args) {

		String str1 = new String("java");
		String str2 = new String("android");
		
		System.out.println(System.identityHashCode(str1));
		
		str1 = str1.concat(str2);
		
		System.out.println(str1);
		System.out.println(System.identityHashCode(str1));

	}
}
---------------출력---------------
985922955
javaandroid
1435804085


</code>
  </pre>
  
  
## StringBuilder, StringBuffer 사용하기
- 내부적으로 가변적인 char[] 배열을 가지고 있는 클래스
- 문자열을 여러 번 연결하거나 변경할 때 사용하면 유용함
- 매번 새로 생성하지 않고 기존 배열을 변경하므로 gabage가 생기지 않음
- StringBuffer는 멀티 쓰레드 프로그래밍에서 동기화(쓰레드 간의 순서를 보장해주는 것)를 보장
- 단일 쓰레드 프로그램에서는 StringBuilder를 사용하기를 권장
- toString() 매서드로 String 반환   
(StringBuilder, StringBuffer는 스트링 클래스는 아니기때문에   
스트링 클래스로 반환하고 싶으면 to String 매서드로 호출하면 String으로 반환된다.)


<code>
  <pre>
  package hahaha;

public class StringBuilderTest {

	public static void main(String[] args) {
		
		String str1 = new String("java");
		
		System.out.println(System.identityHashCode(str1));
		
		StringBuilder buffer = new StringBuilder(str1);
		System.out.println(System.identityHashCode(buffer));
		
		buffer.append("  and");
		buffer.append("  android");
		buffer.append("   ddd");
		buffer.append("   abc");
		buffer.append("   def");
		buffer.append("   hrj");
		
		
		System.out.println(System.identityHashCode(buffer));
		
		String str3 = buffer.toString();    //toString을 사용하여 스트링 클래스로 반환.
		System.out.println(str3);
	}
}


</code>
  </pre>
  
  
  ## Wrapper
  - intValue() : Integer 클래스 내부의 int 자료형 값을 가져오기 위해 쓰임.
  - valueOf() : 생성자를 사용하지 않고 정수나 문자열을 바로 Integer 클래스로 반환받을 수 있음
  - parseInt() : 문자열이 어떤 숫자를 나타낼 때 문자열에서 int값을 바로 가져와서 반환할 수 있음.
<code>
  <pre>
  package hahaha;

public class StringBuilderTest {

	public static void main(String[] args) {
		
		Integer iValue = new Integer(100);
		int myValue = iValue.intValue()	;
		System.out.println(myValue);
		
		Integer number1 = Integer.valueOf("200");
		Integer number2 = Integer.valueOf(200);
		System.out.println(number1);
		System.out.println(number2);
		
		int num = Integer.parseInt("300");
		System.out.println(num);
    
---------------출력---------------
100
200
200
300

    
	}
}
</code>
  </pre>
  
## 오토박싱과 언박싱
package hahaha;

public class StringBuilderTest {

	public static void main(String[] args) {
		
		Integer num1 = new Integer(100);  //Wrapper클래스 Integer intValue()형.
		int num2 = 200;   //int 정수형.
		int sum = num1 + num2;
		Integer num3 = num2;
		System.out.println(num3);
	}

}
 
