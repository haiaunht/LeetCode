# [41. First Missing Positive (Hard)](https://leetcode.com/problems/first-missing-positive/)

<p>Given an unsorted integer array <code>nums</code>, return the smallest missing positive integer.</p>

<p>You must implement an algorithm that runs in <code>O(n)</code> time and uses constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,0]
<strong>Output:</strong> 3
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [3,4,-1,1]
<strong>Output:</strong> 2
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [7,8,9,11,12]
<strong>Output:</strong> 1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Adobe](https://leetcode.com/company/adobe), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Wish](https://leetcode.com/company/wish), [Cisco](https://leetcode.com/company/cisco), [Docusign](https://leetcode.com/company/docusign)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:

- [Missing Number (Easy)](https://leetcode.com/problems/missing-number/)
- [Find the Duplicate Number (Medium)](https://leetcode.com/problems/find-the-duplicate-number/)
- [Find All Numbers Disappeared in an Array (Easy)](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
- [Couples Holding Hands (Hard)](https://leetcode.com/problems/couples-holding-hands/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/first-missing-positive/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public int firstMissingPositive(int[] nums) {
        //[3,4,-1,1] -> missing 2
        //use set to store all number while keeping what is the max num, if num < 1 which means missing 1
        //Space O(n)
        Set<Integer> set = new HashSet<>();
        int maxNum = Integer.MIN_VALUE;
        for (int num : nums) {
            set.add(num);
            maxNum = Math.max(maxNum, num);
        }
        //if max is < 1 ->return 1
        if (maxNum < 1) {
            return 1;
        }
        //if maxNum is not < 1-> loop from 1 -> max, check what num is not in set that is the missing num
        for (int i=1; i<maxNum; i++) {
            if (!set.contains(i)) {
                return i;
            }
        }
        //if there is a sequence of num 1->maxNum, the missing is maxNum+1
        return maxNum+1;
    }
}

```
