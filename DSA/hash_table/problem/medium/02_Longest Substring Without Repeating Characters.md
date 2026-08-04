# 3. Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without duplicate characters.

# example 

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.

# code 
class Solution {
public:
    int lengthOfLongestSubstring(string s) {

        unordered_set<char> window;

        int left = 0;
        int maxLength = 0;

        for (int right = 0; right < s.size(); right++) {

            while (window.count(s[right])) {
                window.erase(s[left]);
                left++;
            }

            window.insert(s[right]);

            maxLength = max(maxLength, right - left + 1);
        }

        return maxLength;
    }
};

# understanding 
string has all char must ne unique  then calculte no of unique chrachter and return all the unique chrachter 

# code break down 

## define the set 

## using slide window  :---- left  to right 
int left = 0;
        int maxLength = 0;

it is tell use what to erase in the string 

## loop checking is still any cnrachter is exiting 
 while (window.count(s[right])) {
                window.erase(s[left]);
                left++;
            }

only work is to check any chracter that exit is to remove 

## insert unique value is only 

## check the length 
maxLength = max(maxLength, right - left + 1);

here there is two lenth we are seeing one is  max lenth which are prev length according to no of insert we made 

new lenth (right - left + 1) which tell if any new chrachter  is insert if yes then update the string 

