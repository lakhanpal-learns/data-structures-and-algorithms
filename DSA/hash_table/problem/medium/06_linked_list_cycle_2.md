# Linked List Cycle II

Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

Do not modify the linked list.


# code 
class Solution {
public:
    ListNode* detectCycle(ListNode* head) {
        unordered_map<ListNode*, int> mp;

        int index = 0;

        while (head != nullptr) {

            // Check if address already exists
            if (mp.count(head)) {
                return head;
            }

            // Store address with its index
            mp[head] = index;

            head = head->next;
            index++;
        }

        return nullptr;
    }
};