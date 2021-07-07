# [637. Average of Levels in Binary Tree (Easy)](https://leetcode.com/problems/average-of-levels-in-binary-tree/)

Given the <code>root</code> of a binary tree, return <em>the average value of the nodes on each level in the form of an array</em>. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/09/avg1-tree.jpg" style="width: 277px; height: 302px;">
<pre><strong>Input:</strong> root = [3,9,20,null,15,7]
<strong>Output:</strong> [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/09/avg2-tree.jpg" style="width: 292px; height: 302px;">
<pre><strong>Input:</strong> root = [3,9,20,15,7]
<strong>Output:</strong> [3.00000,14.50000,11.00000]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-2<sup>31</sup> &lt;= Node.val &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:

- [Binary Tree Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-level-order-traversal/)
- [Binary Tree Level Order Traversal II (Medium)](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/average-of-levels-in-binary-tree/
// Author: Please set your name in options page
// Time: O()
// Space: O()
        traversal(root, 0, level);
        for (List<Integer> l : level) {
            result.add(getAvg(l));
        }
        return result;
    }
    private static void traversal(TreeNode root, int level, List<List<Integer>> list) {
        if (list.size() == level) {
            list.add(new ArrayList<>());
        }
        list.get(level).add(root.val);
        if (root.left != null) traversal(root.left, level+1, list);
        if (root.right != null) traversal(root.right, level+1, list);
    }
    private static Double getAvg(List<Integer> list) {
        int len = list.size();
        if (len == 0) return 0.0;
        Double sum = 0.0;
        for (Integer i:list) sum+=i;
        return sum * 1.0/len;
    }
}

```
