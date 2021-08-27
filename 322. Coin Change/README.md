# [322. Coin Change (Medium)](https://leetcode.com/problems/coin-change/)

<p>You are given an integer array <code>coins</code> representing coins of different denominations and an integer <code>amount</code> representing a total amount of money.</p>

<p>Return <em>the fewest number of coins that you need to make up that amount</em>. If that amount of money cannot be made up by any combination of the coins, return <code>-1</code>.</p>

<p>You may assume that you have an infinite number of each kind of coin.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> coins = [1,2,5], amount = 11
<strong>Output:</strong> 3
<strong>Explanation:</strong> 11 = 5 + 5 + 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> coins = [2], amount = 3
<strong>Output:</strong> -1
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> coins = [1], amount = 0
<strong>Output:</strong> 0
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> coins = [1], amount = 1
<strong>Output:</strong> 1
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> coins = [1], amount = 2
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= coins.length &lt;= 12</code></li>
	<li><code>1 &lt;= coins[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>0 &lt;= amount &lt;= 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Bloomberg](https://leetcode.com/company/bloomberg), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Adobe](https://leetcode.com/company/adobe), [Uber](https://leetcode.com/company/uber), [Citadel](https://leetcode.com/company/citadel), [Zoom](https://leetcode.com/company/zoom), [tcs](https://leetcode.com/company/tcs)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:

- [Minimum Cost For Tickets (Medium)](https://leetcode.com/problems/minimum-cost-for-tickets/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/coin-change/
// Author: Please set your name in options page
// Time: O(amount * n)
// Space: O(amount)
class Solution {
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) return 0;
        //create a dp array to store the min move of each value of 0 -> amount
        int[] dp = new int[amount+1];
        Arrays.fill(dp, amount+1); //we can do Max_integer as well
        dp[0] = 0;
        for (int i=1; i<=amount; i++) {
            for (int j=0; j<coins.length; j++) {
                if (coins[j] <= i) {
                    dp[i] = Math.min(dp[i], dp[i-coins[j]] + 1);
                }
            }
        }
        if (dp[amount] > amount) return -1;
        return dp[amount];
    }
}

```
