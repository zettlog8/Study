## 배열과 링크트 리스트의 차이
- 링크드리스트는 원하는 인덱스를 찾기위해선 무조건 첫번째 배열부터 쭉 찾으러 가야하는데 배열은 물리적위치와 논리적 위치가 같기때문에   
  인덱스 연산이 가능해서 원하는 위치를 찾기가 쉽다.
- 배열이 유동적이라면 Linked List를 쓰면 좋고, 유동적이지 않을 경우 배열을 쓰면 유용하다.

## Linked List
- 링크드 리스트의 각 요소는 다음 요소를 가리키는 주소 값을 가짐.
- 물리적 메모리는 떨어져 이어도 논리적으로는 앞뒤 순서가 있음.
- 장점: 중간에 자료를 넣고 제거하는 데 시간이 적게 걸림.   
        크기를 동적으로 증가시킬 수 있음.
- 단점: 물리적 위치와 논리적 위치가 동일하지 않기때문에 하나의 인덱스를 찾기에 어려움.

# ArrayList
## Stack
- 위로 쌓는 방식.
- 꺼낼땐 맨 나중에 올린 상자를 먼저 꺼내야 됨.(Last In First Out;LIFO)
- 넣을땐 push, 꺼낼땐 pop.
- peek은 pop같이 원본삭제, 가져오는게 아니라 원본은 잠구고 읽기 기능만 주는 것. 원본이 사라지지 않는다.
- 가장 최근에 추가된 자료의 위치를 top이라고 함.

## Queue
- 옆으로 쌓는 방식.
- 선착순.
- 선입선출. 먼저 추가된 데이터부터 꺼내서 사용하는 방식.(First In First Out;FIFO)

## Iterator
- 요소를 순회할 때 사용하는 매서드
- hashNext() : 이후에 요소가 더 있는지 체크하고, 요소가 있다면 true를 반환.
- E next() : 다음에 있는 요소를 반환.

<code>
  <pre>
package arraylist;

import java.lang.reflect.Member;
import java.util.ArrayList;
import java.util.Iterator;

public class MemberArrayList {

	private ArrayList<Member> arrayList;
	
	public MemberArrayList() {
		arrayList = new ArrayList<Member>();
	}
	
	public void addMember(Member member) {
		arrayList.add(member);
	}
	
	public boolean removeMember(int memberId) {
		
		Iterator<Member> iterator = arrayList.listIterator();
		while(iterator.hasNext()) { //다음 요소가 있는지 확인하고 있으면  while문을 순회.
			Member member = iterator.next();  //다음 요소가 있는 동안 다음 회원을 반환 받음. 다음 요소가 없을 경우 null.
			int tempId = member.getMemberId();
			if(memberId == tempId) {
				arrayList.remove(member);
				return true;
		}
	 }
		System.out.println(memberId + "가 존재하지 않습니다.");
		return false;
	}
}
</code>
  </pre>
