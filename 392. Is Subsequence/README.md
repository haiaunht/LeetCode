# [392. Is Subsequence (Easy)](https://leetcode.com/problems/is-subsequence/)

<p>Given two strings <code>s</code> and <code>t</code>, return <code>true</code><em> if </em><code>s</code><em> is a <strong>subsequence</strong> of </em><code>t</code><em>, or </em><code>false</code><em> otherwise</em>.</p>

<p>A <strong>subsequence</strong> of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., <code>"ace"</code> is a subsequence of <code>"<u>a</u>b<u>c</u>d<u>e</u>"</code> while <code>"aec"</code> is not).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "abc", t = "ahbgdc"
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "axc", t = "ahbgdc"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 100</code></li>
	<li><code>0 &lt;= t.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> and <code>t</code> consist only of lowercase English letters.</li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Suppose there are lots of incoming <code>s</code>, say <code>s<sub>1</sub>, s<sub>2</sub>, ..., s<sub>k</sub></code> where <code>k &gt;= 10<sup>9</sup></code>, and you want to check one by one to see if <code>t</code> has its subsequence. In this scenario, how would you change your code?

**Companies**:  
[Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Binary Search](https://leetcode.com/tag/binary-search/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Greedy](https://leetcode.com/tag/greedy/)

**Similar Questions**:

- [Number of Matching Subsequences (Medium)](https://leetcode.com/problems/number-of-matching-subsequences/)
- [Shortest Way to Form String (Medium)](https://leetcode.com/problems/shortest-way-to-form-string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/is-subsequence/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isSubsequence(String s, String t) {
        if (t.length() < s.length()) return false;
        if (s.length() == 0) return true;
        // s = "abc", t = "ahbgdc"
        Queue<Character> s_stack = new LinkedList();
        for (char c : s.toCharArray()) {
            s_stack.add(c);
        }
        int pt = 0;
        while (pt < t.length()) {
            if (s_stack.size() != 0 && t.charAt(pt) == s_stack.peek()) {
                s_stack.remove();
            }
            pt++;
        }
        if (s_stack.size() == 0) return true;
        return false;
    }
}

```
