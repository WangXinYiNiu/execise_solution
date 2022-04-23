## Given the head of a linked list, return the list after sorting it in ascending order.
Example 1:
Input: head = [4,2,1,3]
Output: [1,2,3,4]

Example 2:
Input: head = [-1,5,3,4,0]
Output: [-1,0,3,4,5]

Example 3:
Input: head = []
Output: []
 

Constraints:

The number of nodes in the list is in the range [0, 5 * 104].
-105 <= Node.val <= 105

Follow up: Can you sort the linked list in O(n logn) time and O(1) memory (i.e. constant space)?

```java
class Solution {
    public ListNode sortList(ListNode head) {
        if(head == null || head.next == null){
            return head;
        }
        ListNode mid = middleNode(head);        
        ListNode next = mid.next;
        mid.next = null;
        return sort(sortList(head), sortList(next));
    }
    
    public ListNode sort(ListNode one, ListNode two) {
        ListNode dummy = new ListNode(-1);
        ListNode cur = dummy;
        //stop condition: one == null || two == null
        while(one != null && two != null){
            if(one.val < two.val){
                cur.next = one;
                one = one.next;
            }else{
                cur.next = two;
                two = two.next;
            }
                cur = cur.next;
            }
        
            if (one != null){
                cur.next = one;
            }else{
                cur.next = two;
            }
            return dummy.next;
        }
    
    public ListNode middleNode(ListNode head) {
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
