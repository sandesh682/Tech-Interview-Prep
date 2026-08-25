---
tags: [DSA, Graph, Algorithms, Computer-Science]
aliases: [Graph Theory, Graphs]
date: 2026-08-04
---

# Graph Data Structure

## Overview

A **Graph** is a non-linear data structure consisting of a finite set of **Vertices** (Nodes) and a set of **Edges** connecting these vertices.

Mathematically: `G = (V, E)`

- **V**: A set of vertices (e.g., `V = {0, 1, 2, 3}`)
- **E**: A set of edges, which are pairs of vertices (e.g., `E = {(0,1), (1,2)}`)

> [!note] Difference between Tree and Graph
> A **Tree** is a special type of graph (an undirected, connected, acyclic graph). While trees have a strict root and hierarchical structure, graphs can have cycles and no defined root node.

---

## 1. Graph Terminology

- **Vertex / Node:** The fundamental unit of a graph.
- **Edge:** A connection between two vertices.
- **Path:** A sequence of vertices connected by edges.
- **Degree:** The number of edges connected to a vertex.
  - **In-degree:** Number of incoming edges (Directed Graphs).
  - **Out-degree:** Number of outgoing edges (Directed Graphs).
- **Cycle:** A path that starts and ends at the same vertex.
- **Connected Component:** A subgraph in which every two vertices are connected to each other by paths.

---

## 2. Types of Graphs

| Type                         | Description                                                                                                                |
| :--------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| **Undirected Graph**         | Edges have no direction. The edge `(u, v)` is identical to `(v, u)`.                                                       |
| **Directed Graph (Digraph)** | Edges have a direction. The edge `(u, v)` means a path goes from `u` to `v` but not necessarily back.                      |
| **Weighted Graph**           | Edges have weights or costs assigned to them (e.g., distance, time).                                                       |
| **Unweighted Graph**         | Edges do not have weights (assumed to be 1).                                                                               |
| **Cyclic Graph**             | Contains at least one cycle.                                                                                               |
| **Acyclic Graph**            | Contains no cycles. (e.g., DAG - Directed Acyclic Graph).                                                                  |
| **Bipartite Graph**          | Vertices can be divided into two disjoint sets such that every edge connects a vertex in one set to a vertex in the other. |

---

## 3. Graph Representation

Graphs are primarily represented in two ways:

1. **Adjacency Matrix**
2. **Adjacency List**

---

## 1. Adjacency Matrix

### Definition

An **Adjacency Matrix** is a **2D array (V × V)** where:

- Rows represent source vertices.
- Columns represent destination vertices.
- `1` → Edge exists.
- `0` → No edge.
- In a **weighted graph**, store the edge weight instead of `1`.

---

### Example Graph

```text
    1
   / \
  2---3---4
```

Edges:

- 1–2
- 1–3
- 2–3
- 3–4

---

### Matrix

|   |1|2|3|4|
|---|---|---|---|---|
|**1**|0|1|1|0|
|**2**|1|0|1|0|
|**3**|1|1|0|1|
|**4**|0|0|1|0|

---

### JavaScript

```javascript
const adjMatrix = [
  [0, 1, 1, 0],
  [1, 0, 1, 0],
  [1, 1, 0, 1],
  [0, 0, 1, 0]
];
```

---

### Complexity

| Operation | Time |
|-----------|:----:|
| Check if edge exists | O(1) |
| Add edge | O(1) |
| Remove edge | O(1) |
| Iterate neighbours | O(V) |
| Space | **O(V²)** |

---

### Advantages

- Constant-time edge lookup.
- Simple and intuitive implementation.
- Ideal for **dense graphs**.

---

### Disadvantages

- Uses a lot of memory for sparse graphs.
- Neighbour traversal requires scanning an entire row.

---

### Best Used When

- Graph is **dense**.
- Frequent edge existence checks are required.

---

## 2. Adjacency List

### Definition

An **Adjacency List** stores a list of neighbouring vertices for every vertex.

---

### Example Graph

```text
    1
   / \
  2---3---4
```

Edges:

- 1–2
- 1–3
- 2–3
- 3–4

---

### List

```text
1 → 2 → 3
2 → 1 → 3
3 → 1 → 2 → 4
4 → 3
```

---

### JavaScript (Array)

