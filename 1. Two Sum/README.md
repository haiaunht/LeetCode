# [1. Two Sum ](https://leetcode.com/problems/two-sum/)

<p>Given an array of integers <code>nums</code>&nbsp;and an integer <code>target</code>, return <em>indices of the two numbers such that they add up to <code>target</code></em>.</p>

<p>You may assume that each input would have <strong><em>exactly</em> one solution</strong>, and you may not use the <em>same</em> element twice.</p>

<p>You can return the answer in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [2,7,11,15], target = 9
<strong>Output:</strong> [0,1]
<strong>Output:</strong> Because nums[0] + nums[1] == 9, we return [0, 1].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,4], target = 6
<strong>Output:</strong> [1,2]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,3], target = 6
<strong>Output:</strong> [0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><strong>Only one valid answer exists.</strong></li>
</ul>

<p>&nbsp;</p>
<strong>Follow-up:&nbsp;</strong>Can you come up with an algorithm that is less than&nbsp;<code>O(n<sup>2</sup>)&nbsp;</code>time complexity?

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Apple](https://leetcode.com/company/apple), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg), [Facebook](https://leetcode.com/company/facebook), [Uber](https://leetcode.com/company/uber), [Oracle](https://leetcode.com/company/oracle), [SAP](https://leetcode.com/company/sap), [Cisco](https://leetcode.com/company/cisco), [tcs](https://leetcode.com/company/tcs), [Nagarro](https://leetcode.com/company/nagarro), [Expedia](https://leetcode.com/company/expedia), [Twitter](https://leetcode.com/company/twitter), [Yahoo](https://leetcode.com/company/yahoo), [Paypal](https://leetcode.com/company/paypal), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Samsung](https://leetcode.com/company/samsung), [Yandex](https://leetcode.com/company/yandex)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:

- [3Sum (Medium)](https://leetcode.com/problems/3sum/)
- [4Sum (Medium)](https://leetcode.com/problems/4sum/)
- [Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [Two Sum III - Data structure design (Easy)](https://leetcode.com/problems/two-sum-iii-data-structure-design/)
- [Subarray Sum Equals K (Medium)](https://leetcode.com/problems/subarray-sum-equals-k/)
- [Two Sum IV - Input is a BST (Easy)](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)
- [Two Sum Less Than K (Easy)](https://leetcode.com/problems/two-sum-less-than-k/)
- [Max Number of K-Sum Pairs (Medium)](https://leetcode.com/problems/max-number-of-k-sum-pairs/)
- [Count Good Meals (Medium)](https://leetcode.com/problems/count-good-meals/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/two-sum/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] twoSum(int[] nums, int target) {
        //[2,7,11,15] target=9
        //step 1: 2+..= 9 => . = 9-2 =7   [ ]
        //step 7: 7+. =9 => 9-7=2 => found return {0,1}
        Map<Integer, Integer> pair = new HashMap<>();
        for (int i=0; i<nums.length; i++ ) {
            int complementNum = target - nums[i];
            if (!pair.containsKey(complementNum)) {
                pair.put(nums[i], i);
            } else {
                return new int[]{pair.get(complementNum), i};
            }
            //step 1 i=0; value =2, com = 7 [2,0]
            //step 2 i=1, value = 7 com =2 => pair.get(2), 1
        }
        return null;
    }
}

```
