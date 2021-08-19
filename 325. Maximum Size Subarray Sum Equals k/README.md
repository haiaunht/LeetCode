# [325. Maximum Size Subarray Sum Equals k (Medium)](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)

<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the maximum length of a subarray that sums to</em> <code>k</code>. If there isn't one, return <code>0</code> instead.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,-1,5,-2,3], k = 3
<strong>Output:</strong> 4
<strong>Explanation:</strong> The subarray [1, -1, 5, -2] sums to 3 and is the longest.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [-2,-1,2,1], k = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong> The subarray [-1, 2] sums to 1 and is the longest.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup>&nbsp;&lt;= k &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:

- [Minimum Size Subarray Sum (Medium)](https://leetcode.com/problems/minimum-size-subarray-sum/)
- [Range Sum Query - Immutable (Easy)](https://leetcode.com/problems/range-sum-query-immutable/)
- [Contiguous Array (Medium)](https://leetcode.com/problems/contiguous-array/)
- [Subarray Product Less Than K (Medium)](https://leetcode.com/problems/subarray-product-less-than-k/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int maxSubArrayLen(int[] nums, int k) {
       int currSum = 0;
        int max = 0;
        Map<Integer, Integer> prefixSum = new HashMap<>();
        for (int i=0; i<nums.length; i++) {
            currSum += nums[i];
            int complement = currSum - k;
            //if. complement at i index == 0 which mean we find the sub(i,k+i)
            if (complement == 0) {
                max = i+1;
            }
            //if. the prefixSum conatin complement which mean at indec map.get(complemt) to i
            else if (prefixSum.containsKey(complement) ) {
                max = Math.max(max, i-prefixSum.get(complement));
            }
            prefixSum.putIfAbsent(currSum, i);
        }
        return max;
    }
}

```
