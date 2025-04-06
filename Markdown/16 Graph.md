16 Graph
16 Graph
# 16 Graphs

## 16.1 What is a Graph?

Graphs are fundamental data structure that represents relationships between objects. Think of graphs as a way to define a connection between things, like friendships in a social network like Facebook or LinkedIn, cities on a map, or the internet.  

Imagine four users in Facebook: Alice, Bob, Charlie, and Diana. Their friendship connections is defined as:
- Alice is friends with Bob and Charlie
- Bob is friends with Alice and Diana
- Charlie is friends with Alice.

The visual representation of this friendship connection can be represented in a graph. 
```
    Alice  
   /    \  
  Bob   Charlie  
   \  
   Diana  
```
## 16.2 Components of a Graph
1. **Vertices (Nodes)** - A vertex (plural: vertices) represents an object. Vertices usually are drawn as points, circles, or the name of the object. Each vertex may have a name or a label (1, 2, 3 or A, B, C or Alice, Bob, Charlie)

2. **Edges** - An edge is a connection between two vertices. Edges can be :  

a. _Undirected_ - No direction, implies the direction is two ways.
For example, an edge **A-B** means there is a connection from A to b, and also a connection from B to A.  

b. _Directed_ - Has a direction, one way connection.  
For example, an edge **A→B** means there is a connection from A to B, but not from B to A.
  
3. **Weight** - In a weighted graph, edges have a weight associated with them. The weights can represent distance, cost, or other numerical values.

## 16.3 Different Types of Graph

