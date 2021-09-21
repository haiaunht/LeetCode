# [43. Multiply Strings (Medium)](https://leetcode.com/problems/multiply-strings/)

<p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as strings, return the product of <code>num1</code> and <code>num2</code>, also represented as a string.</p>

<p><strong>Note:</strong>&nbsp;You must not use any built-in BigInteger library or convert the inputs to integer directly.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> num1 = "2", num2 = "3"
<strong>Output:</strong> "6"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> num1 = "123", num2 = "456"
<strong>Output:</strong> "56088"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 200</code></li>
	<li><code>num1</code> and <code>num2</code> consist of digits only.</li>
	<li>Both <code>num1</code> and <code>num2</code>&nbsp;do not contain any leading zero, except the number <code>0</code> itself.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [String](https://leetcode.com/tag/string/), [Simulation](https://leetcode.com/tag/simulation/)

**Similar Questions**:

- [Add Two Numbers (Medium)](https://leetcode.com/problems/add-two-numbers/)
- [Plus One (Easy)](https://leetcode.com/problems/plus-one/)
- [Add Binary (Easy)](https://leetcode.com/problems/add-binary/)
- [Add Strings (Easy)](https://leetcode.com/problems/add-strings/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/multiply-strings/
// Author: Please set your name in options page
// Time: O(num1.length() * num2.length())
// Space: O(num1.length() + num2.length())
class Solution {
    public String multiply(String num1, String num2) {
        if (num1.equals("0") || num2.equals("0")) return "0";
        if (num1.equals("1")) return num2;
        if (num2.equals("1")) return num1;
        int[] result = new int[num1.length() + num2.length()];
        for (int i=num1.length()-1; i>=0; i--) {
            for (int j=num2.length()-1; j>=0; j--) {
                int multi = (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
                int currentSum = result[i+j+1] + multi;
                result[i+j+1] = currentSum % 10;
                result[i+j] += currentSum / 10;
            }
        }
        StringBuilder sb = new StringBuilder();
        for (int i : result) {
            if (sb.length() != 0 || i != 0) {
                sb.append(i);
            }
        }
        return sb.toString();
    }
}

```
