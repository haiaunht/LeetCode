# [239. Sliding Window Maximum (Hard)](https://leetcode.com/problems/sliding-window-maximum/)

<p>You are given an array of integers&nbsp;<code>nums</code>, there is a sliding window of size <code>k</code> which is moving from the very left of the array to the very right. You can only see the <code>k</code> numbers in the window. Each time the sliding window moves right by one position.</p>

<p>Return <em>the max sliding window</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,-1,-3,5,3,6,7], k = 3
<strong>Output:</strong> [3,3,5,5,6,7]
<strong>Explanation:</strong> 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       <strong>3</strong>
 1 [3  -1  -3] 5  3  6  7       <strong>3</strong>
 1  3 [-1  -3  5] 3  6  7      <strong> 5</strong>
 1  3  -1 [-3  5  3] 6  7       <strong>5</strong>
 1  3  -1  -3 [5  3  6] 7       <strong>6</strong>
 1  3  -1  -3  5 [3  6  7]      <strong>7</strong>
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1,-1], k = 1
<strong>Output:</strong> [1,-1]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> nums = [9,11], k = 2
<strong>Output:</strong> [11]
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> nums = [4,-2], k = 2
<strong>Output:</strong> [4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Microsoft](https://leetcode.com/company/microsoft), [Twilio](https://leetcode.com/company/twilio), [Rubrik](https://leetcode.com/company/rubrik), [Citadel](https://leetcode.com/company/citadel), [Yahoo](https://leetcode.com/company/yahoo), [Infosys](https://leetcode.com/company/infosys)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Queue](https://leetcode.com/tag/queue/), [Sliding Window](https://leetcode.com/tag/sliding-window/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/), [Monotonic Queue](https://leetcode.com/tag/monotonic-queue/)

**Similar Questions**:

- [Minimum Window Substring (Hard)](https://leetcode.com/problems/minimum-window-substring/)
- [Min Stack (Easy)](https://leetcode.com/problems/min-stack/)
- [Longest Substring with At Most Two Distinct Characters (Medium)](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
- [Paint House II (Hard)](https://leetcode.com/problems/paint-house-ii/)
- [Jump Game VI (Medium)](https://leetcode.com/problems/jump-game-vi/)

## Solution 1.

````java
# [239. Sliding Window Maximum (Hard)](https://leetcode.com/problems/sliding-window-maximum/)

<p>You are given an array of integers&nbsp;<code>nums</code>, there is a sliding window of size <code>k</code> which is moving from the very left of the array to the very right. You can only see the <code>k</code> numbers in the window. Each time the sliding window moves right by one position.</p>

<p>Return <em>the max sliding window</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,-1,-3,5,3,6,7], k = 3
<strong>Output:</strong> [3,3,5,5,6,7]
<strong>Explanation:</strong>
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       <strong>3</strong>
 1 [3  -1  -3] 5  3  6  7       <strong>3</strong>
 1  3 [-1  -3  5] 3  6  7      <strong> 5</strong>
 1  3  -1 [-3  5  3] 6  7       <strong>5</strong>
 1  3  -1  -3 [5  3  6] 7       <strong>6</strong>
 1  3  -1  -3  5 [3  6  7]      <strong>7</strong>
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1,-1], k = 1
<strong>Output:</strong> [1,-1]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> nums = [9,11], k = 2
<strong>Output:</strong> [11]
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> nums = [4,-2], k = 2
<strong>Output:</strong> [4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>


**Companies**:
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Microsoft](https://leetcode.com/company/microsoft), [Twilio](https://leetcode.com/company/twilio), [Rubrik](https://leetcode.com/company/rubrik), [Citadel](https://leetcode.com/company/citadel), [Yahoo](https://leetcode.com/company/yahoo), [Infosys](https://leetcode.com/company/infosys)

**Related Topics**:
[Array](https://leetcode.com/tag/array/), [Queue](https://leetcode.com/tag/queue/), [Sliding Window](https://leetcode.com/tag/sliding-window/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/), [Monotonic Queue](https://leetcode.com/tag/monotonic-queue/)

**Similar Questions**:
* [Minimum Window Substring (Hard)](https://leetcode.com/problems/minimum-window-substring/)
* [Min Stack (Easy)](https://leetcode.com/problems/min-stack/)
* [Longest Substring with At Most Two Distinct Characters (Medium)](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
* [Paint House II (Hard)](https://leetcode.com/problems/paint-house-ii/)
* [Jump Game VI (Medium)](https://leetcode.com/problems/jump-game-vi/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/sliding-window-maximum/solution/
// Author: Please set your name in options page
// Time: O(N)
// Space: O(N)
class Solution {
  public int[] maxSlidingWindow(int[] nums, int k) {
    //edge case where nums is null or k=0
      if (nums.length*k == 0) return new int[0];
      if (k==1) return nums;
      //else the length of the result will be nums.length - k + 1
      int[] result = new int[nums.length - k + 1];
      //create a array to store the max of each block k from start to end index from LEFT -> RIGHT
      int[] leftMax = new int[nums.length];
      leftMax[0] = nums[0];
      //create a array to store the max of each block k from end to start index from RIGHT -> LEFT
      int[] rightMax = new int[nums.length];
      rightMax[nums.length-1] = nums[nums.length-1];
      //generate the leftMax and rightMax
      for (int i=1; i<nums.length; i++) {
          //from left to right, at each element start at each block, keep that number, else number after will be Math.max(left(i-1),nums[i])
          //each block k, the start index will % k == 0 ex: k=3, start index will be 0 (0->2) or 3(3->5) or 6...
          if (i%k == 0) {
              leftMax[i] = nums[i];
          } else {
              leftMax[i] = Math.max(leftMax[i-1], nums[i]);
          }
          //rightMax, where end index of each block j is oposite i position = n-i-1
          int j = nums.length - i - 1; //j at 2, 5, ... so j+1%k==0
          if ((j+1)%k == 0) {
              rightMax[j] = nums[j];
          } else {
              rightMax[j] = Math.max(rightMax[j+1], nums[j]);
          }
      }
      //loop throught comparet end of block of Left to start of block of right
      for (int i=0; i<nums.length-k+1; i++) {
          result[i] = Math.max(leftMax[i+k-1], rightMax[i]);
      }
      return result;
  }
}

````
