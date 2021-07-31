# [270. Closest Binary Search Tree Value (Easy)](https://leetcode.com/problems/closest-binary-search-tree-value/)

<p>Given the <code>root</code> of a binary search tree and a <code>target</code> value, return <em>the value in the BST that is closest to the</em> <code>target</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/closest1-1-tree.jpg" style="width: 292px; height: 302px;">
<pre><strong>Input:</strong> root = [4,2,5,1,3], target = 3.714286
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1], target = 4.428571
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Walmart Labs](https://leetcode.com/company/walmart-labs)

**Related Topics**:  
[Binary Search](https://leetcode.com/tag/binary-search/), [Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Count Complete Tree Nodes (Medium)](https://leetcode.com/problems/count-complete-tree-nodes/)
- [Closest Binary Search Tree Value II (Hard)](https://leetcode.com/problems/closest-binary-search-tree-value-ii/)
- [Search in a Binary Search Tree (Easy)](https://leetcode.com/problems/search-in-a-binary-search-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/closest-binary-search-tree-value/
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
    int result;
    double min = Double.MAX_VALUE;
    public int closestValue(TreeNode root, double target) {
        findClosest(root, target);
        return result;
    }
    private void findClosest(TreeNode root, double target) {
        if (root == null) return;
        //if found, asign result = root.val
        if (Math.abs(root.val - target) < min) {
            min = Math.abs(root.val - target);
            result = root.val;
        }
        //if target < root.val -> should move to the right to find the closet
        if (target < root.val) {
            findClosest(root.left, target);
        } else {
            findClosest(root.right, target);
        }
    }
}

```
