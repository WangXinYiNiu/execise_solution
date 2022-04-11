经典的 Binary Search Summary

```java
public class Solution {
  public int binarySearch(int[] array, int target) {
    // Write your solution here
    int left = 0;
    int right = array.length - 1;
    //Due to we set the left equal to mid + 1, we need to check the situation about left equal to right.
    //left <= right 是为了当数组长度为1时，也能进循环去check.
    while(left <= right){
      int mid = left + (right - left) / 2;
      if(array[mid] == target){
        return mid;
      }else if(array[mid] < target){
      //the left needs to equal mid plus one instead of mid. eg. If we input [1, 2] to find the index of 2. it's obvious.
      //如果我找的是target而没有限定条件的话（只要返回target就行 此时这个mid不被我们在考虑了，可以排出在外  就可以用left = mid + 1。
      //不用left = mid + 1的话会死循环。
        left = mid + 1;
      }else{
      //但是right 可以不用 mid - 1。 因为编程语言都是向下取整。
      //eg. {1, 2} target 找 2 -> left = 0, right = 1; mid = 0. If left = mid, time out.
        right = mid - 1;
      }
    }
    return -1; 
  }
}
```

