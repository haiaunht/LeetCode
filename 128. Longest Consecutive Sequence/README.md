# [128. Longest Consecutive Sequence (Medium)](https://leetcode.com/problems/longest-consecutive-sequence/)

<p>Given an unsorted array of integers <code>nums</code>, return <em>the length of the longest consecutive elements sequence.</em></p>

<p>You must write an algorithm that runs in&nbsp;<code>O(n)</code>&nbsp;time.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [100,4,200,1,3,2]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The longest consecutive elements sequence is <code>[1, 2, 3, 4]</code>. Therefore its length is 4.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [0,3,7,2,5,8,4,6,0,1]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Twitter](https://leetcode.com/company/twitter), [Qualtrics](https://leetcode.com/company/qualtrics)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Union Find](https://leetcode.com/tag/union-find/)

**Similar Questions**:

- [Binary Tree Longest Consecutive Sequence (Medium)](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/longest-consecutive-sequence/
// Author: Please set your name in options page
// Time: O(n)
// Space: O(n)
class Solution {
    public int longestConsecutive(int[] nums) {
        //[100,4,200,1,3,2]
        //brute force
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }
        int longestSequence = 0;
        for (int num : set) {
            //check if any num-1 in the set, if not currentNum can add to sequence start from num
            if (!set.contains(num - 1)) {
                int currentNumInSequence = num;
                int currentLongestSequence = 1;
                //loop through the set to find the next number and ++ if found, else calculate current longestSequence
                while (set.contains(currentNumInSequence+1)) {
                    currentNumInSequence++;
                    currentLongestSequence++;
                }
                //if the while done, calculate the length and get the longest
                longestSequence = Math.max(longestSequence, currentLongestSequence);
            }
        }
        return longestSequence;
    }
}

```
