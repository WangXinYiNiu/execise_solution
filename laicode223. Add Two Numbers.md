# laicode223. Add Two Numbers

You are given two linked lists representing two non-negative numbers.     
The digits are stored in reverse order and each of their nodes contain a single digit.      
Add the two numbers and return it as a linked list.     

Example
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)      
Output: 7 -> 0 -> 8

## Version one (by xinyi)
```java
public class Solution {
  public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    // Write your solution here
    ListNode head = new ListNode(-1);
    ListNode cur = head;
    int i = 0;
    while(l1 != null && l2 != null){
      int value = l1.value + l2.value + i;
      ListNode node = new ListNode(value);      
      if(value + i < 10){
        cur.next = node;
        i = 0;
      }else{
        node.value = value % 10;
        cur.next = node;
        i = value / 10;       
      }
      cur = cur.next;
      l1 = l1.next;
      l2 = l2.next;
    }

    while(l1 != null){
      int value = l1.value + i;
      ListNode node = new ListNode(value);
      if(value + i < 10){
        cur.next = node;
        i = 0;
      }else{
        node.value = value % 10;
        cur.next = node;
        i = value / 10;
      }
      cur = cur.next;
      l1 = l1.next;
    }

    while(l2 != null){
      int value = l2.value + i;
      ListNode node = new ListNode(value);
      if(value + i < 10){
        cur.next = node;
        i = 0;
      }else{
        node.value = value % 10;
        cur.next = node;
        i = value / 10;
      }
      cur = cur.next;
      l2 = l2.next;
    }

    if(i != 0){
      cur.next = new ListNode(i);
    }
    return head.next;
  }
}
```
其实可以包在第一个循环里的，太傻太笨了！

## Version two
```java
public class Solution {
  public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    // Write your solution here
    ListNode dummy = new ListNode(-1);
    ListNode cur = dummy;
    int i = 0;
    //stop condition: l1 == null && l2 == null && i == 0
    while(l1 != null || l2 != null || i != 0){
      if(l1 != null){
        i = i + l1.value;
        l1 = l1.next;
      }
      if(l2 != null){
        i = i + l2.value;
        l2 = l2.next;
      }
      cur.next = new ListNode(i % 10);
      cur = cur.next;
      i = i / 10;
    }
    return dummy.next;
  }
}
```
答案的时间复杂度是
TC: O(max(n,m))       
SC: O(max(n,m))       
还没搞懂？？？
  




