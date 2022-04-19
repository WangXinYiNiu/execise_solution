# laicode9. Merge Sort

```java
public class Solution {
  public int[] mergeSort(int[] array) {
    // Write your solution here
    if (array == null || array.length <= 1) {
            return array;
        }
        return merge(array, 0, array.length - 1);
  }
  
  public int[] merge(int[] array, int left, int right) {
        //base case
        if (left == right) {
            return new int[]{array[left]};
        }
        int mid = left + (right - left) / 2;
        int[] leftArray = merge(array, left, mid);
        int[] rightArray = merge(array, mid + 1, right);
        return sort(leftArray, rightArray);
    }
      public int[] sort(int[] left, int[] right) {
        int i = 0;
        int j = 0;
        int[] result = new int[left.length + right.length];
        int k = 0;
        while (i != left.length && j != right.length) {
            if (left[i] < right[j]) {
                result[k] = left[i];
                i++;
            } else {
                result[k] = right[j];
                j++;
            }
            k++;
        }
        while (i != left.length) {
            result[k] = left[i];
            k++;
            i++;
        }
        while (j != right.length) {
            result[k] = right[j];
            k++;
            j++;
        }
        return result;
    }
}
```
```时间复杂度：O(NlogN)```        
divide: O(logN)               
conquer: O(NlogN) -> conquer的时候每层要看所有的元素一共看logN层              

```空间复杂度：O(N)```
recursion 在 stack上占用的空间 O(logN)         
创建新的array占用的空间 n + n/2 + n/4 + ... + 1 = 2n -> O(N)           

特点：时间复杂度和空间复杂度都很稳定 
