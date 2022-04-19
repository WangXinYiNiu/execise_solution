# laicode34. Reverse Linked List (iterative, recursion)

Reverse a singly-linked list iteratively.     
Examples    
L = null, return null     
L = 1 -> null, return 1 -> null     
L = 1 -> 2 -> 3 -> null, return 3 -> 2 -> 1 -> null     

```java
class ListNode{
  public int value;
  public ListNode next;
  public ListNode(int value){
    this.value = value;
    next = null;
  }
}
```

## iterative
```java
public class Solution {
  public ListNode reverseLinkedList(ListNode head) {
    ListNode prev = null;
    while (head != null) {
      ListNode next = head.next;
      head.next = prev;
      prev = head;
      head = next;
    }
    return prev;
  }
}
```
时间复杂度: O(n)     
空间复杂度: O(1)     

## recursion
```java
public class Solution {
  public ListNode reverseLinkedList(ListNode head){
    // be careful about the base case,
    // need to make sure the later head.next.next != null.
    if (head == null || head.next == null){
      return head;
    }
    ListNode newHead = reverseLinkedList(head.next);
    head.next.next = head;
    head.next = null;
    return newHead;
  }
}
```
时间复杂度: O(n)
空间复杂度: O(n)
