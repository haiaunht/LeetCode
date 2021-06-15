# [414. Third Maximum Number (Easy)](https://leetcode.com/problems/third-maximum-number/)

<p>Given integer array <code>nums</code>, return <em>the third maximum number in this array</em>. If the third maximum does not exist, return the maximum number.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,1]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The third maximum is 1.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The third maximum does not exist, so the maximum (2) is returned instead.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [2,2,3,1]
<strong>Output:</strong> 1
<strong>Explanation:</strong> Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Can you find an <code>O(n)</code> solution?

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/)

**Similar Questions**:

- [Kth Largest Element in an Array (Medium)](https://leetcode.com/problems/kth-largest-element-in-an-array/)

## Solution 1.

```Java
// OJ: https://leetcode.com/problems/third-maximum-number/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int thirdMax(int[] nums) { 
        Set<Integer> set = new HashSet<>();
        //add to the set to eliminate duplicate
        for (int i : nums) 
            set.add(i);
        int[] result = new int[set.size()];
        int count=0;
        for (int i:set) {
            result[count++] = i;
        }
        //now sort the array, if array >= 3, get the index at length-3, else return max which last element
        Arrays.sort(result);
        if (result.length < 3) {
            return result[result.length-1];
        } else {
            return result[result.length-3];
        }
    }
}

```
