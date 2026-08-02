# Letter Combinations of a Phone Number
![alt text](image.png)

# understnading 
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

# example 
Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]


# code 
class Solution {
public:

    void backtrack(string &digits,
                   int index,
                   unordered_map<char, vector<char>> &mp,
                   string &current,
                   vector<string> &answer)
    {
        // Base Case
        if (index == digits.size())
        {
            answer.push_back(current);
            return;
        }

        // Current digit
        char digit = digits[index];

        // Try every letter for this digit
        for (char ch : mp[digit])
        {
            // Choose
            current.push_back(ch);

            // Explore
            backtrack(digits, index + 1, mp, current, answer);

            // Undo (Backtrack)
            current.pop_back();
        }
    }

    vector<string> letterCombinations(string digits) {

        vector<string> answer;

        if (digits.empty())
            return answer;

        unordered_map<char, vector<char>> mp = {
            {'2', {'a', 'b', 'c'}},
            {'3', {'d', 'e', 'f'}},
            {'4', {'g', 'h', 'i'}},
            {'5', {'j', 'k', 'l'}},
            {'6', {'m', 'n', 'o'}},
            {'7', {'p', 'q', 'r', 's'}},
            {'8', {'t', 'u', 'v'}},
            {'9', {'w', 'x', 'y', 'z'}}
        };

        string current = "";

        backtrack(digits, 0, mp, current, answer);

        return answer;
    }
};

