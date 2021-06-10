# [973. K Closest Points to Origin (Medium)](https://leetcode.com/problems/k-closest-points-to-origin/)

<p>Given an array of <code>points</code> where <code>points[i] = [x<sub>i</sub>, y<sub>i</sub>]</code> represents a point on the <strong>X-Y</strong> plane and an integer <code>k</code>, return the <code>k</code> closest points to the origin <code>(0, 0)</code>.</p>

<p>The distance between two points on the <strong>X-Y</strong> plane is the Euclidean distance (i.e., <code>√(x<sub>1</sub> - x<sub>2</sub>)<sup>2</sup> + (y<sub>1</sub> - y<sub>2</sub>)<sup>2</sup></code>).</p>

<p>You may return the answer in <strong>any order</strong>. The answer is <strong>guaranteed</strong> to be <strong>unique</strong> (except for the order that it is in).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/03/closestplane1.jpg" style="width: 400px; height: 400px;">
<pre><strong>Input:</strong> points = [[1,3],[-2,2]], k = 1
<strong>Output:</strong> [[-2,2]]
<strong>Explanation:</strong>
The distance between (1, 3) and the origin is sqrt(10).
The distance between (-2, 2) and the origin is sqrt(8).
Since sqrt(8) &lt; sqrt(10), (-2, 2) is closer to the origin.
We only want the closest k = 1 points from the origin, so the answer is just [[-2,2]].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> points = [[3,3],[5,-1],[-2,4]], k = 2
<strong>Output:</strong> [[3,3],[-2,4]]
<strong>Explanation:</strong> The answer [[-2,4],[3,3]] would also be accepted.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= points.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt; x<sub>i</sub>, y<sub>i</sub> &lt; 10<sup>4</sup></code></li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [DoorDash](https://leetcode.com/company/doordash), [LinkedIn](https://leetcode.com/company/linkedin), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Uber](https://leetcode.com/company/uber), [ByteDance](https://leetcode.com/company/bytedance), [Apple](https://leetcode.com/company/apple), [Asana](https://leetcode.com/company/asana)

**Related Topics**:  
[Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Heap](https://leetcode.com/tag/heap/), [Sort](https://leetcode.com/tag/sort/)

**Similar Questions**:

- [Kth Largest Element in an Array (Medium)](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [Top K Frequent Elements (Medium)](https://leetcode.com/problems/top-k-frequent-elements/)
- [Top K Frequent Words (Medium)](https://leetcode.com/problems/top-k-frequent-words/)
- [Find Nearest Point That Has the Same X or Y Coordinate (Easy)](https://leetcode.com/problems/find-nearest-point-that-has-the-same-x-or-y-coordinate/)

## Solution 1.

```JAVA
// OJ: https://leetcode.com/problems/k-closest-points-to-origin/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[][] kClosest(int[][] points, int k) {
        int n = points.length;
        int[] distances = new int[n];
        //calculate distance for each points
        for (int i=0; i<n; i++) {
            int x = points[i][0];
            int y = points[i][1];
            int dis = (x*x + y*y);
            distances[i] = dis;
        }
        //how to sort distances and keep track of its points???        
        Integer[] orderByDistance = new Integer[n];
        for (int i=0; i<n; i++) {
            orderByDistance[i] = i;
        }
        //now sort the number in orderByDistance by caomparing value in distance
        Arrays.sort(orderByDistance, (a,b) -> Integer.compare(distances[a], distances[b]));
        //now from 0->k-1, retreive the order in orderByDistance and its values in points[][]
        int[][] result = new int[k][2];
        for (int i=0; i<k; i++) {
            //get orderByDistance value from 0-k-1 
            result[i] = points[orderByDistance[i]];
        }
        return result;
    }
}

```
