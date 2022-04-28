# laicode306. Check If Linked List Is Palindrome
Given a linked list, check whether it is a palindrome.

Examples:     
Input:   1 -> 2 -> 3 -> 2 -> 1 -> null      
output: true.     

Input:   1 -> 2 -> 3 -> null        
output: false.      

Requirements:     
Space complexity must be O(1)     

## Solution:
```java
public class Solution {
  public boolean isPalindrome(ListNode head) {
    // Write your solution here
    // corner case
    if(head == null || head.next == null){
      return true;
    }
    ListNode mid = findMid(head);
    ListNode right = mid.next;
    mid.next = null;
    right = reverse(right);
    while(head != null && right != null){
      if(head.value != right.value){
        return false;
      }
      head = head.next;
      right = right.next;
    }
    return true;
  }

  private ListNode findMid(ListNode head){
    ListNode slow = head;
    ListNode fast = head;
    while(fast.next != null && fast.next.next != null){
      slow = slow.next;
      fast = fast.next.next;
    }
    return slow;
  }

  private ListNode reverse(ListNode head){
    if(head.next == null){return head;}
    ListNode newHead = reverse(head.next);
    head.next.next = head;
    head.next = null;
    return newHead;
  }
}
```
TC: O(n)
SC: O(1)
