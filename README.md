# Cousins in Binary Tree
## https://leetcode.com/problems/cousins-in-binary-tree

In a binary tree, the root node is at depth 0, and children of each depth k node are at depth k+1.

Two nodes of a binary tree are cousins if they have the same depth, but have different parents.

We are given the root of a binary tree with unique values, and the values x and y of two different nodes in the tree.

Return true if and only if the nodes corresponding to the values x and y are cousins.


## Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
   Map<Integer, Integer> depth;
   Map<Integer, TreeNode> parent;

    public boolean isCousins(TreeNode root, int x, int y) {
        depth = new HashMap();
        parent = new HashMap();
        dfs(root, null);
        return (depth.get(x) == depth.get(y) && parent.get(x) != parent.get(y));
    }

    public void dfs(TreeNode node, TreeNode parentNode) {
        if (node != null) {
            depth.put(node.val, parentNode != null ? 1 + depth.get(parentNode.val) : 0);
            parent.put(node.val, parentNode);
            dfs(node.left, node);
            dfs(node.right, node);
        }
    }
}
```
