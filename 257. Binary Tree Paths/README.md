# [257. Binary Tree Paths (Easy)](https://leetcode.com/problems/binary-tree-paths/)

<p>Given the <code>root</code> of a binary tree, return <em>all root-to-leaf paths in <strong>any order</strong></em>.</p>

<p>A <strong>leaf</strong> is a node with no children.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/paths-tree.jpg" style="width: 207px; height: 293px;">
<pre><strong>Input:</strong> root = [1,2,3,null,5]
<strong>Output:</strong> ["1-&gt;2-&gt;5","1-&gt;3"]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> ["1"]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-first Search](https://leetcode.com/tag/depth-first-search/)

**Similar Questions**:

- [Path Sum II (Medium)](https://leetcode.com/problems/path-sum-ii/)
- [Smallest String Starting From Leaf (Medium)](https://leetcode.com/problems/smallest-string-starting-from-leaf/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/binary-tree-paths/
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
    public List<String> binaryTreePaths(TreeNode root) {
       List<String> results = new ArrayList<>();
        if (root == null) {
            return results;
        }
        helper(root, "", results);
        return results;
    }
    private void helper(TreeNode root, String ret, List<String> results) {
        if (root != null) {
            ret += root.val;
            //base case if see the leaf node, done with the string, add to the list
            if (root.left == null && root.right == null) {
                results.add(ret);
            }
            ret += "->";
            helper(root.left, ret, results);
            helper(root.right, ret, results);
        }
    }
}

```
