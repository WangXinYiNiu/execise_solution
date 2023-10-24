# laicode46. Check If Binary Tree Is Balanced
Check if a given binary tree is balanced. A balanced binary tree is one in which the depths of every node’s left and right subtree differ by at most 1.

```
Examples
        5
      /   \
    3       8
  /   \       \
1      4       11

is a balanced binary tree,

        5

      /

    3

  /   \

1      4

is not a balanced binary tree.

Corner Cases

What if the binary tree is null? Return true in this case.
```

```java
public class Solution {
  public boolean isBalanced(TreeNode root) {
    // Write your solution here
    if (root == null) {
      return true;
    }
    // 先判断高度差，不满足就不用递归判断左右子树了
    if (Math.abs(findHeight(root.left) - findHeight(root.right)) > 1) {
      return false;
    }
    return isBalanced(root.left) && isBalanced(root.right);
  }
  public int findHeight(TreeNode root) {
    if (root == null) {
      return 0;
    }
    return Math.max(findHeight(root.left),findHeight(root.right)) + 1;
  }
}
```
