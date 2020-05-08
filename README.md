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
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    Map<Integer,Integer> parentMap = new HashMap<>();
    Map<Integer,Integer> depthMap = new HashMap<>();
    
    public boolean isCousins(TreeNode root, int x, int y) {
        if(root == null)
            return false;
        dfs(root, null, 0);
        return (parentMap.get(x) != parentMap.get(y)) && (depthMap.get(x) == depthMap.get(y));
    }
    
    private void dfs(TreeNode node, TreeNode parent, int depth) {
        parentMap.put(node.val, parent == null ? null : parent.val);
        depthMap.put(node.val, depth);
        if(node.left != null)
            dfs(node.left, node, depth+1);
        if(node.right != null)
            dfs(node.right, node, depth+1);
    }
}
```
