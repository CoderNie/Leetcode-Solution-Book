# 21. Merge Two Sorted Lists

# 解题思路**：**

从头至尾一起遍历，每次比较头结点的大小，先添加小的结点，直到某一个链表为空为止，最后将另一个还不为空的链表添加末尾。

### 实现代码：

```
// 21. Merge Two Sorted Lists
ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
  ListNode* head = new ListNode(0);
  ListNode* p = head;
  while (l1 != NULL && l2 != NULL) {
    if (l1->val < l2 ->val) {
      p->next = l1;
      l1 = l1->next;
    } else {
      p->next = l2;
      l2 = l2->next;
    }
    p = p->next;
  }
  if (l1 != NULL) {
    p->next = l1;
  } else if (l2 != NULL) {
    p->next = l2;
  }
  return head->next;
}
```

### 问题描述：

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```



