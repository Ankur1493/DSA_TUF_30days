# Reverse Linked List

## Iteratively

1) just have to change the addresses stored, so we will have to remember three nodes
2) prevNode whose address we changed and have no link with it 
3) currentNode whose address we will change
4) nextNode to keep track of Linked list further

5) Now just run a loop until nextNode != null

**code**
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        
            if(head == NULL || head->next == NULL) return head;

            ListNode* currentNode = head->next;
            ListNode* prevNode = head;
            ListNode* temp = NULL;

            while(currentNode!= NULL){

                prevNode->next = temp;
                temp = prevNode;
                prevNode = currentNode;
                currentNode = currentNode->next;

            }

            prevNode->next = temp;
            return prevNode; 
    }
};
```

**Time Complexity**  O(n) 

