# laicode48. Symmetric Binary Tree
Check if a given binary tree is symmetric.

```
Examples

        5

      /    \

    3        3

  /   \    /   \

1      4  4      1

is symmetric.

        5

      /    \

    3        3

  /   \    /   \

1      4  1      4

is not symmetric.
```

```java
public class Solution {

  public boolean isSymmetric(TreeNode root) {
    // Write your solution here
    // high-level: if root.left 和 root.right是symmetric的话 -> root这个tree是symmetric的
    // check root.left.left 和 root.right.right if symmetric 且...
    if(root == null){
      return true;
    }
    return isSymmetric(root.left, root.right);
  }

  public boolean isSymmetric(TreeNode left, TreeNode right){
    if(left == null && right == null){
      return true;
    }
    if(left == null || right == null){
      return false;
    }
    if(left.key != right.key){
      return false;
    }
    return isSymmetric(left.left, right.right) && isSymmetric(left.right, right.left);
  }
}
```
