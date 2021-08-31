# [636. Exclusive Time of Functions (Medium)](https://leetcode.com/problems/exclusive-time-of-functions/)

<p>On a <strong>single-threaded</strong> CPU, we execute a program containing <code>n</code> functions. Each function has a unique ID between <code>0</code> and <code>n-1</code>.</p>

<p>Function calls are <strong>stored in a <a href="https://en.wikipedia.org/wiki/Call_stack">call stack</a></strong>: when a function call starts, its ID is pushed onto the stack, and when a function call ends, its ID is popped off the stack. The function whose ID is at the top of the stack is <strong>the current function being executed</strong>. Each time a function starts or ends, we write a log with the ID, whether it started or ended, and the timestamp.</p>

<p>You are given a list <code>logs</code>, where <code>logs[i]</code> represents the <code>i<sup>th</sup></code> log message formatted as a string <code>"{function_id}:{"start" | "end"}:{timestamp}"</code>. For example, <code>"0:start:3"</code> means a function call with function ID <code>0</code> <strong>started at the beginning</strong> of timestamp <code>3</code>, and <code>"1:end:2"</code> means a function call with function ID <code>1</code> <strong>ended at the end</strong> of timestamp <code>2</code>. Note that a function can be called <b>multiple times, possibly recursively</b>.</p>

<p>A function's <strong>exclusive time</strong> is the sum of execution times for all function calls in the program. For example, if a function is called twice, one call executing for <code>2</code> time units and another call executing for <code>1</code> time unit, the <strong>exclusive time</strong> is <code>2 + 1 = 3</code>.</p>

<p>Return <em>the <strong>exclusive time</strong> of each function in an array, where the value at the </em><code>i<sup>th</sup></code><em> index represents the exclusive time for the function with ID </em><code>i</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/04/05/diag1b.png" style="width: 550px; height: 239px;">
<pre><strong>Input:</strong> n = 2, logs = ["0:start:0","1:start:2","1:end:5","0:end:6"]
<strong>Output:</strong> [3,4]
<strong>Explanation:</strong>
Function 0 starts at the beginning of time 0, then it executes 2 for units of time and reaches the end of time 1.
Function 1 starts at the beginning of time 2, executes for 4 units of time, and ends at the end of time 5.
Function 0 resumes execution at the beginning of time 6 and executes for 1 unit of time.
So function 0 spends 2 + 1 = 3 units of total time executing, and function 1 spends 4 units of total time executing.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 1, logs = ["0:start:0","0:start:2","0:end:5","0:start:6","0:end:6","0:end:7"]
<strong>Output:</strong> [8]
<strong>Explanation:</strong>
Function 0 starts at the beginning of time 0, executes for 2 units of time, and recursively calls itself.
Function 0 (recursive call) starts at the beginning of time 2 and executes for 4 units of time.
Function 0 (initial call) resumes execution then immediately calls itself again.
Function 0 (2nd recursive call) starts at the beginning of time 6 and executes for 1 unit of time.
Function 0 (initial call) resumes execution at the beginning of time 7 and executes for 1 unit of time.
So function 0 spends 2 + 4 + 1 + 1 = 8 units of total time executing.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 2, logs = ["0:start:0","0:start:2","0:end:5","1:start:6","1:end:6","0:end:7"]
<strong>Output:</strong> [7,1]
<strong>Explanation:</strong>
Function 0 starts at the beginning of time 0, executes for 2 units of time, and recursively calls itself.
Function 0 (recursive call) starts at the beginning of time 2 and executes for 4 units of time.
Function 0 (initial call) resumes execution then immediately calls function 1.
Function 1 starts at the beginning of time 6, executes 1 units of time, and ends at the end of time 6.
Function 0 resumes execution at the beginning of time 6 and executes for 2 units of time.
So function 0 spends 2 + 4 + 1 = 7 units of total time executing, and function 1 spends 1 unit of total time executing.
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> n = 2, logs = ["0:start:0","0:start:2","0:end:5","1:start:7","1:end:7","0:end:8"]
<strong>Output:</strong> [8,1]
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> n = 1, logs = ["0:start:0","0:end:0"]
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>1 &lt;= logs.length &lt;= 500</code></li>
	<li><code>0 &lt;= function_id &lt; n</code></li>
	<li><code>0 &lt;= timestamp &lt;= 10<sup>9</sup></code></li>
	<li>No two start events will happen at the same timestamp.</li>
	<li>No two end events will happen at the same timestamp.</li>
	<li>Each function has an <code>"end"</code> log for each <code>"start"</code> log.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [LinkedIn](https://leetcode.com/company/linkedin), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Amazon](https://leetcode.com/company/amazon)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Stack](https://leetcode.com/tag/stack/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/exclusive-time-of-functions/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int[] exclusiveTime(int n, List<String> logs) {
       //"0:start:0" split by : will be {0,"start",0}
        //create an array to store all the CPU's id and a stack to put id is running in until see "end"
        int[] cpu = new int[n];
        Stack<Integer> idRunning = new Stack();
        int currentTimeStamp = 0;
        for (String log : logs) {
            String[] currLog = log.split(":");  //{id, start or end, timestamp}
            //if id is start, push to the stack,
            if (currLog[1].equals("start")) {
                if (!idRunning.isEmpty()) {
                    int lastInStack = idRunning.peek();
                    cpu[lastInStack] += Integer.parseInt(currLog[2]) - currentTimeStamp; //add up to what ever running
                }
                idRunning.push(Integer.parseInt(currLog[0]));
                currentTimeStamp = Integer.parseInt(currLog[2]);
            } else {
                //when see end, get the last id is running and calculate the time
                int last = idRunning.pop();
                cpu[last] += Integer.parseInt(currLog[2]) - currentTimeStamp + 1; //ex: from 2-5 we have 5-2 = 3, so need + 1 slot to have 4 {2,3,4,5}
                currentTimeStamp = Integer.parseInt(currLog[2]) + 1;
            }
        }
        return cpu;
    }
}

```