# laicode4. Selection Sort
Given an array of integers, sort the elements in the array in ascending order. The selection sort algorithm should be used to solve this problem.

Examples

{1} is sorted to {1}
{1, 2, 3} is sorted to {1, 2, 3}
{3, 2, 1} is sorted to {1, 2, 3}
{4, 2, -3, 6, 1} is sorted to {-3, 1, 2, 4, 6}
Corner Cases

What if the given array is null? In this case, we do not need to do anything.
What if the given array is of length zero? In this case, we do not need to do anything.

- 自己代码  
```java
public class Solution {
    public int[] solve(int[] array) {
        // Write your solution here
        // selection sort an array a[] with size n.
        if (array == null || array.length == 0) {
            return array;
        }
        for (int i = 0; i < array.length; i++) {
            int globalMin = array[i];
            for (int j = i; j < array.length; j++) {
                if (array[j] < globalMin) {
                    globalMin = array[j];
                    int temp = array[j];
                    array[j] = array[i];
                    array[i] = temp;
                }
            }
        }
        return array;
    }
}
```
TC: O(n ^ 2) -> n represent # of array      
SC: O(1)

- 老师代码  
```java
public class Solution {
    public int[] solve(int[] array) {
        // Write your solution here
        // selection sort an array a[] with size n.
        if (array == null || array.length == 0) {
            return array;
        }
        for (int i = 0; i < array.length; i++) {
            int globalMin = i;
            //1. j should caculate from i + 1 rather than i.
            for (int j = i + 1; j < array.length; j++) {
                if (array[j] < array[globalMin]) {
                    globalMin = j;
                }
            }
            //2.
            int temp = array[i];
            array[i] = array[globalMin];
            array[globalMin] = temp;
        }
        return array;
    }
}
```
TC: O(n ^ 2)      
SC: O(1)
