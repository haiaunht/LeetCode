# [415. Add Strings (Easy)](https://leetcode.com/problems/add-strings/)

<p>Given two non-negative integers, <code>num1</code> and <code>num2</code> represented as string, return <em>the sum of</em> <code>num1</code> <em>and</em> <code>num2</code> <em>as a string</em>.</p>

<p>You must solve the problem without using any built-in library for handling large integers (such as <code>BigInteger</code>). You must also not convert the inputs to integers directly.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> num1 = "11", num2 = "123"
<strong>Output:</strong> "134"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> num1 = "456", num2 = "77"
<strong>Output:</strong> "533"
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> num1 = "0", num2 = "0"
<strong>Output:</strong> "0"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 10<sup>4</sup></code></li>
	<li><code>num1</code> and <code>num2</code> consist of only digits.</li>
	<li><code>num1</code> and <code>num2</code> don't have any leading zeros except for the zero itself.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Oracle](https://leetcode.com/company/oracle), [Wayfair](https://leetcode.com/company/wayfair)

**Related Topics**:  
[String](https://leetcode.com/tag/string/)

**Similar Questions**:

- [Add Two Numbers (Medium)](https://leetcode.com/problems/add-two-numbers/)
- [Multiply Strings (Medium)](https://leetcode.com/problems/multiply-strings/)
- [Add to Array-Form of Integer (Easy)](https://leetcode.com/problems/add-to-array-form-of-integer/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/add-strings/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder result = new StringBuilder();
        int carry = 0;
        int len1 = num1.length()-1;
        int len2 = num2.length()-1;
        while (len1 >= 0 || len2 >= 0) {
            int first = 0,second = 0;
            if (len1 >= 0)
                first = num1.charAt(len1--) - '0';
            if (len2 >= 0)
                second = num2.charAt(len2--) - '0';
            int sum = carry + first + second;
            carry = 0;
            if (sum > 9) {
                carry = sum / 10;
            }
            result.append(sum % 10);
        }
        //if we are done and carry still = 1, add
        if (carry == 1) result.append(carry);
        return result.reverse().toString();
    }
}

```
