# laicode39. Insert In Sorted Linked List
Insert a value in a sorted linked list.

Examples
L = null, insert 1, return 1 -> null        
L = 1 -> 3 -> 5 -> null, insert 2, return 1 -> 2 -> 3 -> 5 -> null          
L = 1 -> 3 -> 5 -> null, insert 3, return 1 -> 3 -> 3 -> 5 -> null          
L = 2 -> 3 -> null, insert 1, return 1 -> 2 -> 3 -> null        

```java
public class Solution{
  public ListNode insert(ListNode head, int value){
    // 因为有可能加到head之前 -> change head pointer -> use dummy.
    ListNode dummy = new ListNode(-1);
    dummy.next = head;
    
    // 先把这个value放到ListNode里
    ListNode newNode = new ListNode(value);
    
    ListNode pre = dummy;
    ListNode cur = head;
    
    //stop condition: cur == null || cur.value > value -> 走到最后一位 或者 cur的值大于value
    while(cur != null && cur.value < value){
      pre = pre.next;
      cur = cur.next;
    }
    
    pre.next = newNode;
    newNode.next = cur;
    return dummy.next;
  }
}
```
TC: O(n)
SC: O(1)
