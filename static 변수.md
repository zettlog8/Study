## static 변수
- 클래스 변수라고도 함.
- 메서드에 static 키워드를 사용하여 구현.
- 주로 static 변수를 위한 기능 제공.
- static 변수는 인스턴스가 생성될 때 마다 다른 메모리를 가지는 것이 아니라   
  프로그램이 메모리에 적재(load)될 때 데이터 영역의 메모리에 생성 됨.   
  따라서 인스턴스의 생성과 관계없이 클래스 이름으로 직접 참조 함.
  Student.serialNum = 100; // serialNum이 static 변수.
  - static 메서드에서는 인스턴스 변수를 쓸 수 없다. 
  인스턴스 변수의 경우 꼭 인스턴스가 먼저 생성되어야 하므로 static 메서드에서는 생성이 불확실한 인스턴스 변수를 사용할 수 없음.
  static 메서드도 인스턴스의 생성과 관계 없이 클래스 이름으로 직접 메서드 호출
  Student.getSerialNum(); //getSerialNum()이 static 메서드
  멤버 변수는 다른 말로 인스턴스 변수라고 함.
- static 변수는 메모리가 상수, 리터럴 등이 놓인 data 영역에 놓이고, stack이나 heap 메모리에 놓이지 않는다. 
  이처럼 놓이는 공간도 다르고 클래스에서 공용되는 변수라고해서 클래스 변수라고도 한다.

<code>
  <pre>
package staticEx;

public class Student {

	private static int serialNum = 10000;
	
	int studentID;
	String studentName;
	
	public Student() {
		serialNum++;
		studentID = serialNum;
	}

	public static int getSerialNum() {
		/*int i = 10;	//지역변수는 static 안에 써도 상관없음.
		
		i++;
		System.out.println(i);*/
		
		//studentName = "홍길동";	//인스턴스 변수(=멤버변수)
		//인스턴스 변수는 new가 될 때 생성이 되는데 여기서는
		// 생성되지도 않은 인스턴스 변수를 놓게 되는 것.
		
		return serialNum;	//static 변수(=클래스 변수)
	}
	
}






package staticEx;

public class StudentTest1 {

	public static void main(String[] args) {

		Student studentJ = new Student();
		System.out.println(Student.getSerialNum());
	
		Student studentT = new Student();
		System.out.println(studentT.studentID);
		
		
	System.out.println(Student.getSerialNum());
	System.out.println(Student.getSerialNum());
	
	
	}
}

-------------------출력-------------------
10001
10002
10002
10002

</code>
  </pre>
  
  
  
지역 변수(로컬 변수) 
- 함수 내부에 선언.
- 함수 내부에서만 사용.
- stack 메모리에 놓임.
- 함수가 호출될 때 생성되고 함수가 끝나면 소멸함.

멤버 변수(인스턴스 변수)
- 클래스 멤버 변수로 선언.
- 클래스 내부에서 사용하고 private이 아니면 참조 변수로 다른 클래스에서 사용 가능.
- heap 메모리에 놓임.
- 인스턴스가 생성될 때 힙에 생성되고, 가비지 콜렉터가 메모리를 수거할 때 소멸됨.

static 변수(클래스 변수)
- static 예약어를 사용하여 클래스 내부에 선언.
- 클래스 내부에서 사용하고 private이 아니면 클래스 이름으로 다른 클래스에서 사용 가능.
- data 영역에 놓임.
- 프로그램에 처음 시작할 때 상수와 함께 데이터 영역에 생성되고 프로그램이 끝나고 메모리 해제할 때 소멸됨.
