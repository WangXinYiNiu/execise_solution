# laicode40. Merge Two Sorted Linked Lists
Merge two sorted lists into one large sorted list.

Examples      
L1 = 1 -> 4 -> 6 -> null, L2 = 2 -> 5 -> null, merge L1 and L2 to 1 -> 2 -> 4 -> 5 -> 6 -> null       
L1 = null, L2 = 1 -> 2 -> null, merge L1 and L2 to 1 -> 2 -> null       
L1 = null, L2 = null, merge L1 and L2 to null       
```java
public class Solution {
  public ListNode merge(ListNode one, ListNode two) {
    // Write your solution here
    ListNode dummy = new ListNode(-1);
    ListNode cur = dummy;
    //stop condition: one == null || two == null
    while(one != null && two != null){
      if(one.value < two.value){
        cur.next = one;
        one = one.next;
      }else{
        cur.next = two;
        two = two.next;
      }
      cur = cur.next;
    }
    // 本来写了俩个while循环去接后面的node 其实没必要
    // linked list could link the remaining possible nodes.
    if (one != null){
      cur.next = one;
    }else{
      cur.next = two;
    }
    return dummy.next;
  }
}
```
时间复杂度: O(m + n)     
空间复杂度: O(1) -> 没有产生额外空间，用的还是原来的reference，只不过指向改变了。
