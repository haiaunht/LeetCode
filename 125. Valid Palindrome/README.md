# [125. Valid Palindrome (Easy)](https://leetcode.com/problems/valid-palindrome/solution/)

<p>Given a string <code>s</code>, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "A man, a plan, a canal: Panama"
<strong>Output:</strong> true
<strong>Explanation:</strong> "amanaplanacanalpanama" is a palindrome.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "race a car"
<strong>Output:</strong> false
<strong>Explanation:</strong> "raceacar" is not a palindrome.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists only of printable ASCII characters.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Yandex](https://leetcode.com/company/yandex), [Apple](https://leetcode.com/company/apple), [Wayfair](https://leetcode.com/company/wayfair), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Palindrome Linked List (Easy)](https://leetcode.com/problems/palindrome-linked-list/)
- [Valid Palindrome II (Easy)](https://leetcode.com/problems/valid-palindrome-ii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/valid-palindrome/solution/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isPalindrome(String s) {
        if (s.length() == 1) return true;
        int left = 0;
        int right = s.length() - 1;
        //loop through to check if s.charAt(left) == s.charAt(right);
        while (left < right ){
            while (!Character.isLetterOrDigit(s.charAt(left)) && left < right) {
                left++;
            }
            while (!Character.isLetterOrDigit(s.charAt(right)) && left < right ) {
                right--;
            }
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right)) ) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}

```
