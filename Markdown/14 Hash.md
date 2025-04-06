# 14 Hash

## 14.1 What is a Hash?
A **hash**, in a general sense, is a value generated from input data (also called a *key*) using a mathematical function known as a **hash function**. ***What do we use a hash for?*** Hashes are widely used in computing for efficient data storage and retrieval.

## 14.2 A Simple Hash Function
A **hash** is the result of applying a **hash function** to data. A hash function takes an input (like an integer or a string) and produces a fixed-size value, usually a number. This value, called a **hash value** or **hash code**, is typically used to uniquely identify the original data. Hashes are commonly used in data structures like **hash tables**, where the hash value helps in quickly finding or storing items.

The provided Java program demonstrates how a simple hash table works using a basic hash function. It stores integer values (grades) into an array based on their hash code, which is calculated using a very basic hashing algorithm.

Let's break down the code step by step:

1. **The `hashCode()` Method:**

```java
static int hashCode(int number) {
    int hash = number % 10;
    return hash;
}
```

- This method is the **hash function**. It takes an integer (`number`) as input and computes its **hash code** by performing a modulo operation (`number % 10`). 
- The result is an integer between `0` and `9`, which serves as the index for storing the value in the array. This index, where the data is stored, is often referred to as a _bucket_.
- **Modulo 10** ensures that the result (hash) fits into an array of size `10`, since the only possible values of this operation is an integer from `0` to `9`. 

2. **The `main()` Method:**
With the `hashCode` method implemented, we can now define our main method to create an array for storing data, specifically `grades` represented as integers.


```java
public static void main(String args[]) {
    int hash;
    int grade;
    int grades[] = new int[10];  // Array to store the grades
    for (int i=0; i<grades.length; i++) {
        grades[i] = -1;  // Initialize all elements of the array to -1 (indicating empty slots)
    }

    grade = 97;
    hash = hashCode(grade);  // Calculate the hash of the grade
    grades[hash] = grade;    // Store the grade at the index corresponding to its hash

    // Repeating for other grades
    grade = 82;
    hash = hashCode(grade);
    grades[hash] = grade;

    grade = 33;
    hash = hashCode(grade);
    grades[hash] = grade;

    // Print the hash table
    System.out.println("Hash Table: " + Arrays.toString(grades));

    // Take user input to search for a number in the hash table
    Scanner keyboard = new Scanner(System.in);
    System.out.print("Enter number: ");
    int number = keyboard.nextInt();
    hash = hashCode(number);  // Calculate the hash of the input number
    if (number == grades[hash])
        System.out.println("The number " + number + " is in the array.");
}
```

#### Key Steps:

1. **Array Initialization:**
   - The `grades` array is created with 10 elements. All elements are initialized to `-1` to indicate that they are empty.

2. **Storing Grades:**
   - The program stores three grades: `97`, `82`, and `33`. Each grade is hashed using the `hashCode()` function, and the resulting hash is used as the index to store the grade in the `grades` array.
   - For example:
     - Grade `97` is hashed as `97 % 10 = 7`, so it is stored at index 7 in the `grades` array.
     - Grade `82` is hashed as `82 % 10 = 2`, so it is stored at index 2.
     - Grade `33` is hashed as `33 % 10 = 3`, so it is stored at index 3.

This is illustrated in the hash table below, where the grades `97`, `82`, and `33` are stored based on the hash function.


3. **Displaying the Hash Table:**
   - After the grades are inserted, the array (hash table) is printed. It will display the grades stored at their corresponding hash indices, and `-1` in the empty slots.

4. **Searching for a Number:**
   - The user is prompted to input a number. The program computes the hash of the number and checks if the number is stored in the corresponding slot in the `grades` array.
   - If the number exists at the computed index, it prints that the number is in the array; otherwise, it prints that the number is not found.

#### Example Output:
```
Hash Table: [-1, -1, 82, 33, -1, -1, -1, 97, -1, -1]
Enter number: 33
The number 33 is in the array.
```

- The hash table shows that `82` is stored at index 2, `33` is stored at index 3, and `97` is stored at index 7.
- When you enter `33`, the program calculates the hash (`33 % 10 = 3`), checks index 3, and confirms that `33` is stored there.

Without the `hashCode` method, we would lack a systematic way to store the grades data in the array, making it difficult and inefficient to check whether the data exists in the array.

#### Collision
Hash tables are a popular data structure used for efficient data retrieval. However, they rely on unique hash values to store keys in buckets (or slots), and sometimes two different keys can generate the same hash value. This situation is called a **collision**. Two primary techniques to resolve collisions are **open addressing** and **chaining**.

###  14.1.1 Open Addressing
In **open addressing**, all elements are stored directly in the hash table itself. When a collision occurs, the algorithm searches for the next available *bucket* (index) in the table based on a probing sequence. Common types of probing are:

- **Linear Probing**: When a collision occurs, the algorithm searches for the next available bucket in a sequential manner. If the current slot is occupied, it moves to the next one and continues this process until an empty slot is found. If the search reaches the end of the array, it wraps around to the beginning and continues looking for a free slot.
- **Example**: In a hash table with 10 buckets (indexed from 0 to 9), if a key hashes to bucket 5 and that bucket is occupied, the algorithm proceeds to check bucket 6, then bucket 7, and continues sequentially. If the search reaches bucket 9 and finds it occupied as well, the search wraps around to bucket 0 and continues from there.
  
### 14.1.2 Separate Chaining
In separate chaining, the elements are not directly in the hash table. What is in the hash table are reference to linked lists which contains the elements of the hash. With this hash, the problem of collission is fixed since if a collission occurs, the new element would simply be added to the linked list. 
- **Example**: 

###  14.1.3 Load Factor and Resizing
### 14.1.4 String Hash

## 14.2 Java HashSet Class
## 14.3 Java HashMap Class
## 14. 4 Java LinkedHashSet Class
## 14,.5 Java LinkedHashMap Class
## 14.6 Exercises

