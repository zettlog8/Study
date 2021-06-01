## Set 인터페이스
- Collection 하위의 인터페이스.
- 중복을 허용하지 않음.
- 아이디, 주민번호, 사번 등 유일한 값이나 객체를 관리할 때 사용.
- List는 순서 기반의 인터페이스지만, Set은 순서가 없음.
- 저장된 순서와 출력 순서는 다를 수 있음.
- get(i) 매서드가 제공되지 않음.

## hashset 인터페이스
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


## TreeSet 인터페이스
- Tree가 붙으면 정렬.
- 객체의 정렬에 사용되는 클래스
- 중복을 허용하지 않으면서 오름차순이나 내림차순으로 객체를 정렬 함
- 내부적으로 이진 검색 트리(binary search tree)로 구현되어 있음
- 이진 검색 트리에 자료가 저장 될 때 비교하여 저장될 위치를 정함
- 객체 비교를 위해 Comparable이나 Comparator 인터페이스를 구현 해야 함.

### Comparable : 자신을 기준으로 오름차순, 내림차순 정렬

<code>
  <pre>
  @Override
	public int compareTo(Member member) {
		
		return (this.memberId - member.memberId);   //오름차순
		//return (this.memberId - member.memberId) *  (-1);   //내림 차순
	}
  
  //나 자신인 member와 넘어온 member를 바이너리 서치 트리로 비교하여 차순 정리.
  
--------------------memberID 오름차순 출력--------------------
김유신 회원님의 아이디는 101입니다.
이순신 회원님의 아이디는 102입니다.
신사임당 회원님의 아이디는 103입니다.
 
 --------------------memberID 내림차순 출력--------------------
 신사임당 회원님의 아이디는 103입니다.
 이순신 회원님의 아이디는 102입니다.
 김유신 회원님의 아이디는 101입니다.
</code>
  </pre>
  
### Comparator : 두 개의 매개 변수를 써서 비교할 수 있음
<code>
  <pre>
  @Override
	public int compare(Member member1, Member member2) {
		return (member1.memberId - member2.memberId);
	}
</code>
  </pre>
  
- 나중에 Comparator방식으로 정렬하고 싶으면
<code>
  <pre>
package collection.treeset;

import java.util.Comparator;
import java.util.TreeSet;

class MyCompare implements Comparator<String>{

	@Override
	public int compare(String str1, String str2) {
		return str1.compareTo(str2) * (-1);
	}
	
	
}

public class ComparatorTest {

	public static void main(String[] args) {

		TreeSet<String> tree =new TreeSet<String>(new MyCompare()); //이렇게 해주면 위의 MyCompare이 하라는대로 들어가서 내림차순 됨.
		
		tree.add("aaa");
		tree.add("ccc");
		tree.add("bbb");
		
		System.out.println(tree);
		
	}
}
</code>
  </pre>
  
  --------------------출력--------------------
  
  [ccc, bbb, aaa]