### 16.2.1 Directed Graph  
A directed graph (also known as a digraph) is a type of graph where the edges have direction. This means that the relationship between vertices is one-way instead of bi-directional.   
**Example**:  
![](https://github.com/joannes630/StackEdit/blob/main/Book/16%20Graph/directed_graph.png?raw=true)
  
In this graph, the edges can represent relationships such as "following." For example:  
- Wilson follows Smith
- Smith follows Wilson and Jones
- Miller follows Smith, Jones, and Taylor
- Jones does not follow anyone
- Taylor follows Wilson and Jones

### 16.2.2 Undirected Graph
An undirected graph is a type of graph where the edges have no direction. This means that if there is an edge between A and B, there is a connection from A to B and also from B to A.  
**Example**:  
  ![](https://github.com/joannes630/StackEdit/blob/main/Book/16%20Graph/undirected_graph.png?raw=true)
In this graph, the "undirected" edges can represent relationships such as "friendship". For example:

- Wilson is friends with Smith, Jones, and Taylor
- Smith is friends with Wilson and Miller
- Miller is friends with Smith and Jones
- Jones is friends with Miller, Wilson, and Taylor
- Taylor is friends with Wilson and Jones

### 16.2.3 Weighted Graph
A weighted graph is a type of graph where each edge has an associated weight or cost. These weights often represent values such as distance, time, or cost. Weighted graphs can take the form of directed or undirected graphs.  
**Example**: 
![](https://github.com/joannes630/StackEdit/blob/main/Book/16%20Graph/weighted_graph.png?raw=true)

In the graph above, the weights of the edges represents the distance between the cities.

### 16.2.4 Cyclic Graph
A cyclic graph is a type of graph that contains at least one cycle. A _cycle_ is a path of edges and vertices where a vertex is visited more than once, and the path returns to the starting vertex.  

**Example**:  
![](https://github.com/joannes630/StackEdit/blob/main/Book/16%20Graph/cyclic_graph.png?raw=true)
In the graph above, the nodes C, E, D, and B form a cycle.

## 16.4 Representation of Graphs
Visualizing graphs in a diagram helps us understand their structure, but representing them logically in a data structure requires a different approach. Graphs can be represented in two primary ways: Adjacency Matrix and Adjacency List. Both representations are used to store the graph data.  

1. Adjacency Matrix
An adjacency matrix is a two-dimensional array (Matrix) used to represent a graph. The rows and columns represents the vertices, and the cell values indicate the presence (and weight for a weighted graph) of edges.

- For unweighted graphs:
- `matrix[i][j] = 1` if there is an edge between vertex i and j.
- `matrix[i][j] = 0` if no edge exists between vertex i and j.

- For weighted graphs:
- `matrix[i][j] = weight` if there is an edge between vertex i and j.
- `matrix[i][j] = 0` if no edge exists between vertex i and j.

Example:  
```
    A ---- B
     \    /
       C
```
Adjacency matrix representation:  

|       | A   | B   | C   |
|-------|-----|-----|-----|
| **A** | 0   | 1   | 1   |
| **B** | 1   | 0   | 1   |
| **C** | 1   | 1   | 0   |


2. Adjacency List
An adjacency list uses a collection (ArrayList or a LinkedList) to store the neighbors of each vertex. Each vertex has a list of edges connected to it. Each vertex points to a list of its neighbors.

Using the graph example above, the adjacency list would be:

A->[B, C]  
B->[A, C]  
C->[A, B]

## 16.5 Graph Traversal
Graph traversal is the process of visiting all the nodes in a graph in a systematic manner. Traversing a graph allows us to explore the structure of the graph, such as paths, connected components, or cycles. There are two primary techniques for graph traversal:

1. Breadth First Search - BFS explores all the neighbors of a vertex before moving on to the next level of nodes. It uses a **queue** to keep track of the vertices to be explored.

**How BFS Works:**
a. Start at a chosen vertex.
b. Mark the vertex as visited and add it to the queue.
c. Remove the vertex from the queue and explore all its unvisited neighbors.
d. Repeat the process until the queue is empty.

2. Depth First Search (DFS)

## 16.6 A Java Implementation of a Graph
As discussed previously, an **adjacency matrix** is a 2D array used to represent a graph. Each cell in the matrix indicates whether there is an edge between a pair of vertices. We are going to do a simple Java implementation of an adjacency matrix of an undirected graph.
  
**Steps to Implement a Graph Using an Adjacency Matrix**
1. Use a 2D array to represent the matrix.  
2. Initialize the matrix with `0` (no edges).  
3. Add edges by updating the matrix with `1` for connections.  
4. Provide methods to add edges, remove edges, display the graph, and check connectivity.

Here is a complete implementation of an undirected graph using an adjacency matrix:  

```java
public class Graph {
    private int[][] adjacencyMatrix; // The adjacency matrix
    private int numVertices;         // Number of vertices in the graph

    // Constructor
    public Graph(int numVertices) {
        this.numVertices = numVertices;
        adjacencyMatrix = new int[numVertices][numVertices];
    }

    // Add an edge to the undirected graph
    public void addEdge(int source, int destination) {
        adjacencyMatrix[source][destination] = 1;
        adjacencyMatrix[destination][source] = 1;
    }

    // Remove an edge from the graph
    public void removeEdge(int source, int destination) {
        adjacencyMatrix[source][destination] = 0;
        adjacencyMatrix[destination][source] = 0;
    }

    // Check if there is an edge between two vertices
    public boolean isEdge(int source, int destination) {
        return adjacencyMatrix[source][destination] == 1;
    }

    // Main method to test the implementation
    public static void main(String[] args) {
        Graph graph = new Graph(4);

        // Adding edges
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 2);
        graph.addEdge(1, 3);

        // Check connectivity
        System.out.println("Is there an edge between 0 and 1? " + graph.isEdge(0, 1));
        System.out.println("Is there an edge between 2 and 3? " + graph.isEdge(2, 3));

        // Removing an edge
        graph.removeEdge(0, 1);
        System.out.println("After removing edge between 0 and 1:");
    }
}
```
**Code Explanation**

1. **`adjacencyMatrix`**: A 2D array of size `numVertices x numVertices` that represents the connections between vertices.  
2. **`addEdge()`**: Adds an edge between two vertices by setting the corresponding matrix values to `1`.  
3. **`removeEdge()`**: Removes an edge by setting the corresponding matrix values to `0`.  
4. **`isEdge()`**: Checks if there is an edge between two vertices.  

---

### **True/False Questions**
1. In an undirected graph, an edge between A and B implies a connection from A to B and from B to A. 
2. A cyclic graph must have at least one cycle. 
3. Breadth-First Search uses a stack to explore nodes.
4. An adjacency list uses a 2D array to represent the graph. 
5. Weighted graphs can be either directed or undirected. 

---

### Written Response Questions

1. **What is a graph?** Explain it using an example.  
2. **Define the following components of a graph:**
   - Vertices  
   - Edges (Directed and Undirected)  
   - Weight  
3. **What is the difference between a directed graph and an undirected graph?**  
4. **Explain the concept of a weighted graph with an example.**  
5. **What is a cyclic graph?** Give an example.  
6. **What is the significance of graph traversal?** Mention the two primary techniques for graph traversal.  
7. **Differentiate between Breadth-First Search (BFS) and Depth-First Search (DFS).**  
8. **What are the two ways to represent graphs in a data structure? Briefly explain each.**  
9. **Represent the following graph using an adjacency matrix:**  
    ```
    A -- B  
     \  
      C  
    ```
10. **Convert the following graph into an adjacency list:**  
   - **Vertices**: A, B, C  
   - **Edges**: A-B, A-C, B-C  

11. Convert the given undirected graph implementation to a **directed graph**. What changes would you make to the `addEdge` method?  

12. Why might an adjacency list be preferred over an adjacency matrix for a sparse graph?  
13. What is the time complexity of checking for an edge in an adjacency matrix?  
14. Provide an example of a real-world application of graphs.  
15. How does the queue data structure facilitate BFS traversal?  
16. Describe the main purpose of the `isEdge()` method in the Java graph implementation.

---
**Answers:**
### **Concepts**

1. A graph is a data structure that represents relationships between objects. It consists of:
   - **Vertices (Nodes)**: Objects or entities.
   - **Edges**: Connections between the vertices.

   **Example**: Social media friendships where each user is a vertex, and a friendship is an edge.
2. 
   - **Vertices**: Represent objects in the graph. (e.g., Alice, Bob, nodes A, B, C).  
   - **Edges**: Connections between vertices.  
     - **Directed**: One-way connection (e.g., A → B).  
     - **Undirected**: Two-way connection (e.g., A — B).  
   - **Weight**: A numerical value associated with edges, representing distance, cost, etc.

3. 
   - **Directed Graph**: Edges have a direction (e.g., A → B).  
   - **Undirected Graph**: Edges do not have direction (e.g., A — B).  

4. A graph where each edge has an associated weight or cost.  
   **Example**: Cities as vertices and distances between them as edge weights.

5. A graph that contains at least one cycle, where a path of edges and vertices starts and ends at the same vertex.  
   **Example**: A → B → C → A.

6. Graph traversal helps explore nodes and paths within the graph. It is used to find connected components, cycles, or shortest paths.

   **Two Techniques**:  
   - **Breadth-First Search (BFS)**: Level-by-level traversal using a queue.  
   - **Depth-First Search (DFS)**: Recursive traversal along branches using a stack.

7. 
| Feature                | BFS                         | DFS                         |
|------------------------|-----------------------------|-----------------------------|
| **Data Structure**     | Queue                      | Stack (or recursion)        |
| **Traversal**          | Level-by-level             | Deep branch exploration     |
| **Use Case**           | Shortest path, level order | Pathfinding, cycle detection|

8. 
   - **Adjacency Matrix**: A 2D array where matrix\[i\]\[j\] = 1 if an edge exists.  
   - **Adjacency List**: A list where each vertex points to its connected vertices.

---

### **Practical Questions**

1. **Adjacency Matrix for the Graph**:

   ```
       A -- B
        \
         C
   ```

   **Matrix**:
   ```
       A B C
   A  [0, 1, 1]
   B  [1, 0, 0]
   C  [1, 0, 0]
   ```
2. **Adjacency List**:
   - **Vertices**: A, B, C  
   - **Edges**: A-B, A-C, B-C  

   **Adjacency List**:
   ```
   A -> [B, C]
   B -> [A, C]
   C -> [A, B]
   ```
3. **Converting to a Directed Graph**:  
   Modify the `addEdge()` method to remove the bidirectional update:  
```java
public void addEdge(int source, int destination) { 
    adjacencyMatrix[source][destination] = 1; // Only one direction
}
```

---

### **True/False**

1. **True**  
2. **True**  
3. **False**
4. **False**
5. **True**  

---

### **Short Answer**
1. An adjacency list uses less memory for sparse graphs because it only stores existing edges, whereas an adjacency matrix wastes space with zeros.
2. \(O(1)\), because accessing a specific cell in the matrix is constant time.
3. Social networks, maps (cities and roads), web page link structures.
4. BFS uses a queue to process vertices level-by-level. It dequeues a vertex, visits its neighbors, and enqueues unvisited vertices.
5. To check if there is an edge between two vertices by verifying the corresponding matrix value.
Markdown 13559 bytes 2075 words 329 lines Ln 329, Col 97HTML 9491 characters 1898 words 243 paragraphs