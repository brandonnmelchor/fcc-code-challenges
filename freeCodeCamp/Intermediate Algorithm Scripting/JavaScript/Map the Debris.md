# Map the Debris

Return a new array that transforms the elements' average altitude into their orbital periods (in seconds).

The array will contain objects in the format {name: 'name', avgAlt: avgAlt}.

You can read about orbital periods on Wikipedia.

The values should be rounded to the nearest whole number. The body being orbited is Earth.

The radius of the earth is 6367.4447 kilometers, and the GM value of earth is 398600.4418 km3s-2.

## Solution

```js
function orbitalPeriod(arr) {
  const GM = 398600.4418;
  const earthRadius = 6367.4447;

  return arr.map(obj => {
    let a = 2 * Math.PI;
    let b = Math.pow(earthRadius + obj.avgAlt, 3);
    let c = Math.sqrt(b / GM);
    let orb = Math.round(a * c);

    return {name: obj.name, orbitalPeriod: orb};
  })
}

orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);
```
