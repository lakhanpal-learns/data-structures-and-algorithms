# power of two 
Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.


Example 1:

Input: n = 1
Output: true
Explanation: 20 = 1
Example 2:

Input: n = 16
Output: true
Explanation: 24 = 16


# key point 
• if it is divide by 2 then it is come in power of 2 
• base case if it is continoulsy divide  by 2 reach 1 then it is under power of 2 
• invalid case  when the value is negative and dont devide 

# code
class Solution {
public:
    bool isPowerOfTwo(int n) {

        // Base case
        if (n == 1)
            return true;

        // Invalid cases
        if (n <= 0 || n % 2 != 0)
            return false;

        // Divide by 2 and solve smaller problem
        return isPowerOfTwo(n / 2);
    }
};
