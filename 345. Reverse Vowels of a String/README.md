# [345. Reverse Vowels of a String (Easy)](https://leetcode.com/problems/reverse-vowels-of-a-string/)

<p>Given a string <code>s</code>, reverse only all the vowels in the string and return it.</p>

<p>The vowels are <code>'a'</code>, <code>'e'</code>, <code>'i'</code>, <code>'o'</code>, and <code>'u'</code>, and they can appear in both cases.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "hello"
<strong>Output:</strong> "holle"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "leetcode"
<strong>Output:</strong> "leotcede"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3 * 10<sup>5</sup></code></li>
	<li><code>s</code> consist of <strong>printable ASCII</strong> characters.</li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Reverse String (Easy)](https://leetcode.com/problems/reverse-string/)
- [Remove Vowels from a String (Easy)](https://leetcode.com/problems/remove-vowels-from-a-string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/reverse-vowels-of-a-string/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String reverseVowels(String s) {
        char[] vowels = {'a','e','i','o','u','A','E','I','O','U'};
        Set<Character> set = new HashSet<>();
        for (char c : vowels) set.add(c);
        Stack<Character> stack = new Stack();
        char[] chars = s.toCharArray();
        for (char c : chars) {
            if (set.contains(c)) stack.push(c);
        }
        for (int i=0; i<chars.length; i++) {
            if (set.contains(chars[i])) {
                chars[i] = stack.pop();
            }
        }
        return new String(chars);
    }
}

```
