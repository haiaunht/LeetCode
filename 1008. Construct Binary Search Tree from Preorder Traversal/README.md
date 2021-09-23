# [1008. Construct Binary Search Tree from Preorder Traversal (Medium)](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/)

<p>Given an array of integers preorder, which represents the <strong>preorder traversal</strong> of a BST (i.e., <strong>binary search tree</strong>), construct the tree and return <em>its root</em>.</p>

<p>It is <strong>guaranteed</strong> that there is always possible to find a binary search tree with the given requirements for the given test cases.</p>

<p>A <strong>binary search tree</strong> is a binary tree where for every node, any descendant of <code>Node.left</code> has a value <strong>strictly less than</strong> <code>Node.val</code>, and any descendant of <code>Node.right</code> has a value <strong>strictly greater than</strong> <code>Node.val</code>.</p>

<p>A <strong>preorder traversal</strong> of a binary tree displays the value of the node first, then traverses <code>Node.left</code>, then traverses <code>Node.right</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/03/06/1266.png" style="height: 386px; width: 590px;">
<pre><strong>Input:</strong> preorder = [8,5,1,7,10,12]
<strong>Output:</strong> [8,5,10,1,7,null,12]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> preorder = [1,3]
<strong>Output:</strong> [1,null,3]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 100</code></li>
	<li><code>1 &lt;= preorder[i] &lt;= 10<sup>8</sup></code></li>
	<li>All the values of <code>preorder</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Expedia](https://leetcode.com/company/expedia)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Stack](https://leetcode.com/tag/stack/), [Tree](https://leetcode.com/tag/tree/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Monotonic Stack](https://leetcode.com/tag/monotonic-stack/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
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
    public static TreeNode bstFromPreorder (int[] preorder) {
        if (preorder.length == 0) return null;
        TreeNode root = new TreeNode(preorder[0]);
        //loop through each element and insert into bst
        for (int i=1; i<preorder.length; i++) {
          TreeNode node = new TreeNode(preorder[i]);
          insertToBST(node , root);
        }
        return root;
      }
      private static void insertToBST(TreeNode node, TreeNode root) {
        //if smaller value, check left node, if null -> replace node, else go down future left side
        if (node.val < root.val) {
          if (root.left == null) root.left = node;
          else {
            insertToBST(node, root.left);
          }
        } else {
          if (root.right == null) root.right = node;
          else {
            insertToBST(node, root.right);
          }
        }
      }
}

```
