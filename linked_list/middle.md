# Middle of linked list 

**Approach** 

1) we will use two pointers slow and fast
2) slow moves ahead by one, and fast moves by two 
**the intution can be when two racers are running if one is at half the speed of other runner, it will be in halfwhen other runner completes/finish the race**
3) return slow 

**CODE**

```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* fast = head;
        ListNode* slow = head;

        while(fast!= NULL && fast->next != NULL){
            slow = slow->next;
            if(fast->next!= NULL)
                fast = fast->next->next;
        }
        return slow;
    }
};
```

**Time Complexity** O(n) mostly n/2 as fast pointer is skipping half elems

