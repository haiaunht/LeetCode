# [921. Minimum Add to Make Parentheses Valid (Medium)](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)

<p>A parentheses string is valid if and only if:</p>

<ul>
	<li>It is the empty string,</li>
	<li>It can be written as <code>AB</code> (<code>A</code> concatenated with <code>B</code>), where <code>A</code> and <code>B</code> are valid strings, or</li>
	<li>It can be written as <code>(A)</code>, where <code>A</code> is a valid string.</li>
</ul>

<p>You are given a parentheses string <code>s</code>. In one move, you can insert a parenthesis at any position of the string.</p>

<ul>
	<li>For example, if <code>s = "()))"</code>, you can insert an opening parenthesis to be <code>"(<strong>(</strong>)))"</code> or a closing parenthesis to be <code>"())<strong>)</strong>)"</code>.</li>
</ul>

<p>Return <em>the minimum number of moves required to make </em><code>s</code><em> valid</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "())"
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "((("
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s[i]</code> is either <code>'('</code> or <code>')'</code>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Twitter](https://leetcode.com/company/twitter), [Amazon](https://leetcode.com/company/amazon), [Visa](https://leetcode.com/company/visa)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/), [Greedy](https://leetcode.com/tag/greedy/)

**Similar Questions**:

- [Minimum Number of Swaps to Make the String Balanced (Medium)](https://leetcode.com/problems/minimum-number-of-swaps-to-make-the-string-balanced/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int minAddToMakeValid(String s) {
        Set<Integer> invalidIndices = new HashSet<>();
        Stack<Integer> stack = new Stack();
        for (int i=0; i<s.length(); i++) {
            char curr = s.charAt(i);
            if (curr == '(') {
                stack.push(i);
            } else if (curr == ')' && stack.isEmpty()) {
                invalidIndices.add(i);
            } else if (curr == ')' && !stack.isEmpty()) {
                stack.pop();
            }
         }
        //here where the case of stackk contains all ((( -> need to check the stack again to add these indices
        while (!stack.isEmpty()) {
            invalidIndices.add(stack.pop());
        }
        return invalidIndices.size();
    }
}
        //here where the case of stackk contains all ((( -> need to check the stack again to add these indices

```
