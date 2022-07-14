# laicode85. Determine If One String Is Another's Substring
Determine if a small string is a substring of another large string.   
  
Return the index of the first occurrence of the small string in the large string.   

Return -1 if the small string is not a substring of the large string.     

Assumptions     

Both large and small are not null
If small is empty string, return 0    

Examples      

“ab” is a substring of “bcabc”, return 2
“bcd” is not a substring of “bcabc”, return -1
"" is substring of "abc", return 0

## Solution
```java
public class Solution {
  public int strstr(String large, String small) {
    // Write your solution here
    if (large.equals(small)) {
      return 0;
    }
    for (int i = 0; i < large.length(); i++) {
      if (match(large, small, i)) {
        return i;
      }
    }
    return -1;
  }

  private boolean match (String large, String small, int start){
    for (int i = 0; i < small.length(); i++) {
      if (start > large.length() - 1 || large.charAt(start) != small.charAt(i)) {
        return false;
      }
      start++;
    }
    return true;
  }
}
```
TC: O(n)    
SC: O(1)    
