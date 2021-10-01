# [1143. Longest Common Subsequence (Medium)](https://leetcode.com/problems/longest-common-subsequence/solution/)

<p>Given two strings <code>text1</code> and <code>text2</code>, return <em>the length of their longest <strong>common subsequence</strong>. </em>If there is no <strong>common subsequence</strong>, return <code>0</code>.</p>

<p>A <strong>subsequence</strong> of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.</p>

<ul>
	<li>For example, <code>"ace"</code> is a subsequence of <code>"abcde"</code>.</li>
</ul>

<p>A <strong>common subsequence</strong> of two strings is a subsequence that is common to both strings.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> text1 = "abcde", text2 = "ace" 
<strong>Output:</strong> 3  
<strong>Explanation:</strong> The longest common subsequence is "ace" and its length is 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> text1 = "abc", text2 = "abc"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The longest common subsequence is "abc" and its length is 3.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> text1 = "abc", text2 = "def"
<strong>Output:</strong> 0
<strong>Explanation:</strong> There is no such common subsequence, so the result is 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= text1.length, text2.length &lt;= 1000</code></li>
	<li><code>text1</code> and <code>text2</code> consist of only lowercase English characters.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Karat](https://leetcode.com/company/karat), [Indeed](https://leetcode.com/company/indeed), [Adobe](https://leetcode.com/company/adobe), [VMware](https://leetcode.com/company/vmware)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)

**Similar Questions**:

- [Longest Palindromic Subsequence (Medium)](https://leetcode.com/problems/longest-palindromic-subsequence/)
- [Delete Operation for Two Strings (Medium)](https://leetcode.com/problems/delete-operation-for-two-strings/)
- [Shortest Common Supersequence (Hard)](https://leetcode.com/problems/shortest-common-supersequence/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/longest-common-subsequence/solution/
// Author: Please set your name in options page
// Time: O(M*N)
// Space: O(min(M,N))
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m+1][n+1];
        for (int i=0; i<m+1; i++) {
            for (int j=0; j<n+1; j++) {
                //top row and first colum = 0
                if (i==0 || j==0) {
                    dp[i][j] = 0;
                } else if (text1.charAt(i-1) == text2.charAt(j-1)) {
                    dp[i][j] = dp[i-1][j-1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        return dp[m][n];
    }
}

```
