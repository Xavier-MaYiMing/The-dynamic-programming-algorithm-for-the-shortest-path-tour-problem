### The Dynamic Programming Algorithm for the Shortest Path Tour Problem

##### Reference: Festa P, Guerriero F, Laganà D, et al. Solving the shortest path tour problem[J]. European Journal of Operational Research, 2013, 230(3): 464-474.

The shortest path tour problem aims to find the shortest path that traverses multiple disjoint node subsets in a given order.

----

| Variables     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| network       | Dictionary, {node1: {node2: length, node3: length, ...}, ...} |
| node_subset   | List, [[subset1], [subset2], ...]                            |
| nn            | The number of nodes                                          |
| ns            | The number of subsets                                        |
| neighbor      | Dictionary, {node1: [the neighbor nodes of node1], ...}      |
| label_set     | All generated labels                                         |
| label         | label[n] denotes all labels of node n                        |
| best_solution | The best solution ever found                                 |
| delta         | The length of the best solution                              |

----

#### Example

![](/Users/xavier/Desktop/Xavier Ma/个人算法主页/The Dynamic Programming Algorithm for the Shortest Path Tour Problem/SPTP example.png)

The SPTP example has four disjoint node subsets: $\{0\}, \{1, 3\}, \{4, 5\}, \{6\}$. The aim is to find the shortest path from node 0 to node 6 that traverse at least one node in $\{1, 3\}$ and $\{4, 5\}$. The optimal solution of the SPTP is $0\rightarrow3\rightarrow4\rightarrow6$.

```python
if __name__ == '__main__':
    test_network = {
        0: {1: 2, 2: 3, 3: 3},
        1: {0: 2, 3: 2},
        2: {0: 3, 3: 3},
        3: {0: 3, 1: 2, 2: 3, 4: 2, 5: 3, 6: 3},
        4: {3: 2, 6: 2},
        5: {3: 3, 6: 3},
        6: {3: 3, 4: 2, 5: 3},
    }
    subset = [[0], [1, 3], [4, 5], [6]]
    print(main(test_network, subset))
```

##### Output

```python
{
  'path': [0, 3, 4, 6], 
  'length': 7
}
```