```javascript
const adjList = [
  [],
  [2, 3],
  [1, 3],
  [1, 2, 4],
  [3]
];
```

---

### JavaScript (Object)

```javascript
const adjList = {
  1: [2, 3],
  2: [1, 3],
  3: [1, 2, 4],
  4: [3]
};
```

---

### Complexity

| Operation | Time |
|-----------|:----:|
| Check if edge exists | O(degree) |
| Add edge | O(1) |
| Remove edge | O(degree) |
| Iterate neighbours | O(degree) |
| Space | **O(V + E)** |

---

### Advantages

- Memory efficient.
- Fast neighbour traversal.
- Ideal for **sparse graphs**.

---

### Disadvantages

- Edge lookup is slower than a matrix.
- Removing an edge requires searching the list.

---

### Best Used When

- Graph is **sparse**.
- Performing **DFS** or **BFS**.
- Solving most interview and competitive programming problems.

---

## Matrix vs List

| Feature | Adjacency Matrix | Adjacency List |
|---------|------------------|----------------|
| Space | O(V²) | O(V + E) |
| Edge Lookup | O(1) | O(degree) |
| Neighbour Traversal | O(V) | O(degree) |
| Add Edge | O(1) | O(1) |
| Remove Edge | O(1) | O(degree) |
| Best For | Dense Graphs | Sparse Graphs |

---

## Interview Tips

### Use Adjacency Matrix

- Dense graphs.
- Frequent edge existence checks.
- Small number of vertices.

---

### Use Adjacency List

- Sparse graphs.
- DFS and BFS.
- Most graph algorithms.
- Preferred in coding interviews.

---

## Quick Revision

### Adjacency Matrix

- 2D array
- Space → **O(V²)**
- Edge Lookup → **O(1)**
- Neighbour Traversal → **O(V)**
- Best for **Dense Graphs**

---

### Adjacency List

- Array/Object of lists
- Space → **O(V + E)**
- Edge Lookup → **O(degree)**
- Neighbour Traversal → **O(degree)**
- Best for **Sparse Graphs**
- Used in **DFS, BFS, Dijkstra, Prim's, Topological Sort**, etc.

---

> 💡 **Interview Rule of Thumb**
>
> If the interviewer doesn't specify the graph representation, **use an Adjacency List**. It is the standard representation for almost all graph algorithms because it is memory-efficient and enables fast graph traversal.
---
## 3. Graph (Adjacency List) - CRUD Operations

---

## ➕ addVertex()

### Purpose

Adds a new vertex to the graph.

---

### Algorithm

```text
1. Check if the vertex already exists.
2. If it doesn't exist:
    - Create an empty array for that vertex.
3. Return the graph.
```

---

### JavaScript

```javascript
addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
        this.adjacencyList[vertex] = [];
    }
    return this;
}
```

---

### Example

#### Before

```text
{
    A: ["B"],
    B: ["A"]
}
```

#### Operation

```javascript
graph.addVertex("C");
```

#### After

```text
{
    A: ["B"],
    B: ["A"],
    C: []
}
```

---

### Complexity

| Time | Space |
|------|-------|
| **O(1)** | **O(1)** |

---

### Notes

- Ignores duplicate vertices.
- Creates an empty neighbor list.
- Constant-time operation.

---

## ➕ addEdge()

### Purpose

Creates an **undirected edge** between two existing vertices.

---

### Algorithm

```text
1. Verify both vertices exist.
2. Add vertex2 to vertex1's adjacency list.
3. Add vertex1 to vertex2's adjacency list.
4. Return the graph.
```

---

### JavaScript

```javascript
addEdge(vertex1, vertex2) {
    if (
        this.adjacencyList[vertex1] &&
        this.adjacencyList[vertex2]
    ) {
        this.adjacencyList[vertex1].push(vertex2);
        this.adjacencyList[vertex2].push(vertex1);
    }

    return this;
}
```

---

### Example

#### Before

```text
A: []
B: []
```

#### Operation

```javascript
graph.addEdge("A", "B");
```

#### After

```text
A: [B]
B: [A]
```

---

### Complexity

| Time | Space |
|------|-------|
| **O(1)** | **O(1)** |

---

### Notes

- Works only if both vertices exist.
- For an **undirected graph**, the edge is added in both directions.
- `push()` is a constant-time operation.

---

## ❌ removeEdge()

### Purpose

