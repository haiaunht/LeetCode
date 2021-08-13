# [227. Basic Calculator II (Medium)](https://leetcode.com/problems/basic-calculator-ii/)

<p>Given a string <code>s</code> which represents an expression, <em>evaluate this expression and return its value</em>.&nbsp;</p>

<p>The integer division should truncate toward zero.</p>

<p>You may assume that the given expression is always valid. All intermediate results will be in the range of <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code>.</p>

<p><strong>Note:</strong> You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as <code>eval()</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "3+2*2"
<strong>Output:</strong> 7
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = " 3/2 "
<strong>Output:</strong> 1
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = " 3+5 / 2 "
<strong>Output:</strong> 5
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists of integers and operators <code>('+', '-', '*', '/')</code> separated by some number of spaces.</li>
	<li><code>s</code> represents <strong>a valid expression</strong>.</li>
	<li>All the integers in the expression are non-negative integers in the range <code>[0, 2<sup>31</sup> - 1]</code>.</li>
	<li>The answer is <strong>guaranteed</strong> to fit in a <strong>32-bit integer</strong>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber), [Roblox](https://leetcode.com/company/roblox), [Snapchat](https://leetcode.com/company/snapchat)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/)

**Similar Questions**:

- [Basic Calculator (Hard)](https://leetcode.com/problems/basic-calculator/)
- [Expression Add Operators (Hard)](https://leetcode.com/problems/expression-add-operators/)
- [Basic Calculator III (Hard)](https://leetcode.com/problems/basic-calculator-iii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/basic-calculator-ii/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int calculate(String s) {
        int result = 0;
        int currentNum = 0;
        int i=0;
        Stack<Integer> stack = new Stack<>();
        char currOperation = '+'; //everthing will add from the stack, so if minus 2 put -2 in the stack
        //"3+2*2"
        while (i<s.length()) {
            //3, check if currChar is still Digit add to currentNum
            //or if is operations, push the digit found before to the stack, at last index do the same
            char currChar = s.charAt(i);
            if (Character.isDigit(currChar)) {
                currentNum = currentNum*10 + (currChar - '0');
            }
            //push to the stack if its + or -, if / or * calculate then push
            if (!Character.isDigit(currChar) && !Character.isWhitespace(currChar) || i==s.length()-1) {
                if (currOperation == '+') {
                    stack.push(currentNum);
                }
                if (currOperation == '-') {
                    stack.push(-currentNum);
                }
                if (currOperation == '*') {
                    stack.push(currentNum * stack.pop());
                }
                if (currOperation == '/') {
                    stack.push(stack.pop() / currentNum );
                }
                //reset the current operation (if char is number will not be here)
                currOperation = currChar;
                currentNum = 0;
            }
            i++;
        }
        for (int num : stack) {
            result += num;
        }
        return result;
    }
}

```
