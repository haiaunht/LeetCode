# [1155. Number of Dice Rolls With Target Sum (Medium)](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/)

<p>You have <code>d</code> dice and each die has <code>f</code> faces numbered <code>1, 2, ..., f</code>.</p>

<p>Return the number of possible ways (out of <code>f<sup>d</sup></code> total ways) <strong>modulo</strong> 10<sup>9</sup> + 7 to roll the dice so the sum of the face-up numbers equals <code>target</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> d = 1, f = 6, target = 3
<strong>Output:</strong> 1
<strong>Explanation: </strong>
You throw one die with 6 faces.  There is only one way to get a sum of 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> d = 2, f = 6, target = 7
<strong>Output:</strong> 6
<strong>Explanation: </strong>
You throw two dice, each with 6 faces.  There are 6 ways to get a sum of 7:
1+6, 2+5, 3+4, 4+3, 5+2, 6+1.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> d = 2, f = 5, target = 10
<strong>Output:</strong> 1
<strong>Explanation: </strong>
You throw two dice, each with 5 faces.  There is only one way to get a sum of 10: 5+5.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> d = 1, f = 2, target = 3
<strong>Output:</strong> 0
<strong>Explanation: </strong>
You throw one die with 2 faces.  There is no way to get a sum of 3.
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> d = 30, f = 30, target = 500
<strong>Output:</strong> 222616187
<strong>Explanation: </strong>
The answer must be returned modulo 10^9 + 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= d, f &lt;= 30</code></li>
	<li><code>1 &lt;= target &lt;= 1000</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)

**Similar Questions**:

- [Equal Sum Arrays With Minimum Number of Operations (Medium)](https://leetcode.com/problems/equal-sum-arrays-with-minimum-number-of-operations/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numRollsToTarget(int d, int f, int target) {
        int MOD = 1000000007;
        if (d==1) {
            if (f < target) return 0;
            else return 1;
        }
        int[][] diceAndTarget = new int[d+1][target+1];
        //assign first cell = 1, then each cell after = the prior cell + current cell
        diceAndTarget[0][0] = 1;
        for (int i=1; i<d+1; i++) {
            for (int j=1; j<target+1; j++) {
                for (int k=1; k<f+1; k++) {
                    if (j - k < 0) continue;
                    diceAndTarget[i][j] = (diceAndTarget[i][j] + diceAndTarget[i-1][j-k]) % MOD;
                }
            }
        }
        return diceAndTarget[d][target];
    }
}

```
