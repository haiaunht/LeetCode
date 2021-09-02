# [213. House Robber II (Medium)](https://leetcode.com/problems/house-robber-ii/)

<p>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are <strong>arranged in a circle.</strong> That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and&nbsp;<b>it will automatically contact the police if two adjacent houses were broken into on the same night</b>.</p>

<p>Given an integer array <code>nums</code> representing the amount of money of each house, return <em>the maximum amount of money you can rob tonight <strong>without alerting the police</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [2,3,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

**Companies**:  
[eBay](https://leetcode.com/company/ebay), [Microsoft](https://leetcode.com/company/microsoft), [Qualtrics](https://leetcode.com/company/qualtrics)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)

**Similar Questions**:

- [House Robber (Medium)](https://leetcode.com/problems/house-robber/)
- [Paint House (Medium)](https://leetcode.com/problems/paint-house/)
- [Paint Fence (Medium)](https://leetcode.com/problems/paint-fence/)
- [House Robber III (Medium)](https://leetcode.com/problems/house-robber-iii/)
- [Non-negative Integers without Consecutive Ones (Hard)](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/)
- [Coin Path (Hard)](https://leetcode.com/problems/coin-path/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/house-robber-ii/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) return nums[0];
        if (nums.length == 2) return Math.max(nums[0], nums[1]);
        int option_1 = robFrom(0, nums.length-2, nums); //rob from 0 and skip last house at index=length-2
        int option_2 = robFrom(1, nums.length-1, nums); //rob from house 1 till last house, which mean skip first house
        return Math.max(option_1, option_2);
    }
    public int robFrom(int start, int end, int[] nums) {
        int[] dp = new int[nums.length + 1];
        //make house from end+1 -> last index = 0
        for (int i=end+1; i<dp.length; i++) {
            dp[i] = 0;
        }
        //get dp[end] = nums[end]
        dp[end]  = nums[end];
        for (int i=end-1; i>=0; i--) {
            dp[i] = Math.max(dp[i+1], dp[i+2]+nums[i]);
        }
        return dp[start];
    }
}

```
