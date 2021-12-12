# [78. Subsets (Medium)](https://leetcode.com/problems/subsets/)

<p>Given an integer array <code>nums</code> of <strong>unique</strong> elements, return <em>all possible subsets (the power set)</em>.</p>

<p>The solution set <strong>must not</strong> contain duplicate subsets. Return the solution in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [[],[0]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>-10 &lt;= nums[i] &lt;= 10</code></li>
	<li>All the numbers of&nbsp;<code>nums</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [ByteDance](https://leetcode.com/company/bytedance), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Twitter](https://leetcode.com/company/twitter)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Backtracking](https://leetcode.com/tag/backtracking/), [Bit Manipulation](https://leetcode.com/tag/bit-manipulation/)

**Similar Questions**:

- [Subsets II (Medium)](https://leetcode.com/problems/subsets-ii/)
- [Generalized Abbreviation (Medium)](https://leetcode.com/problems/generalized-abbreviation/)
- [Letter Case Permutation (Medium)](https://leetcode.com/problems/letter-case-permutation/)
- [Find Array Given Subset Sums (Hard)](https://leetcode.com/problems/find-array-given-subset-sums/)
- [Count Number of Maximum Bitwise-OR Subsets (Medium)](https://leetcode.com/problems/count-number-of-maximum-bitwise-or-subsets/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/subsets/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(0, nums, new ArrayList<>(), result);
        return result;
    }
    public void backtrack(int index, int[] nums, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));
        for (int i=index; i<nums.length; i++) {
            current.add(nums[i]);
            backtrack(i+1, nums, current, result);
            current.remove(current.size()-1);
        }
    }
}

```
