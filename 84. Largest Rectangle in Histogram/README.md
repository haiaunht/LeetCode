# [84. Largest Rectangle in Histogram (Hard)](https://leetcode.com/problems/largest-rectangle-in-histogram/)

<p>Given an array of integers <code>heights</code> representing the histogram's bar height where the width of each bar is <code>1</code>, return <em>the area of the largest rectangle in the histogram</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg" style="width: 522px; height: 242px;">
<pre><strong>Input:</strong> heights = [2,1,5,6,2,3]
<strong>Output:</strong> 10
<strong>Explanation:</strong> The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg" style="width: 202px; height: 362px;">
<pre><strong>Input:</strong> heights = [2,4]
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= heights.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= heights[i] &lt;= 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [eBay](https://leetcode.com/company/ebay)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Stack](https://leetcode.com/tag/stack/), [Monotonic Stack](https://leetcode.com/tag/monotonic-stack/)

**Similar Questions**:

- [Maximal Rectangle (Hard)](https://leetcode.com/problems/maximal-rectangle/)
- [Maximum Score of a Good Subarray (Hard)](https://leetcode.com/problems/maximum-score-of-a-good-subarray/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/largest-rectangle-in-histogram/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public int largestRectangleArea(int[] heights) {
        //use a stack to push a next height[i] > height[i-1], else calculate max
        Stack<Integer> stack = new Stack();
        stack.push(-1);
        int maxRectArea = 0;
        for (int i=0; i<=heights.length; i++) {
            //if the stack is not contain only -1 and the current height <= height[stack.peek()] -> calucalte
            int current = (i==heights.length) ? 0 : heights[i];
            while (stack.peek() != -1 && current <= heights[stack.peek()]) {
                int rightMinIndex = i;
                int h = heights[stack.pop()];
                int leftMinIndex = stack.peek();
                maxRectArea = Math.max(maxRectArea, h * (rightMinIndex - leftMinIndex - 1));
            }
            stack.push(i);
        }
        return maxRectArea;
    }
}

```
