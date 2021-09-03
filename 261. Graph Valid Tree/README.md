# [261. Graph Valid Tree (Medium)](https://leetcode.com/problems/graph-valid-tree/)

<p>You have a graph of <code>n</code> nodes labeled from <code>0</code> to <code>n - 1</code>. You are given an integer n and a list of <code>edges</code> where <code>edges[i] = [a<sub>i</sub>, b<sub>i</sub>]</code> indicates that there is an undirected edge between nodes <code>a<sub>i</sub></code> and <code>b<sub>i</sub></code> in the graph.</p>

<p>Return <code>true</code> <em>if the edges of the given graph make up a valid tree, and</em> <code>false</code> <em>otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/tree1-graph.jpg" style="width: 222px; height: 302px;">
<pre><strong>Input:</strong> n = 5, edges = [[0,1],[0,2],[0,3],[1,4]]
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/tree2-graph.jpg" style="width: 382px; height: 222px;">
<pre><strong>Input:</strong> n = 5, edges = [[0,1],[1,2],[2,3],[1,3],[1,4]]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= 2000 &lt;= n</code></li>
	<li><code>0 &lt;= edges.length &lt;= 5000</code></li>
	<li><code>edges[i].length == 2</code></li>
	<li><code>0 &lt;= a<sub>i</sub>, b<sub>i</sub> &lt; n</code></li>
	<li><code>a<sub>i</sub> != b<sub>i</sub></code></li>
	<li>There are no self-loops or repeated edges.</li>
</ul>

**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin), [Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Graph](https://leetcode.com/tag/graph/)

**Similar Questions**:

- [Course Schedule (Medium)](https://leetcode.com/problems/course-schedule/)
- [Number of Connected Components in an Undirected Graph (Medium)](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
- [Keys and Rooms (Medium)](https://leetcode.com/problems/keys-and-rooms/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/graph-valid-tree/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public boolean validTree(int n, int[][] edges) {
       int[] graph = new int[n];
        Arrays.fill(graph, -1);
        for (int[] edge : edges) {
            int x = find(graph, edge[0]);
            int y = find(graph, edge[1]);
            //if (x==y) there is a cycle exist -> return false
            if (x == y) return false;
            union(graph, x, y);
        }
        //return edges.length == n-1 in case there is no cycle but there is not connect graph of all vertexies
        //example 4  [[0,1],[2,3]] -> no cycle but there only 2 edges for 4 vertexies -> false
        return edges.length==n-1;
    }
    private int find(int[] graph, int x) {
        if (graph[x] == -1) return x;
        return find(graph, graph[x]);
    }
    private void union(int[] graph, int x, int y) {
        graph[x] = y;
    }
}

```
