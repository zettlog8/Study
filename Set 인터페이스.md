## Set 인터페이스
- Collection 하위의 인터페이스.
- 중복을 허용하지 않음.
- 아이디, 주민번호, 사번 등 유일한 값이나 객체를 관리할 때 사용.
- List는 순서 기반의 인터페이스지만, Set은 순서가 없음.
- 저장된 순서와 출력 순서는 다를 수 있음.
- get(i) 매서드가 제공되지 않음.

<code>
  <pre>
package hashset;

import java.util.HashSet;

public class HashSetTest {

	public static void main(String[] args) {

		HashSet<String> set = new HashSet<String>();
		
		boolean b1 = set.add("aaa");
    
    System.out.println(b1);
		set.add("bbb");
		set.add("ccc");
		
		System.out.println(set);
    
    boolean b = set.add("aaa");
    System.out.println(b);
	}
}
----------------------출력----------------------
true
[aaa, ccc, bbb]
false


//순서대로 나오지 않음.
//b1과 b가 같지 않음. 중복을 허용하지 않는다는 말.

</code>
  </pre>
  
- String은 equals가 이미 구현이 되어있지만 구현되어있지 않은 것은 직접 hashSet을 구현을 해야한다.   
  구현을 해야 hashSet에서 add를 할 때 기존에 있는 멤버와 새로 들어갈 멤버가 같은지를 체크한다.
