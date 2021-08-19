# [9. Palindrome Number (Easy)](https://leetcode.com/problems/palindrome-number/)

<p>Given an integer <code>x</code>, return <code>true</code> if <code>x</code> is palindrome integer.</p>

<p>An integer is a <strong>palindrome</strong> when it reads the same backward as forward. For example, <code>121</code> is palindrome while <code>123</code> is not.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> x = 121
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> x = -121
<strong>Output:</strong> false
<strong>Explanation:</strong> From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> x = 10
<strong>Output:</strong> false
<strong>Explanation:</strong> Reads 01 from right to left. Therefore it is not a palindrome.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> x = -101
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-2<sup>31</sup>&nbsp;&lt;= x &lt;= 2<sup>31</sup>&nbsp;- 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you solve it without converting the integer to a string?

**Companies**:  
[Adobe](https://leetcode.com/company/adobe), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Bloomberg](https://leetcode.com/company/bloomberg), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Infosys](https://leetcode.com/company/infosys)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/)

**Similar Questions**:

- [Palindrome Linked List (Easy)](https://leetcode.com/problems/palindrome-linked-list/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/palindrome-number/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || ((x!=0) && (x%10==0))) return false;
        int tmp = x;
        int reverseX = 0;
        //121 => 121 % 10 = 1 then reverseX = 0*10 + 1
        while (tmp!=0) {
            int lastDigit = tmp%10;
            reverseX = reverseX*10 + lastDigit;
            tmp = tmp/10;
        }
        return (x == reverseX);
    }
}

```
