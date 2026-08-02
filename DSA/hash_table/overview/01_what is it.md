# Chapter 1 — Why do we need Hash Tables?
Imagine this list:

Apple
Banana
Orange
Mango
Grapes

Now I ask

<!-- Is "Orange" inside the list? -->

Without a hash table you search

Apple ❌
Banana ❌
Orange ✅

<!-- Time taken

O(n) -->

because worst case you check everything.

## Now imagine

100 million names

Searching one by one is slow.

We need something much faster.

<!-- Hash Table gives

Average O(1) -->

which means

<!-- Almost Instant -->

# Real-Life Example

Imagine your city.

Without house numbers

Rahul
Aman
John
Riya

Postman searches every house.

Slow.

<!-- Now every house has an address -->

Street 1 House 25
Street 4 House 10
Street 9 House 11

Now postman goes directly there.

Hash Table works exactly like this.

# Chapter 2 — What is a Hash Table?

<!-- A hash table stores

Key → Value -->

Example

Name → Age

John → 25
Alice → 30
Mike → 21

Instead of searching every name,

it converts

John

into

Index 5

Then directly jumps there.

Visual

Memory

0
1
2
3
4
5 ---> John : 25
6
7
8
9

<!-- No searching.

Direct access. -->

# Chapter 3 — Hash Function

Question:

How does

John

become

5

Answer

<!-- Hash Function. -->

hash("John")

↓

5

Similarly

hash("Alice")

↓

2
hash("Mike")

↓

8

<!-- Hash function converts -->

Key

↓

Integer

Think of it as

Name

↓

Magic Machine

↓

Number

Example

John

↓

7348368382

↓

7348368382 % 10

↓

2

So John goes into bucket 2.

# Chapter 4 — Buckets

Suppose our table size is

10

Indexes

0
1
2
3
4
5
6
7
8
9

Every position is called a

Bucket

# Chapter 5 — Collision

The biggest problem.

Suppose

John

↓

2

and

Mike

↓

2

Both want the same bucket.

Bucket 2

↓

John

↓

Mike

Impossible.

This is called

Collision

Two different keys produce the same bucket.

## Why collisions happen?

Suppose

1000 keys

only

10 buckets

Obviously

many keys share buckets.

Even with millions of buckets, collisions can still happen because the hash function maps a huge space of possible keys into a finite number of buckets.

# Chapter 6 — Collision Resolution

<!-- There are two famous methods. -->
## Method 1

<!-- Separate Chaining -->

Bucket stores a linked list.

Bucket 2

↓

John

↓

Mike

↓

Alice

↓

David

Searching

hash(John)

↓

Bucket 2

↓

Scan linked list

### Visual

0

1

2 ---> John
        ↓
       Mike
        ↓
      Alice

3

4

5

Most languages use some form of chaining (often with optimizations).

## Method 2

Open Addressing

Instead of a linked list

find another empty bucket.

Example

Bucket

0

1

2 → John

3 → Empty

4

5

Mike hashes to

2

Occupied.

Go to

3

Store Mike.

<!-- This is called

Linear Probing -->

<!-- Other probing methods include

Quadratic Probing

Double Hashing -->

# Chapter 7 — Load Factor

Important interview concept.

Formula

Load Factor=
Number of Buckets
Number of Elements
	​


Example

Buckets = 10

Elements = 5

Load Factor

5 / 10

=

0.5

Suppose

Buckets = 10

Elements = 20

Load Factor

2

Now every bucket has multiple items.

Performance drops.

# Chapter 8 — Rehashing

Suppose

Buckets = 10

Elements = 100

Very crowded.

Solution

Increase table.

10

↓

20

↓

40

↓

80

Then calculate each key's new bucket using the new table size and move every element.

<!-- This is called

Rehashing -->

# Chapter 9 — Time Complexity
Operation	Average	Worst
Search	O(1)	O(n)
Insert	O(1)	O(n)
Delete	O(1)	O(n)

Why worst O(n)?

Imagine every key hashes into one bucket.

Bucket

↓

John

↓

Mike

↓

Alice

↓

David

↓

...

Now you scan everything.

# Chapter 10 — HashMap vs HashSet

<!-- HashMap

Stores

Key → Value -->

Example

Age

John → 21

Alice → 30

<!-- HashSet

Stores only

Keys -->

Example

John

Alice

Mike

No values.

Used to quickly check if something exists.



# Ordered vs Unordered

Many beginners confuse these.

<!-- map -->
map<int,string> m;

Output

1

2

3

4

5

Always sorted.

Time Complexity

O(log n)

because map uses a Red-Black Tree.

<!-- unordered_map -->
unordered_map<int,string> m;

Output

5

1

3

2

Random order.

Average

O(1)

because it uses a Hash Table.