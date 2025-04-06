# 15 Tree

## 15.1 What is a Tree?

A tree is a hierarchical data structure that consists of nodes connected by edges. It begins with a single node, known as the root, and branches out to child nodes, forming a tree-like structure. Each node can have zero or more child nodes, and nodes without children are called leaves. 

Trees are widely used to represent relationships such as hierarchical data (for example a family tree), file systems (with folders and either another folder or files within the folder), or decision-making processes. Common types of trees include:
1. **General trees** - A tree where there is no restriction on the number of chilren a node can have.
2. **Binary trees** - A general tree where each node has at most two children,
3. **Binary search trees** - A binary tree that is used for efficient searching and sorting, following a rule where nodes with values smaller than the parent are placed in the left subtree, and nodes with values larger than the parent are placed in the right subtree.
4. **AVL and Red-Black trees** - An AVL tree and a Red-Black tree are specialized variants of binary search trees that are re-balanced automatically after each insertion or deletion of a node.

## 15.2 Terminologies

Here are the key terminologies commonly used for trees:
1.  **Node**: A basic unit of a tree containing data and links to its children.
2.  **Root**: The topmost node in the tree, serving as the starting point.
3.  **Parent**: A node that has one or more child nodes.
4.  **Child**: A node that has a parent node.
5.  **Leaf**: A node with no children.
6.  **Edge**: A connection between two nodes, typically from a parent to a child.
7.  **Subtree**: A portion of a tree that itself forms a tree, starting from a node and including all its descendants.
8.  **Height of a Node**: The longest path from the node to a leaf.
9.  **Height of a Tree**: The height of the root node, or the longest path from the root to a leaf.
10.  **Depth of a Node**: The number of edges from the root to the node.
11.  **Level**: The depth of a node, with the root node being at level 0.
12.  **Degree of a Node**: The number of children a node has.
13.  **Traversal**: The process of visiting all the nodes in the tree (e.g., in-order, pre-order, post-order, level-order).

## 15.3 General Tree
A general tree is the most flexible form of a tree. Each node can have **any number of children**. There is no restriction on the number of child nodes a parent node can have. It is commonly used to represent hierarchical structures like a family tree, file system and organization charts. 

![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/general_tree.png?raw=true)

## 15.4 Binary Tree
A **binary tree** is a hierarchical data structure where each node can have up to **two children**, known as the **left child** and the **right child**. It is widely used for its simplicity in organizing data. There are no specific rules governing whether a child is placed in the left or right subtree.

![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/binary_tree.png?raw=true)

## 15.5 Binary Search Tree (BST)
A **Binary Search Tree (BST)** is a special type of **binary tree** where the nodes are arranged in a specific order to enable **efficient searching, insertion, and deletion** operations. Each node in a BST follows the **binary search property**:

- The **left child** contains values **smaller** than the parent node.
- The **right child** contains values **greater** than the parent node.
- This rule applies **recursively** to all nodes in the tree.

![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/binary_search_tree.png?raw=true)

###  15.5.1 BST Node Insertion
Inserting a node into a binary search tree follows specific rules. As mentioned earlier, a binary search tree organizes nodes such that values smaller than the parent are placed in the left subtree, while values greater than the parent are placed in the right subtree. In a binary search tree, duplicate values are typically not allowed.

Consider the binary search tree shown below, which initially consists of the nodes 2, 1, and 5, inserted in that order. Starting with an empty tree, 2 was inserted first, becoming the root. Next, 1 was added; since 1 is less than 2, it was placed in the left subtree. Finally, 5 was inserted; as 5 is greater than 2, it was placed in the right subtree.

Next, we want to insert a node with a value of 3. Starting at the root node, we see that 3 is greater than 2, so we move to the right subtree. Then, since 3 is less than 5, we move to the left subtree of 5. Finding that spot empty, we insert node 3 in the left subtree of 5.

![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/node_insertion_1.png?raw=true)

Inserting nodes can be compared to a pinball machine, where the ball (node) moves left or right based on its value relative to the current node. If the value is smaller, it moves to the left subtree; if it’s larger, it moves to the right subtree.

