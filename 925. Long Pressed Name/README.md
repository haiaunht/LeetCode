# [925. Long Pressed Name (Easy)](https://leetcode.com/problems/long-pressed-name/)

<p>Your friend is typing his <code>name</code> into a keyboard. Sometimes, when typing a character <code>c</code>, the key might get <em>long pressed</em>, and the character will be typed 1 or more times.</p>

<p>You examine the <code>typed</code> characters of the keyboard. Return <code>True</code> if it is possible that it was your friends name, with some characters (possibly none) being long pressed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> name = "alex", typed = "aaleex"
<strong>Output:</strong> true
<strong>Explanation: </strong>'a' and 'e' in 'alex' were long pressed.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> name = "saeed", typed = "ssaaedd"
<strong>Output:</strong> false
<strong>Explanation: </strong>'e' must have been pressed twice, but it wasn't in the typed output.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> name = "leelee", typed = "lleeelee"
<strong>Output:</strong> true
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> name = "laiden", typed = "laiden"
<strong>Output:</strong> true
<strong>Explanation: </strong>It's not necessary to long press any character.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= name.length &lt;= 1000</code></li>
	<li><code>1 &lt;= typed.length &lt;= 1000</code></li>
	<li><code>name</code> and <code>typed</code> contain only lowercase English letters.</li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/long-pressed-name/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        int i,j;
        for (i=0,j=0; i<name.length() && j<typed.length(); ) {
            if (name.charAt(i) != typed.charAt(j)) return false;
            int count_1 = countSameChar(name.charAt(i), i, name);
            int count_2 = countSameChar(typed.charAt(j), j, typed);
            if (count_1 > count_2) return false;
            i += count_1;
            j += count_2;
        }
        if (i != name.length() || j != typed.length()) return false;
        return true;
    }
    private int countSameChar(char character, int startIndex, String s) {
        int count = 1;
        while (startIndex < s.length() -1 && s.charAt(startIndex) == s.charAt(startIndex+1)) {
            count++;
            startIndex++;
        }
        return count;
    }
}

```
