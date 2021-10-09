# [1249. Minimum Remove to Make Valid Parentheses (Medium)](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/)

<p>Given a string <font face="monospace">s</font> of <code>'('</code> , <code>')'</code> and lowercase English characters.</p>

<p>Your task is to remove the minimum number of parentheses ( <code>'('</code> or <code>')'</code>, in any positions ) so that the resulting <em>parentheses string</em> is valid and return <strong>any</strong> valid string.</p>

<p>Formally, a <em>parentheses string</em> is valid if and only if:</p>

<ul>
	<li>It is the empty string, contains only lowercase characters, or</li>
	<li>It can be written as <code>AB</code> (<code>A</code> concatenated with <code>B</code>), where <code>A</code> and <code>B</code> are valid strings, or</li>
	<li>It can be written as <code>(A)</code>, where <code>A</code> is a valid string.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "lee(t(c)o)de)"
<strong>Output:</strong> "lee(t(c)o)de"
<strong>Explanation:</strong> "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "a)b(c)d"
<strong>Output:</strong> "ab(c)d"
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "))(("
<strong>Output:</strong> ""
<strong>Explanation:</strong> An empty string is also valid.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> s = "(a(b(c)d)"
<strong>Output:</strong> "a(b(c)d)"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is either<code>'('</code> , <code>')'</code>, or lowercase English letter<code>.</code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Amazon](https://leetcode.com/company/amazon), [Yahoo](https://leetcode.com/company/yahoo), [Uber](https://leetcode.com/company/uber), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/)

**Similar Questions**:

- [Minimum Number of Swaps to Make the String Balanced (Medium)](https://leetcode.com/problems/minimum-number-of-swaps-to-make-the-string-balanced/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
    public String minRemoveToMakeValid(String s) {
        //find all the invalid indices in order at the end stringbuilder will not add those char at invalid indice
        Set<Integer> inValidIndices = new HashSet<>();
        Stack<Integer> stack = new Stack();
        for (int i=0; i<s.length(); i++) {
            char c = s.charAt(i);
            //if see (, add to stack, if stack.empty and see ) -> invalid, else if ) and stack.notEmpty -> pop stack
            if (c == '(') {
                stack.push(i);
            } else if (c == ')' && stack.isEmpty()) {
                inValidIndices.add(i);
            } else if (c == ')' && !stack.isEmpty()) {
                stack.pop();
            }
        }
        //here where the case of stackk contains all ((( -> need to check the stack again to add these indices
        while (!stack.isEmpty()) {
            inValidIndices.add(stack.pop());
        }
        //now output the String without invalid index
        StringBuilder sb = new StringBuilder();
        for (int i=0; i<s.length(); i++) {
            if (inValidIndices.contains(i)) continue;
            else sb.append(s.charAt(i));
        }
        return sb.toString();
  }
}

```
