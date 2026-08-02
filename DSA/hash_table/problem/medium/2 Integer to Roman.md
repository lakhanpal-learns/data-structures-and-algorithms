# integor to roman 
Seven different symbols represent Roman numerals with the following values:

Symbol	Value
I	1
V	5
X	10
L	50
C	100
D	500
M	1000


# understanding 
Rule 1: Always use the largest Roman value possible.
Rule 2: Repeat I, X, C, M at most 3 times.
Rule 3: Never repeat V, L, or D.
Rule 4: Use subtraction for numbers ending in 4 or 9.
| Number | Roman | Meaning    |
| -----: | ----- | ---------- |
|      4 | IV    | 5 − 1      |
|      9 | IX    | 10 − 1     |
|     40 | XL    | 50 − 10    |
|     90 | XC    | 100 − 10   |
|    400 | CD    | 500 − 100  |
|    900 | CM    | 1000 − 100 |


# code 
class Solution {
public:
    string intToRoman(int num) {

        vector<pair<int, string>> value = {
            {1000, "M"},
            {900, "CM"},
            {500, "D"},
            {400, "CD"},
            {100, "C"},
            {90, "XC"},
            {50, "L"},
            {40, "XL"},
            {10, "X"},
            {9, "IX"},
            {5, "V"},
            {4, "IV"},
            {1, "I"}
        };

        string ans = "";

        // Visit each Roman numeral from largest to smallest
        for (auto &p : value) {

            // Keep using the current Roman numeral while it fits
            while (num >= p.first) {
                ans += p.second;
                num -= p.first;
            }
        }

        return ans;
    }
};

# code break down 

# loop 
for (auto &p : value)

range-based for loop (introduced in C++11).

**First iteration**

p = {1000, "M"}

So

p.first   // 1000
p.second  // "M"

to unitl end 

**It is exactly equivalent to**
for (int i = 0; i < value.size(); i++)
{
    cout << value[i].first;
    cout << value[i].second;
}

**What does & mean?**

& means reference.

Instead of making a copy of each pair, p refers directly to the element inside the vector.

for (auto &p : value)
no copy is made, so it's more efficient.

**When does the loop stop?**

The loop automatically stops after the last element.

The iterations are:

Iteration 1  -> {1000,"M"}
Iteration 2  -> {900,"CM"}
Iteration 3  -> {500,"D"}
...
Iteration 13 -> {1,"I"}

After processing {1, "I"}, there are no more elements, so the loop ends automatically.



