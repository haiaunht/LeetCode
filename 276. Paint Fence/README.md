# [276. Paint Fence (Medium)](https://leetcode.com/problems/paint-fence/)

<p>You are painting a fence of <code>n</code> posts with <code>k</code> different colors. You must paint the posts following these rules:</p>

<ul>
	<li>Every post must be painted <strong>exactly one</strong> color.</li>
	<li>There <strong>cannot</strong> be three or more <strong>consecutive</strong> posts with the same color.</li>
</ul>

<p>Given the two integers <code>n</code> and <code>k</code>, return <em>the <strong>number of ways</strong> you can paint the fence</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/28/paintfenceex1.png" style="width: 507px; height: 313px;">
<pre><strong>Input:</strong> n = 3, k = 2
<strong>Output:</strong> 6
<strong>Explanation: </strong>All the possibilities are shown.
Note that painting all the posts red or all the posts green is invalid because there cannot be three posts in a row with the same color.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1, k = 1
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 7, k = 2
<strong>Output:</strong> 42
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>1 &lt;= k &lt;= 10<sup>5</sup></code></li>
	<li>The testcases are generated such that the answer is in the range <code>[0, 2<sup>31</sup> - 1]</code> for the given <code>n</code> and <code>k</code>.</li>
</ul>

**Companies**:  
[JPMorgan](https://leetcode.com/company/jpmorgan)

**Related Topics**:  
[Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)

**Similar Questions**:

- [House Robber (Medium)](https://leetcode.com/problems/house-robber/)
- [House Robber II (Medium)](https://leetcode.com/problems/house-robber-ii/)
- [Paint House (Medium)](https://leetcode.com/problems/paint-house/)
- [Paint House II (Hard)](https://leetcode.com/problems/paint-house-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/paint-fence/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public int numWays(int n, int k) {
        int[] dp = new int[n+1];
        if (n==1) return k;
        if (n==2) return k*k;
        dp[1] = k;
        dp[2] = k*k;
        for (int i=3; i<dp.length; i++) {
            dp[i] = (k-1) * (dp[i-1] + dp[i-2]);
        }
        return dp[n];
    }
}

```
