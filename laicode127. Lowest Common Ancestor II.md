Given two nodes in a binary tree (with parent pointer available), find their lowest common ancestor.

Assumptions
There is parent pointer for the nodes in the binary tree
The given two nodes are not guaranteed to be in the binary tree

Examples

         5
       /   \
      9     12
     /  \      \
    2    3      14

The lowest common ancestor of 2 and 14 is 5
The lowest common ancestor of 2 and 9 is 9
The lowest common ancestor of 2 and 8 is null (8 is not in the tree)

```java
public class TreeNodeP {
  public int key;
  public TreeNodeP left;
  public TreeNodeP right;
  public TreeNodeP parent;
  public TreeNodeP(int key, TreeNodeP parent) {
    this.key = key;
    this.parent = parent;
   }
}

public class Solution {
    public TreeNodeP lowestCommonAncestor(TreeNodeP one, TreeNodeP two) {
        // Write your solution here.
        // 先找到两个node的深度差 -- 然后深得node先走到和浅的node深度一致时，开始比较两个node，不相等同步往上走，相等返回任意一个

        int l1 = length(one);
        int l2 = length(two);
        //This is a small trick that can guarantee when calling mergeNode(), the first list is the shorter list, the second lis is the longer one.
        return l1 > l2 ? mergeNode(one, two, l1 - l2) : mergeNode(two, one, l2 - l1);
    }

    private TreeNodeP mergeNode(TreeNodeP shorter, TreeNodeP longer, int diff) {
        // 深的node先走到和浅的node的深度
        while (diff > 0) {
            shorter = shorter.parent;
            diff--;
        }
        // 然后同时出发，没找到就同步往上找，找到返回任意一个。
        while (shorter != longer) {
            shorter = shorter.parent;
            longer = longer.parent;
        }
        return shorter;
    }

    private int length(TreeNodeP node) {
        // 这个初始Depth想设为多少就是多少，不会影响结果。这里设为0，指root的深度为1。
        int Depth = 0;
        while (node != null) {
            node = node.parent;
            Depth++;
        }
        return Depth;
    }
}
```

//TC: O(n) -> 本来以为时间复杂度是O(log n),没考虑到不是binary tree而是一条链下来的话就得看整个node.
//SC: O(1)
