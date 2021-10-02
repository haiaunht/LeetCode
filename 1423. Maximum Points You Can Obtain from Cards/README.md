# [1423. Maximum Points You Can Obtain from Cards (Medium)](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

<p>There are several cards <strong>arranged in a row</strong>, and each card has an associated number of points. The points are given in the integer array <code>cardPoints</code>.</p>

<p>In one step, you can take one card from the beginning or from the end of the row. You have to take exactly <code>k</code> cards.</p>

<p>Your score is the sum of the points of the cards you have taken.</p>

<p>Given the integer array <code>cardPoints</code> and the integer <code>k</code>, return the <em>maximum score</em> you can obtain.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> cardPoints = [1,2,3,4,5,6,1], k = 3
<strong>Output:</strong> 12
<strong>Explanation:</strong> After the first step, your score will always be 1. However, choosing the rightmost card first will maximize your total score. The optimal strategy is to take the three cards on the right, giving a final score of 1 + 6 + 5 = 12.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> cardPoints = [2,2,2], k = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Regardless of which two cards you take, your score will always be 4.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> cardPoints = [9,7,7,9,7,7,9], k = 7
<strong>Output:</strong> 55
<strong>Explanation:</strong> You have to take all the cards. Your score is the sum of points of all cards.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> cardPoints = [1,1000,1], k = 1
<strong>Output:</strong> 1
<strong>Explanation:</strong> You cannot take the card in the middle. Your best score is 1. 
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> cardPoints = [1,79,80,1,1,1,200,1], k = 3
<strong>Output:</strong> 202
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= cardPoints.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= cardPoints[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= cardPoints.length</code></li>
</ul>

**Companies**:  
[Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Sliding Window](https://leetcode.com/tag/sliding-window/), [Prefix Sum](https://leetcode.com/tag/prefix-sum/)

**Similar Questions**:

- [Maximum Score from Performing Multiplication Operations (Medium)](https://leetcode.com/problems/maximum-score-from-performing-multiplication-operations/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(1)
class Solution {
    public int maxScore(int[] cardPoints, int k) {
        int len = cardPoints.length;
        if (len == k) return Arrays.stream(cardPoints).sum();
        if (k == 1) return Math.max(cardPoints[0], cardPoints[len-1]);
        int frontTotal = 0;
        int backTotal = 0;
        //cal total of the first k from the front, then pop from k-1 + back[len-(k-i)] and compare each time
        int maxScore = 0;
        for (int i=0; i < k; i++) {
            frontTotal += cardPoints[i];
        }
        //assign this as max score for now
        maxScore = frontTotal;
        for (int i=k-1; i>=0; i--) {
            backTotal += cardPoints[len - (k-i)] ;
            //minus element at right most from front side, cal total again and compare
            frontTotal -= cardPoints[i];
            int currentTotal = frontTotal + backTotal;
            maxScore = Math.max(maxScore, currentTotal);
        }
        return maxScore;
    }
}

```