Removes the edge between two vertices.

---

### Algorithm

```text
1. Verify both vertices exist.
2. Remove vertex2 from vertex1's adjacency list.
3. Remove vertex1 from vertex2's adjacency list.
4. Return the graph.
```

---

### JavaScript

```javascript
removeEdge(vertex1, vertex2) {
    if (
        this.adjacencyList[vertex1] &&
        this.adjacencyList[vertex2]
    ) {
        this.adjacencyList[vertex1] =
            this.adjacencyList[vertex1].filter(
                v => v !== vertex2
            );

        this.adjacencyList[vertex2] =
            this.adjacencyList[vertex2].filter(
                v => v !== vertex1
            );
    }

    return this;
}
```

---

### Example

#### Before

```text
A: [B, C]
B: [A]
C: [A]
```

#### Operation

```javascript
graph.removeEdge("A", "B");
```

#### After

```text
A: [C]
B: []
C: [A]
```

---

### Complexity

| Time | Space |
|------|-------|
| **O(V)** *(or O(deg(v₁) + deg(v₂)))* | **O(V)** |

> **Why?**
>
> `filter()` scans the entire adjacency list and creates a new array.

---

### Notes

- Removes the edge from **both vertices**.
- Does **not** delete the vertices.
- Uses `filter()`, so removal is not constant time.

---

## ❌ removeVertex()

### Purpose

Removes a vertex along with **all of its connected edges**.

---

### Algorithm

```text
1. Check if the vertex exists.
2. While the vertex has neighbors:
    - Remove one connected edge.
3. Delete the vertex.
4. Return the graph.
```

---

### JavaScript

```javascript
removeVertex(vertex) {
    while (this.adjacencyList[vertex].length) {
        const adjacentVertex =
            this.adjacencyList[vertex].pop();

        this.removeEdge(vertex, adjacentVertex);
    }

    delete this.adjacencyList[vertex];

    return this;
}
```

---

### Example

#### Before

```text
A: [B, C]
B: [A, C]
C: [A, B]
```

#### Operation

```javascript
graph.removeVertex("B");
```

#### Step 1

```text
Remove edge (B, C)

A: [B, C]
B: [A]
C: [A]
```

#### Step 2

```text
Remove edge (B, A)

A: [C]
B: []
C: [A]
```

#### Step 3

```text
Delete vertex B

A: [C]
C: [A]
```

---

### Complexity

| Time | Space |
|------|-------|
| **O(V + E)** | **O(V)** |

#### Why?

For each adjacent vertex:

- `pop()` → **O(1)**
- `removeEdge()` → uses `filter()` → **O(degree)**

Across the entire operation, every connected edge is removed once.

Overall complexity:

```text
O(V + E)
```

---

### Notes

- Removes **all connected edges first**.
- Prevents dangling references.
- Deletes the vertex only after all edges have been removed.
- Standard interview implementation for adjacency lists.

---

## 📊 Complexity Summary

| Operation | Time | Space |
|-----------|------|-------|
| `addVertex()` | **O(1)** | **O(1)** |
| `addEdge()` | **O(1)** | **O(1)** |
| `removeEdge()` | **O(V)** *(or O(deg(v₁) + deg(v₂)))* | **O(V)** |
| `removeVertex()` | **O(V + E)** | **O(V)** |

---

## 💡 Interview Tips

- Always create an empty adjacency list when adding a new vertex.
- For an **undirected graph**, every edge must be added and removed from **both vertices**.
- `removeEdge()` uses `filter()`, which creates a new array, so it is **not O(1)**.
- Always remove **all incident edges** before deleting a vertex.
- `pop()` is **O(1)**, making it efficient for iterating through connected vertices during vertex removal.

---
## 5. Graph Traversals

#### Recursive Depth-First Search (DFS)

DFS explores a graph by going **as deep as possible** before backtracking.

> **DFS = Visit → Mark → Go Deeper → Backtrack**

#### Example

```text
       A
      / \
     B   C
    / \   \
   D   E   F
```

DFS from `A`:

```text
A → B → D → E → C → F
```

#### Code

```javascript
DFS(start) {
    const result = [];
    const visited = {};

    const dfs = (vertex) => {
        if (!this.adjacencyList[vertex]) return;

        visited[vertex] = true;
        result.push(vertex);

        for (const neighbor of this.adjacencyList[vertex]) {
            if (!visited[neighbor]) {
                dfs(neighbor);
            }
        }
    };

    dfs(start);

    return result;
}
```

