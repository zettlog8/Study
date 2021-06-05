## this가 하는 일
- 자신의 메모리를 가리킴.
- 생성자에서 다른 생성자를 호출.
- 자신의 주소를 반환 함.

### 자신의 메모리를 가리킴.
<code>
  <pre>
  package thisEx;

class Birthday{
	int day;
	int month;
	int year;
	
	public void setYear(int year) {	//매개변수는 지역변수고
		this.year = year;		//this가 가리키는건 heap 메모리에 저장된 인스턴스이다.
	}							//그렇기 때문에 다른 메모리 공간에 있는 값들을 가리켜줘야한다.
	
	public void printThis() {
		System.out.println(this);
	}
	
	
}
public class ThisExample {

	public static void main(String[] args) {

		Birthday b1 = new Birthday();
		Birthday b2 = new Birthday();
		
		System.out.println(b1);
		System.out.println(b2);
		b1.printThis();
		b2.printThis();
	}

}

//this로 가리키는 주소값과 인스턴스의 주소값이 같음. 
    
--------------------출력--------------------
thisEx.Birthday@6a5fc7f7
thisEx.Birthday@3b6eb2ec
thisEx.Birthday@6a5fc7f7
thisEx.Birthday@3b6eb2ec


</code>
  </pre>
  
## 생성자에서 다른 생성자를 호출, 자신의 주소 반환.
- 생성자에서 다른 생성자를 호출할때는 new를 안써도 된다.

<code>
  <pre>
package thisEx;

class Person{
	
	String name;
	int age;
	
	public Person() {		
		//int i = 0;	//this를 쓸 때는 이 앞에 어떠한 문장도 올 수 없다. 
		
		this("이름없음", 1);	//2. 디폴트 생성자에서 쓸 수 있다.
	}
	
	public Person(String name, int age) {	//1. 꼭 쓰고싶은 멤버변수가 있을때 매개변수로 지정하면
		this.name = name;
		this.age = age;
	}
	
	public Person returnSelf() {
		return this;
}

}
	
	
public class CallAnotherConst {
	
	public static void main(String[] args) {

		
		Person p1 = new Person();
		System.out.println(p1.name);
		
		System.out.println(p1.returnSelf());
	}

}

--------------------출력--------------------
이름없음
thisEx.Person@6a5fc7f7

</code>
  </pre>
