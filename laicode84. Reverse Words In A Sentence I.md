# laicode84. Reverse Words In A Sentence I
Reverse the words in a sentence.

Assumptions   

Words are separated by single space   

There are no heading or tailing white spaces      

Examples      

“I love Google” → “Google love I”     

Corner Cases      
  
If the given string is null, we do not need to do anything.     

```java
public class Solution {
  public String reverseWords(String input) {
    // Write your solution here
    char[] array = input.toCharArray();
    // 上来先整个反转一下，然后再逐个反转每个单词
    reverse(array,0,array.length - 1);
    int i = 0;
    for (int j = 0;j < array.length;j++) {
      // j一直走，直到遇到空格(此时的j)把i到j-1反转，然后更新i到下一个单词的首位(j+1)准备反转下一个单词
      if (array[j] == ' ') {
        reverse(array,i,j - 1);
        i = j+1;
      }
      if (j == array.length - 1) { // 当j走到最后，把i到j反转
        reverse(array,i,j);
      }
    }
    return new String(array);
  }
  public void reverse(char[] array,int left,int right) {
    while (left < right) {
      swap(array,left++,right--);
    }
  }
  public void swap(char[] array,int x,int y) {
    char temp = array[x];
    array[x] = array[y];
    array[y] = temp;
  }
}
```

// TC: O(n)
// SC: O(n) -> toCharArray()
