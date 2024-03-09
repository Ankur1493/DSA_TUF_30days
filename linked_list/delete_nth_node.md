# Delete nth node from end

## Approach

1) First we will calculate the no of nodes in list 
2) get deleteIndex from start, nodeLength - n 
3) loop until you get to the previous node from the nth node 
4) temp->next =  temp->next->next;

**Edge Case** when nodelength and n = 1 delete head and return NULL

## Code 

```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        int nodeLength = 1;
        ListNode* temp = head;
        while( temp->next != NULL ){
            nodeLength += 1;
            temp = temp->next;
        }

        if(n == nodeLength){
            return head->next;
        }

        int deleteIndex = nodeLength - n ;
        temp = head;
        while( deleteIndex > 1 ){
            temp = temp->next;
            deleteIndex -= 1;
        }

        temp-> next = temp->next->next;
        return head;
    }
};
```

**Time Complexity** O(n) as we traverse the whole linked list for calculating the length;
