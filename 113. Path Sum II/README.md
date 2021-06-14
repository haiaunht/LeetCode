# [113. Path Sum II (Medium)](https://leetcode.com/problems/path-sum-ii/)

<p>Given the <code>root</code> of a binary tree and an integer <code>targetSum</code>, return all <strong>root-to-leaf</strong> paths where each path's sum equals <code>targetSum</code>.</p>

<p>A <strong>leaf</strong> is a node with no children.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/18/pathsumii1.jpg" style="width: 500px; height: 356px;">
<pre><strong>Input:</strong> root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
<strong>Output:</strong> [[5,4,11,2],[5,8,4,5]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg" style="width: 212px; height: 181px;">
<pre><strong>Input:</strong> root = [1,2,3], targetSum = 5
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1,2], targetSum = 0
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 5000]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
	<li><code>-1000 &lt;= targetSum &lt;= 1000</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-first Search](https://leetcode.com/tag/depth-first-search/)

**Similar Questions**:

- [Path Sum (Easy)](https://leetcode.com/problems/path-sum/)
- [Binary Tree Paths (Easy)](https://leetcode.com/problems/binary-tree-paths/)
- [Path Sum III (Medium)](https://leetcode.com/problems/path-sum-iii/)
- [Path Sum IV (Medium)](https://leetcode.com/problems/path-sum-iv/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/path-sum-ii/
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
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        List<List<Integer>> results = new ArrayList<>();
        List<Integer> result = new ArrayList<>();
        helper(root, targetSum, result, results);
        return results;
    }
    private void helper(TreeNode root, int target, List<Integer> current, List<List<Integer>> results) {
        //base case
        if (root == null) return;
        current.add(root.val);
        //if I am at the leaf and found match target, add the current path to results and return for new path
        if (target == root.val && root.left == null && root.right == null) {
            results.add(current);
            return;
        }
        helper(root.left, target - root.val, new ArrayList<>(current), results);
        helper(root.right, target - root.val, new ArrayList<>(current), results);
    }
}

```
