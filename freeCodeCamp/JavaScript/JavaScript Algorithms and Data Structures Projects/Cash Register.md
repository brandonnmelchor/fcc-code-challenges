# Cash Register

Design a cash register drawer function checkCashRegister() that accepts purchase price as the first argument (price), payment as the second argument (cash), and cash-in-drawer (cid) as the third argument.

cid is a 2D array listing available currency.

The checkCashRegister() function should always return an object with a status key and a change key.

Return {status: "INSUFFICIENT_FUNDS", change: []} if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return {status: "CLOSED", change: [...]} with cash-in-drawer as the value for the key change if it is equal to the change due.

Otherwise, return {status: "OPEN", change: [...]}, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

<table class='table table-striped'><tr><th>Currency Unit</th><th>Amount</th></tr><tr><td>Penny</td><td>$0.01 (PENNY)</td></tr><tr><td>Nickel</td><td>$0.05 (NICKEL)</td></tr><tr><td>Dime</td><td>$0.1 (DIME)</td></tr><tr><td>Quarter</td><td>$0.25 (QUARTER)</td></tr><tr><td>Dollar</td><td>$1 (ONE)</td></tr><tr><td>Five Dollars</td><td>$5 (FIVE)</td></tr><tr><td>Ten Dollars</td><td>$10 (TEN)</td></tr><tr><td>Twenty Dollars</td><td>$20 (TWENTY)</td></tr><tr><td>One-hundred Dollars</td><td>$100 (ONE HUNDRED)</td></tr></table>

```js
[
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90],
  ["FIVE", 55],
  ["TEN", 20],
  ["TWENTY", 60],
  ["ONE HUNDRED", 100]
]
```

## Solution

```js
function checkCashRegister(price, cash, cid) {
  let diff = (cash - price);
  let total = cid.reduce((sum, money) => Math.round((sum + money[1]) * 100) / 100, 0);

  if (total == diff) return {status: "CLOSED", change: cid};
  else if (total < diff) return {status: "INSUFFICIENT_FUNDS", change: []};

  let value = [["PENNY", .01], ["NICKEL", .05], ["DIME", .1], ["QUARTER", .25],
    ["ONE", 1], ["FIVE", 5], ["TEN", 10], ["TWENTY", 20], ["ONE HUNDRED", 100]];

  for (let i = 0; i < cid.length; i++) {
    if (cid[i][0] == value[i][0]) cid[i].push(Math.round(cid[i][1] / value[i][1]))
  }

  let change = cid.reverse().reduce((arr, money) => {
    if (diff - (money[1] / money[2]) >= 0) {
      let count = 0;

      for (let i = 1; i <= money[2] && (diff - (money[1] / money[2])) >= 0; i++) {
        diff = Math.round((diff - (money[1] / money[2])) * 100) / 100;
        count++;
      }

      money[1] = (money[1] / money[2]) * count;
      money.pop();
      arr.push(money);
    }

    return arr;
  }, [])

  if (diff > 0) return {status: "INSUFFICIENT_FUNDS", change: []}; 
  else return {status: "OPEN", change: change};
}

checkCashRegister(3.26, 100, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25],
  ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
```
