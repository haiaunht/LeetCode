# [724. Find Pivot Index (Easy)](https://leetcode.com/problems/find-pivot-index/)

<p>Given an array of integers <code>nums</code>, calculate the <strong>pivot index</strong> of this array.</p>

<p>The <strong>pivot index</strong> is the index where the sum of all the numbers <strong>strictly</strong> to the left of the index is equal to the sum of all the numbers <strong>strictly</strong> to the index's right.</p>

<p>If the index is on the left edge of the array, then the left sum is <code>0</code> because there are no elements to the left. This also applies to the right edge of the array.</p>

<p>Return <em>the <strong>leftmost pivot index</strong></em>. If no such index exists, return -1.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,7,3,6,5,6]
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> -1
<strong>Explanation:</strong>
There is no index that satisfies the conditions in the problem statement.</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [2,1,-1]
<strong>Output:</strong> 0
<strong>Explanation:</strong>
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>

**Companies**:  
[Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Expedia](https://leetcode.com/company/expedia), [Adobe](https://leetcode.com/company/adobe)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Prefix Sum](https://leetcode.com/tag/prefix-sum/)

**Similar Questions**:

- [Subarray Sum Equals K (Medium)](https://leetcode.com/problems/subarray-sum-equals-k/)
- [Find the Middle Index in Array (Easy)](https://leetcode.com/problems/find-the-middle-index-in-array/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-pivot-index/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int pivotIndex(int[] nums) {
        //[1,7,3,6,5,6]
        //    11 6 11 total = 11 + 6 + 11
        // use leftSum to keep track total sum before each nums[i]
        int leftSum = 0;
        int sum = 0;
        for (int num : nums) {
            sum += num;
        }
        //at each nums[i], if sum - nums[i] - leftSum = rightSum = leftSum -> found i
        for (int i=0; i<nums.length; i++) {
            int rightSide = sum - nums[i] - leftSum;
            if (leftSum == rightSide) {
                return i;
            } else {
                leftSum += nums[i];
            }
        }
        return -1;
    }
}

```
