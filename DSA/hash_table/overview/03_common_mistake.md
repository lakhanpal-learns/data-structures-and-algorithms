# Common Interview Mistakes
## Mistake 1

Using map

instead of

unordered_map

when order doesn't matter.

## Mistake 2

Using vector search

for(...)

instead of

unordered_set

## Mistake 3

Using

m[key]

for searching.

Bad

if(m["John"])

because this inserts "John" if it wasn't already present.

Use

if(m.find("John")!=m.end())

## Mistake 4

Thinking hash tables are always O(1).

Reality

Average

O(1)

Worst

O(n)

because collisions can force many elements into the same bucket.

## Mistake 5

Expecting sorted output.

Hash tables do not maintain order.

Example

Inserted

1

2

3

4

Output might be

4

1

3

2

This is completely normal.
