# laicode649. String Replace (basic)

Given an original string input, and two strings S and T, from left to right replace all occurrences of S in input with T.       

Assumptions     
input, S and T are not null, S is not empty string      

Examples      
input = "appledogapple", S = "apple", T = "cat", input becomes "catdogcat"        
input = "laicode", S = "code", T = "offer", input becomes "laioffer"        

## Solution one
short -> long     
long -> short
```java
public class Solution {
  public String replace(String input, String s, String t) {
    // Write your solution here
    //Assumptions: input, s, t are not null, s is not empty.
        char[] array = input.toCharArray();
        if (s.length() >= t.length()) {
            return replaceShorter(array, s, t);
        }
        return replaceLonger(array, s, t); 
  }

    public String replaceShorter(char[] input, String s, String t) {
        //We reuse the input char array since the number of characters needed is less.
        //fast and slow pointers both from left to right direction.
        int slow = 0;
        int fast = 0;
        while (fast < input.length) {
            //When we find a match of s on the substring starting from the fast pointer.
            //We copy the t at slow pointer.
            if (fast <= input.length - s.length() && equalSubstring(input, fast, s)) { //fast <= 10 - 3
                copySubstring(input, slow, t);
                slow += t.length();
                fast += s.length();
            } else {
                input[slow++] = input[fast++];
            }

        }
        return new String(input, 0, slow);
    }

    public String replaceLonger(char[] input, String s, String t) {
        //Notice: we will need a longer array in the case, and if the requirement
        //is "in place", usually you can assume you are given a long enough
        //char array already, and the original input string resides
        //on part of the char array starting from index 0.
        //In this solution, we actually allocate a larger array on demand, and the
        //purpose of the solution is to demonstrate how to do it "in place".

        //get all the matches end positions in the input char array of string s.
        ArrayList<Integer> matches = getAllMatches(input, s);
        //calculate the new length needed.
        char[] result = new char[input.length + matches.size() * (t.length() - s.length())];
        //fast and slow pointer both from right to left direction.
        //low: the position when traversing the new length.
        //fast: the position when traversing the old length.
        //lastIndex: the rightmost matching end position's index.
        int lastIndex = matches.size() - 1;
        int fast = input.length - 1;
        int slow = result.length - 1;
        while (fast >= 0) {
            //only if we still have some match and slow is in the position of
            //rightmost matching end position, we should copy it.
            if (lastIndex >= 0 && fast == matches.get(lastIndex)) {
                copySubstring(result, slow - t.length() + 1, t);
                slow -= t.length();
                fast -= s.length();
                lastIndex--;
            } else {
                result[slow--] = input[fast--];
            }
        }
        return new String(result);
    }

    //check if the subString from fromIndex is the same as s.
    private boolean equalSubstring(char[] input, int fromIndex, String s) {
        for (int i = 0; i < s.length(); i++) {
            if (input[fromIndex + i] != s.charAt(i)) {
                return false;
            }
        }
        return true;
    }

    //copy the string t to result at fromIndex
    private void copySubstring(char[] result, int fromIndex, String t) {
        for (int i = 0; i < t.length(); i++) {
            result[i + fromIndex] = t.charAt(i);
        }
    }

    //get all the matches of s end positions in input.
    private ArrayList<Integer> getAllMatches(char[] input, String s) {
        ArrayList<Integer> matches = new ArrayList<>();
        int i = 0;
        while (i <= input.length - s.length()) {
            //we record the match substring's end index instead of start index.
            //for later convenience
            if (equalSubstring(input, i, s)) {
                matches.add(i + s.length() - 1);
                i += s.length();
            } else {
                i++;
            }
        }
        return matches;
    }
}
```
TC: O(n)      
SC: O(n)

## Solution 2:
Use StringBuilder
```java
public solution{
    public String replace(String input, String s, String t) {
        StringBuilder sb = new StringBuilder();
        int fromIndex = 0;
        // The indexOf() method returns the position of the first occurrence of specified character(s) in a string. 
        // Tip: Use the lastIndexOf method to return the position of the last occurrence of specified character(s) in a string.
        int matchIndex = input.indexOf(s, fromIndex);
        while (matchIndex != -1) {
            sb.append(input, fromIndex, matchIndex).append(t);
            fromIndex = matchIndex + s.length();
            matchIndex = input.indexOf(s, fromIndex);
        }
        // 这一步很关键
        // .length() 左闭右开 -> don't forget to append the remnant in original String.
        sb.append(input, fromIndex,input.length());
        return sb.toString();
    }
}
```
TC: O(n)      
SC: O(n)
