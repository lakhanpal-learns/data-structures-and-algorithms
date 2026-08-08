# Valid Palindrome
You are given a string s.

You need to check if it is a palindrome after:

Converting uppercase letters to lowercase.
Removing all spaces and special characters.
Keeping only letters and numbers.

If the final string reads the same forward and backward, return true.

Input:
"A man, a plan, a canal: Panama"

After cleaning:
"amanaplanacanalpanama"

Forward  = amanaplanacanalpanama
Backward = amanaplanacanalpanama

Output:
true

# key points 
1. move both point in the  left to right 
2. use function isalnum and lower 
3. so outisde while loop and inside while loop   with left < right ( stack overflow problem does not come )

# code 
class Solution {
public:
    bool isPalindrome(string s) {
        int left = 0;
        int right = s.size() - 1;

        while (left < right) {

            while (left < right && !isalnum(s[left])) {
                left++;
            }

            while (left < right && !isalnum(s[right])) {
                right--;
            }

            if (tolower(s[left]) != tolower(s[right])) {
                return false;
            }

            left++;
            right--;
        }

        return true;
    }
};