# Summary
1. 不能丢掉对头的控制权。如果头有可能会改变，因为不确定头是谁，使用dummy node 是个很好的选择，在增，删，reorder之后返回dumm.next作为新头
```java
ListNode dummy = new ListNode(-1);
ListNode cur = dummy;
...
cur.next = ...
return dummy.next;
```
2. 可能修改/断开的地方，时刻注意是否找得到某个node，如果可能丢失，就用一个指针mark住。
3. 理解recursion在linked list中的应用。如果将大的问题，分解成小一号的问题，在最小单元上完成一个重复性操作，在这个操作逐步recurse，完整整个问题。

## discuss
    1. When to use Iterative way vs Recursion way
    a. In real work environment, consider using iterative way first to avoid call stack overflow
    b. In interview environment
      i. For tree related problems, the recursion way is more preferred (usually easier)
      ii. For other problems, you can evaluate the real problem,
        1. if you can use both methods, and their time complexity are the same, the you can use either way.
        2. if their time complexity is different. E.g. Fibonacci, recursion vs DP (iterative way). Of course, you should pick the one with smaller time complexity
