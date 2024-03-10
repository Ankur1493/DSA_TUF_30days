# Intersection point of linked lists

## Brute Force

1) Let's say we select first list as main list 
2) then we will check for every node one by one in first with each node of second 
3) The point where it matches is the point of intersection 

**Code** 

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* node1 = headA;
        ListNode* node2 = headB;
        while(node1 != NULL){
            ListNode* temp = node2;
            while(temp != NULL){
                if(temp == node1) return node1;

                temp = temp-> next;
            }
            node1 = node1->next;
        }
        return NULL;
    }
};
```

**Time Complexity** O(m*n) as we are traversing completely the first list and traversing second list for every element in first

## Optimal

1) first we will take two dummy nodes for each head 
2) then we will calculate length of each list 
3) Now move the node1 or node2 whichever have the greater length, this will make the remaining length equal
4) now when node1 = node2 it's the point of intersection

**code**

```cpp
class Solution {
public:

    int calculateListLength(ListNode* node){
        int lengthList = 1;
        while(node != NULL){
            lengthList += 1;
            node = node->next;
        }
        return lengthList;
    }

    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* node1 = headA;
        ListNode* node2  = headB;

        int lengthList1 = calculateListLength(node1);
        int lengthList2 = calculateListLength(node2);
        int lengthDifference = abs(lengthList1 - lengthList2);

        node1 = headA;
        node2 = headB;
        if(lengthList1 > lengthList2){
            while(lengthDifference > 0){
                node1 = node1->next;
                lengthDifference -= 1;
            }
        }else{
            while(lengthDifference > 0){
                node2 = node2->next;
                lengthDifference -= 1;
            }
        }

        while(node1 != NULL){
            if(node1 == node2){
                return node1;
            }
            node1 = node1->next;
            node2 = node2->next;
        }

        return NULL;

    }
};
```
**Time Complexity** O(m+n);

