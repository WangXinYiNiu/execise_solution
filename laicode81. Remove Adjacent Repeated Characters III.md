# laicode81. Remove Adjacent Repeated Characters III

Remove adjacent, repeated characters in a given string, leaving no character for each group of such characters. The characters in the string are sorted in ascending order.

Assumptions
Try to do it in place.    

Examples    
“aaaabbbc” is transferred to “c”    
Corner Cases      
      
If the given string is null, we do not need to do anything.

```java
public class Solution {
  public String deDup(String input) {
    // Write your solution here
    char[] array = input.toCharArray();
    int slow = 0;
    int fast = 0;
    // 如果我加入的元素和我的栈顶相同，我就挡板左移动，且删除后面一样的
    while (fast < array.length) {
      if (fast > 0 && slow > 0 && array[fast] == array[slow - 1]) {
        slow--;
        Character c = array[fast];
        while (fast < array.length && array[fast] == c) {
          fast++;
        }
      } else {
        array[slow++] = array[fast++];
      }
    }
    // baaabbbc
    // s
    //        f
    return new String (array, 0, slow);
  }
}
```
