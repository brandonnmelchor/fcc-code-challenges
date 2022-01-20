# Palindrome Checker

Return true if the given string is a palindrome. Otherwise, return false.

A palindrome is a word or sentence that's spelled the same way both forward and backward, ignoring punctuation, case, and spacing.

Note: You'll need to remove all non-alphanumeric characters (punctuation, spaces and symbols) and turn everything into the same case (lower or upper case) in order to check for palindromes.

We'll pass strings with varying formats, such as racecar, RaceCar, and race CAR among others.

We'll also pass strings with special symbols, such as 2A3*3a2, 2A3 3a2, and 2_A3*3#A2.

## Solution

```js
function palindrome(str) {
  let word1 = "";
  let word2 = "";
  let arr = str.toLowerCase().match(/[a-z0-9]/ig);

  for (let i = 0; i < arr.length; i++) {
    word1 += arr[i];
  }

  for (let j = arr.length - 1; j >= 0; j--) {
    word2 += arr[j];
  }

  return word1 === word2;
}

palindrome("1 eye for of 1 eye");
```
