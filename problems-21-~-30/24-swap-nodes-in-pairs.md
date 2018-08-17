# 24. Swap Nodes in Pairs

# 解题思路**：**

两两交换即可，这里每轮需要变换三个指向，第一个的next要指向第二个的next，第二个的next要指向第一个，前驱的next要指向第二个，每轮过后让 p 指向第一个即可。

### 实现代码：

```
// 24. Swap Nodes in Pairs
ListNode* swapPairs(ListNode* head) {
  ListNode *dump = new ListNode(0), *p = dump, *first, *second;
  dump->next = head;
  while (p != NULL && p->next != NULL && p->next->next != NULL) {
    first = p->next;
    second = p->next->next;
    first->next = second->next;
    second->next = first;
    p->next = second;
    p = first;
  }
  return dump->next; 
}
```

### 问题描述：

Given a linked list, swap every two adjacent nodes and return its head.

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

**Note:**

* Your algorithm should use only constant extra space.
* You may **not **modify the values in the list's nodes, only nodes itself may be changed.



