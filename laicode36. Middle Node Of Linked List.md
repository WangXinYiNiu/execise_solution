# laicode36. Middle Node Of Linked List

Find the middle node of a given linked list.

Examples        
L = null, return null       
L = 1 -> null, return 1       
L = 1 -> 2 -> null, return 1        
L = 1 -> 2 -> 3 -> null, return 2       
L = 1 -> 2 -> 3 -> 4 -> null, return 2        

### Note:
Given an even number of nodes (2 middle nodes), stop at 1st one because you'll still keep the choice to get the 2nd one. (f.n.n = null)


```java
public class Solution {
  public ListNode middleNode(ListNode head) {
    // Write your solution here
    if(head == null){
      return head;
    }
    ListNode fast = head;
    ListNode slow = head;
    while(fast.next != null && fast.next.next != null){
      slow = slow.next;
      fast = fast.next.next;
    }
    return slow;
  }
}
```
TC: O(n)
SC: O(n)
