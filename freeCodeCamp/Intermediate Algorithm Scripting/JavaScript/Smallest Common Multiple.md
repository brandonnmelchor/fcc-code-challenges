# Smallest Common Multiple

Find the smallest common multiple of the provided parameters that can be evenly divided by both, as well as by all sequential numbers in the range between these parameters.

The range will be an array of two numbers that will not necessarily be in numerical order.

For example, if given 1 and 3, find the smallest common multiple of both 1 and 3 that is also evenly divisible by all numbers between 1 and 3. The answer here would be 6.

## Solution

```js
function smallestCommons(arr) {
  let count = 0;
  let [min, max] = arr.sort((a, b) => a - b);
  let numbers = Array(max - min + 1).fill()
    .map((val, index) => index + min);

  for (let i = 1; count < numbers.length; i++) {
    count = 0;

    for (let j = 0; j < numbers.length; j++) {
      if (i % numbers[j] == 0) count++;
    }

    if (count == numbers.length) return i;
  }
}

console.log(smallestCommons([5, 1]));
```
