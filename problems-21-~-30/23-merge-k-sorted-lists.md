# 23. Merge k Sorted Lists

# 解题思路**：**

考虑使用**优先队列**，这道题相当于21题的加强版，但是如果单纯使用21题的每轮比较法，那么每轮只要要比较 k 次，而我们知道这其中肯定会存在很多重复的比较，所以我们可以使用二叉堆来保存每一轮的比较信息，而在C++中STL已经为我们实现了这种数据结构，那就是优先队列priority\_queue，直接调用即可。

### 实现代码：

```
// 23. Merge k Sorted Lists
ListNode* mergeKLists(vector<ListNode*>& lists) {
  ListNode *dump = new ListNode(0), *p = dump, *nowPoint;
  // val, node
  priority_queue<pair<int, ListNode*>, vector<pair<int, ListNode*>>, greater<pair<int, ListNode*>> > pQueue;
  for (ListNode* node : lists) {
    if (node != NULL)
      pQueue.push({node->val, node});
  }
  while (!pQueue.empty()) {
    nowPoint = pQueue.top().second;
    p->next = nowPoint;
    p = p->next;
    pQueue.pop();
    if (nowPoint->next != NULL) {
      pQueue.push({nowPoint->next->val, nowPoint->next});
    }
  }
  return dump->next;
}
```

### 问题描述：

Merge\_k\_sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Example:**

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```