#### Complexity

- **Time:** `O(V + E)`
    
- **Space:** `O(V)`
    

> `visited` prevents infinite loops in cyclic graphs.

## 🔑 Golden Rule — Iterative BFS & DFS

> **Always mark `visited` when you enter the node, before exploring neighbors.**
---
### Iterative Depth-First Search (DFS)

#### What is DFS?

Iterative DFS uses a **stack** instead of recursion.

> **DFS = Stack → Pop → Visit → Push Neighbors**

#### Example

```text
       A
      / \
     B   C
    / \   \
   D   E   F
```

DFS from `A`:

```text
A → B → D → E → C → F
```

#### Code

```javascript
DFSIterative(start) {
    const result = [];
    const visited = {};
    
    const stack = [start];
    visited[start] = true;

    while (stack.length) {
        const vertex = stack.pop();

        result.push(vertex);

        for (const neighbor of this.adjacencyList[vertex]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                stack.push(neighbor);
            }
        }
    }

    return result;
}
```

#### Complexity

- **Time:** `O(V + E)`
    
- **Space:** `O(V)`
    

> **Recursive DFS → Call Stack**  
> **Iterative DFS → Explicit Stack**

----
# Iterative Breadth-First Search (BFS)

## What is BFS?

BFS visits a graph **level by level** using a **Queue (FIFO)**.

> **BFS = Queue → Dequeue → Visit → Enqueue Neighbors**

### Example

```text
       A
      / \
     B   C
    / \   \
   D   E   F
```

BFS from `A`:

```text
A → B → C → D → E → F
```

## JavaScript

```javascript
BFSIterative(start) {
    const result = [];
    const visited = {};
    const queue = [start];

    visited[start] = true;

    while (queue.length) {
        const vertex = queue.shift();

        result.push(vertex);

        for (const neighbor of this.adjacencyList[vertex]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                queue.push(neighbor);
            }
        }
    }

    return result;
}
```

## Complexity

```text
Time:  O(V + E)
Space: O(V)
```

- `V` = vertices
    
- `E` = edges
    

## Key Points

- **Queue → FIFO**
    
- Visits **level by level**
    
- Uses `visited` to handle cycles
    
- Useful for **shortest path in unweighted graphs**
    

## 🔑 Golden Rule — Iterative BFS & DFS

> **Always mark a vertex as visited when you PUSH/ENQUEUE it, not when you POP/DEQUEUE it.**

```text
DFS → push → mark visited
BFS → enqueue → mark visited
```

This prevents the same vertex from being added to the stack/queue multiple times.

---
## 6. Must-Know Algorithms

### Shortest Path Algorithms

1. **[[Dijkstra's Algorithm]]:** Finds the shortest path from a single source node to all other nodes.
   - _Constraint:_ Works only on graphs with non-negative weights.
   - _Time Complexity:_ `O(E log V)` (using a Priority Queue / Min-Heap).
2. **[[Bellman-Ford Algorithm]]:** Finds shortest path from a single source node.
   - _Feature:_ Can handle **negative weight edges** and detect negative weight cycles.
   - _Time Complexity:_ `O(V * E)`.
3. **[[Floyd-Warshall Algorithm]]:** Finds the shortest paths between **all pairs** of vertices.
   - _Time Complexity:_ `O(V^3)`.

### Minimum Spanning Tree (MST)

An MST is a subset of the edges of a connected, edge-weighted graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.

1. **[[Kruskal's Algorithm]]:** Sorts edges by weight and uses a [[Disjoint Set (Union-Find)]] data structure to avoid cycles.
2. **[[Prim's Algorithm]]:** Builds the tree one vertex at a time, picking the minimum weight edge that connects a tree vertex to a non-tree vertex (using a Priority Queue).

### Other Key Algorithms

- **[[Topological Sorting]]:** A linear ordering of vertices in a Directed Acyclic Graph (DAG) such that for every directed edge `uv`, vertex `u` comes before `v`. Useful in task scheduling (e.g., compiling dependencies).
- **[[Kosaraju's Algorithm]] / Tarjan's Algorithm:** Used for finding **Strongly Connected Components (SCCs)** in a directed graph.

---
