\## Problem: 

Given a string s, determine if it is a palindrome after converting all uppercase letters to lowercase and removing all non-alphanumeric characters.

link: https://leetcode.com/problems/valid-palindrome/submissions/1927393363/





\# Intuition

To determine whether a string is a palindrome, we only need to compare valid alphanumeric characters while ignoring case and special characters.



\## Approach 1 — Using StringBuilder + Filtering

\- Convert the string to lowercase.

\- Remove all non-alphanumeric characters.

\- Reverse the cleaned string.

\- Compare original and reversed strings.



\#### Time complexity: O(n)

\#### Space complexity: O(n)



\#### Java Code

``` java \[]

class Solution {

&nbsp;   public boolean isPalindrome(String s) {

&nbsp;       s = s.toLowerCase();

&nbsp;       StringBuilder sb = new StringBuilder();

&nbsp;       for (int i = 0; i < s.length(); i++) {

&nbsp;           char c = s.charAt(i);

&nbsp;           if ((c >= 'a' \&\& c <= 'z') || (c >= '0' \&\& c <= '9')) {

&nbsp;               sb.append(c);

&nbsp;           }

&nbsp;       }

&nbsp;       String str = sb.toString();

&nbsp;       String rev = sb.reverse().toString();

&nbsp;       return str.equals(rev);

&nbsp;   }

}

```





\## Approach 2 — Using Regex + StringBuilder

\- Use regex to remove non-alphanumeric characters.

\- Reverse and compare.



\#### Time complexity: O(n)

\#### Space complexity: O(n)

\*\*Drawback:\*\* Regex is internally expensive → Slower than manual traversal.



\#### Java Code

```java \[]

class Solution {

&nbsp;   public boolean isPalindrome(String s) {

&nbsp;       String str=s.replaceAll("\[^a-zA-Z0-9]+", "");

&nbsp;       return new StringBuilder(str).reverse().toString().equalsIgnoreCase(str);

&nbsp;   }

}

```



\## Approach 3 — Two Pointer Technique

\- Use two pointers, one from start and one from end. 

\- Skip non-alphanumeric characters. 

\- Compare characters directly. 

\- No extra memory required.





\#### Time complexity: O(n)

\#### Space complexity: O(1)



\#### Java Code

```java \[]

class Solution {

&nbsp;   public boolean isPalindrome(String s) {

&nbsp;       int left = 0, right = s.length() - 1;

&nbsp;       while (left < right) {

&nbsp;           while (left < right \&\& !Character.isLetterOrDigit(s.charAt(left)))

&nbsp;               left++;

&nbsp;           while (left < right \&\& !Character.isLetterOrDigit(s.charAt(right)))

&nbsp;               right--;

&nbsp;           if (Character.toLowerCase(s.charAt(left)) !=

&nbsp;               Character.toLowerCase(s.charAt(right)))

&nbsp;               return false;

&nbsp;           left++;

&nbsp;           right--;

&nbsp;       }

&nbsp;       return true;

&nbsp;   }

}

```





\## CPP / C++ Code



```Cpp \[]

class Solution {

public:

&nbsp;   bool isPalindrome(string s) {

&nbsp;       int left = 0, right = s.length() - 1;

&nbsp;       while (left < right) {

&nbsp;           while (left < right \&\& !isalnum(s\[left]))

&nbsp;               left++;

&nbsp;           while (left < right \&\& !isalnum(s\[right]))

&nbsp;               right--;

&nbsp;           if (tolower(s\[left]) != tolower(s\[right]))

&nbsp;               return false;

&nbsp;           left++;

&nbsp;           right--;

&nbsp;       }

&nbsp;       return true;

&nbsp;   }

};

```



\## JavaScript Code

``` javascript \[]

var isPalindrome = function(s) {

&nbsp;   let left = 0, right = s.length - 1;

&nbsp;   while (left < right) {

&nbsp;       while (left < right \&\& !isAlphaNumeric(s\[left]))

&nbsp;           left++;

&nbsp;       while (left < right \&\& !isAlphaNumeric(s\[right]))

&nbsp;           right--;

&nbsp;       if (s\[left].toLowerCase() !== s\[right].toLowerCase())

&nbsp;           return false;

&nbsp;       left++;

&nbsp;       right--;

&nbsp;   }

&nbsp;   return true;

};



function isAlphaNumeric(ch) {

&nbsp;   return (

&nbsp;       (ch >= 'a' \&\& ch <= 'z') ||

&nbsp;       (ch >= 'A' \&\& ch <= 'Z') ||

&nbsp;       (ch >= '0' \&\& ch <= '9')

&nbsp;   );

}

```

