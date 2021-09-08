### 1. Finding Non-overlapping members between different sets of arrays


```javascript
function sym(args) {
  let arr = []
  for (let i=0;i<arguments.length;i++) {
    arr = helper2(arr, arguments[i])
  }
  return arr
}

function helper2(arg1, arg2) {
  let arr = []
  for (const ar1 of arg1) {
    if (!arg2.includes(ar1) && !arr.includes(ar1)) {
      arr.push(ar1)
    }
  }
  for (const ar2 of arg2) {
    if (!arg1.includes(ar2) && !arr.includes(ar2)) {
      arr.push(ar2)
    }
  }
  return arr
}

sym([1, 2, 3], [5, 2, 1, 4]);
```

___

### 2. Inventory Update

Compare and update the inventory stored in a 2D array against a second 2D array of a fresh delivery. Update the current existing inventory item quantities (in ```arr1```). If an item cannot be found, add the new item and quantity into the inventory array. The returned inventory array should be in alphabetical order by item.

Example
```updateInventory([[21, "Bowling Ball"], [2, "Dirty Sock"], [1, "Hair Pin"], [5, "Microphone"]], [[2, "Hair Pin"], [3, "Half-Eaten Apple"], [67, "Bowling Ball"], [7, "Toothpaste"]]) should return [[88, "Bowling Ball"], [2, "Dirty Sock"], [3, "Hair Pin"], [3, "Half-Eaten Apple"], [5, "Microphone"], [7, "Toothpaste"]].```

Solution:

```javascript

function updateInventory(arr1, arr2) {
  
    //create a dictionary where second index of each array is key and first index of each array is value
    const inv1 = arr1.reduce((acc, init) => {
        acc[init[1]] = init[0]
        return acc
    }, {})
    
    //build further from the dictionary created above
    const inv2 = arr2.reduce((acc, init) => {
        if (acc[init[1]] !== undefined) {
            acc[init[1]] = acc[init[1]] + init[0]
        } else {
            acc[init[1]] = init[0]
        }
        return acc
    }, inv1)

    //sort inv2 keys in alphabetical order
    const inv3 = Object.keys(inv2).sort().reduce((acc, init) => {
        acc[init] = inv1[init]
        return acc
        }, {})

    //switch dictionary back to array object
    let low = []
    for (let i=0; i<Object.keys(inv3).length; i++) {
        low.push([Object.values(inv3)[i], Object.keys(inv3)[i]])
    }

    return low;
}

// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory(curInv, newInv);
```

