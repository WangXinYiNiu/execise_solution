# laicode10. Quick Sort
Quick Sort: divide and conquer. Choosing a random pivot, put every smaller element left than it, bigger elements right than it.   

```java
public class Solution {
  public int[] quickSort(int[] array) {
    // Write your solution here
    if(array == null || array.length == 0){
      return array;
    }
    quickSort(array, 0, array.length - 1);
    return array;
  }
  
  //overload
  public void quickSort(int[] array, int left, int right){
    //recursion 要写 base case
    //bug: 不能写 == 要写 >= 
    //思考: [2,1]pivot选到index为1,排完后进下一个recursion时,left为2(pivot + 1)，right为1时
    //我们是需要return,不希望进函数里. 若进去right - left 为负数会nextInt会报错
    //(IllegalArgumentException: bound must be positive,因为nextInt里的区间只能(0, x]不能出现负数    
    if(left >= right){
      return;
    }
    //因为nextInt 左闭右开 所以要 + 1
    int pivotPos = partition(array, left, right); 
    quickSort(array, left, pivotPos - 1);
    quickSort(array, pivotPos + 1, right);
  }

  private int partition(int[] array, int left, int right){
    //给随机的这个pivotIndex找到正确的位置
    int pivotIndex = pivotIndex(left, right);
    swap(array, pivotIndex, right);
    int leftBound = left;
    int rightBound = right - 1;
    // leftBound == rightBound 需要检查嘛？-> 需要/因为最后是要把pivotIndex换回来 如果不检查的话不能换
    while(leftBound <= rightBound){
      if(array[leftBound] < array[right]){
        leftBound++;
      }else if(array[rightBound] >= array[right]){
        rightBound--;
      }else{
        swap(array, leftBound++, rightBound--);
      }
    }
    swap(array, leftBound, right);
    return leftBound;    
  }

  private int pivotIndex(int left, int right){
    //This method returns a pseudorandom double greater than or equal to 0.0 and less than 1.0.
    //又因为加了java是向下取整，所以right - left + 1 -> need to plus one.
    return left + (int)(Math.random() * (right - left + 1));
  }

  public void swap(int[] array, int i, int j) {
    int temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }  
}
```
```时间复杂度```     
worst case: 每次都选到最大的数或者最小 O(n^2)     
average case: O(NlogN)

```空间复杂度```     
worst case: O(N)        
average case: O(logN)       

分析：Although Quick Sort is not stable but it is an in-place algorithm and the probability of the worst case is very low. So, it's better than Merge Sort.
