# Queue & Stack Summary
1. Queue  
```
  a. Example: wait a line, FIFO == Fisrt in first out       
  b. Usages: Breadth-First Search related problems        
  c. Java api:      
     offer() - offer at the tail  
     poll() - poll at the head    
     peek() - look at the head without polling it out   
  d. 典型问题
    1. Tree printout by level   
    2. Sliding window problems(Deque: double ends manipulation Queue = {p2 p3 p4})    
```
 2. Stack                                                                    
```
LIFO - Last in first out: like a box
stack的移动操作的常见特性？
  a. 将stack1 所有元素全部move 到stack2，元素在stack2的顺序完全reverse
  b. 将stack1 所有元素move 到stack2，然后元素全部(或者部分)move回stack1。
  则回到原来stack1的元素的顺序不变，amortized的时间复杂度分摊到每一个move的元素的时间往往可以变为O(1).
```

## Four popular (queue-stack related) interview questions:
### Question 0: How to sort numbers with 3 stacks(no duplicate values)
```
global min = 2
Stack1 (input)[
Stack2 (buffer)[ 3 2 4
Stack3 (result)[ 1 2

Time: O(n^2)
```
### Question 1: How to sort numbers with 2 stacks(no duplicate values)
