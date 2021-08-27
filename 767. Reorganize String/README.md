# [767. Reorganize String (Medium)](https://leetcode.com/problems/reorganize-string/)

<p>Given a string <code>s</code>, rearrange the characters of <code>s</code> so that any two adjacent characters are not the same.</p>

<p>Return <em>any possible rearrangement of</em> <code>s</code> <em>or return</em> <code>""</code> <em>if not possible</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "aab"
<strong>Output:</strong> "aba"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "aaab"
<strong>Output:</strong> ""
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 500</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Wish](https://leetcode.com/company/wish), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Greedy](https://leetcode.com/tag/greedy/), [Sorting](https://leetcode.com/tag/sorting/), [Heap (Priority Queue)](https://leetcode.com/tag/heap-priority-queue/), [Counting](https://leetcode.com/tag/counting/)

**Similar Questions**:

- [Rearrange String k Distance Apart (Hard)](https://leetcode.com/problems/rearrange-string-k-distance-apart/)
- [Task Scheduler (Medium)](https://leetcode.com/problems/task-scheduler/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/reorganize-string/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public String reorganizeString(String s) {
        //get count of each letters
        Map<Character, Integer> map = new HashMap<>();
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0)+1);
        }
        //use a max heap to put the characters with highest count first to pop to a stringbuilder
        PriorityQueue<Character> maxHeap = new PriorityQueue<>((a,b) -> map.get(b) - map.get(a));
        maxHeap.addAll(map.keySet());
        //now get every two character and add to string
        StringBuilder sb = new StringBuilder();
        while (maxHeap.size() > 1) {
            char first = maxHeap.remove();
            char second = maxHeap.remove();
            sb.append(first).append(second);
            //minus -1 from the map
            map.put(first, map.get(first)-1);
            map.put(second, map.get(second)-1);
            //after -1 still have count left, add back to the heap
            if (map.get(first) > 0) {
                maxHeap.add(first);
            }
            if (map.get(second) > 0) {
                maxHeap.add(second);
            }
        }
        //at last if there is only one character left in heap and the count is 1 -> true
        if (!maxHeap.isEmpty()) {
            char last = maxHeap.remove();
            if (map.get(last) > 1)  {
                return "";
            } else {
                sb.append(last);
            }
        }
        return sb.toString();
    }
}

```
