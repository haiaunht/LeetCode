# [347. Top K Frequent Elements (Medium)](https://leetcode.com/problems/top-k-frequent-elements/)

<p>Given an integer array <code>nums</code> and an integer <code>k</code>, return <em>the</em> <code>k</code> <em>most frequent elements</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,1,2,2,3], k = 2
<strong>Output:</strong> [1,2]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>k</code> is in the range <code>[1, the number of unique elements in the array]</code>.</li>
	<li>It is <strong>guaranteed</strong> that the answer is <strong>unique</strong>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Your algorithm's time complexity must be better than <code>O(n log n)</code>, where n is the array's size.</p>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Yelp](https://leetcode.com/company/yelp), [VMware](https://leetcode.com/company/vmware), [Uber](https://leetcode.com/company/uber), [Adobe](https://leetcode.com/company/adobe), [eBay](https://leetcode.com/company/ebay), [HBO](https://leetcode.com/company/hbo)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Sorting](https://leetcode.com/tag/sorting/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/), [Bucket Sort](https://leetcode.com/tag/bucket-sort/), [Counting](https://leetcode.com/tag/counting/), [Quickselect](https://leetcode.com/tag/quickselect/)

**Similar Questions**:

- [Word Frequency (Medium)](https://leetcode.com/problems/word-frequency/)
- [Kth Largest Element in an Array (Medium)](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [Sort Characters By Frequency (Medium)](https://leetcode.com/problems/sort-characters-by-frequency/)
- [Split Array into Consecutive Subsequences (Medium)](https://leetcode.com/problems/split-array-into-consecutive-subsequences/)
- [Top K Frequent Words (Medium)](https://leetcode.com/problems/top-k-frequent-words/)
- [K Closest Points to Origin (Medium)](https://leetcode.com/problems/k-closest-points-to-origin/)
- [Sort Features by Popularity (Medium)](https://leetcode.com/problems/sort-features-by-popularity/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/top-k-frequent-elements/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        if (k == nums.length) return nums;
        //[1,1,1,2,2,3] -> {1:3, 2:2, 3:1} O(n)
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        //build a min heap to push each num and by its freq, poll() all the head only kep k count in heap
        PriorityQueue<Integer> minHeap = new PriorityQueue<>( (num1, num2) -> map.get(num1) - map.get(num2));
        //loop through map and add to min, for those min value ahead of k count in heap, discard
        for (int num : map.keySet()) {
            minHeap.add(num);
            if (minHeap.size() > k) {
                minHeap.poll();
            }
        }
        int[] result = new int[k];
        for (int i=0; i<result.length; i++) {
            result[i] = minHeap.poll();
        }
        return result;
    }
}

```
