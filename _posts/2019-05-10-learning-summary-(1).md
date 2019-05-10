---
layout: post
title: Learning Summary (1)
data: 2019-05-10 21:26:20 +0700
---

## Algorithm

#### - Cracking the Code Interview (Chapter 1 Arrays and Strings)

1. __Determine if a string has all unique characters__

   Use HashMap to count characters, when `count.containsKey(char), return false`

   or use `count[256]` if ASCII

2. __Remove duplicates in a string without using additional buffer__

   - _(no large additional buffer but O(n^2))_ use a `tail` pointer to record; before `tail` are all different chars;

     compare all chars before `tail` with `str[i]`, if all different, `tail++; str[tail] = str[i]`

   - _(constant additional buffer O(n))_ use `count[256]` to record if a certain character appears; 

     also use a `tail` pointer, `if count[c] == false` then `str[tail] = c; tail++; count[c] = true`

3. __Anagram__

   different length => `return false`

   use `counts[256]` to count the frequency of every character in `s1`  `count[c]++`;

   then scan `s2` check `if counts[c] == 0 return false`  `counts[c]--`

4. __Replace all spaces in a string with "%20"__

   count the number of spaces to calculate the new length of string `newLen = len + count * 2`

   use a pointer to record the position to copy we can copy from the end of the string

5. __Rotate N*N matrix by 90 degrees__

   Start from the external layers(round) of the matrix, then internal layers

   **1**  1  1  1  **1**	 `int layer = 0; layer < N / 2; layer++`

   1  1  1  1  1	 In the above for loop, we have `first = layer; last = N - 1 - layer`

   1  1  1  1  1			then loop `i` from `first` to `last`, we have `offset = i - first`

   1  1  1  1  1				record the top value `int top = matrix[first][i]`

   **1**  1  1  1  **1**				`matrix[first][i] = matrix[last - offset][first]`

   /*   then    */				`matrix[last - offset][first] = matrix[last][last - offset]`

   1 **1**  1  1  1					`matrix[last][last - offset] = matrix[i][last]`

   1  1  1  1  **1**					`matrix[i][last] = top`

   1  1  1  1  1

   **1**  1  1  1  1

   1  1  1  **1**  1

   

6. __If an element in M*N matrix is 0, set its row and column to 0__

   record all the 0 elements' positions, its row and column;

   set 0 according to that record `if row[i] == true || col[j] == true , then  matrix[i][j] = 0 `

7. __check s2 is a rotation of s1__

   check if length equal

   concatenate s1 with itself, then check if s2 is a substring of that























