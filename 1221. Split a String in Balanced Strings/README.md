# [1221. Split a String in Balanced Strings (Easy)](https://leetcode.com/problems/split-a-string-in-balanced-strings/)

<p><strong>Balanced</strong> strings are those that have an equal quantity of <code>'L'</code> and <code>'R'</code> characters.</p>

<p>Given a <strong>balanced</strong> string <code>s</code>, split it in the maximum amount of balanced strings.</p>

<p>Return <em>the maximum amount of split <strong>balanced</strong> strings</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "RLRRLLRLRL"
<strong>Output:</strong> 4
<strong>Explanation: </strong>s can be split into "RL", "RRLL", "RL", "RL", each substring contains same number of 'L' and 'R'.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "RLLLLRRRLR"
<strong>Output:</strong> 3
<strong>Explanation: </strong>s can be split into "RL", "LLLRRR", "LR", each substring contains same number of 'L' and 'R'.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "LLLLRRRR"
<strong>Output:</strong> 1
<strong>Explanation: </strong>s can be split into "LLLLRRRR".
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = "RLRRRLLRLL"
<strong>Output:</strong> 2
<strong>Explanation: </strong>s can be split into "RL", "RRRLLRLL", since each substring contains an equal number of 'L' and 'R'
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s[i]</code> is either <code>'L'</code> or <code>'R'</code>.</li>
	<li><code>s</code> is a <strong>balanced</strong> string.</li>
</ul>

**Companies**:  
[Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Greedy](https://leetcode.com/tag/greedy/), [Counting](https://leetcode.com/tag/counting/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/split-a-string-in-balanced-strings/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int balancedStringSplit(String s) {
        int max = 0;
        int L_count = 0;
        int R_count = 0;
        for (int i=0; i<s.length(); i++) {
            if (s.charAt(i) == 'L') L_count++;
            else R_count++;
            if (L_count == R_count) max++;
        }
        return max;
    }
}

```
