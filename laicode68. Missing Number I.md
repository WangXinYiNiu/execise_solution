# laicode68. Missing Number I

Given an integer array of size N - 1, containing all the numbers from 1 to N except one, find the missing number.   

Assumptions     

The given array is not null, and N >= 1       
  
Examples      

A = {2, 1, 4}, the missing number is 3      
A = {1, 2, 3}, the missing number is 4    
A = {}, the missing number is 1     

## Solution
```java
public class Solution {
  public int missing(int[] array) {
    // Write your solution here
    long sum = (1 + array.length + 1) * (array.length + 1) / 2;
    for (int i : array) {
      sum -= i;
    }
    return (int)sum;
  }
}
```
TC: O(n) -> n: array.length
SC: O(1)

## 注意
在加一个int组成的array时，一定要注意work over flow的问题
