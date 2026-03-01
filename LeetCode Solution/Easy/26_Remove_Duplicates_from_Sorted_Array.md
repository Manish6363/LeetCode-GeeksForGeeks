\## Problem

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.



Consider the number of unique elements in nums to be k​​​​​​​​​​​​​​. After removing duplicates, return the number of unique elements k.



The first k elements of nums should contain the unique numbers in sorted order. The remaining elements beyond index k - 1 can be ignored.



link: https://leetcode.com/problems/remove-duplicates-from-sorted-array/



\# Intuition

Since the array is already sorted, all duplicate elements appear next to each other.  

So, we can iterate through the array and keep only the first occurrence of each number by overwriting duplicates in-place using two pointers. But we will see all way of solving it.



\# Approach-1 Brute Force Approach

\- Create a temporary array / list.

\- Traverse the array and store only unique values. 

\- Copy the result back into the original array. 



This is not in-place, but easiest to understand. This approach is not allowed as per problem constraints because it uses extra space.



\#### Time complexity: \*\*O(n)\*\*

\#### Space complexity: \*\*O(n)\*\*

\## Java Code

```java \[]

class Solution {

&nbsp;   public int removeDuplicates(int\[] nums) {

&nbsp;       if (nums.length == 0) return 0;

&nbsp;       int\[] temp = new int\[nums.length];

&nbsp;       int k = 0;

&nbsp;       temp\[k++] = nums\[0];

&nbsp;       for (int i = 1; i < nums.length; i++) {

&nbsp;           if (nums\[i] != nums\[i - 1]) {

&nbsp;               temp\[k++] = nums\[i];

&nbsp;           }

&nbsp;       }

&nbsp;       for (int i = 0; i < k; i++) {

&nbsp;           nums\[i] = temp\[i];

&nbsp;       }

&nbsp;       return k;

&nbsp;   }

}

```



\# Approach-2 Better Approach (Shifting Elements In-place)

Traverse array.

When a new unique element appears, shift it left.

Since array is sorted, we don't really need nested loop — which leads directly to Approach-3.



\#### Time complexity: \*\*O(n²)\*\*

\#### Space complexity: \*\*O(1)\*\*

\## Java Code

```java \[]

class Solution {

&nbsp;   public int removeDuplicates(int\[] nums) {

&nbsp;       int k = 0;

&nbsp;       for (int i = 0; i < nums.length; i++) {

&nbsp;           boolean isDuplicate = false;

&nbsp;           for (int j = 0; j < k; j++) {

&nbsp;               if (nums\[i] == nums\[j]) {

&nbsp;                   isDuplicate = true;

&nbsp;                   break;

&nbsp;               }

&nbsp;           }

&nbsp;           if (!isDuplicate) {

&nbsp;               nums\[k++] = nums\[i];

&nbsp;           }

&nbsp;       }

&nbsp;       return k;

&nbsp;   }

}

```



\# Approach-3 Optimal Approach (using Two Pointer)

\*\*Why two pointers?\*\*

Since array is sorted, all duplicates are adjacent. Two pointers allow us to overwrite duplicates in-place while maintaining order and using O(1) extra space.

Already array is sorted, duplicates are adjacent.

\- i → last unique index

\- j → scan pointer



Whenever a new element is found, move it forward.



\#### Time complexity: \*\*O(n)\*\*

\#### Space complexity: \*\*O(1)\*\*

\## Java Code

```java \[]

class Solution {

&nbsp;   public int removeDuplicates(int\[] nums) {

&nbsp;       int i=0;

&nbsp;       for(int j=1; j<nums.length; j++){

&nbsp;           if(nums\[i]!=nums\[j]){

&nbsp;               i++;

&nbsp;               nums\[i]=nums\[j];

&nbsp;           }

&nbsp;       }

&nbsp;       return i+1;

&nbsp;   }

}

```



\## CPP / C++ Code

```cpp \[]

class Solution {

public:

&nbsp;   int removeDuplicates(vector<int>\& nums) {

&nbsp;       int i = 0;

&nbsp;       for (int j = 1; j < nums.size(); j++) {

&nbsp;           if (nums\[i] != nums\[j]) {

&nbsp;               i++;

&nbsp;               nums\[i] = nums\[j];

&nbsp;           }

&nbsp;       }

&nbsp;       return i + 1;

&nbsp;   }

};

```



\## JavaScript Code

```javascript \[]

var removeDuplicates = function(nums) {

&nbsp;   let i = 0;

&nbsp;   for (let j = 1; j < nums.length; j++) {

&nbsp;       if (nums\[i] !== nums\[j]) {

&nbsp;           i++;

&nbsp;           nums\[i] = nums\[j];

&nbsp;       }

&nbsp;   }

&nbsp;   return i + 1;

};

```

