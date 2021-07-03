# [1389. Create Target Array in the Given Order (Easy)](https://leetcode.com/problems/create-target-array-in-the-given-order/)

<p>Given two arrays of integers&nbsp;<code>nums</code> and <code>index</code>. Your task is to create <em>target</em> array under the following rules:</p>

<ul>
	<li>Initially <em>target</em> array is empty.</li>
	<li>From left to right read nums[i] and index[i], insert at index <code>index[i]</code>&nbsp;the value <code>nums[i]</code>&nbsp;in&nbsp;<em>target</em> array.</li>
	<li>Repeat the previous step until there are no elements to read in <code>nums</code> and <code>index.</code></li>
</ul>

<p>Return the <em>target</em> array.</p>

<p>It is guaranteed that the insertion operations will be valid.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [0,1,2,3,4], index = [0,1,2,2,1]
<strong>Output:</strong> [0,4,1,3,2]
<strong>Explanation:</strong>
nums       index     target
0            0        [0]
1            1        [0,1]
2            2        [0,1,2]
3            2        [0,1,3,2]
4            1        [0,4,1,3,2]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3,4,0], index = [0,1,2,3,0]
<strong>Output:</strong> [0,1,2,3,4]
<strong>Explanation:</strong>
nums       index     target
1            0        [1]
2            1        [1,2]
3            2        [1,2,3]
4            3        [1,2,3,4]
0            0        [0,1,2,3,4]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1], index = [0]
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length, index.length &lt;= 100</code></li>
	<li><code>nums.length == index.length</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 100</code></li>
	<li><code>0 &lt;= index[i] &lt;= i</code></li>
</ul>

**Companies**:  
[Apple](https://leetcode.com/company/apple), [Visa](https://leetcode.com/company/visa)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Simulation](https://leetcode.com/tag/simulation/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/create-target-array-in-the-given-order/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] createTargetArray(int[] nums, int[] index) {
        List<Integer> target = new ArrayList<>();
        for (int i=0; i<nums.length; i++) {
            target.add(index[i], nums[i]);
        }
        //convert list->array
        int[] result = new int[target.size()];
        for (int i=0; i<target.size(); i++) {
            result[i] = target.get(i);
        }
        return result;
    }
}

```
