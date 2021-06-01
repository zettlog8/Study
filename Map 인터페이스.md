## HashMap 
- key-value pair 의 객체를 관리하는데 필요한 매서드가 정의 됨.
- value는 중복될 수 있지만, key는 중복 될 수 없음.(ex. 사전: 단어(key) 하나에 뜻(value)은 여러 개일 수 있다.)
- 검색을 위한 자료 구조.
- key를 이용하여 값을 저장하거나 검색, 삭제 할 때 사용하면 편리함.
- 내부적으로 hash 방식으로 구현 됨.   
     index = hash(key) //index는 저장 위치.
- key가 되는 객체는 객체의 유일성함의 여부를 알기 위해 equals()와 hashCode() 매서드를 재정의 함.

<code>
  <pre>
  package collection.hashmap;

import java.util.HashMap;
import java.util.Iterator;

import collection.Member;

public class MemberHashMap {

	private HashMap<Integer, Member> hashMap;
	
	public MemberHashMap()	{
		hashMap = new HashMap<Integer, Member>();
	}
	
	public void addMember(Member member) {
		hashMap.put(member.getMemberId(), member); //hashMap에서 넣는 것 put.
	}
	
	public boolean removeMember(int memberId) {
		
		if(hashMap.containsKey(memberId)){
			
			hashMap.remove(memberId);
			return true;
		}
		
		System.out.println(memberId + "가 존재하지 않습니다");
		return false;
	}
	
	public void showAllMember() {
		Iterator<Integer> ir = hashMap.keySet().iterator();
		
		while(ir.hasNext()) {
			int key = ir.next();
			
			Member member = hashMap.get(key);
			System.out.println(member);
		}
	}
}
</code>
  </pre>
<code>
  <pre>
  package collection.hashmap;

import collection.Member;
import collection.treeset.MemberTreeSet;

public class MemberHashMapTest {

	public static void main(String[] args) {
		MemberHashMap memberHashMap = new MemberHashMap();
		
		Member memberLee = new Member(102, "이순신");
		Member memberKim = new Member(101, "김유신");
		Member memberShin = new Member(103, "신사임당");
	
		memberHashMap.addMember(memberLee);
		memberHashMap.addMember(memberKim);
		memberHashMap.addMember(memberShin);
		
		memberHashMap.showAllMember();

		memberHashMap.removeMember(102);  //출력해보면 아이디 102가 없어진 것을 볼 수 있다.
		memberHashMap.showAllMember();


	}
}

-------------출력-------------
김유신 회원님의 아이디는 101입니다
이순신 회원님의 아이디는 102입니다
신사임당 회원님의 아이디는 103입니다
김유신 회원님의 아이디는 101입니다
신사임당 회원님의 아이디는 103입니다

//아이디 102 없음.


</code>
  </pre>


## TreeMap 클래스
- key 객체를 정렬하여 key-value를 pair로 관리하는 클래스.
- key에 사용되는 클래스에 Comparable, Comparator 인터페이스를 구현.
- java에 많은 클래스들은 이미 Comparable이 구현되어 있음.
- 구현 된 클래스를 key로 사용하는 경우는 구현할 필요 없음.

<code>
  <pre>
  package collection.treemap;

import java.util.Iterator;
import java.util.TreeMap;

import collection.Member;

public class MemberTreeMap {

	private TreeMap<Integer, Member> treeMap;
	
	public MemberTreeMap()	{
		treeMap = new TreeMap<Integer, Member>();
	}
	
	public void addMember(Member member) {
		treeMap.put(member.getMemberId(), member); //hashMap에서 넣는 것 put.
	}
	
	public boolean removeMember(int memberId) {
		
		if(treeMap.containsKey(memberId)){
			
			treeMap.remove(memberId);
			return true;
		}
		
		System.out.println(memberId + "가 존재하지 않습니다");
		return false;
	}
	
	public void showAllMember() {
		Iterator<Integer> ir = treeMap.keySet().iterator();
		
		while(ir.hasNext()) {
			int key = ir.next();
			
			Member member = treeMap.get(key);
			System.out.println(member);
		}
	}
}
</code>
  </pre>
<code>
  <pre>
package collection.treemap;

import collection.Member;
import collection.treeset.MemberTreeSet;

public class MemberTreeMapTest {

	public static void main(String[] args) {
		MemberTreeMap memberTreeMap = new MemberTreeMap();
		
		Member memberLee = new Member(102, "이순신");
		Member memberKim = new Member(101, "김유신");
		Member memberShin = new Member(103, "신사임당");
	
		memberTreeMap.addMember(memberLee);
		memberTreeMap.addMember(memberKim);
		memberTreeMap.addMember(memberShin);
		
		memberTreeMap.showAllMember();

		/*memberTreeMap.removeMember(102);
		memberTreeMap.showAllMember();*/
	}
}

---------------출력---------------
김유신 회원님의 아이디는 101입니다
이순신 회원님의 아이디는 102입니다
신사임당 회원님의 아이디는 103입니다

comparable과 treeMap의 차이점은 
comparable은 이름으로 정렬하고,
treeMap은 key와 value로 정렬한다는 것. 
이것도 마찬가지로 다시 정렬하고싶으면 comparator로 하면 됨.
</code>
  </pre>
