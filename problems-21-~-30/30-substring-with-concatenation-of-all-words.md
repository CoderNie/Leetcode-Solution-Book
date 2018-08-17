# 30. Substring with Concatenation of All Words

# 解题思路**：**

使用哈希表存储 words 数组中各个单词的数量，然后使用暴力匹配即可。

### 实现代码：

```
// 30. Substring with Concatenation of All Words
vector<int> findSubstring(string s, vector<string>& words) {
  vector<int> result;
  if (words.size() == 0 || words[0].size() == 0 || s.size() < words.size() * words[0].size()) {
    return result;
  }
  unordered_map<string, int> counts;
  for (string word : words) {
    if (counts.find(word) == counts.end()) {
      counts[word] = 1;
    } else {
      counts[word]++;
    }
  }
  int wordCount = words.size(), wordLength = words[0].size(), strLength = s.size();
  for (int i = 0; i <= strLength - wordLength * wordCount; i++) {
    unordered_map<string, int> innerCounts = counts;
    bool flag = true;
    for (int j = 0; j < wordCount; j++) {
      string nowStr = s.substr(i + j * wordLength, wordLength);
      if (innerCounts.find(nowStr) == innerCounts.end() || innerCounts[nowStr] == 0) {
        flag = false;
        break;
      } else {
        innerCounts[nowStr]--;
      }
    }
    if (flag) {
      result.push_back(i);
    }
  }
  return result;
}
```

### 问题描述：

You are given a string,**s**, and a list of words,**words**, that are all of the same length. Find all starting indices of substring\(s\) in**s**that is a concatenation of each word in**words**exactly once and without any intervening characters.

**Example 1:**

```
Input:
  s = "barfoothefoobarman",
  words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoor" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```

**Example 2:**

```
Input:
  s = "wordgoodstudentgoodword",
  words = ["word","student"]
Output: []
```



