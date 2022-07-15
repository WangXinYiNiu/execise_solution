# laicode397. Right Shift By N Characters

Right shift a given string by n characters.

Assumptions       
The given string is not null.       
n >= 0.       

Examples        
"abc", 4 -> "cab"       

## Solution 1
```java
public class Solution {
  public String rightShift(String input, int n) {
    // Write your solution here
    if (input == null || input.length() == 0) {
      return input;
    }
    n = n % input.length();
    StringBuilder sb = new StringBuilder();
    for(int i = input.length() - n; i < input.length(); i++) {
      sb.append(input.charAt(i));
    }
    for (int i = 0; i < input.length() - n; i++) {
      sb.append(input.charAt(i));
    }
    return sb.toString();    
  }
  // TC: O(n)
  // SC: O(n)
}
```

## Solution 2
**I love Yahoo** Trick
```java
public class Solution {
  public String rightShift(String input, int n) {
    // Write your solution here
    // I Love Yahoo Trick
    // reverse index length - n to index length - 1
    // reverse index 0 to length - n - 1
    if (input == null || input.length() == 0){
      return input;
    }
    n = n % input.length();
    // 反转的时候一定要过个例子去反转，要不很容易索引搞错
    // abc de -> 2 -> de abc
    // cba ed
    // deabc
    char[] array = input.toCharArray();
    array = reverse(array, 0, array.length - 1 - n);
    array = reverse(array, array.length - n, array.length - 1);    
    array = reverse(array, 0, array.length - 1);
    return new String(array);
  }

  private char[] reverse (char[] array, int i, int j) {
    while (i < j) {
      Character c = array[i];
      array[i] = array[j];
      array[j] = c;
      i++;
      j--;
    }
    return array;
  }
}
// TC: O(n)
// SC: O(n)
```
