# [1231. Divide Chocolate (Hard)](https://leetcode.com/problems/divide-chocolate/)

<p>You have one chocolate bar that consists of some chunks. Each chunk has its own sweetness given by the array&nbsp;<code>sweetness</code>.</p>

<p>You want to share the chocolate with your <code>k</code>&nbsp;friends so you start cutting the chocolate bar into <code>k + 1</code>&nbsp;pieces using&nbsp;<code>k</code>&nbsp;cuts, each piece consists of some <strong>consecutive</strong> chunks.</p>

<p>Being generous, you will eat the piece with the <strong>minimum total sweetness</strong> and give the other pieces to your friends.</p>

<p>Find the <strong>maximum total sweetness</strong> of the&nbsp;piece you can get by cutting the chocolate bar optimally.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> sweetness = [1,2,3,4,5,6,7,8,9], k = 5
<strong>Output:</strong> 6
<b>Explanation: </b>You can divide the chocolate to [1,2,3], [4,5], [6], [7], [8], [9]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> sweetness = [5,6,7,8,9,1,2,3,4], k = 8
<strong>Output:</strong> 1
<b>Explanation: </b>There is only one way to cut the bar into 9 pieces.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> sweetness = [1,2,2,1,2,2,1,2,2], k = 2
<strong>Output:</strong> 5
<b>Explanation: </b>You can divide the chocolate to [1,2,2], [1,2,2], [1,2,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= k &lt; sweetness.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= sweetness[i] &lt;= 10<sup>5</sup></code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/)

**Similar Questions**:

- [Split Array Largest Sum (Hard)](https://leetcode.com/problems/split-array-largest-sum/)
- [Capacity To Ship Packages Within D Days (Medium)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/divide-chocolate/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int maximizeSweetness(int[] sweetness, int k) {
        //if i have k friends, max can be sum / k+1
        int low = 1, high = Arrays.stream(sweetness).sum() / (k+1);
        while (low < high) {
            int mid = (low + high+1) / 2; //avoid infinite loop when low = mid
            if (canDivideChocolate(sweetness, k, mid)) {
                low = mid;
            } else {
                high = mid - 1;
            }
        }
        return low;
    }
    public boolean canDivideChocolate(int[] sweetness, int k, int mid) {
        int sum = 0;
        int chunks = 0;
        for (int i=0; i<sweetness.length; i++) {
            sum += sweetness[i];
            //if the sum so far >= mid, is good cut, -> chunks++ and reset sum to 0
            if (sum >= mid) {
                chunks++;
                sum = 0;
            }
        } 
        return chunks >= (k+1);
    }
}

```
