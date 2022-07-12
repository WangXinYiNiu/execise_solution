# laicode80. Remove Adjacent Repeated Characters II

Remove adjacent, repeated characters in a given string, leaving only two characters for each group of such characters. The characters in the string are sorted in ascending order.

Assumptions

Try to do it in place.      

Examples    

“aaaabbbc” is transferred to “aabbc”
Corner Cases

If the given string is null, we do not need to do anything.

## Solution
```java
public class Solution {
  public String deDup(String input) {
    // Write your solution here
    // check how many times I meet this character.
    char[] array = input.toCharArray();
    int slow = 0;
    int fast = 0;
    while (fast < array.length) {
      Character c = array[fast];
      int count = 0;
      while (fast < array.length && array[fast] == c) {
        if (count < 2) {
          array[slow++] = array[fast]; 
        }
        fast++;
        count++;
      }
    }
    return new String (array, 0, slow);
  }
}
```
TC: O(n)
SC: O(n)
