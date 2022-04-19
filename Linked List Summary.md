## Key Points:
1. When you want to dereference a ListNode, make sure it is not a NULL pointer -> NPE       
2. Never ever lost the control of the head pointer of Linked List        

## 常见考题：       
1. [laicode34. Reverse Linked List (iterative, recursion)](https://github.com/wangxinyiiu/execise_solution/blob/main/laicode34.%20Reverse%20Linked%20List%20(iterative%2C%20recursion).md)    
    ```
    Discussion:
    1. When to use Iterative way vs Recursion way
    a. In real work environment, consider using iterative way first to avoid call stack overflow
    b. In interview environment
      i. For tree related problems, the recursion way is more preferred (usually easier)
      ii. For other problems, you can evaluate the real problem,
        1. if you can use both methods, and their time complexity are the same, the you can use either way.
        2. if their time complexity is different. E.g. Fibonacci, recursion vs DP (iterative way). Of course, you should pick the one with smaller time complexity
    ```
2.[]
