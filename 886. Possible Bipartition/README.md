# [886. Possible Bipartition (Medium)](https://leetcode.com/problems/possible-bipartition/)

<p>We want to split a group of <code>n</code> people (labeled from <code>1</code> to <code>n</code>) into two groups of <strong>any size</strong>. Each person may dislike some other people, and they should not go into the same group.</p>

<p>Given the integer <code>n</code> and the array <code>dislikes</code> where <code>dislikes[i] = [a<sub>i</sub>, b<sub>i</sub>]</code> indicates that the person labeled <code>a<sub>i</sub></code> does not like the person labeled <code>b<sub>i</sub></code>, return <code>true</code> <em>if it is possible to split everyone into two groups in this way</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 4, dislikes = [[1,2],[1,3],[2,4]]
<strong>Output:</strong> true
<strong>Explanation:</strong> group1 [1,4] and group2 [2,3].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 3, dislikes = [[1,2],[1,3],[2,3]]
<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 5, dislikes = [[1,2],[2,3],[3,4],[4,5],[1,5]]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2000</code></li>
	<li><code>0 &lt;= dislikes.length &lt;= 10<sup>4</sup></code></li>
	<li><code>dislikes[i].length == 2</code></li>
	<li><code>1 &lt;= dislikes[i][j] &lt;= n</code></li>
	<li><code>a<sub>i</sub> &lt; b<sub>i</sub></code></li>
	<li>All the pairs of <code>dislikes</code> are <strong>unique</strong>.</li>
</ul>

**Companies**:  
[ByteDance](https://leetcode.com/company/bytedance), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Graph](https://leetcode.com/tag/graph/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/possible-bipartition/
// Author: Please set your name in options page
// Time: O(n)
// Space: O(n)
class Solution {
    public boolean possibleBipartition(int n, int[][] dislikes) {
        List<Integer>[] graph = new List[n+1]; //number is from 1->4 so List[0] will be ignore
        int[] sides = new int[n+1];
        for (int i=0; i<n+1; i++) {
            graph[i] = new ArrayList<>();
        }
        for (int[] d : dislikes) {
            graph[d[0]].add(d[1]);
            graph[d[1]].add(d[0]);
        }
        //loop through, if adj list has differnt side then ok, if 0 which mean not visit, then visit
        for (int i=1; i<n+1; i++) {
            //check if == 0, not visit, 1 or -1 is visited
            if (sides[i] == 0) {
                //bfs
                Queue<Integer> queue = new LinkedList<>();
                queue.add(i);
                sides[i] = 1;
                while (!queue.isEmpty()) {
                    int curr = queue.poll();
                    //if curr has same sides with its adj which is wrong
                    for (int adj : graph[curr]) {
                        if (sides[curr] == sides[adj]) return false;
                        if (sides[adj] == 0) {
                            queue.add(adj);
                            sides[adj] = -sides[curr];
                        }
                    }
                }
            }
        }
        return true;
    }
}

```
