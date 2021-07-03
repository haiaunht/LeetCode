# [229. Majority Element II (Medium)](https://leetcode.com/problems/majority-element-ii/)

<p>Given an integer array of size <code>n</code>, find all elements that appear more than <code>⌊ n/3 ⌋</code> times.</p>

<p><strong>Follow-up: </strong>Could you solve the problem&nbsp;in linear time and in O(1) space?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,3]
<strong>Output:</strong> [3]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1]
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> [1,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Sorting](https://leetcode.com/tag/sorting/), [Counting](https://leetcode.com/tag/counting/)

**Similar Questions**:

- [Majority Element (Easy)](https://leetcode.com/problems/majority-element/)
- [Check If a Number Is Majority Element in a Sorted Array (Easy)](https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/majority-element-ii/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> result = new ArrayList<>();
        Map<Integer,Integer> map = new HashMap<>();
        for (int i:nums) {
            map.put(i, map.getOrDefault(i,0)+1);
        }
        int len=nums.length/3;
        for(Map.Entry<Integer,Integer> entry : map.entrySet()) {
            if (entry.getValue() > len) result.add(entry.getKey());
        }
        return result;
    }
}

```
