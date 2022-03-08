# Roman Numeral Converter

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

## Solution

```js
function convertToRoman(num) {
  let rom = [];
  let arr = Array.from(String(num), (val => Number(val)));
  let romans = ['I', 'II', 'III', 'IV', 'V', 'VI', 'VII', 'VIII', 'IX',
    'X', 'XX', 'XXX', 'XL', 'L', 'LX', 'LXX', 'LXXX', 'XC',
    'C', 'CC', 'CCC', 'CD', 'D', 'DC', 'DCC', 'DCCC', 'CM'];

  for (let i = 0; i < arr.length; i++) {
    arr[i] = arr[i] * Math.pow(10, arr.length - (i + 1));

    if (arr[i] >= 1000) {
      for (let m = 1000; m <= arr[i]; m += 1000) {
        rom.push('M');
      }
    } else if (arr[i] >= 100) rom.push(romans[(arr[i] / 100) + 17]);
      else if (arr[i] >= 10) rom.push(romans[(arr[i] / 10) + 8]);
      else if (arr[i] > 0) rom.push(romans[arr[i] - 1]);
  }

  return rom.join('');
}

convertToRoman(1984);
```
