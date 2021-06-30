# [1120. Maximum Average Subtree (Medium)](https://leetcode.com/problems/maximum-average-subtree/)

<p>Given the <code>root</code> of a binary tree, find the maximum average value of any subtree of that tree.</p>

<p>(A subtree of a tree is any node of that tree plus all its descendants. The average value of a tree is the sum of its values, divided by the number of nodes.)</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/04/09/1308_example_1.png" style="width: 132px; height: 123px;"></p>

<pre><strong>Input: </strong><span id="example-input-1-1">[5,6,1]</span>
<strong>Output: </strong><span id="example-output-1">6.00000</span>
<strong>Explanation: </strong>
For the node with value = 5 we have an average of (5 + 6 + 1) / 3 = 4.
For the node with value = 6 we have an average of 6 / 1 = 6.
For the node with value = 1 we have an average of 1 / 1 = 1.
So the answer is 6 which is the maximum.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>The number of nodes in the tree is between <code>1</code> and <code>5000</code>.</li>
	<li>Each node will have a value between <code>0</code> and <code>100000</code>.</li>
	<li>Answers will be accepted as correct if they are within <code>10^-5</code> of the correct answer.</li>
</ol>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-average-subtree/
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
    static double max;
    public double maximumAverageSubtree(TreeNode root) {
        max = 0.0;
        avgNode(root);
        return max;
    }
    private static int[] avgNode(TreeNode node) {
        int count = 1;
        if (node == null) return new int[]{0,0};
        int currentSum = node.val;
        //get the array of sum, count of left and right nodes
        int[] left = avgNode(node.left);
        int[] right = avgNode(node.right);
        //calculate sum by adding first element of two arrays
        currentSum += left[0] + right[0];
        count += left[1] + right[1];
        max = Math.max(max, currentSum * 1.0/ count);
        return new int[]{currentSum, count};
    }
}
        }

```
