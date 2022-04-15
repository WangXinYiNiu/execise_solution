![汉诺塔问题](https://raw.githubusercontent.com/WangXinYiNiu/execise_solution/main/image/hanota.png?token=GHSAT0AAAAAABTGBTGE75TUOU7267ENUMMMYSYUPQA)

```java
public class Solution {
    public static void helper(int n, char a, char b, char c) {
        if (n == 1) {
            System.out.println(a + "->" + c);
        } else {
            helper(n - 1, a, c, b);
            System.out.println(a + "->" + c);
            helper(n - 1, b, a, c);
        }
    }

    public static void main(String[] args) {
        char a = 'a';
        char b = 'b';
        char c = 'c';
        Solution solution = new Solution();
        solution.helper(3, a, b,c);
    }
}
```
