# LeetCode 2094 — Finding 3-Digit Even Numbers

# problem 
You are given an array digits, for example:

[2, 1, 3, 0]

You need to form 3-digit even numbers using these digits

**Rules:**

The number must have exactly 3 digits → first digit cannot be 0.
The last digit must be even → 0, 2, 4, 6, 8.
You cannot use a digit more times than it appears in the input.


# key point 






# solution :- brute force 
class Solution {
public:
    vector<int> findEvenNumbers(vector<int>& digits) {

        set<int> ans;

        for (int i = 0; i < digits.size(); i++) {
            for (int j = 0; j < digits.size(); j++) {
                for (int k = 0; k < digits.size(); k++) {

                    // Can't use the same index twice
                    if (i == j || i == k || j == k)
                        continue;

                    // First digit can't be 0
                    if (digits[i] == 0)
                        continue;

                    // Last digit must be even
                    if (digits[k] % 2 != 0)
                        continue;

                    // Create the 3-digit number
                    int num = digits[i] * 100
                            + digits[j] * 10
                            + digits[k];

                    // set removes duplicates
                    ans.insert(num);
                }
            }
        }

        // Convert set → vector
        return vector<int>(ans.begin(), ans.end());
    }
};

# key point 

# solution :- recursion 
class Solution {
public:

    void backtrack(vector<int>& digits,
                   vector<bool>& used,
                   int num,
                   int count,
                   set<int>& ans) {

        // We have selected 3 digits
        if (count == 3) {
            if (num % 2 == 0) {
                ans.insert(num);
            }
            return;
        }

        // Try every digit
        for (int i = 0; i < digits.size(); i++) {

            // Same index cannot be used twice
            if (used[i])
                continue;

            // First digit cannot be 0
            if (count == 0 && digits[i] == 0)
                continue;

            // Choose
            used[i] = true;

            // Recurse
            backtrack(
                digits,
                used,
                num * 10 + digits[i],
                count + 1,
                ans
            );

            // Undo
            used[i] = false;
        }
    }

    vector<int> findEvenNumbers(vector<int>& digits) {

        set<int> ans;

        vector<bool> used(digits.size(), false);

        backtrack(digits, used, 0, 0, ans);

        return vector<int>(ans.begin(), ans.end());
    }
};