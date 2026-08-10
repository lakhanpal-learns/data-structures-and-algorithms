# Reverse Linked List
Given the head of a singly linked list, reverse the list, and return the reversed list.

Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]


# key points 
• reach last node don't return the  null ptr instead return the last node 
• build new connection 
• break old connection 
• return head 


# code 
class Solution {
public:
    ListNode* reverseList(ListNode* head) {

        // Stop at last node
        if (head == nullptr || head->next == nullptr)
            return head;

        // Reverse everything after current node
        ListNode* newHead = reverseList(head->next);

        // Make next node point backwards
        head->next->next = head;

        // Break old forward connection
        head->next = nullptr;

        // Return the new first node
        return newHead;
    }
};

