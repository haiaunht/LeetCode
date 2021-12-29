# [199. Binary Tree Right Side View (Medium)](https://leetcode.com/problems/binary-tree-right-side-view/)

<p>Given the <code>root</code> of a binary tree, imagine yourself standing on the <strong>right side</strong> of it, return <em>the values of the nodes you can see ordered from top to bottom</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/14/tree.jpg" style="width: 401px; height: 301px;">
<pre><strong>Input:</strong> root = [1,2,3,null,5,null,4]
<strong>Output:</strong> [1,3,4]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1,null,3]
<strong>Output:</strong> [1,3]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Amazon](https://leetcode.com/company/amazon), [ByteDance](https://leetcode.com/company/bytedance), [Oracle](https://leetcode.com/company/oracle), [Qualtrics](https://leetcode.com/company/qualtrics), [Adobe](https://leetcode.com/company/adobe), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [FactSet](https://leetcode.com/company/factset)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Populating Next Right Pointers in Each Node (Medium)](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
- [Boundary of Binary Tree (Medium)](https://leetcode.com/problems/boundary-of-binary-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/binary-tree-right-side-view/
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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> rightSideNodes = new ArrayList<>();
        if (root == null) return rightSideNodes;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            for (int i=0; i<levelSize; i++) {
                TreeNode curr = queue.poll();
                //now add only the last node of the level
                if (i == levelSize-1) {
                    rightSideNodes.add(curr.val);
                }
                if (curr.left != null) queue.add(curr.left);
                if (curr.right != null) queue.add(curr.right);
            }
        }
        return rightSideNodes;
    }
}

```
