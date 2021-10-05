# [1088. Confusing Number II (Hard)](https://leetcode.com/problems/confusing-number-ii/)

<p>A <strong>confusing number</strong> is a number that when rotated <code>180</code> degrees becomes a different number with <strong>each digit valid</strong>.</p>

<p>We can rotate digits of a number by <code>180</code> degrees to form new digits.</p>

<ul>
	<li>When <code>0</code>, <code>1</code>, <code>6</code>, <code>8</code>, and <code>9</code> are rotated <code>180</code> degrees, they become <code>0</code>, <code>1</code>, <code>9</code>, <code>8</code>, and <code>6</code> respectively.</li>
	<li>When <code>2</code>, <code>3</code>, <code>4</code>, <code>5</code>, and <code>7</code> are rotated <code>180</code> degrees, they become <strong>invalid</strong>.</li>
</ul>

<p>Note that after rotating a number, we can ignore leading zeros.</p>

<ul>
	<li>For example, after rotating <code>8000</code>, we have <code>0008</code> which is considered as just <code>8</code>.</li>
</ul>

<p>Given an integer <code>n</code>, return <em>the number of <strong>confusing numbers</strong> in the inclusive range </em><code>[1, n]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 20
<strong>Output:</strong> 6
<strong>Explanation:</strong> The confusing numbers are [6,9,10,16,18,19].
6 converts to 9.
9 converts to 6.
10 converts to 01 which is just 1.
16 converts to 91.
18 converts to 81.
19 converts to 61.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 100
<strong>Output:</strong> 19
<strong>Explanation:</strong> The confusing numbers are [6,9,10,16,18,19,60,61,66,68,80,81,86,89,90,91,98,99,100].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google)

**Related Topics**:  
[Math](https://leetcode.com/tag/math/), [Backtracking](https://leetcode.com/tag/backtracking/)

**Similar Questions**:

- [Confusing Number (Easy)](https://leetcode.com/problems/confusing-number/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/confusing-number-ii/
// Author: Please set your name in options page
// only 2 test cases not passing due to TLE
// Time: O(E)
// Space: O(1)
class Solution {
    public int confusingNumberII(int n) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 0);
        map.put(1, 1);
        map.put(6, 9);
        map.put(8, 8);
        map.put(9, 6);
        Map<Integer, Integer> confuseNumChecked = new HashMap<>();
        int count = 0;
        for (int i=1; i<=n; i++) {
            int curr = isConfuse(i, map);
            if (curr != -1 && rotate(i, map) != i) {
                count++;
                confuseNumChecked.put(i, curr);
            }
        }
        return count;
    }
    public int isConfuse(int num, Map<Integer, Integer> map) {
        int tmp = 0;
        while (num > 0) {
            if (!map.containsKey(num%10) ) return -1;
            tmp = map.get(num%10);
            num /= 10;
        }
        return tmp;
    }
    public int rotate(int num, Map<Integer, Integer> map) {
        int res = 0;
        while (num > 0) {
            res = res*10 + map.get(num%10);
            num /= 10;
        }
        return res;
    }
}

```
