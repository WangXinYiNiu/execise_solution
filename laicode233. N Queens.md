Get all valid ways of putting N Queens on an N * N chessboard so that no two Queens threaten each other.
  
Assumptions                
N > 0     

Return      
A list of ways of putting the N Queens    
Each way is represented by a list of the Queen's y index for x indices of 0 to (N - 1)        

Example       
N = 4, there are two ways of putting 4 queens:    
[1, 3, 0, 2] --> the Queen on the first row is at y index 1, the Queen on the second row is at y index 3, the Queen on the third row is at y index 0 and the Queen on the fourth row is at y index 2.       
[2, 0, 3, 1] --> the Queen on the first row is at y index 2, the Queen on the second row is at y index 0, the Queen on the third row is at y index 3 and the Queen on the fourth row is at y index 1.       

## Solution
```java
public class Solution {
    public List<List<Integer>> nqueens(int n) {
        // Write your solution here
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> cur = new ArrayList<>();
        nqueens(res, cur, 0, n);
        return res;
    }

    public void nqueens(List<List<Integer>> res, List<Integer> cur, int row, int n) {
        // base case
        // if the last row element been valid filled.	We add to result.
        //if (row == n) {
        if (row == n) {
            res.add(new ArrayList<>(cur));
            return;
            // Don't forget to return.
        }
        // recursion rule
        // if this position be filled valid, we go to next layer which means next row. to put element.
        // i: the postion which I need to push in current layer.
        for (int i = 0; i < n; i++) {
            if (valid(cur, row, i)) {
                // add
                cur.add(i);
                nqueens(res, cur, row + 1, n);
                // delete
                // delete a element from list need to use remove
                cur.remove(cur.size() - 1);
            }
        }
    }

    private boolean valid(List<Integer> cur, int row, int column) {
        // emanate this postion to its up. If there is element on it. return false;
        for (int i = 0; i < cur.size(); i++) {
            // 本种写法是错误的。因为如果 Math.abs((column - cur.get(i)) / (row - i) == 1.5
            // 会被向下去整到1 从而错过正确答案
/*            if (cur.get(i) == column || Math.abs((column - cur.get(i)) / (row - i)) == 1) {
                return false;
            }*/
            if (cur.get(i) == column || Math.abs(cur.get(i) - column) == row - i) {
                return false;
            }
        }
        return true;
    }
}
```

TC: Recursion tree 每一层分n个branches, 总共分n层 -> n^n 但是因为每一层其实建枝了 所以就是 n! (ps: 如果用了StringBuilder 最后 sb.toString()需要n 所以就是 n^n * n)
SC: recursion 在 stack上是 O(n), heap 上因为是结果要返回的数据，所以没有。

