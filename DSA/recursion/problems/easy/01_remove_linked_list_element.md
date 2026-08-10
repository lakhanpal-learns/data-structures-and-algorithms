# Remove Linked List Elements

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]


# key point 
• we have to check every point  is it equal to val 
• we have to change the direction of the arrow to next 
• how recursion help it is check the each node then if it  is match then it is send next element that we connect that connection to it 



# code 
// Base case
        if (head == nullptr)
            return nullptr;

        // Recursively clean the rest of the list
        head->next = removeElements(head->next, val);

        // Remove current node if needed
        if (head->val == val)
            return head->next;

        return head;


# understading 
1. What is my state?

The current node:
head

2. What is my base case?

If there is no node:

if (head == nullptr)
    return nullptr;

3. What smaller problem can I solve?

Ask recursion to solve the rest of the list:

head->next = removeElements(head->next, val);

