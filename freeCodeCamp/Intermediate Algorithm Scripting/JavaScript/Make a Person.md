# Make a Person

Fill in the object constructor with the following methods below:

```js
getFirstName()
getLastName()
getFullName()
setFirstName(first)
setLastName(last)
setFullName(firstAndLast)
```

Run the tests to see the expected output for each method. The methods that take an argument must accept only one argument and it has to be a string. These methods must be the only available means of interacting with the object.

## Solution

```js
const Person = function(firstAndLast) {
  let [first, last] = firstAndLast.split(' ');

  this.getFirstName = () => first;
  this.getLastName = () => last;
  this.getFullName = () => [first, last].join(' ');

  this.setFirstName = (f) => first = f;
  this.setLastName = (l) => last = l;
  this.setFullName = (fL) => [first, last] = fL.split(' ')
};

const bob = new Person('Bob Ross');
```
