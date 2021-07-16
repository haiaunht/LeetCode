# [1022. Sum of Root To Leaf Binary Numbers (Easy)](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)

<p>You are given the <code>root</code> of a binary tree where each node has a value <code>0</code>&nbsp;or <code>1</code>.&nbsp; Each root-to-leaf path represents a binary number starting with the most significant bit.&nbsp; For example, if the path is <code>0 -&gt; 1 -&gt; 1 -&gt; 0 -&gt; 1</code>, then this could represent <code>01101</code> in binary, which is <code>13</code>.</p>

<p>For all leaves in the tree, consider the numbers represented by the path&nbsp;from the root to that leaf.</p>

<p>Return <em>the sum of these numbers</em>. The answer is <strong>guaranteed</strong> to fit in a <strong>32-bits</strong> integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/04/04/sum-of-root-to-leaf-binary-numbers.png" style="width: 450px; height: 296px;">
<pre><strong>Input:</strong> root = [1,0,1,0,1,0,1]
<strong>Output:</strong> 22
<strong>Explanation: </strong>(100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [0]
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> root = [1,1]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 1000]</code>.</li>
	<li><code>Node.val</code> is <code>0</code> or <code>1</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/
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
    private int sum;
    public int sumRootToLeaf(TreeNode root) {
        sum = 0;
        dfs(root, 0);
        return sum;
    }
    private void dfs(TreeNode root, int valPath) {
        if (root == null) return;
        //from left to right, valPath start value = 0, 100 = (((0*2+1) * 2) + 0) * 2 + 0
        valPath *= 2;
        valPath += root.val;
        if (root.left == null && root.right == null) sum += valPath;
        dfs(root.left, valPath);
        dfs(root.right, valPath);
    }
}

```
