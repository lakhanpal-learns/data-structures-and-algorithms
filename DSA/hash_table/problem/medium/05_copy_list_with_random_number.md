# Copy List with Random Pointer



# understanding 
## Step 1: Understand the Node

Normal linked list node:

+-------+-------+
| val   | next  |
+-------+-------+

This problem adds another pointer:

+-------+-------+---------+
| val   | next  | random  |
+-------+-------+---------+

So every node has:

val
next
random

## Step 2: What is a Deep Copy?

We cannot return the original list.

We must create

A' -----> B' -----> C'

where every node is new.

Original:

A

Copy:

A'

These are different objects in memory.

## Wrong Deep Copy

Suppose you do

copy->random = original->random;

Then

Copy Node

↓

random

↓

Original Node

This is wrong.

The copied list should never point back into the original list.

## Step 3: The Biggest Problem

Suppose you're copying node B.

You need to assign

copyB->random = ?

Original says

B.random = A

You need

copyB.random = copyA

Question:

How do you find copyA?

## Without extra memory, you only know

Original A

You do not know where

Copy A

is.

That's the core difficulty.

## Step 4: HashMap Idea

Store

Original Node

↓

Copied Node

Exactly like

unordered_map<Node*, Node*> mp;

Key

↓

Original node pointer

Value

↓

Copied node pointer

## Step 5: Two Passes
### Pass 1

Create all new nodes.

Store mapping.

Original

↓

Copy

A → A'

B → B'

C → C'

## Pass 2

Fix pointers.

For every original node

Original

↓

Copy

Assign

copy->next = mp[original->next];

Assign

copy->random = mp[original->random];

Because the map already knows every copy.

## For every original node:

Take the current original node.
Look at where its random pointer points (another original node).
Use the hash map to find the copy of that original node.
Connect the copied node's random pointer to that copied target.

## So the main challenge is:

Not

Create copy nodes

but

Connect every copied node's random pointer
to the correct copied node.

The hash map solves exactly that problem.

## One sentence to remember for interviews

The hash map stores a mapping from each original node to its copied node, so we can set next and random pointers in O(1) time without searching the copied list.

# code 
class Solution {
public:
    Node* copyRandomList(Node* head) {

        if (head == NULL)
            return NULL;

        unordered_map<Node*, Node*> mp;

        Node* curr = head;

        // Pass 1: Create copy nodes
        while (curr != NULL)
        {
            mp[curr] = new Node(curr->val);
            curr = curr->next;
        }

        // Pass 2: Connect next and random pointers
        curr = head;

        while (curr != NULL)
        {
            mp[curr]->next = mp[curr->next];
            mp[curr]->random = mp[curr->random];

            curr = curr->next;
        }

        return mp[head];
    }
};

# important points 
1. First Pass - Create All Copy Nodes in pass 1 
2. here we are not creating  any connection of next and radome 
3. in pass 2 we build that connection 



