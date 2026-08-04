# reverse string with the vowel 

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

 
Example 1:

Input: s = "IceCreAm"

Output: "AceCreIm"

Explanation:

The vowels in s are ['I', 'e', 'e', 'A']. On reversing the vowels, s becomes "AceCreIm".

# code 
class Solution {
public:
    string reverseVowels(string s) {
        int l =0;
           int r = s.size()-1;
        while ( l < r )
        {
             if (!isVowel(s[l]))
        {
            l++;
        }
        else if (!isVowel(s[r]))
        {
            r--;
        }
        else
        {
            swap(s[l], s[r]);
            l++;
            r--;
        }

        }
           return s;        
    }


    bool isVowel(char ch)
    {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' ||
            ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U';
    }
};

# point 
1. wait both left and right pointer to get the value 

