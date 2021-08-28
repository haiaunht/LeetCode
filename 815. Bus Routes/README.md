# [815. Bus Routes (Hard)](https://leetcode.com/problems/bus-routes/)

<p>You are given an array <code>routes</code> representing bus routes where <code>routes[i]</code> is a bus route that the <code>i<sup>th</sup></code> bus repeats forever.</p>

<ul>
	<li>For example, if <code>routes[0] = [1, 5, 7]</code>, this means that the <code>0<sup>th</sup></code> bus travels in the sequence <code>1 -&gt; 5 -&gt; 7 -&gt; 1 -&gt; 5 -&gt; 7 -&gt; 1 -&gt; ...</code> forever.</li>
</ul>

<p>You will start at the bus stop <code>source</code> (You are not on any bus initially), and you want to go to the bus stop <code>target</code>. You can travel between bus stops by buses only.</p>

<p>Return <em>the least number of buses you must take to travel from </em><code>source</code><em> to </em><code>target</code>. Return <code>-1</code> if it is not possible.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> routes = [[1,2,7],[3,6,7]], source = 1, target = 6
<strong>Output:</strong> 2
<strong>Explanation:</strong> The best strategy is take the first bus to the bus stop 7, then take the second bus to the bus stop 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> routes = [[7,12],[4,5,15],[6],[15,19],[9,12,13]], source = 15, target = 12
<strong>Output:</strong> -1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= routes.length &lt;= 500</code>.</li>
	<li><code>1 &lt;= routes[i].length &lt;= 10<sup>5</sup></code></li>
	<li>All the values of <code>routes[i]</code> are <strong>unique</strong>.</li>
	<li><code>sum(routes[i].length) &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= routes[i][j] &lt; 10<sup>6</sup></code></li>
	<li><code>0 &lt;= source, target &lt; 10<sup>6</sup></code></li>
</ul>

**Companies**:  
[Uber](https://leetcode.com/company/uber), [Square](https://leetcode.com/company/square), [Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/bus-routes/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int numBusesToDestination(int[][] routes, int source, int target) {
        if (source == target) return 0;
        Map<Integer, List<Integer>> graph = new HashMap<>();
        generateGraph(routes, graph);
        Set<Integer> visited = new HashSet<>();
        Queue<Integer> queue = new LinkedList<>();
        queue.add(source);
        int level = 0;
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i=0; i<size; i++) {
                int stopNum = queue.poll();
                //if found return the level, else mark as visited and add all the stop relate to it
                if (stopNum == target) return level;
                //call all the bus # associate with this stop
                List<Integer> buses = graph.get(stopNum);
                for (int bus : buses) {
                    if (visited.contains(bus)) continue;
                    visited.add(bus);
                    //loop through all the stop belong to this bus
                    for (int stop=0; stop<routes[bus].length; stop++) {
                       queue.add(routes[bus][stop]);
                    }
                }
            }
            level++;
        }
        return -1;
    }
    private void generateGraph(int[][] routes, Map<Integer, List<Integer>> graph) {
        //at each route #, add its bus's number
        for (int i=0; i<routes.length; i++) {
            for (int j=0; j<routes[i].length; j++) {
                graph.putIfAbsent(routes[i][j], new ArrayList<>());
                graph.get(routes[i][j]).add(i);
            }
        }
    }
}

```
