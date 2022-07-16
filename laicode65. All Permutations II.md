# laicode65. All Permutations II
Given a string with possible duplicate characters, return a list with all permutations of the characters.       

Examples          

Set = “abc”, all permutations are [“abc”, “acb”, “bac”, “bca”, “cab”, “cba”]      
Set = "aba", all permutations are ["aab", "aba", "baa"]     
Set = "", all permutations are [""]       
Set = null, all permutations are []     

## Bad Version
```java
public Solution{
    public List<String> permutations(String input) {
        // Write your solution here
        // HighLevel: 如果我这个Character被换到index的位置时，在本层遇到同样的就不用在换了。
        // 一层确定一个index的元素
        char[] array = input.toCharArray();
        Arrays.sort(array);
        List<String> res = new ArrayList<>();
        permutations(res, array, 0);
        return res;
    }

    //方法的重载和访问修饰符以及返回值类型无关。
    public void permutations(List<String> res, char[] array, int index) {
        if (index == array.length) {
            res.add(new String(array));
            return;
        }
        for (int i = index; i < array.length; i++) {
            // 当我和我的下一个不一样的时候我就换 或者 我是最后一个 我也被换
            if (i == array.length - 1 || array[i] != array[i + 1]) {
                swap(array, i, index);
                permutations(res, array, index + 1);
                swap(array, i, index);
            }
        }
    }

    private void swap (char[] array, int i, int j) {
        Character c = array[i];
        array[i] = array[j];
        array[j] = c;
        return;
    }
  /* 时间复杂度: 总共有n层(n = input.length)
                第一层分 n 个branches
                第二层分 n - 1 个branched
                ...
                O(n! + nlogn) n! -> Rercursion, nlogn -> sort
     空间复杂度: charArray -> n

  */
}
```
**但是上述想法是错误的，不能先sort, 因为sort后只能保证第一层是OK的，后面顺序就都变了**
```
                           aabc
                   /        |          \
                 a|abc    b|aac       c|aba
                                     /   |   \
                                 ca|ba  ca|ba  ca|ba
                                 发生重复了，因为顺序变了
```

## Solution









