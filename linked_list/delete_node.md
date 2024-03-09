# Delete node from linked list

## Approach

1) we will just copy the data of next node in current and remove the existence of next node

## Code

```
class Solution {
public:
    void deleteNode(ListNode* node) {
        
        node->val = node->next->val;
        node->next = node->next->next;

    }
};
```

**Time complexity** O(1)
