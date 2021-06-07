# [39. Combination Sum (Medium)](https://leetcode.com/problems/combination-sum/)

<p>Given an array of <strong>distinct</strong> integers <code>candidates</code> and a target integer <code>target</code>, return <em>a list of all <strong>unique combinations</strong> of </em><code>candidates</code><em> where the chosen numbers sum to </em><code>target</code><em>.</em> You may return the combinations in <strong>any order</strong>.</p>

<p>The <strong>same</strong> number may be chosen from <code>candidates</code> an <strong>unlimited number of times</strong>. Two combinations are unique if the frequency of at least one of the chosen numbers is different.</p>

<p>It is <strong>guaranteed</strong> that the number of unique combinations that sum up to <code>target</code> is less than <code>150</code> combinations for the given input.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> candidates = [2,3,6,7], target = 7
<strong>Output:</strong> [[2,2,3],[7]]
<strong>Explanation:</strong>
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> candidates = [2,3,5], target = 8
<strong>Output:</strong> [[2,2,2,2],[2,3,3],[3,5]]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> candidates = [2], target = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> candidates = [1], target = 1
<strong>Output:</strong> [[1]]
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> candidates = [1], target = 2
<strong>Output:</strong> [[1,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= candidates.length &lt;= 30</code></li>
	<li><code>1 &lt;= candidates[i] &lt;= 200</code></li>
	<li>All elements of <code>candidates</code> are <strong>distinct</strong>.</li>
	<li><code>1 &lt;= target &lt;= 500</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Airbnb](https://leetcode.com/company/airbnb), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Apple](https://leetcode.com/company/apple), [eBay](https://leetcode.com/company/ebay), [Bloomberg](https://leetcode.com/company/bloomberg), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Backtracking](https://leetcode.com/tag/backtracking/)

**Similar Questions**:

- [Letter Combinations of a Phone Number (Medium)](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
- [Combination Sum II (Medium)](https://leetcode.com/problems/combination-sum-ii/)
- [Combinations (Medium)](https://leetcode.com/problems/combinations/)
- [Combination Sum III (Medium)](https://leetcode.com/problems/combination-sum-iii/)
- [Factor Combinations (Medium)](https://leetcode.com/problems/factor-combinations/)
- [Combination Sum IV (Medium)](https://leetcode.com/problems/combination-sum-iv/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/combination-sum/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> results = new ArrayList<List<Integer>>();
        LinkedList<Integer> comb = new LinkedList<Integer>();
        this.backtrack(target, comb, 0, candidates, results);
        return results;
    }
    private void backtrack(int remain, LinkedList<Integer> comb, int start, int[] candidates, List<List<Integer>> results) {
        if (remain == 0) {
            results.add(new ArrayList<Integer>(comb));
            return;
        } else if (remain < 0) {
            return;
        }
        for (int i=start; i<candidates.length; i++) {
            comb.add(candidates[i]);
            backtrack(remain-candidates[i], comb, i, candidates, results);
            comb.removeLast();
        }
    }
}

```
