# Spinal Tap Case

Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.

## Solution

```js
function spinalCase(str) {
  return str.replace(/([a-z])([A-Z])/g, '$1 $2')
    .split(/[^a-z]/i).join('-').toLowerCase();
}
```
