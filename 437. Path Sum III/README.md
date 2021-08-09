# [437. Path Sum III (Medium)](https://leetcode.com/problems/path-sum-iii/)

<p>Given the <code>root</code> of a binary tree and an integer <code>targetSum</code>, return <em>the number of paths where the sum of the values&nbsp;along the path equals</em>&nbsp;<code>targetSum</code>.</p>

<p>The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/09/pathsum3-1-tree.jpg" style="width: 450px; height: 386px;">
<pre><strong>Input:</strong> root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8
<strong>Output:</strong> 3
<strong>Explanation:</strong> The paths that sum to 8 are shown.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 1000]</code>.</li>
	<li><code>-10<sup>9</sup> &lt;= Node.val &lt;= 10<sup>9</sup></code></li>
	<li><code>-1000 &lt;= targetSum &lt;= 1000</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Path Sum (Easy)](https://leetcode.com/problems/path-sum/)
- [Path Sum II (Medium)](https://leetcode.com/problems/path-sum-ii/)
- [Path Sum IV (Medium)](https://leetcode.com/problems/path-sum-iv/)
- [Longest Univalue Path (Medium)](https://leetcode.com/problems/longest-univalue-path/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/path-sum-iii/
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
    int count = 0;
    public int pathSum(TreeNode root, int targetSum) {
        List<Integer> path = new ArrayList<>();
        if (root==null) return 0;
        findPath(root, targetSum, path);
        return count;
    }
    private void findPath(TreeNode root, int targetSum, List<Integer> path) {
        if (root == null) return;
        int currentSum = 0;
        path.add(root.val);
        //go through the list from the newest element backward to see if we found the targetSum, if not, recursive
        for (int i=path.size()-1; i>=0; i--) {
            currentSum += path.get(i);
            if (currentSum == targetSum) {
                count++;
            }
        }
        findPath(root.left, targetSum, path);
        findPath(root.right, targetSum, path);
        //remove the last element to continue checking
        path.remove(path.size()-1);
    }
}

```
