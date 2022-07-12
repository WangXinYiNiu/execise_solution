# laicode82. Remove Adjacent Repeated Characters IV
Repeatedly remove all adjacent, repeated characters in a given string from left to right.   

No adjacent characters should be identified in the final string.      

Examples      

"abbbaaccz" → "aaaccz" → "ccz" → "z"      
"aabccdc" → "bccdc" → "bdc"     

**HighLevel: If the element is equal to the top of the stack, remove the top of the stack element (baffle left move), and remove all equal elements.**
## Solution
```java
public class Solution {
  public String deDup(String input) {

      char[] array = input.toCharArray();
      // 设置挡板当作stack顶端，挡板左边区域当作stack(包含挡板）, 从数组左边开始
      int end = 0;
      for (int i = 1; i < array.length; i++) {
      // 如果有元素和栈顶元素相等，应该消除栈顶元素（挡板左移），同时消除所有连续相等的元素
      // 如果stack是空的（end == -1） 或 栈顶元素和当前元素不相等， 直接加进stack（end++）
        if (end == -1 || array[i] != array[end]) {
          end++;
        }
        // 和栈顶相等，继续往后检查，把所有相等的元素和栈顶同时消除
        else {
          while (i + 1 < array.length && array[i] == array[i + 1]) {
          i++;
        }
        end--;
        }
      }
      return new String(array, 0, end + 1);
  }
}
```

TC:O(n) -> for loop
SC:O(n) -> toCharArray
