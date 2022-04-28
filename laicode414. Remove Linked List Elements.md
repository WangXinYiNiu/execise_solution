# laicode414. Remove Linked List Elements
Remove all elements from a linked list of integers that have value val.

Example
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5

## Solution:
```java
public class Solution {
  public ListNode removeElements(ListNode head, int val) {
    // Write your solution here
    // 头有可能会发生变化 所以建dummy
    ListNode dummy = new ListNode(-1);
    ListNode prev = dummy;
    prev.next = head;
    while(head != null){
      // 这一步没有必要
      // ListNode node = head.next;
      if(head.value == val){
        prev.next = head.next;
        // 这一步很关键，如果prev.next = node的话
        // prev 则不需要移动了。
      }else{
        prev = prev.next;
      }
      head = head.next;
    }
    return dummy.next;
  }
}
```
TC:O(n)   
SC:O(1)
