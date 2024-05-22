# Regular Expression Matching
> Given an input string s and a pattern p, implement regular expression matching with support for '.' and '*' where:
>
> - '.' Matches any single character.​​​​
> - '*' Matches zero or more of the preceding element.
>   
> The matching should cover the entire input string (not partial).

## SOLUTION (python)
```python

class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        i= 0
        j= 0
        n= len(s)
        m= len(p)

        if n != m:
            return False
            #if the strings have different lenghts they can't match

        for i in range(n):
            if s[i] == p[i] or s[i] == "." or p[i] == "." :
                continue
                #if both start with the same character or one starts by "." the loop can continue because of the special definition of the character "."

            elif p[i] == "*" :
                p = p[:i] + p[i-1] + p[i+1:]
                #if we find the special character "*" we change it in the original string p by the preceding element and repeat the comparison above
                
                if s[i] == p[i] or s[i] == "." or p[i] == "." :
                    continue
                else:
                    return False
            else:
                return False
        return True
```


## EXAMPLES

#### Example 1:

Input: s = "aa", p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".


#### Example 2:

Input: s = "aa", p = "a*"
Output: true
- Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".


#### Example 3:

Input: s = "ab", p = ".*"
Output: true
- Explanation: ".*" means "zero or more (*) of any character (.)".

##########################################################################

RESULT: Solution ACCEPTED

RUNTIME: 8ms

        
