# Missing letters

Find the missing letter in the passed letter range and return it.

If all letters are present in the range, return undefined.

## Solution

```js
function fearNotLetter(str) {
  const range = 'abcdefghijklmnopqrstuvwxyz';

  for (let i = range.indexOf(str[0]); i < range.length; i++) {
    if (str.indexOf(range[i]) < 0) {
      return range[i];
    }
  }
}

fearNotLetter("stvwx");
```
