# [1509. Minimum Difference Between Largest and Smallest Value in Three Moves (Medium)](https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/)

<p>Given an array <code>nums</code>, you are allowed to choose one element of <code>nums</code> and change it by any&nbsp;value in one move.</p>

<p>Return the minimum difference between the largest and smallest value of <code>nums</code>&nbsp;after perfoming at most 3 moves.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [5,3,2,4]
<strong>Output:</strong> 0
<strong>Explanation:</strong> Change the array [5,3,2,4] to [<strong>2</strong>,<strong>2</strong>,2,<strong>2</strong>].
The difference between the maximum and minimum is 2-2 = 0.</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,5,0,10,14]
<strong>Output:</strong> 1
<strong>Explanation:</strong> Change the array [1,5,0,10,14] to [1,<strong>1</strong>,0,<strong>1</strong>,<strong>1</strong>]. 
The difference between the maximum and minimum is 1-0 = 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [6,6,0,1,1,4,6]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> nums = [1,5,6,14,15]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10^5</code></li>
	<li><code>-10^9 &lt;= nums[i] &lt;= 10^9</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Greedy](https://leetcode.com/tag/greedy/), [Sorting](https://leetcode.com/tag/sorting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int minDifference(int[] nums) {
        if(nums.length <= 4)
            return 0;
        int len = nums.length;
        Arrays.sort(nums);
        //option1 replace the last 3 numbers, that lead the different is nums[len - 1- 3] - nums[0]
        //option2 replace the first and last 2 number to the second num, lead to nums[len-1-2] - num[1]....and so on
        int option1 = nums[len-4] - nums[0];
        int option2 = nums[len-3] - nums[1];
        int option3 = nums[len-2] - nums[2];
        int option4 = nums[len-1] - nums[3];
        return Math.min(option1, Math.min(option2, Math.min(option3,option4)));
    }
}

```
