# [50. Pow(x, n) (Medium)](https://leetcode.com/problems/powx-n/)

<p>Implement <a href="http://www.cplusplus.com/reference/valarray/pow/" target="_blank">pow(x, n)</a>, which calculates <code>x</code> raised to the power <code>n</code> (i.e., <code>x<sup>n</sup></code>).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> x = 2.00000, n = 10
<strong>Output:</strong> 1024.00000
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> x = 2.10000, n = 3
<strong>Output:</strong> 9.26100
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> x = 2.00000, n = -2
<strong>Output:</strong> 0.25000
<strong>Explanation:</strong> 2<sup>-2</sup> = 1/2<sup>2</sup> = 1/4 = 0.25
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-100.0 &lt;&nbsp;x&nbsp;&lt; 100.0</code></li>
	<li><code>-2<sup>31</sup>&nbsp;&lt;= n &lt;=&nbsp;2<sup>31</sup>-1</code></li>
	<li><code>-10<sup>4</sup> &lt;= x<sup>n</sup> &lt;= 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [LinkedIn](https://leetcode.com/company/linkedin), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon), [Walmart Labs](https://leetcode.com/company/walmart-labs), [eBay](https://leetcode.com/company/ebay), [Oracle](https://leetcode.com/company/oracle), [Salesforce](https://leetcode.com/company/salesforce)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:

- [Sqrt(x) (Easy)](https://leetcode.com/problems/sqrtx/)
- [Super Pow (Medium)](https://leetcode.com/problems/super-pow/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/powx-n/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public double myPow(double x, int n) {
        long N = n;
        if (N < 0) {
            x = 1/x;
            N = -N;
        }
        return fastPow(x, N);
    }
    public double fastPow(double x, long n) {
        if (n==0) return 1.0;
        double half = fastPow(x, n / 2);
        if (n%2==0) {
            return half * half;
        } else {
            return x * half * half;
        }
    }
}
        } else {

```
