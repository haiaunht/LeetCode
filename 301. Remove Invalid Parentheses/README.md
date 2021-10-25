# [301. Remove Invalid Parentheses (Hard)](https://leetcode.com/problems/remove-invalid-parentheses/)

<p>Given a string <code>s</code> that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.</p>

<p>Return <em>all the possible results</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> s = "()())()"
<strong>Output:</strong> ["(())()","()()()"]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> s = "(a)())()"
<strong>Output:</strong> ["(a())()","(a)()()"]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> s = ")("
<strong>Output:</strong> [""]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 25</code></li>
	<li><code>s</code> consists of lowercase English letters and parentheses <code>'('</code> and <code>')'</code>.</li>
	<li>There will be at most <code>20</code> parentheses in <code>s</code>.</li>
</ul>

**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Uber](https://leetcode.com/company/uber), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Backtracking](https://leetcode.com/tag/backtracking/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:

- [Valid Parentheses (Easy)](https://leetcode.com/problems/valid-parentheses/)
- [Minimum Number of Swaps to Make the String Balanced (Medium)](https://leetcode.com/problems/minimum-number-of-swaps-to-make-the-string-balanced/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/remove-invalid-parentheses/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public List<String> removeInvalidParentheses(String s) {
        List<String> result = new ArrayList<>();
        if (s==null || s.length()==0) return result;
        //create a visited set and Queue add each attempts string which are posible valid
        Set<String> visited = new HashSet<>();
        Queue<String> attempts = new LinkedList<>();
        attempts.add(s);
        visited.add(s);
        while (!attempts.isEmpty()) {
            //loop through attempts list each time, if any is valid, push to result
            for (String str : attempts) {
                if (isValid(str)) {
                    result.add(str);
                }
            }
            //if the result is good return
            if (!result.isEmpty()) return result;
            //use a temporary list to store all the new attempts are not visited then assigned to attempts to start the while loop again
            LinkedList<String> temp = new LinkedList<>();
            for (String str : attempts) {
                //create all posible string removing one of ( or ) and check if that is visited, if not put in temp to get checked
                for (int i=0; i<str.length(); i++) {
                    if (str.charAt(i) != '(' && str.charAt(i) != ')') continue;
                    String newString = str.substring(0,i) + str.substring(i+1); //Ex: (())( -> {())(, ())(, (()(, (())}
                    if (!visited.contains(newString)) {
                        visited.add(newString);
                        temp.add(newString);
                    }
                }
            }
            attempts = temp;
        }
        return result;
    }
    private boolean isValid(String s) {
        int count = 0;
        for (char c : s.toCharArray()) {
            if (c == '(') count++;
            if (c == ')') {
                if (count == 0) return false; //as this is )....->invalid
                count--;
            }
        }
        return (count==0);
    }
}

```
