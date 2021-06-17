# [459. Repeated Substring Pattern (Easy)](https://leetcode.com/problems/repeated-substring-pattern/)

<p>Given a string <code>s</code>, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "abab"
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring "ab" twice.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "aba"
<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "abcabcabcabc"
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring "abc" four times or the substring "abcabc" twice.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Implement strStr() (Easy)](https://leetcode.com/problems/implement-strstr/)
- [Repeated String Match (Medium)](https://leetcode.com/problems/repeated-string-match/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/repeated-substring-pattern/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        int n = s.length();
        for (int len=n/2; len>0; len--) {
            if (n%len == 0) {
                int i=0;
                while(i+len < n && s.charAt(i) == s.charAt(i+len)) {
                    i++;
                }
                if (i+len == n) {
                    return true;
                }
            }
        }
        return false;
    }
}

```
