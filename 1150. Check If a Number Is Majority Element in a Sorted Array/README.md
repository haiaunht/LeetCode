# [1150. Check If a Number Is Majority Element in a Sorted Array (Easy)](https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/)

<p>Given an array <code>nums</code> sorted in <strong>non-decreasing</strong> order, and a number <code>target</code>, return <code>True</code> if and only if <code>target</code> is a majority element.</p>

<p>A <em>majority element</em> is an element that appears <strong>more than <code>N/2</code></strong> times in an array of length <code>N</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>nums = <span id="example-input-1-1">[2,4,5,5,5,5,5,6,6]</span>, target = <span id="example-input-1-2">5</span>
<strong>Output: </strong><span id="example-output-1">true</span>
<strong>Explanation: </strong>
The value 5 appears 5 times and the length of the array is 9.
Thus, 5 is a majority element because 5 &gt; 9/2 is true.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input: </strong>nums = <span id="example-input-2-1">[10,100,101,101]</span>, target = <span id="example-input-2-2">101</span>
<strong>Output: </strong><span id="example-output-2">false</span>
<strong>Explanation: </strong>
The value 101 appears 2 times and the length of the array is 4.
Thus, 101 is not a majority element because 2 &gt; 4/2 is false.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10^9</code></li>
	<li><code>1 &lt;= target &lt;= 10^9</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Salesforce](https://leetcode.com/company/salesforce)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/)

**Similar Questions**:

- [Majority Element (Easy)](https://leetcode.com/problems/majority-element/)
- [Majority Element II (Medium)](https://leetcode.com/problems/majority-element-ii/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isMajorityElement(int[] nums, int target) {
        List<Integer> major = majorNumber(nums);
        if (major.get(1) > nums.length/2) {
            if (major.get(0) == target) {
                return true;
            }
        }
        return false;
    }
    private static List<Integer> majorNumber(int[] nums) {
        List<Integer> ret = new ArrayList<>();
        Map<Integer,Integer> map = new HashMap<>();
        for (int i:nums) {
            map.put(i, map.getOrDefault(i,0)+1);
        }
        Map.Entry<Integer,Integer> major = null;
        for(Map.Entry<Integer,Integer> entry : map.entrySet()) {
            if (major==null || major.getValue() < entry.getValue()) {
                major = entry;
            }
        }
        ret.add(major.getKey());
        ret.add(major.getValue());
        return ret;
    }
}

```
