# 19. Remove Nth Node From End of List

# 解题思路**：**

**快慢指针思想**，让两个指针 p, q都指向头结点，p 先向后移动 n + 1 步，然后p, q一起向后移动，当 p 到达尾结点时，q指向目标节点的前驱结点，做删除操作，然后按照题目要求返回头结点即可。

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



