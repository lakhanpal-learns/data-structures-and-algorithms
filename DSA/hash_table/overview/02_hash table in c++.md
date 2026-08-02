# Hash Table in C++

# In C++, a hash table is provided by the STL through:

unordered_map
unordered_set

These containers are implemented using hash tables, which is why their average time complexity is O(1) for insert, search, and delete.

# 1. unordered_map

Stores data as:

Key → Value

Example:

#include <iostream>
#include <unordered_map>
using namespace std;

int main() {

    unordered_map<string, int> age;

    age["John"] = 20;
    age["Alice"] = 25;
    age["Mike"] = 30;

    cout << age["John"];

}

Output

20

Memory conceptually looks like

John  → 20

Alice → 25

Mike  → 30

You don't know where these are stored physically.

The hash function decides that.

## operations 

### Insert
age["Bob"] = 40;
Update
age["John"] = 22;

Now

John → 22

### Search

#### Method 1

cout << age["Alice"];

Output

25

#### Method 2 (Recommended)

if(age.find("Alice") != age.end())
{
    cout << "Found";
}

<!-- Why use find()?

Because

age["David"]

will create a new key if it doesn't already exist. -->

Example

unordered_map<string,int> age;

cout << age["David"];

Output

0

Now "David" has been inserted with value 0.

This is often not what you want.

Instead use

if(age.find("David") != age.end())
{
    cout<<"Exists";
}
else
{
    cout<<"Not Found";
}

### Delete
age.erase("Mike");

Now Mike is removed.

Size
cout << age.size();
Empty
if(age.empty())
{
    cout<<"Empty";
}

# unordered_set

Stores only keys.

No values.

Example

#include <unordered_set>

unordered_set<int> s;

s.insert(10);
s.insert(20);
s.insert(30);

Memory

10

20

30

## operations 

Search

if(s.find(20)!=s.end())
{
    cout<<"Found";
}

Delete

s.erase(20);

# unordered_map vs unordered_set
unordered_map	unordered_set
Key → Value	Only Key
Student → Marks	Student IDs
Product → Price	Unique Products
Employee → Salary	Unique Employee IDs

