# 25. Reverse Nodes in k-Group

# 解题思路**：**

这题相当于24题的加强版，将24题中的2变成了k，换汤不换药，稍微复杂一点，所以建议把每一步的思路理清楚，不然很容易弄错，大的思路是先检查是否还剩下足够数量的结点；然后进行反向操作：反向操作分为三步，中间结点关系反向，头结点指向处理 和 尾结点指向处理；最后让 p 结点后挪即可。

### 实现代码：

```
// 25. Reverse Nodes in k-Group
ListNode* reverseKGroup(ListNode* head, int k) {
  if (k == 1) return head;
  vector<ListNode*> nodeList;
  ListNode *dump = new ListNode(0), *p = dump, *former, *latter, *nextLatter, *q;
  dump->next = head;
  while (true) {
    // check count of left nodes
    q = p;
    for (int i = 0; i < k + 1; i++) {
      if (q != NULL) {
        q = q->next;
      } else {
        return dump->next;      
      }
    }
    // deal with medial relations 
    former = p->next;
    latter = former->next;
    for (int i = 0; i < k - 1; i++) {
      // save latter->next as next latter
      nextLatter = latter->next;
      // latter->next = former
      latter->next = former;
      // save latter as next former  
      former = latter;
      latter = nextLatter;
    }
    // deal with head
    q = p->next;
    p->next = former;
    // deal with tail
    q->next = latter;

    p = q;
  }
  return dump->next;      
}
```

### 问题描述：

Given a linked list, reverse the nodes of a linked list\_k\_at a time and return its modified list.

**k** is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of\_k\_then left-out nodes in the end should remain as it is.

**Example:**

Given this linked list:`1->2->3->4->5`

For_k_= 2, you should return:`2->1->4->3->5`

For_k_= 3, you should return:`3->2->1->4->5`

**Note:**

* Only constant extra memory is allowed.
* You may not alter the values in the list's nodes, only nodes itself may be changed.



