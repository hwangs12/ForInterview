## Finding Non-overlapping members between different sets of arrays

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
