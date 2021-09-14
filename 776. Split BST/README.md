# [776. Split BST (Medium)](https://leetcode.com/problems/split-bst/)

<p>Given the <code>root</code> of a binary search tree (BST) and an integer <code>target</code>, split the tree into two subtrees where one subtree has nodes that are all smaller or equal to the target value, while the other subtree has all nodes that are greater than the target value. It Is not necessarily the case that the tree contains a node with the value <code>target</code>.</p>

<p>Additionally, most of the structure of the original tree should remain. Formally, for any child <code>c</code> with parent <code>p</code> in the original tree, if they are both in the same subtree after the split, then node <code>c</code> should still have the parent <code>p</code>.</p>

<p>Return <em>an array of the two roots of the two subtrees</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/13/split-tree.jpg" style="width: 600px; height: 193px;">
<pre><strong>Input:</strong> root = [4,2,6,1,3,5,7], target = 2
<strong>Output:</strong> [[2,1],[4,3,6,null,null,5,7]]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1], target = 1
<strong>Output:</strong> [[1],[]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 50]</code>.</li>
	<li><code>0 &lt;= Node.val, target &lt;= 1000</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Recursion](https://leetcode.com/tag/recursion/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Delete Node in a BST (Medium)](https://leetcode.com/problems/delete-node-in-a-bst/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/split-bst/
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
    public TreeNode[] splitBST(TreeNode root, int target) {
        TreeNode[] result = new TreeNode[2];
        if (root == null) return result;
        //check if the node is <= target, then the that node is = result[0] and node.right = result[1] and node.right = null
        if (root.val == target) {
            result[0] = root;
            result[1] = root.right;
            root.right = null; //need to point right node to null
        }
        //if node.val > target -> need to go to the left
        else if (root.val > target) {
            //left[0] is the result[0] but left[1] need to be connect back to the root
            TreeNode[] left = splitBST(root.left, target);
            //assign root.left to the right of left
            root.left = left[1];
            //split left, the right will be the rest of root
            result[0] = left[0];
            result[1] = root;
        }
        else {
            TreeNode[] right = splitBST(root.right, target);
            //connect back to the root.right
            root.right = right[0];
            result[0] = root;
            result[1] = right[1];
        }
        return result;
    }
}

```
