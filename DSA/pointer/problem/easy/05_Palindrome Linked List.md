# Palindrome Linked List

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

Input: head = [1,2,2,1]
Output: true

Input: head = [1,2]
Output: false


# key points 

# problem :- 
1 we only move forward 
2 we have to compare left side with right side 


# solution 

1. part 1 find the mid point 
2. part 2 reverse the  connection from mid to end 
3. part 3 use new pointer to compare left and right both together 


# code 
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        ListNode* curr = head; 
        ListNode* slow = head;
        ListNode* fast = head; 

       while (fast != nullptr && fast->next != nullptr)
        {
            slow = slow->next;           // 1 step
            fast = fast->next->next;     // 2 steps
        }
        
        ListNode* prev = nullptr;
        ListNode* currs = slow;

        while (currs != nullptr)
        {
            ListNode* next = currs->next;
            
            currs->next = prev;
            
            prev = currs;
            currs = next;
        }
        ListNode* left = head;
        ListNode* right = prev;
        while (right != nullptr)
        {
            if (left->val != right->val)
                return false;

            left = left->next;
            right = right->next;
        }

        return true;
           

    }
};