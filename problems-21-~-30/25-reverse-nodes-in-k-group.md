# 25.Reverse Nodes in k-Group

# 解题思路**：**

这题相当于24题的加强版，将24题中的2变成了k，换汤不换药，稍微复杂一点。

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

Given a linked list, reverse the nodes of a linked list_k_at a time and return its modified list.

_k_is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of_k_then left-out nodes in the end should remain as it is.

**Example:**

Given this linked list:`1->2->3->4->5`

For_k_= 2, you should return:`2->1->4->3->5`

For_k_= 3, you should return:`3->2->1->4->5`

**Note:**

* Only constant extra memory is allowed.
* You may not alter the values in the list's nodes, only nodes itself may be changed.



