# [528. Random Pick with Weight (Medium)](https://leetcode.com/problems/random-pick-with-weight/)

<p>You are given an array of positive integers <code>w</code> where <code>w[i]</code> describes the weight of <code>i</code><sup><code>th</code>&nbsp;</sup>index (0-indexed).</p>

<p>We need to call the function&nbsp;<code>pickIndex()</code> which <strong>randomly</strong> returns an integer in the range <code>[0, w.length - 1]</code>.&nbsp;<code>pickIndex()</code>&nbsp;should return the integer&nbsp;proportional to its weight in the <code>w</code> array. For example, for <code>w = [1, 3]</code>, the probability of picking the index <code>0</code> is <code>1 / (1 + 3)&nbsp;= 0.25</code> (i.e 25%)&nbsp;while the probability of picking the index <code>1</code> is <code>3 / (1 + 3)&nbsp;= 0.75</code> (i.e 75%).</p>

<p>More formally, the probability of picking index <code>i</code> is <code>w[i] / sum(w)</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["Solution","pickIndex"]
[[[1]],[]]
<strong>Output</strong>
[null,0]

<strong>Explanation</strong>
Solution solution = new Solution([1]);
solution.pickIndex(); // return 0. Since there is only one single element on the array the only option is to return the first element.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input</strong>
["Solution","pickIndex","pickIndex","pickIndex","pickIndex","pickIndex"]
[[[1,3]],[],[],[],[],[]]
<strong>Output</strong>
[null,1,1,1,1,0]

<strong>Explanation</strong>
Solution solution = new Solution([1, 3]);
solution.pickIndex(); // return 1. It's returning the second element (index = 1) that has probability of 3/4.
solution.pickIndex(); // return 1
solution.pickIndex(); // return 1
solution.pickIndex(); // return 1
solution.pickIndex(); // return 0. It's returning the first element (index = 0) that has probability of 1/4.

Since this is a randomization problem, multiple answers are allowed so the following outputs can be considered correct :
[null,1,1,1,1,0]
[null,1,1,1,1,1]
[null,1,1,1,0,0]
[null,1,1,1,0,1]
[null,1,0,1,0,0]
......
and so on.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= w.length &lt;= 10000</code></li>
	<li><code>1 &lt;= w[i] &lt;= 10^5</code></li>
	<li><code>pickIndex</code>&nbsp;will be called at most <code>10000</code> times.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Yelp](https://leetcode.com/company/yelp), [LinkedIn](https://leetcode.com/company/linkedin), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [ByteDance](https://leetcode.com/company/bytedance), [Bloomberg](https://leetcode.com/company/bloomberg), [Expedia](https://leetcode.com/company/expedia), [Cruise Automation](https://leetcode.com/company/cruise-automation)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [Binary Search](https://leetcode.com/tag/binary-search/), [Prefix Sum](https://leetcode.com/tag/prefix-sum/), [Randomized](https://leetcode.com/tag/randomized/)

**Similar Questions**:

- [Random Pick Index (Medium)](https://leetcode.com/problems/random-pick-index/)
- [Random Pick with Blacklist (Hard)](https://leetcode.com/problems/random-pick-with-blacklist/)
- [Random Point in Non-overlapping Rectangles (Medium)](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/random-pick-with-weight/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    int[] array;
    int sum;
    public Solution(int[] w) {
        int currentSum=0;
        array = new int[w.length];
        for (int i=0; i<array.length; i++) {
            currentSum += w[i];
            array[i] = currentSum;
        }
        sum = currentSum;
    }
    public int pickIndex() {
        double random = Math.random() * (sum);
        int i=0;
        for (i=0; i<array.length; i++) {
            if (random < array[i]) return i;
        }
        return i-1;
    }
}
/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(w);
 * int param_1 = obj.pickIndex();
 */

```
