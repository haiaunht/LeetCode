# [298. Binary Tree Longest Consecutive Sequence (Medium)](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/)

<p>Given the <code>root</code> of a binary tree, return <em>the length of the longest consecutive sequence path</em>.</p>

<p>The path refers to any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The longest consecutive path needs to be from parent to child (cannot be the reverse).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/consec1-1-tree.jpg" style="width: 322px; height: 421px;">
<pre><strong>Input:</strong> root = [1,null,3,2,4,null,null,null,5]
<strong>Output:</strong> 3
<strong>Explanation:</strong> Longest consecutive sequence path is 3-4-5, so return 3.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/consec1-2-tree.jpg" style="width: 262px; height: 421px;">
<pre><strong>Input:</strong> root = [2,null,3,2,null,1]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Longest consecutive sequence path is 2-3, not 3-2-1, so return 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 3 * 10<sup>4</sup>]</code>.</li>
	<li><code>-3 * 10<sup>4</sup> &lt;= Node.val &lt;= 3 * 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[ByteDance](https://leetcode.com/company/bytedance), [Facebook](https://leetcode.com/company/facebook), [Pinterest](https://leetcode.com/company/pinterest), [tiktok](https://leetcode.com/company/tiktok)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Longest Consecutive Sequence (Medium)](https://leetcode.com/problems/longest-consecutive-sequence/)
- [Binary Tree Longest Consecutive Sequence II (Medium)](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/
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
    private  int max = 0;
    public  int longestConsecutive(TreeNode root) {
        if (root == null) return 0;
        traverseBT(root, 0, root.val);
        return max;
    }
    public  void traverseBT(TreeNode node, int currentCount, int target) {
        if (node == null) return;
        if (node.val == target) currentCount++;
        else currentCount = 1;
        max = Math.max(max, currentCount);
        traverseBT(node.left, currentCount, node.val+1);
        traverseBT(node.right, currentCount, node.val+1);
    }
}
        if (node.val == target) currentCount++;

```
