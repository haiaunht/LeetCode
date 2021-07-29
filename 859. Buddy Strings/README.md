# [859. Buddy Strings (Easy)](https://leetcode.com/problems/buddy-strings/)

<p>Given two strings <code>s</code> and <code>goal</code>, return <code>true</code><em> if you can swap two letters in </em><code>s</code><em> so the result is equal to </em><code>goal</code><em>, otherwise, return </em><code>false</code><em>.</em></p>

<p>Swapping letters is defined as taking two indices <code>i</code> and <code>j</code> (0-indexed) such that <code>i != j</code> and swapping the characters at <code>s[i]</code> and <code>s[j]</code>.</p>

<ul>
	<li>For example, swapping at indices <code>0</code> and <code>2</code> in <code>"abcd"</code> results in <code>"cbad"</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "ab", goal = "ba"
<strong>Output:</strong> true
<strong>Explanation:</strong> You can swap s[0] = 'a' and s[1] = 'b' to get "ba", which is equal to goal.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "ab", goal = "ab"
<strong>Output:</strong> false
<strong>Explanation:</strong> The only letters you can swap are s[0] = 'a' and s[1] = 'b', which results in "ba" != goal.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "aa", goal = "aa"
<strong>Output:</strong> true
<strong>Explanation:</strong> You can swap s[0] = 'a' and s[1] = 'a' to get "aa", which is equal to goal.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = "aaaaaaabc", goal = "aaaaaaacb"
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length, goal.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>s</code> and <code>goal</code> consist of lowercase letters.</li>
</ul>

**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Determine if Two Strings Are Close (Medium)](https://leetcode.com/problems/determine-if-two-strings-are-close/)
- [Check if One String Swap Can Make Strings Equal (Easy)](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/buddy-strings/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean buddyStrings(String s, String goal) {
        if (s.length() != goal.length()) return false;
        if (s.equals(goal)) {
            Set<Character> set = new HashSet<>();
            for (char c : s.toCharArray()) {
                set.add(c);
            }
            if (set.size() < s.length()) return true;
            return false;
        } else {
            List<Integer> diff = new ArrayList<>();
            for (int i=0; i<s.length(); i++) {
                if (s.charAt(i) != goal.charAt(i)) {
                    diff.add(i);
                }
            }
            if (diff.size() != 2) return false;
            return (s.charAt(diff.get(0)) == goal.charAt(diff.get(1)))
                    && (s.charAt(diff.get(1)) == goal.charAt(diff.get(0)));
        }
    }
}
            return false;

```
