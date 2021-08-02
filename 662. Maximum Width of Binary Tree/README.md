# [662. Maximum Width of Binary Tree (Medium)](https://leetcode.com/problems/maximum-width-of-binary-tree/)

<p>Given the <code>root</code> of a binary tree, return <em>the <strong>maximum width</strong> of the given tree</em>.</p>

<p>The <strong>maximum width</strong> of a tree is the maximum <strong>width</strong> among all levels.</p>

<p>The <strong>width</strong> of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes are also counted into the length calculation.</p>

<p>It is <strong>guaranteed</strong> that the answer will in the range of <strong>32-bit</strong> signed integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/width1-tree.jpg" style="width: 359px; height: 302px;">
<pre><strong>Input:</strong> root = [1,3,2,5,3,null,9]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The maximum width existing in the third level with the length 4 (5,3,null,9).
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/width2-tree.jpg" style="width: 224px; height: 302px;">
<pre><strong>Input:</strong> root = [1,3,null,5,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The maximum width existing in the third level with the length 2 (5,3).
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/width3-tree.jpg" style="width: 289px; height: 299px;">
<pre><strong>Input:</strong> root = [1,3,2,5]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The maximum width existing in the second level with the length 2 (3,2).
</pre>

<p><strong>Example 4:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/width4-tree.jpg" style="width: 500px; height: 244px;">
<pre><strong>Input:</strong> root = [1,3,2,5,null,null,9,6,null,null,7]
<strong>Output:</strong> 8
<strong>Explanation:</strong> The maximum width existing in the fourth level with the length 8 (6,null,null,null,null,null,null,7).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 3000]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>

**Companies**:  
[Apple](https://leetcode.com/company/apple), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-width-of-binary-tree/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class NodeLevelIndex {
    TreeNode node;
    Integer index;
    NodeLevelIndex(TreeNode node, Integer index) {
        this.node = node;
        this.index = index;
    }
    public int getLevelIndex() {
        return this.index;
    }
    public TreeNode getNode() {
        return this.node;
    }
}
class Solution {
    public int widthOfBinaryTree(TreeNode root) {
        if (root == null) return 0;
        int maxWidth = 0;
        //use LinkedList to use .peekFirst() and peekLast()
        LinkedList<NodeLevelIndex> queue = new LinkedList<>(); 
        queue.add(new NodeLevelIndex(root, 0));
        //now loop from the root to add its children from left and right
        while (!queue.isEmpty()) {
            int size = queue.size();
            maxWidth = Math.max(maxWidth, (queue.peekLast().getLevelIndex() - queue.peekFirst().getLevelIndex()) + 1);
            for (int i=0; i<size; i++) {
                NodeLevelIndex parent = queue.poll();
                if (parent.getNode().left != null) {
                    queue.add(new NodeLevelIndex(parent.getNode().left, parent.getLevelIndex()*2));
                }
                if (parent.getNode().right != null) {
                    queue.add(new NodeLevelIndex(parent.getNode().right, parent.getLevelIndex()*2 + 1));
                }
            }
        }
        return maxWidth;
    }
}

```
