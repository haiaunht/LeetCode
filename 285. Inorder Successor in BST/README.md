# [285. Inorder Successor in BST (Medium)](https://leetcode.com/problems/inorder-successor-in-bst/)

<p>Given the <code>root</code> of a binary search tree and a node <code>p</code> in it, return <em>the in-order successor of that node in the BST</em>. If the given node has no in-order successor in the tree, return <code>null</code>.</p>

<p>The successor of a node <code>p</code> is the node with the smallest key greater than <code>p.val</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/23/285_example_1.PNG" style="width: 122px; height: 117px;">
<pre><strong>Input:</strong> root = [2,1,3], p = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong> 1's in-order successor node is 2. Note that both p and the return value is of TreeNode type.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/23/285_example_2.PNG" style="width: 246px; height: 229px;">
<pre><strong>Input:</strong> root = [5,3,6,2,4,null,null,1], p = 6
<strong>Output:</strong> null
<strong>Explanation:</strong> There is no in-order successor of the current node, so the answer is <code>null</code>.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li>All Nodes will have unique values.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Binary Tree Inorder Traversal (Easy)](https://leetcode.com/problems/binary-tree-inorder-traversal/)
- [Binary Search Tree Iterator (Medium)](https://leetcode.com/problems/binary-search-tree-iterator/)
- [Inorder Successor in BST II (Medium)](https://leetcode.com/problems/inorder-successor-in-bst-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/inorder-successor-in-bst/
// Author: Please set your name in options page
// Time: O()
// Space: O()
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
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        //successor of a node p must be smallest,
        TreeNode inOrderSucc = null;
        while (root != null) {
            if (root.val <= p.val) { //node p on the right child, continue
                root = root.right;
            } else {
                inOrderSucc = root;
                root = root.left;
            }
        }
        return inOrderSucc;
    }
}

```
