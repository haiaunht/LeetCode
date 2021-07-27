# [791. Custom Sort String (Medium)](https://leetcode.com/problems/custom-sort-string/)

<p>You are given two strings order and s. All the words of <code>order</code> are <strong>unique</strong> and were sorted in some custom order previously.</p>

<p>Permute the characters of <code>s</code> so that they match the order that <code>order</code> was sorted. More specifically, if a character <code>x</code> occurs before a character <code>y</code> in <code>order</code>, then <code>x</code> should occur before <code>y</code> in the permuted string.</p>

<p>Return <em>any permutation of </em><code>s</code><em> that satisfies this property</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> order = "cba", s = "abcd"
<strong>Output:</strong> "cbad"
<strong>Explanation:</strong> 
"a", "b", "c" appear in order, so the order of "a", "b", "c" should be "c", "b", and "a". 
Since "d" does not appear in order, it can be at any position in the returned string. "dcba", "cdba", "cbda" are also valid outputs.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> order = "cbafg", s = "abcd"
<strong>Output:</strong> "cbad"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= order.length &lt;= 26</code></li>
	<li><code>1 &lt;= s.length &lt;= 200</code></li>
	<li><code>order</code> and <code>s</code> consist of lowercase English letters.</li>
	<li>All the characters of <code>order</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Sorting](https://leetcode.com/tag/sorting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/custom-sort-string/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String customSortString(String order, String s) {
        //use counting sort to track what char and the frequency
        int[] sCounting = new int[26];
        for (char c : s.toCharArray()) {
            sCounting[c - 'a']++;
        }
        //loop through order string to add to result, the remainder will taker later
        StringBuilder result = new StringBuilder();
        for (char c : order.toCharArray()) {
            int count = sCounting[c - 'a'];
            for (int i=0; i<count; i++) {
                result.append(c);
            }
            //reset the count to only have the remaider != 0
            sCounting[c - 'a'] = 0;
        }
        for (char c='a'; c<='z'; c++) {
            int count = sCounting[c - 'a'];
            for (int i=0; i<count; i++) {
                result.append(c);
            }
        }
        return result.toString();
    }
}

```
