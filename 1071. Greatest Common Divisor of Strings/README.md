# [1071. Greatest Common Divisor of Strings (Easy)](https://leetcode.com/problems/greatest-common-divisor-of-strings/)

<p>For two strings <code>s</code> and <code>t</code>, we say "<code>t</code> divides <code>s</code>" if and only if <code>s = t + ... + t</code>&nbsp; (<code>t</code> concatenated with itself 1 or more times)</p>

<p>Given two strings str1 and str2, return the largest string <code>x</code> such that <code>x</code> divides both&nbsp;<code><font face="monospace">str1</font></code>&nbsp;and <code><font face="monospace">str2</font></code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> str1 = "ABCABC", str2 = "ABC"
<strong>Output:</strong> "ABC"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> str1 = "ABABAB", str2 = "ABAB"
<strong>Output:</strong> "AB"
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> str1 = "LEET", str2 = "CODE"
<strong>Output:</strong> ""
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> str1 = "ABCDEF", str2 = "ABC"
<strong>Output:</strong> ""
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= str1.length &lt;= 1000</code></li>
	<li><code>1 &lt;= str2.length &lt;= 1000</code></li>
	<li><code>str1</code>&nbsp;and <code>str2</code>&nbsp;consist of&nbsp;English uppercase letters.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Atlassian](https://leetcode.com/company/atlassian), [Visa](https://leetcode.com/company/visa)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/greatest-common-divisor-of-strings/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        //if str1 < str2 length -> reverse the order
        if (str1.length() < str2.length()) return gcdOfStrings(str2, str1);
        if (str1.equals(str2)) return str2;
        if (str1.startsWith(str2)) {
            return gcdOfStrings(str1.substring(str2.length()), str2);
        }
        //if cannot find
        return "";
    }
}

```
