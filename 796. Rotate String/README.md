# [796. Rotate String (Easy)](https://leetcode.com/problems/rotate-string/)

<p>We are given two strings, <code>s</code> and <code>goal</code>.</p>

<p>A <em>shift on </em><code>s</code> consists of taking string <code>s</code> and moving the leftmost character to the rightmost position. For example, if <code>s = 'abcde'</code>, then it will be <code>'bcdea'</code> after one shift on <code>s</code>. Return <code>true</code> if and only if <code>s</code> can become <code>goal</code> after some number of shifts on <code>s</code>.</p>

<pre><strong>Example 1:</strong>
<strong>Input:</strong> s = 'abcde', goal = 'cdeab'
<strong>Output:</strong> true

<strong>Example 2:</strong>
<strong>Input:</strong> s = 'abcde', goal = 'abced'
<strong>Output:</strong> false
</pre>

<p><strong>Note:</strong></p>

<ul>
	<li><code>s</code> and <code>goal</code> will have length at most <code>100</code>.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [String Matching](https://leetcode.com/tag/string-matching/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/rotate-string/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean rotateString(String s, String goal) {
        if (s.equals(goal)) return true;
        //shift all possible time, store in map and look for goal
        Map<String, Integer> map = new HashMap<>();
        for (int i=1; i<s.length(); i++) {
            String shift = s.substring(i) + s.substring(0, i);
            map.put(shift, map.getOrDefault(shift,0)+1);
        }
        return map.containsKey(goal);
    }
}

```
