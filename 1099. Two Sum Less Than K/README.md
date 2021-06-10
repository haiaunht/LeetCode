# [1099. Two Sum Less Than K (Easy)](https://leetcode.com/problems/two-sum-less-than-k/)

<p>Given an array <code>nums</code> of integers and&nbsp;integer <code>k</code>, return the maximum <code>sum</code> such that there exists <code>i &lt; j</code> with <code>nums[i] + nums[j] = sum</code> and <code>sum &lt; k</code>. If no <code>i</code>, <code>j</code> exist satisfying this equation, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [34,23,1,24,75,33,54,8], k = 60
<strong>Output:</strong> 58
<strong>Explanation: </strong>We can use 34 and 24 to sum 58 which is less than 60.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [10,20,30], k = 15
<strong>Output:</strong> -1
<strong>Explanation: </strong>In this case it is not possible to get a pair sum less that 15.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= 2000</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Sort](https://leetcode.com/tag/sort/)

**Similar Questions**:

- [Two Sum (Easy)](https://leetcode.com/problems/two-sum/)
- [Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [3Sum Smaller (Medium)](https://leetcode.com/problems/3sum-smaller/)
- [Subarray Product Less Than K (Medium)](https://leetcode.com/problems/subarray-product-less-than-k/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/two-sum-less-than-k/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int twoSumLessThanK(int[] nums, int k) {
        int maxSum = Integer.MIN_VALUE;
        Arrays.sort(nums);
        int left = 0;
        int right = nums.length - 1;
        while (left < right) {
            if (nums[left] + nums[right] >= k) {
                right--;
            } else {
                maxSum = Math.max(maxSum, nums[left] + nums[right]);
                left++;
            }
        }
        if (maxSum == Integer.MIN_VALUE) return -1;
        return maxSum;
    }
}

```
