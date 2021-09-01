# [208. Implement Trie (Prefix Tree) (Medium)](https://leetcode.com/problems/implement-trie-prefix-tree/)

<p>A <a href="https://en.wikipedia.org/wiki/Trie" target="_blank"><strong>trie</strong></a> (pronounced as "try") or <strong>prefix tree</strong> is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.</p>

<p>Implement the Trie class:</p>

<ul>
	<li><code>Trie()</code> Initializes the trie object.</li>
	<li><code>void insert(String word)</code> Inserts the string <code>word</code> into the trie.</li>
	<li><code>boolean search(String word)</code> Returns <code>true</code> if the string <code>word</code> is in the trie (i.e., was inserted before), and <code>false</code> otherwise.</li>
	<li><code>boolean startsWith(String prefix)</code> Returns <code>true</code> if there is a previously inserted string <code>word</code> that has the prefix <code>prefix</code>, and <code>false</code> otherwise.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input</strong>
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
<strong>Output</strong>
[null, null, true, false, true, null, true]

<strong>Explanation</strong>
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length, prefix.length &lt;= 2000</code></li>
	<li><code>word</code> and <code>prefix</code> consist only of lowercase English letters.</li>
	<li>At most <code>3 * 10<sup>4</sup></code> calls <strong>in total</strong> will be made to <code>insert</code>, <code>search</code>, and <code>startsWith</code>.</li>
</ul>

**Companies**:  
[Twitter](https://leetcode.com/company/twitter), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [eBay](https://leetcode.com/company/ebay), [Pinterest](https://leetcode.com/company/pinterest)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Design](https://leetcode.com/tag/design/), [Trie](https://leetcode.com/tag/trie/)

**Similar Questions**:

- [Design Add and Search Words Data Structure (Medium)](https://leetcode.com/problems/design-add-and-search-words-data-structure/)
- [Design Search Autocomplete System (Hard)](https://leetcode.com/problems/design-search-autocomplete-system/)
- [Replace Words (Medium)](https://leetcode.com/problems/replace-words/)
- [Implement Magic Dictionary (Medium)](https://leetcode.com/problems/implement-magic-dictionary/)
- [Implement Trie II (Prefix Tree) (Medium)](https://leetcode.com/problems/implement-trie-ii-prefix-tree/)

## Solution 1.

```Java - using hashmap
// OJ: https://leetcode.com/problems/implement-trie-prefix-tree/
// Author: Please set your name in options page
// Time: O()
// Space: O()
class Trie {
    Map<String, Integer> map;
    /** Initialize your data structure here. */
    public Trie() {
        map = new HashMap<>();
    }
    /** Inserts a word into the trie. */
    public void insert(String word) {
        map.putIfAbsent(word, 1);
    }
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        return map.containsKey(word);
    }
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        for (String key : map.keySet()) {
            if (key.startsWith(prefix)) return true;
        }
        return false;
    }
}
/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */



 -- USING TRIE() DATA STRUCTURE
 // OJ: https://leetcode.com/problems/implement-trie-prefix-tree/solution/
// Author: Please set your name in options page
// Time: O()
// Space: O()
    }
class TrieNode {
    // R links to node children
    private TrieNode[] links;
    private final int R = 26;
    private boolean isEnd;
    public TrieNode() {
        links = new TrieNode[R];
    }
    public boolean containsKey(char ch) {
        return links[ch -'a'] != null;
    }
    public TrieNode get(char ch) {
        return links[ch -'a'];
    }
    public void put(char ch, TrieNode node) {
        links[ch -'a'] = node;
    }
    public void setEnd() {
        isEnd = true;
    }
    public boolean isEnd() {
        return isEnd;
    }
}
class Trie {
    private TrieNode root;
    public Trie() {
            if (!node.containsKey(currentChar)) {

```
