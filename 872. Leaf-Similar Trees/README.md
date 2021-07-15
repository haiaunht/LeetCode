# [872. Leaf-Similar Trees (Easy)](https://leetcode.com/problems/leaf-similar-trees/)

<p>Consider all the leaves of a binary tree, from&nbsp;left to right order, the values of those&nbsp;leaves form a <strong>leaf value sequence</strong><em>.</em></p>

<p><img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/16/tree.png" style="width: 400px; height: 336px;"></p>

<p>For example, in the given tree above, the leaf value sequence is <code>(6, 7, 4, 9, 8)</code>.</p>

<p>Two binary trees are considered <em>leaf-similar</em>&nbsp;if their leaf value sequence is the same.</p>

<p>Return <code>true</code> if and only if the two given trees with head nodes <code>root1</code> and <code>root2</code> are leaf-similar.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/03/leaf-similar-1.jpg" style="width: 750px; height: 297px;">
<pre><strong>Input:</strong> root1 = [3,5,1,6,2,9,8,null,null,7,4], root2 = [3,5,1,6,7,4,2,null,null,null,null,null,null,9,8]
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root1 = [1], root2 = [1]
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root1 = [1], root2 = [2]
<strong>Output:</strong> false
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> root1 = [1,2], root2 = [2,2]
<strong>Output:</strong> true
</pre>

<p><strong>Example 5:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/03/leaf-similar-2.jpg" style="width: 450px; height: 165px;">
<pre><strong>Input:</strong> root1 = [1,2,3], root2 = [1,3,2]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in each tree will be in the range <code>[1, 200]</code>.</li>
	<li>Both of the given trees will have values in the range <code>[0, 200]</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```java

// OJ: https://leetcode.com/problems/leaf-similar-trees/
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
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> l1 = new ArrayList<>();
        List<Integer> l2 = new ArrayList<>();
        //iterate each node and store all the leaves
        countLeaf(root1, l1);
        countLeaf(root2, l2);
        return l1.equals(l2);
    }
    private static void countLeaf(TreeNode root, List<Integer> list) {
        if (root == null) return;
        if (root.left == null && root.right == null) list.add(root.val);
        countLeaf(root.left, list);
        countLeaf(root.right, list);
    }
}

```
