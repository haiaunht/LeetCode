# [1328. Break a Palindrome (Medium)](https://leetcode.com/problems/break-a-palindrome/)

<p>Given a palindromic string of lowercase English letters <code>palindrome</code>, replace <strong>exactly one</strong> character with any lowercase English letter so that the resulting string is <strong>not</strong> a palindrome and that it is the <strong>lexicographically smallest</strong> one possible.</p>

<p>Return <em>the resulting string. If there is no way to replace a character to make it not a palindrome, return an <strong>empty string</strong>.</em></p>

<p>A string <code>a</code> is lexicographically smaller than a string <code>b</code> (of the same length) if in the first position where <code>a</code> and <code>b</code> differ, <code>a</code> has a character strictly smaller than the corresponding character in <code>b</code>. For example, <code>"abcc"</code> is lexicographically smaller than <code>"abcd"</code> because the first position they differ is at the fourth character, and <code>'c'</code> is smaller than <code>'d'</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> palindrome = "abccba"
<strong>Output:</strong> "aaccba"
<strong>Explanation:</strong> There are many ways to make "abccba" not a palindrome, such as "<u>z</u>bccba", "a<u>a</u>ccba", and "ab<u>a</u>cba".
Of all the ways, "aaccba" is the lexicographically smallest.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> palindrome = "a"
<strong>Output:</strong> ""
<strong>Explanation:</strong> There is no way to replace a single character to make "a" not a palindrome, so return an empty string.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> palindrome = "aa"
<strong>Output:</strong> "ab"</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> palindrome = "aba"
<strong>Output:</strong> "abb"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= palindrome.length &lt;= 1000</code></li>
	<li><code>palindrome</code> consists of only lowercase English letters.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Greedy](https://leetcode.com/tag/greedy/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/break-a-palindrome/solution/
// Author: Please set your name in options page
// Time: O(N/2) = O(N)
// Space: O(N)
class Solution {
    public String breakPalindrome(String palindrome) {
        if (palindrome.length() == 1) return "";
        char[] arr = palindrome.toCharArray();
        //because of palindrome, only need to go 1/2 length
        for (int i=0; i<arr.length/2; i++) {
            if (arr[i] != 'a') {
                arr[i] = 'a';
                return String.valueOf(arr);
            }
        }
        //in case whole palindrom is aaaaa
        arr[arr.length -1] = 'b';
        return String.valueOf(arr);
    }
}

```
