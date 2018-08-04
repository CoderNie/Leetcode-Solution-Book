# 22. Generate Parentheses

# 解题思路**：**

**回溯法**，用一个数组记录【当前字符串，左括号数量，右括号数量】，做 2n 次循环，每次循环遍历当前数组，对左括号不足 n 的添加左括号，右括号不足左括号的添加右括号（确保parentheses是有效的）

### 实现代码：

```
// 22. Generate Parentheses O(2^N)
vector<string> generateParenthesis(int n) {
  if (n == 0) return {};
  // nowString, leftCount, rightCount
  vector<pair<string, pair<int, int> > > res = {{"", {0, 0}}};
  vector<pair<string, pair<int, int> > > linshi;
  for (int i = 0; i < 2 * n; i++) {
    for (int j = 0; j < res.size(); j++) {
      string oldString = res[j].first;
      if (res[j].second.first < n) {
        linshi.push_back({oldString + '(', {res[j].second.first + 1, res[j].second.second}});
      }
      if (res[j].second.first > res[j].second.second) {
        linshi.push_back({oldString + ')', {res[j].second.first, res[j].second.second + 1}});
      }
    }
    res = linshi;
    linshi = {};
  }
  vector<string> result;
  for (int i = 0; i < res.size(); i++) {
    result.push_back(res[i].first);
  }
  return result;
}
```

### 问题描述：

Givennpairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```



