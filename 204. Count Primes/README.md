# [204. Count Primes (Easy)](https://leetcode.com/problems/count-primes/)

<p>Count the number of prime numbers less than a non-negative number, <code>n</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 5 * 10<sup>6</sup></code></li>
</ul>

**Companies**:  
[Apple](https://leetcode.com/company/apple), [Capital One](https://leetcode.com/company/capital-one), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Twitter](https://leetcode.com/company/twitter), [Docusign](https://leetcode.com/company/docusign), [Cisco](https://leetcode.com/company/cisco)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Math](https://leetcode.com/tag/math/)

**Similar Questions**:

- [Ugly Number (Easy)](https://leetcode.com/problems/ugly-number/)
- [Ugly Number II (Medium)](https://leetcode.com/problems/ugly-number-ii/)
- [Perfect Squares (Medium)](https://leetcode.com/problems/perfect-squares/)

## Solution 1.

```java
// OJ: https://leetcode.com/problems/count-primes/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Solution {
    public int countPrimes(int n) {
        if (n <= 2) return 0;
        // Map<Integer, Integer> map = new HashMap<>();
        // for (int i=2; i<n; i++) {
        //     if (isPrime(i)) {
        //         map.put(i, 1);
        //     }
        // }
        // return map.size();
        //Sieve of Eratosthenes
        boolean[] numbers = new boolean[n];
        for (int i=2; i<=Math.sqrt(n); i++) {
            if (numbers[i] == false) {
                for (int j=i*i; j<n; j+= i) {
                    numbers[j] = true;
                }
            }
        }
        int result = 0;
        for (int i=2; i<n; i++) {
            if (numbers[i] == false) result++;
        }
        return result;
    }
    //LeetCode not accpeted this as time limit exceeded
//     private boolean isPrime(int num) {
//         if (num <= 1) return false;
//         for (int i=2; i<=Math.sqrt(num); i++) {
//             if (num % i == 0) return false;
//         }
//         return true;
//     }
}

```
