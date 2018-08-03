# 20. Valid Parentheses

# 解题思路**：**

**栈思想**，从左往右遍历，如果是左括号则入栈，右括号则出栈，最后判断栈是否为空，空则为有效括号组，否则无效。

### 实现代码：

```
// 20. Valid Parentheses
bool isValid(string s) {
  stack<char> brackets;
  map<char, char> bracketMap;
  bracketMap[')'] = '(';
  bracketMap[']'] = '[';
  bracketMap['}'] = '{';
  for (int i = 0; i < s.size(); i++) {
    if (s[i] == '(' || s[i] == '[' || s[i] == '{') {
      brackets.push(s[i]);
    } else if (s[i] == ')' || s[i] == ']' || s[i] == '}') {
      if (!brackets.empty() && brackets.top() == bracketMap[s[i]]) {
        brackets.pop();
      } else {
        return false;
      }
    }
  }
  if (brackets.empty()) return true;
  else return false;
}
```

### 问题描述：

Given a string containing just the characters`'('`,`')'`,`'{'`,`'}'`,`'['`and`']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```
Input: "()"
Output: true
```

**Example 2:**

```
Input: "()[]{}"
Output: true
```

**Example 3:**

```
Input: "(]"
Output: false
```

**Example 4:**

```
Input: "([)]"
Output: false
```

**Example 5:**

```
Input: "{[]}"
Output: true
```



