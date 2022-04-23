# laicode42. Partition Linked List
Given a linked list and a target value T, partition it such that all nodes less than T are listed before the nodes larger than or equal to target value T. The original relative order of the nodes in each of the two partitions should be preserved.    

Examples  
L = 2 -> 4 -> 3 -> 5 -> 1 -> null, T = 3, is partitioned to 2 -> 1 -> 4 -> 3 -> 5 -> null     

## Solution
```java
public class Solution {
  public ListNode partition(ListNode head, int target) {
    // Write your solution here
    if (head == null || head.next == null) {
      return head;
    }
    // 创建两个dummynode当作两个挡板，把a类放a挡板后，b类放b挡板后，最后得到两个list，把两个list连起来
    ListNode small = new ListNode(-1);
    ListNode cursmall = small;
    ListNode big = new ListNode(-1);
    ListNode curbig = big;
    // 所有node都要遍历一遍
    while (head != null) {
      // 小于target放small挡板后面
      if (head.value < target) { 
        cursmall.next = head;
        cursmall = cursmall.next;
      }
      // 题目要求大于等于视为一样，否则再加一个判断，分三类 -- list分n类n个挡板
      else { 
        // array分n类n-1个挡板
        curbig.next = head;                     
        curbig = curbig.next;
      } 
      head = head.next;
    }
    // 走完while，所有node都已经站好队，把两个list连起来
    cursmall.next = big.next;
    curbig.next = null;
    return small.next;
  }
}
```
