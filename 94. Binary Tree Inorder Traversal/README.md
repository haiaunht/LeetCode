# [94. Binary Tree Inorder Traversal (Easy)](https://leetcode.com/problems/binary-tree-inorder-traversal/)

<p>Given the <code>root</code> of a binary tree, return <em>the inorder traversal of its nodes' values</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg" style="width: 202px; height: 324px;">
<pre><strong>Input:</strong> root = [1,null,2,3]
<strong>Output:</strong> [1,3,2]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 4:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/15/inorder_5.jpg" style="width: 202px; height: 202px;">
<pre><strong>Input:</strong> root = [1,2]
<strong>Output:</strong> [2,1]
</pre>

<p><strong>Example 5:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/15/inorder_4.jpg" style="width: 202px; height: 202px;">
<pre><strong>Input:</strong> root = [1,null,2]
<strong>Output:</strong> [1,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Goldman Sachs](https://leetcode.com/company/goldman-sachs)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Stack](https://leetcode.com/tag/stack/), [Tree](https://leetcode.com/tag/tree/)

**Similar Questions**:

- [Validate Binary Search Tree (Medium)](https://leetcode.com/problems/validate-binary-search-tree/)
- [Binary Tree Preorder Traversal (Easy)](https://leetcode.com/problems/binary-tree-preorder-traversal/)
- [Binary Tree Postorder Traversal (Easy)](https://leetcode.com/problems/binary-tree-postorder-traversal/)
- [Binary Search Tree Iterator (Medium)](https://leetcode.com/problems/binary-search-tree-iterator/)
- [Kth Smallest Element in a BST (Medium)](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
- [Closest Binary Search Tree Value II (Hard)](https://leetcode.com/problems/closest-binary-search-tree-value-ii/)
- [Inorder Successor in BST (Medium)](https://leetcode.com/problems/inorder-successor-in-bst/)
- [Convert Binary Search Tree to Sorted Doubly Linked List (Medium)](https://leetcode.com/problems/convert-binary-search-tree-to-sorted-doubly-linked-list/)
- [Minimum Distance Between BST Nodes (Easy)](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/binary-tree-inorder-traversal/
// Author: Please set your name in options page
// Time: O()
// Space: O()
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        inorderTraversal(root, result);
        return result;
    }
    private void inorderTraversal(TreeNode root, List<Integer> result) {
        if (root != null) {
             if (root.left != null) {
                inorderTraversal(root.left, result);
            }
            result.add(root.val);
            if (root.right != null) {
                inorderTraversal(root.right, result);
            }
        }
    }
}

```
