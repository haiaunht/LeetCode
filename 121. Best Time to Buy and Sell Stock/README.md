# [121. Best Time to Buy and Sell Stock (Easy)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

<p>You are given an array <code>prices</code> where <code>prices[i]</code> is the price of a given stock on the <code>i<sup>th</sup></code> day.</p>

<p>You want to maximize your profit by choosing a <strong>single day</strong> to buy one stock and choosing a <strong>different day in the future</strong> to sell that stock.</p>

<p>Return <em>the maximum profit you can achieve from this transaction</em>. If you cannot achieve any profit, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> prices = [7,1,5,3,6,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> prices = [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transactions are done and the max profit = 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= prices.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= prices[i] &lt;= 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [tcs](https://leetcode.com/company/tcs), [eBay](https://leetcode.com/company/ebay), [Bloomberg](https://leetcode.com/company/bloomberg), [Snapchat](https://leetcode.com/company/snapchat), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [ByteDance](https://leetcode.com/company/bytedance), [BlackRock](https://leetcode.com/company/blackrock), [Uber](https://leetcode.com/company/uber), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Visa](https://leetcode.com/company/visa), [Qualcomm](https://leetcode.com/company/qualcomm), [Intuit](https://leetcode.com/company/intuit), [Expedia](https://leetcode.com/company/expedia), [VMware](https://leetcode.com/company/vmware)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)

**Similar Questions**:

- [Maximum Subarray (Easy)](https://leetcode.com/problems/maximum-subarray/)
- [Best Time to Buy and Sell Stock II (Easy)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
- [Best Time to Buy and Sell Stock III (Hard)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
- [Best Time to Buy and Sell Stock IV (Hard)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
- [Best Time to Buy and Sell Stock with Cooldown (Medium)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int maxProfit(int[] prices) {
        //check each currrent - lowestStockprice > maxProfit then it will be the max profit
        int maxProfit = 0;
        int lowestStockPrice = Integer.MAX_VALUE;
        for (int i=0; i<prices.length; i++) {
            //first pointer to find the min stock price
            if (prices[i] < lowestStockPrice) {
                lowestStockPrice = prices[i];
            }
            //second pointer to keep track maxProfit
            if (prices[i] - lowestStockPrice > maxProfit) {
                maxProfit = prices[i] - lowestStockPrice;
            }
        }
        return maxProfit;
    }
}

```
