# All Subset I
Given a set of characters represented by a String, return a list containing all subsets of the characters.

Assumptions

There are no duplicate characters in the original set.

Examples

Set = "abc", all the subsets are [“”, “a”, “ab”, “abc”, “ac”, “b”, “bc”, “c”]     
Set = "", all the subsets are [""]      
Set = null, all the subsets are []      

```java
public class Solution {
    public List<String> subSets(String set) {
        // Write your solution here.
        List<String> res = new ArrayList<>();
        // 本题没有必要把String转化成Array 直接用 String.charAt(index) 即可
        // 要把这个 检测放在toCharArray前面 因为如果是null的话就不能toCharArray了
        if (set == null){
            return res;
        }        
        StringBuilder sb = new StringBuilder();
        char[] array = set.toCharArray();
        dfs(res, array, sb, 0);
        return res;
    }

    public void dfs(List<String> res, char[] array, StringBuilder sb, int index) {
        if (index == array.length){
            res.add(sb.toString());
            return;
        }
        sb.append(array[index]);
        // 为什么index++完去下一层index值不变呢？？？
        // 写成index + 1就可以
        // 因为index++ 是先传值在+所以错了
        // 然后写成 ++index 还是错的 -> 返回是之后index不退 index 也需要????
        // 找到原因了 因为++index 已经把index的值改变了 所以去从下一层退回来的时候需要 -1.
        dfs(res, array, sb, index + 1);
        sb.deleteCharAt(sb.length() - 1);

        dfs(res, array, sb, index + 1);
    }
}
```
