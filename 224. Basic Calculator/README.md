# [224. Basic Calculator (Hard)](https://leetcode.com/problems/basic-calculator/)

<p>Given a string <code>s</code> representing a valid expression, implement a basic calculator to evaluate it, and return <em>the result of the evaluation</em>.</p>

<p><strong>Note:</strong> You are <strong>not</strong> allowed to use any built-in function which evaluates strings as mathematical expressions, such as <code>eval()</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "1 + 1"
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = " 2-1 + 2 "
<strong>Output:</strong> 3
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = "(1+(4+5+2)-3)+(6+8)"
<strong>Output:</strong> 23
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3&nbsp;* 10<sup>5</sup></code></li>
	<li><code>s</code> consists of digits, <code>'+'</code>, <code>'-'</code>, <code>'('</code>, <code>')'</code>, and <code>' '</code>.</li>
	<li><code>s</code> represents a valid expression.</li>
	<li><code>'+'</code> is not used as a unary operation.</li>
	<li><code>'-'</code> could be used as a unary operation but it has to be inside parentheses.</li>
	<li>There will be no two consecutive operators in the input.</li>
	<li>Every number and running calculation will fit in a signed 32-bit integer.</li>
</ul>

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Karat](https://leetcode.com/company/karat), [Amazon](https://leetcode.com/company/amazon), [Roblox](https://leetcode.com/company/roblox), [Google](https://leetcode.com/company/google), [eBay](https://leetcode.com/company/ebay), [Apple](https://leetcode.com/company/apple), [Bolt](https://leetcode.com/company/bolt), [Indeed](https://leetcode.com/company/indeed), [Yahoo](https://leetcode.com/company/yahoo), [ByteDance](https://leetcode.com/company/bytedance), [Wish](https://leetcode.com/company/wish), [Shopee](https://leetcode.com/company/shopee)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/), [Stack](https://leetcode.com/tag/stack/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:

- [Evaluate Reverse Polish Notation (Medium)](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
- [Basic Calculator II (Medium)](https://leetcode.com/problems/basic-calculator-ii/)
- [Different Ways to Add Parentheses (Medium)](https://leetcode.com/problems/different-ways-to-add-parentheses/)
- [Expression Add Operators (Hard)](https://leetcode.com/problems/expression-add-operators/)
- [Basic Calculator III (Hard)](https://leetcode.com/problems/basic-calculator-iii/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/basic-calculator/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int calculate(String s) {
        //use the stack to store operation after '('
        //if curr operation = stack.pop() = + or - =>{ -(-) = + || +(+) = + } else = -
        //only store oper after ( so if stack empty => oper is +
        Stack<Character> operations = new Stack<>();
        int result = 0;
        int currentNum = 0;
        char operation = '+';
        int i=0;
        // Stack<Character> stackInParentheses = new Stack<>();
        while (i<s.length()) {
            char currChar = s.charAt(i);
            if (Character.isDigit(currChar)) {
                currentNum = currentNum*10 + (currChar - '0');
            }
            if (currChar == '+' || currChar == '-' || i==s.length()-1) {
                // +(+)= + and -(-)=+, else -(+)=-
                if (operation=='+') {
                    result = result + currentNum;
                } else {
                    result = result - currentNum;
                }
                //reset the operation
                if (operations.isEmpty()) {
                    operation = currChar;
                } else {
                    operation = (currChar==operations.peek()) ? '+' : '-';
                }
                currentNum = 0;
            } else if (currChar == '(') {
                operations.push(operation);
            } else if (currChar == ')') {
                operations.pop();
            }
            i++;
        }
        return result;
    }
}

```
