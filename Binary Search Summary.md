经典的 Binary Search Summary

```java
public class Solution {
  public int binarySearch(int[] array, int target) {
    // Write your solution here
    int left = 0;
    int right = array.length - 1;
    //Due to we set the left equal to mid + 1, we need to check the situation about left equal to right.
    while(left <= right){
      int mid = left + (right - left) / 2;
      if(array[mid] == target){
        return mid;
      }else if(array[mid] < target){
      //the left needs to equal mid plus one instead of mid. eg. If we input [1, 2] to find the index of 2. it's obvious.
        left = mid + 1;
      }else{
        right = mid - 1;
      }
    }
    return -1; 
  }
}
```
