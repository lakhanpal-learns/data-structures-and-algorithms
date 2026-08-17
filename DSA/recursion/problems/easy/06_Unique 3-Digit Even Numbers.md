# Unique 3-Digit Even Numbers

# code 
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
    int totalNumbers(vector<int>& digits) {
                set<int> ans;

        vector<bool> used(digits.size(), false);

        backtrack(digits, used, 0, 0, ans);

        return ans.size();
    }
};