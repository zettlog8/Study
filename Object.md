## String toString
<code>
  <pre>
package object;

class Book{
	String title;
	String author;
	
	Book(String title, String author){
		this.title = title;
		this.author = author;
	}

	@Override
	public String toString() {
		return title + "," + author;
	}
	
	
}


public class ToStringEx {

	public static void main(String[] args) {

		Book book = new Book("두잇자바","은종님");
		System.out.println(book);

		String str = new String("test"); //String toString은 자신의 문자열을 출력하도록 되어있음.
		System.out.println(str);
	}
}

</code>
  </pre>
  
  
## Equals 
- String은 같은 문자열의 경우 true를 반환.
- Integer는 정수 값이 같은 경우 true를 반환.
<code>
  <pre>
package object;

class Student{
	int studentID;
	String studentName;
	
	Student(int studentID, String studentName) {
		this.studentID = studentID;
		this.studentName = studentName;
	}
  
 
  public class EqualsTest {

	public static void main(String[] args) {
		String str1 = new String("Test");
		String str2 = new String("Test");
		
		System.out.println(str1 == str2); // 힙 메모리가 달라서 false; 물리적
		System.out.println(str1.equals(str2)); //str1과 str2의 문자열이 같은지를 체크하는 것.
											                     //문자열이 같으면 동일한 것으로 해줌; 논리적 
										                    	//논리적 동일성을 정의할때 equals를 씀.
	
		
		
		Student std1 = new Student(10001, "Tomas");
		Student std2 = new Student(10001, "Tomas");
		
		System.out.println(std1 == std2);
		System.out.println(std1.equals(std2));
	}

}
------------------------출력------------------------
false
true

</code>
  </pre>
  
<code>
  <pre>
  
package object;

class Student{
	int studentID;
	String studentName;
	
	Student(int studentID, String studentName) {
		this.studentID = studentID;
		this.studentName = studentName;
	}

	@Override //재정의를 안해주면 false로 나오기때문에 재정의를 해줘야한다. 
	public boolean equals(Object obj) {   //Object로 업캐스팅 된 것을
  
		if( obj instanceof Student) {     //다운캐스팅 해줌
			Student std = (Student)obj;
			if(studentID == std.studentID) 
				return true;
			else 
				return false;
		}
	 return false;
	}
	
}

public class EqualsTest {

	public static void main(String[] args) {
		
		Student std1 = new Student(10001, "Tomas");
		Student std2 = new Student(10001, "Tomas");
		
		System.out.println(std1 == std2);   //두 개의 메모리가 달라서 false.(물리적)
		System.out.println(std1.equals(std2));  //equals의 원래 원형은 ==과 같아서 false가 나옴. 이럴땐 재정의를 해줘야함.
	}

}

------------------------출력------------------------

false
true

  
</code>
  </pre>
  
## hashCode
- hash : 정보를 저장, 검색하기 위해 사용하는 자료구조
- 자료의 특정 값(키 값)에 대해 저장 위치를 반환해주는 해시 함수를 사용함   
          index(저장위치) = hash(해시함수)(key)(객체정보)
- 해시 함수는 어떤 정보인가에 따라 다르게 구현 됨
- hashCode() 매서드는 인스턴스의 저장 주소를 반환함
- 힙 메모리에 인스턴스가 저장되는 방식이 hash
- hashCode()의 반환 값: 자바 가상 머신이 저장한 인스턴스의 주소값을 10진수로 나타냄

### 서로 다른 메모리의 두 인스턴스가 같다면?
- 재정의 된 equals() 매서드의 값이 true
- 동일한 hashCode() 반환 값을 가져야함
- 논리적으로 돈일함을 위해 equals() 매서드를 재정의 하였다면 hashCode() 매서드로 재정의 하여 동일한 값이 반환 되도록 함   
   (그래서 일반적으로 equals 매서드를 재정의 하였다면 hashCode 매서드도 재정의 한다.)
- String 클래스 : 동일한 문자열 인스턴스에 대해 동일한 정수가 반환 됨
- Integer 클래스 : 동일한 정수값의 인스턴스에 대해 같은 정수값이 반환 됨   


## clone 
- 객체의 원본 복제하는데 사용하는 매서드
- 원본을 유지해 놓고 복사본을 사용할 때
- 기본 틀을 두고 복잡한 생성과정을 반복하지 않고 복제
- clone 매서드를 사용하면 객체의 정보(멤버변수 값)가 같은 인스턴스가 또 생성되는 것이므로   
  객체 지향 프로그램의 정보은닉, 객체 보호의 관점에서 위배될 수 있음
- 객체의 clone 매서드 사용을 허용한다는 의미로 cloneable 인터페이스를 명시해줌
