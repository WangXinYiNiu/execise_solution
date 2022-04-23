# laicode29. Merge Sort Linked List

Given a singly-linked list, where each node contains an integer value, sort it in ascending order. The merge sort algorithm should be used to solve this problem.

Examples
null, is sorted to null   
1 -> null, is sorted to 1 -> null    
1 -> 2 -> 3 -> null, is sorted to 1 -> 2 -> 3 -> null    
4 -> 2 -> 6 -> -3 -> 5 -> null, is sorted to -3 -> 2 -> 4 -> 5 -> 6    

## Solution
```java
public class Solution {
     public ListNode mergeSort(ListNode head) {
        //base case:
        if (head == null || head.next == null) {
            return head;
        }
        ListNode middle = findMiddle(head);
        ListNode middleNext = middle.next;
        middle.next = null;
        //subProblem
        ListNode left = mergeSort(head);
        ListNode right = mergeSort(middleNext);
        return sort(left, right);
    }

    private ListNode findMiddle(ListNode head) {
        if (head == null) {
            return null;
        }
        ListNode slow = head;
        ListNode quick = head;
        while (quick.next != null && quick.next.next != null) {
            slow = slow.next;
            quick = quick.next.next;
        }
        return slow;
    }

    private ListNode sort(ListNode left, ListNode right) {
        ListNode curLeft = left;
        ListNode curRight = right;
        ListNode newHead = new ListNode(-1);
        ListNode cur = newHead;
        while (curLeft != null && curRight != null) {
            if (curLeft.value <= curRight.value) {
                cur.next = curLeft;
                curLeft = curLeft.next;
            } else {
                cur.next = curRight;
                curRight = curRight.next;
            }
            cur = cur.next;
        }
        while (curLeft != null) {
            cur.next = curLeft;
            cur = cur.next;
            curLeft = curLeft.next;
        }
        while (curRight != null) {
            cur.next = curRight;
            cur = cur.next;
            curRight = curRight.next;
        }
        return newHead.next;
    }
}
```

时间复杂度：O(nlogn)                
空间复杂度: O(logn) -> stack                 
