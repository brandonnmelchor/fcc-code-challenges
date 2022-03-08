# DNA Pairing

The DNA strand is missing the pairing element. Take each character, get its pair, and return the results as a 2d array.

Base pairs are a pair of AT and CG. Match the missing element to the provided character.

Return the provided character as the first element in each array.

For example, for the input GCG, return [["G", "C"], ["C","G"], ["G", "C"]]

The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.

## Solution

```js
function pairElement(str) {
  let arr = [];

  for (let i = 0; i < str.length; i++) {
    let pair = [str[i]];

    switch(str[i]) {
      case 'A':
        pair.push('T');
        break;
      case 'T':
        pair.push('A');
        break;
      case 'C':
        pair.push('G');
        break;
      case 'G':
        pair.push('C');
        break;
    }

    arr.push(pair);
  }

  return arr;
}

pairElement("ATCGA");
```
