# [1283. Find the Smallest Divisor Given a Threshold (Medium)](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/)

<p>Given an array of integers <code>nums</code> and an integer <code>threshold</code>, we will choose a positive integer <code>divisor</code>, divide all the array by it, and sum the division's result. Find the <strong>smallest</strong> <code>divisor</code> such that the result mentioned above is less than or equal to <code>threshold</code>.</p>

<p>Each result of the division is rounded to the nearest integer greater than or equal to that element. (For example: <code>7/3 = 3</code> and <code>10/2 = 5</code>).</p>

<p>It is guaranteed that there will be an answer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,5,9], threshold = 6
<strong>Output:</strong> 5
<strong>Explanation:</strong> We can get a sum to 17 (1+2+5+9) if the divisor is 1. 
If the divisor is 4 we can get a sum of 7 (1+1+2+3) and if the divisor is 5 the sum will be 5 (1+1+1+2). 
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [44,22,33,11,1], threshold = 5
<strong>Output:</strong> 44
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [21212,10101,12121], threshold = 1000000
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> nums = [2,3,5,7,11], threshold = 11
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>nums.length &lt;= threshold &lt;= 10<sup>6</sup></code></li>
</ul>

**Companies**:  
[Salesforce](https://leetcode.com/company/salesforce)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/
// Author: Please set your name in options page
// Time: O(N) sumOf()=N, log1000000 = 6
// Space: O(1)
class Solution {
    public int smallestDivisor(int[] nums, int threshold) {
        int left = 1;
        int right = 1000000;
        while (left <= right) {
            int mid = (left + right)/2;
            //if the sum is > threshold, which means we need highter divisor so move to the right
            if (sumOf(nums, mid) > threshold) {
                left = mid + 1;
            } else {
                right = mid -1;
            }
        }
        return left;
    }
    public int sumOf(int[] nums, int divisor) {
        int sum = 0;
        for (int i=0; i<nums.length; i++) {
            sum += (nums[i] - 1)/divisor + 1; //7/3 = 2+1=3
        }
        return sum;
    }
}

```