### 15.5.2 BST Node Deletion
Deleting a node in a binary search tree (BST) is a structured process, as it requires maintaining the tree's ordered properties. There are three primary cases to consider when deleting a node:

1.  **Node with No Children (Leaf Node)**:
    
If the node to be deleted is a leaf node, then it is very straigtforward. It can be removed directly, as it has no dependencies. 

For example, if the node has a value of 5, and it has no children, it is simply disconnected from its parent.
![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/node_deletion_leaf.png?raw=true)

2.  **Node with One Child**:
    
If the node to be deleted has only one child, its child replaces it. The parent's reference to the node is updated to point to the node's single child, ensuring the tree remains connected.

For instance, if the node with a value of 3 is deleted and it has only one child, we simply promote the child of node 3 to take its place.

![](https://github.com/joannes630/StackEdit/blob/main/Book/15%20Tree/node_deletion_one_child.png?raw=true)

    
3.  **Node with Two Children**:
    
If the node to be deleted has two children, the process is more complex. The node must be replaced with either:
-   **The in-order successor** (the smallest value in its right subtree), or
-   **The in-order predecessor** (the largest value in its left subtree).
-   After finding the replacement, the successor or predecessor node is removed from its original location (as it will either be a leaf or have one child) and placed in the position of the deleted node.

**Steps for Node Deletion**:

1.  Locate the node to be deleted using a traversal, comparing values as in a standard search.
2.  Identify which of the three cases applies.
3.  Perform the necessary restructuring to maintain the BST properties.

**Example**: Consider a BST with the values 10, 5, 15, and 12:

-   Deleting 5 (leaf node): The node is removed directly.
-   Deleting 15 (one child): The child (12) replaces 15.
-   Deleting 10 (two children): Replace 10 with the in-order successor (12) and update links.

By following these steps, the BST remains properly structured after deletion. This process ensures that the efficiency of operations like search, insert, and delete remains optimal.

### 15.5.3 BST Tree Traversal
As we have discussed, in a BST, each node contains a key, and the keys follow a specific ordering property: for any given node, the keys in the left subtree are less than the node's key, and the keys in the right subtree are greater than the node's key. This property makes traversal a critical operation for accessing and processing data stored in a BST.

**Traversal** refers to visiting each node in the tree systematically, ensuring that every element is processed exactly once. Traversals are fundamental in various applications, such as searching for specific elements, sorting data, or performing operations on every node.

The primary types of BST traversal include breadth first search and depth first search.

#### 15.4.3.1 Breadth First Search
**Breadth-First Search (BFS)** is a tree traversal technique that explores all the nodes at a given depth level before moving on to nodes at the next depth level. Unlike depth-first search, which dives deep into one branch before backtracking, BFS proceeds level by level, making it ideal for tasks that require exploration of all immediate neighbors before moving deeper.

BFS requires a **queue** data structure to keep track of nodes to visit next. Nodes are enqueued as they are discovered and dequeued as they are processed.

#### **Algorithm**

The BFS algorithm for a binary tree is as follows:

1.  Initialize an empty queue.
2.  Enqueue the root node.
3.  While the queue is not empty:
    -   Dequeue the front node from the queue.
    -   Process the node (e.g., print or store its value).
    -   If the dequeued node has a left child, enqueue it.
    -   If the dequeued node has a right child, enqueue it.

#### **Example**

Consider the following binary tree:
```
        1
       / \
      2   3
     / \   \
    4   5   6
```

**Step-by-Step BFS Traversal:**

-   Start with the root: Enqueue `1`.
-   Dequeue `1` and enqueue its children: `2`, `3`.
-   Dequeue `2` and enqueue its children: `4`, `5`.
-   Dequeue `3` and enqueue its child: `6`.
-   Dequeue `4`, `5`, and `6` (no children to enqueue).

**Output**: `1, 2, 3, 4, 5, 6`

#### 15.5.3.2 Depth First Search
**Depth-First Search (DFS)** is a tree or graph traversal technique that explores as far down a branch as possible before backtracking to explore other branches. It prioritizes depth over breadth, making it particularly useful for tasks that require examining all possible paths or deep structures.

Depth-First Search (DFS) uses a **stack** to traverse a tree by systematically exploring each branch as deeply as possible before backtracking. The root node is pushed onto the stack, and at each step, the top node is popped, processed, and its children are pushed onto the stack (right child first, then left child) to ensure the left child is processed next. The stack ensures that nodes are revisited in the correct order as the algorithm backtracks, enabling efficient exploration of the tree structure.

#### **Types of DFS Traversals (for Binary Trees)**

1.  **Preorder Traversal**:
    
    -   Visit the root, then traverse the left subtree, followed by the right subtree.
    -   Order: **Root → Left → Right**
2.  **Inorder Traversal**:
    
    -   Traverse the left subtree, visit the root, then traverse the right subtree.
    -   Order: **Left → Root → Right**
    -   Yields sorted order in Binary Search Trees (BSTs).
3.  **Postorder Traversal**:
    
    -   Traverse the left subtree, then the right subtree, and finally visit the root.
    -   Order: **Left → Right → Root**
  
  Below are examples of **preorder**, **inorder**, and **postorder** traversal on a binary tree, along with their explanations.

### **Example Tree**
```
        1
       / \
      2   3
     / \   \
    4   5   6
```

### **1. Preorder Traversal**
Preorder traversal visits nodes in the order:
**Root → Left Subtree → Right Subtree**

#### **Steps**:
1. Visit the root node (`1`).
2. Traverse the left subtree:
   - Visit `2`, then `4` (left child), and `5` (right child).
3. Traverse the right subtree:
   - Visit `3`, then `6` (right child).

#### **Output**:
```
1, 2, 4, 5, 3, 6
```

### **2. Inorder Traversal**
Inorder traversal visits nodes in the order:
**Left Subtree → Root → Right Subtree**

#### **Steps**:
1. Traverse the left subtree:
   - Visit `4`, then `2`, and then `5`.
2. Visit the root node (`1`).
3. Traverse the right subtree:
   - Visit `3`, then `6`.

#### **Output**:
```
4, 2, 5, 1, 3, 6
```

### **3. Postorder Traversal**
Postorder traversal visits nodes in the order:
**Left Subtree → Right Subtree → Root**

#### **Steps**:
1. Traverse the left subtree:
   - Visit `4` and `5`, then `2`.
2. Traverse the right subtree:
   - Visit `6`, then `3`.
3. Visit the root node (`1`).

#### **Output**:
```
4, 5, 2, 6, 3, 1
```
##### 
## 15.6 Balance Binary Search Tree
The last tree we will discuss is a balanced binary search tree. A **Balanced Binary Search Tree (Balanced BST)** is a type of binary tree where the height of the tree is kept as small as possible to ensure efficient operations. For a tree to be considered **balanced**, the heights of the left and right subtrees of any node must not differ by more than 1.

Balanced BSTs are designed to overcome the inefficiencies of unbalanced BSTs, where operations like search, insertion, and deletion can degrade to $O(n)$ time complexity in the worst case (e.g., when the tree starts resembling a linked list). By maintaining balance, these trees guarantee $O(\log n)$ time complexity for these operations, making them ideal for scenarios requiring frequent and efficient data access.

An examples of balanced BST is an AVL tree.

### 15.6.1 AVL Tree
Here’s an explanation and example of an **AVL Tree**, including how it works.

As mentioned earlier, an **AVL Tree** is a Balancing BST where the difference in height between the left and right subtrees (called the **balance factor**) of any node is at most 1. If this balance is violated during insertion or deletion, the tree performs rotations (single or double) to restore balance.

### **Example of an AVL Tree**

Let’s construct an AVL Tree by inserting the numbers: `10`, `20`, `30`, `40`, `50`, `25`.

#### **Step-by-Step Construction**

1.  **Insert 10**:
    
    -   Tree:
        
        ```
        10
        
        ```
        
    -   No imbalance since it’s the first node.
2.  **Insert 20**:
    
    -   Tree:
        
        ```
        10
          \
          20
        
        ```
        
    -   Balance factor for root (10) = `0 (left height) - 1 (right height) = -1`.
    -   No rotations needed.
3.  **Insert 30**:
    
    -   Tree:
        
        ```
        10
          \
          20
            \
            30
        
        ```
        
    -   Balance factor for root (10) = `0 - 2 = -2`.
        
    -   **Imbalance detected** at 10 → Perform a **left rotation** around 10.
        
    -   After rotation:
        
        ```
          20
         /  \
        10   30
        
        ```
        
4.  **Insert 40**:
    
    -   Tree:
        
        ```
          20
         /  \
        10   30
                \
                40
        
        ```
        
    -   Balance factors:
        -   Node 20 = `1 (left height) - 2 (right height) = -1`.
        -   No rotations needed.
5.  **Insert 50**:
    
    -   Tree:
        
        ```
          20
         /  \
        10   30
                \
                40
                  \
                  50
        
        ```
        
    -   Balance factors:
        
        -   Node 20 = `1 - 3 = -2` → Imbalance detected at 20.
        -   Perform a **left rotation** around 20.
    -   After rotation:
        
        ```
            30
           /  \
          20   40
         /       \
        10        50
        
        ```
        
6.  **Insert 25**:
    
    -   Tree:
        
        ```
            30
           /  \
          20   40
         /  \     \
        10   25    50
        
        ```
        
    -   Balance factors:
        -   Node 30 = `2 (left height) - 2 (right height) = 0`.
        -   No rotations needed.

----------

### **Final AVL Tree**

```
         30
        /  \
       20   40
      /  \     \
     10   25    50

```
Note that, in an **AVL tree**, you must check the **balance factor** of every node on the path from the insertion point **up to the root**, not just the root itself. This is because an imbalance can occur at any ancestor node of the newly inserted node.

**Why Check All Nodes on the Path?**

-   Each insertion modifies the height of the tree.
-   Changes in height can propagate upward, potentially violating the AVL balance property (balance factor = -1, 0, or 1) for any ancestor of the inserted node.
-   If you only check the root, imbalances in lower levels of the tree could go undetected.

**Example**

Let’s insert nodes `10`, `20`, and `30` into an initially empty AVL tree:

1.  Insert `10`:
    
    -   Tree:
        
        ```
        10
        
        ```
        
    -   No imbalance. Only root exists.
2.  Insert `20`:
    
    -   Tree:
        
        ```
        10
          \
          20
        
        ```
        
    -   Check balance factors:
        -   Node `20`: Balanced.
        -   Node `10`: Balance factor = `0 (left) - 1 (right) = -1`. Still balanced.
3.  Insert `30`:
    
    -   Tree:
        
        ```
        10
          \
          20
            \
            30
        
        ```
        
    -   Check balance factors:
        
        -   Node `30`: Balanced.
        -   Node `20`: Balance factor = `0 (left) - 1 (right) = -1`. Balanced.
        -   **Node `10`:** Balance factor = `0 (left) - 2 (right) = -2`. **Imbalanced** → Perform a **left rotation** at `10`.
    -   After rotation:
        
        ```
          20
         /  \
        10   30
        
        ```
Again, the balance must be checked **at every ancestor** of the newly inserted node because changes in subtree height can propagate upward. Rotations are applied only where the imbalance is detected, and adjustments ripple upward until the tree is balanced.

### Types of Imbalances in an AVL Tree

In an **AVL tree**, there are four types of imbalances, based on the direction of insertion or deletion. These imbalances are resolved using **rotations** (single or double) to restore balance.

### **1. Left-Left (LL) Imbalance**

-   **Description**: Occurs when a new node is inserted into the left subtree of the left child of an imbalanced node.
    
-   **Example**:
    
    ```
            30
           /
         20
        /
      10
    
    ```
    
    -   Balance factors:
        -   Node `10`: 0 (balanced).
        -   Node `20`: 1(left)−0(right)=11 (left) - 0 (right) = 1 (balanced).
        -   Node `30`: 2(left)−0(right)=22 (left) - 0 (right) = 2 (**imbalanced**).
-   **Solution**: Perform a **right rotation** on the imbalanced node (`30`).
    
    -   After rotation:
        
        ```
              20
             /  \
           10    30
        
        ```
        
### **2. Right-Right (RR) Imbalance**

-   **Description**: Occurs when a new node is inserted into the right subtree of the right child of an imbalanced node.
    
-   **Example**:
    
    ```
        10
          \
           20
             \
             30
    
    ```
    
    -   Balance factors:
        -   Node `30`: 0 (balanced).
        -   Node `20`: 0(left)−1(right)=−10 (left) - 1 (right) = -1 (balanced).
        -   Node `10`: 0(left)−2(right)=−20 (left) - 2 (right) = -2 (**imbalanced**).
-   **Solution**: Perform a **left rotation** on the imbalanced node (`10`).
    
    -   After rotation:
        
        ```
              20
             /  \
           10    30
        
        ```
        
### **3. Left-Right (LR) Imbalance**

-   **Description**: Occurs when a new node is inserted into the right subtree of the left child of an imbalanced node.
    
-   **Example**:
    
    ```
            30
           /
         10
           \
           20
    
    ```
    
    -   Balance factors:
        -   Node `20`: 0 (balanced).
        -   Node `10`: 0(left)−1(right)=−10 (left) - 1 (right) = -1 (balanced).
        -   Node `30`: 2(left)−0(right)=22 (left) - 0 (right) = 2 (**imbalanced**).
-   **Solution**: Perform a **left rotation** on the left child (`10`), followed by a **right rotation** on the imbalanced node (`30`).
    
    -   After rotations:
        
        ```
              20
             /  \
           10    30
        
        ```
        
### **4. Right-Left (RL) Imbalance**

-   **Description**: Occurs when a new node is inserted into the left subtree of the right child of an imbalanced node.
    
-   **Example**:
    
    ```
        10
          \
           30
          /
        20
    
    ```
    
    -   Balance factors:
        -   Node `20`: 0 (balanced).
        -   Node `30`: 1(left)−0(right)=11 (left) - 0 (right) = 1 (balanced).
        -   Node `10`: 0(left)−2(right)=−20 (left) - 2 (right) = -2 (**imbalanced**).
-   **Solution**: Perform a **right rotation** on the right child (`30`), followed by a **left rotation** on the imbalanced node (`10`).
    
    -   After rotations:
        
        ```
              20
             /  \
           10    30
        
        ```
        
The type of imbalance depends on the direction of insertion relative to the imbalanced node. Single rotations are sufficient for **LL** and **RR** imbalances, while double rotations are needed for **LR** and **RL** imbalances. These rotations ensure the AVL tree remains balanced, maintaining $O(\log n)$ time complexity for search, insertion, and deletion operations.

## 15.6 Java TreeSet Class
The **TreeSet** class in Java is a part of the `java.util` package and implements the `NavigableSet` interface, which extends the `SortedSet` interface. It is a collection that uses a **Red-Black Tree** (a self-balancing binary search tree) to store its elements. The elements in a `TreeSet` are sorted in their **natural order** (ascending). 

### **Key Features of TreeSet**
1. **Sorted Order**: Elements are always maintained in sorted order.
2. **No Duplicates**: TreeSet does not allow duplicate elements.
3. **Performance**: Operations like add, remove, and search run in $O(\log n)$ time complexity because it uses a Red-Black Tree.

#### **Basic Example**
```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> set = new TreeSet<>();
        set.add(10);
        set.add(20);
        set.add(5);
        set.add(15);

        System.out.println("TreeSet: " + set); // Output: [5, 10, 15, 20]
        System.out.println("First Element: " + set.first()); // Output: 5
        System.out.println("Last Element: " + set.last()); // Output: 20
    }
}
```
### **Common Methods**
| **Method**              | **Description**                                              |
|-------------------------|-------------------------------------------------------------|
| `add(E e)`              | Adds an element to the set.                                  |
| `remove(Object o)`      | Removes the specified element from the set.                  |
| `contains(Object o)`    | Checks if the set contains the specified element.            |
| `size()`                | Returns the number of elements in the set.                   |
| `isEmpty()`             | Checks if the set is empty.                                  |
| `first()`               | Retrieves the first (lowest) element.                        |
| `last()`                | Retrieves the last (highest) element.                        |

The `TreeSet` class is a powerful tool for managing sorted, unique data with efficient operations and a variety of utility methods for navigation and querying.

## 15.7 Java TreeMap Class
The **TreeMap** class in Java is part of the `java.util` package and implements the `NavigableMap` interface, which extends the `SortedMap` interface. It is a **Map** that stores its keys in a **sorted order**, based on their natural ordering or a custom comparator provided at the time of creation. Internally, `TreeMap` uses a **Red-Black Tree**, a self-balancing binary search tree, to store key-value pairs.

---

### **Key Features of TreeMap**
1. **Sorted Order**: The keys are always maintained in sorted order.
2. **No Duplicate Keys**: Keys must be unique, but values can be duplicated.
3. **Performance**: Operations like insertion, deletion, and search run in $O(\log n)$ time complexity because it uses a Red-Black Tree.

#### **Basic Example**
```java
import java.util.TreeMap;

public class TreeMapExample {
    public static void main(String[] args) {
        TreeMap<Integer, String> map = new TreeMap<>();
        map.put(3, "Three");
        map.put(1, "One");
        map.put(2, "Two");

        System.out.println("TreeMap: " + map); // Output: {1=One, 2=Two, 3=Three}
        System.out.println("First Key: " + map.firstKey()); // Output: 1
        System.out.println("Last Key: " + map.lastKey()); // Output: 3
    }
}
```

### **Common Methods**
| **Method**                   | **Description**                                              |
|------------------------------|-------------------------------------------------------------|
| `put(K key, V value)`        | Inserts a key-value pair into the map.                      |
| `get(Object key)`            | Retrieves the value associated with the specified key.      |
| `remove(Object key)`         | Removes the key-value pair for the specified key.           |
| `containsKey(Object key)`    | Checks if the map contains the specified key.               |
| `containsValue(Object value)`| Checks if the map contains the specified value.             |
| `size()`                     | Returns the number of key-value pairs in the map.           |
| `isEmpty()`                  | Checks if the map is empty.                                 |


The **TreeMap** class is a powerful choice when working with maps that require sorted keys and efficient range-based operations. It offers a flexible and efficient way to organize and manipulate data.
A tree is defined as a non-linear hierarchical data structure that consists of nodes (or vertices) connected by edges. It is widely used to represent relationships between data elements.

A tree is a collection of nodes where:
1. There is a single root node (the topmost node).
2. Each node can have zero or more child nodes.
3. There is exactly one path between any two nodes.

## 15.1 Terminologies

## 15.2 General Tree
A general tree is the most flexible form of a tree. Each node can have **any number of children**. There is no restriction on the number of child nodes a parent node can have. It is commonly used to represent hierarchical structures like a file system and organization charts. 
![](.pastes/2024-12-17-21-58-44.png)

## 15.3 Binary Tree
A **binary tree** is a hierarchical data structure in which each node has at most **two children**, referred to as the **left child** and the **right child**. It is widely for its simplicity and efficiency in searching, sorting, and organizing data.

![](.pastes/2024-12-19-22-32-10.png)

## 15.4 Binary Search Tree (BST)
A **Binary Search Tree (BST)** is a special type of **binary tree** where the nodes are arranged in a specific order to enable **efficient searching, insertion, and deletion** operations. Each node in a BST follows the **binary search property**:

- The **left child** contains values **smaller** than the parent node.
- The **right child** contains values **greater** than the parent node.
- This rule applies **recursively** to all nodes in the tree.

![](.pastes/2024-12-19-22-35-11.png)

###  15.4.1 Node Insertion
### 15.4.2 Node Deletion
### 15.4.3 Tree Traversal
#### 15.4.3.1 Breadth First Search
#### 15.4.3.2 Depth First Search
#####  15.4.3.2.1 Preorder Traversal
##### 15.4.3.2.2 Inorder Traversal
##### 15.4.3.2.3 Postorder Traversal
##### 
## 15.5 Balance Binary Search Tree
### 15.5.1 AVL Tree
### 15.5.2 Types of Imbalances
#### 15.5.2.1 LL Imbalance
#### 15.5.2.2 RR Imbalance
#### 15.5.2.3 LR Imbalance
#### 15.5.2.3 RL Imbalance

## 15.6 Java TreeSet Class
## 15.7 Java TreeMap Class
## 15.8 Exercises