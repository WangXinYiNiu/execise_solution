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
    // 先把head的下一个node记住，在把head的next指向prev（反转），否则下一次prev移动到当前的head，head不知道该前去哪里
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
    // 反转head为头的list，子问题是反转以head.next为头的list，当前层要做的就是把反转后的子问题的尾巴（head.next)指向head
    ListNode newHead = reverseLinkedList(head.next); 
    // 此时head指向head.next(原list)，head.next也指向head(当前操作产生的结果)，产生环
    head.next.next = head;
    // 把上一步中提到的原list之间的键断开
    head.next = null;  
    // return 这个新的head -> 其实就是原来的最后一个
    return newHead;
  }
}
```
时间复杂度: O(n)     
空间复杂度: O(n)
