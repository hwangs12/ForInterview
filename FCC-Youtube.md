# Depth First Search

Please watch the [link](https://www.youtube.com/watch?v=tWVWeAqZ0WU&t=581s) for depth-first-search and breadth-first-search solutions. 

I am writing table illustration to help better understand the solutions


```javascript
const depthFirstPrint = (graph, startingPoint) => {
  const stack = [ startingPoint ]
  
  while (stack.length > 0) {
    const current = stack.pop()
    console.log(current);
  
    for (let neighbor of graph[current]) {
      stack.push(neighbor)
    }
  
  }
}

const graph = {
  a: ['b', 'c'],
  b: ['d'],
  c: ['e'],
  d: ['f'],
  e: [],
  f: []
}

depthFirstPrint(graph, 'a')

```

First of all, the function invoked will show 'acebdf' in order from left to right. 

For the variables in the while loop, here's the table illustration 

| stack opening | current | neighbor | stack closing |
|---------------|---------|----------|---------------|
| []            |    a    |  [b, c]  |     [b, c]    |
| [b]           |    c    |  [e]     |     [b, e]    |
| [b]           |    e    |  []      |     [b]       |
| []            |    b    |  [d]     |     [d]       |
| []            |    d    |  [f]     |     [f]       |
| []            |    f    |  []      |     []        |

