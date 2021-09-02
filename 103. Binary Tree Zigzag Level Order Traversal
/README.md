# [103. Binary Tree Zigzag Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

<p>Given the <code>root</code> of a binary tree, return <em>the zigzag level order traversal of its nodes' values</em>. (i.e., from left to right, then right to left for the next level and alternate between).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg" style="width: 277px; height: 302px;">
<pre><strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> [[3],[20,9],[15,7]]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> [[1]]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 2000]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [eBay](https://leetcode.com/company/ebay), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [ByteDance](https://leetcode.com/company/bytedance), [Bloomberg](https://leetcode.com/company/bloomberg), [LinkedIn](https://leetcode.com/company/linkedin), [ServiceNow](https://leetcode.com/company/servicenow)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Binary Tree Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-level-order-traversal/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/
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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;
        int level = 0;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> currentLevel = new ArrayList<>();
            for (int i=0; i<size; i++) {
                TreeNode curr = queue.remove();
                currentLevel.add(curr.val);
                if (curr.left != null) queue.add(curr.left);
                if (curr.right != null) queue.add(curr.right);
            }
            //start from node is from left to right, level 1 from right to left and so on, so odd level is right -> left
            if (level % 2 != 0) {
                Collections.reverse(currentLevel);
                result.add(currentLevel);
            } else {
                result.add(currentLevel);
            }
            level++;
        }
        return result;
    }
}

```
