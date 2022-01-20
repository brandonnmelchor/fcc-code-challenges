# Steamroller

Flatten a nested array. You must account for varying levels of nesting.

Your solution should not use the Array.prototype.flat() or Array.prototype.flatMap() methods.

## Solution

```js
function steamrollArray(arr) {
  let newArr = [];

  function flat(val) {
    for (let i = 0; i < val.length; i++) {
      if (typeof val[i] == 'number') {
        newArr.push(val[i]);
      } else if (!Array.isArray(val[i])) {
        newArr.push(val[i]);
      } else {
        flat(val[i])
      }
    }
  }

  flat(arr);
  return newArr;
}

steamrollArray([1, {}, [3, [[4]]]]);
```
