# Collections in Java 
- The Collection in Java is a framework that provides an architecture to store 
and manipulate the group of objects,Java Collections can achieve all the operations that you perform on a data 
such as searching, sorting, insertion, manipulation, and deletion. 

- Java Collection means a single unit of objects. Java Collection framework 
provides many interfaces (Set, List, Queue, Deque) and classes (ArrayList, 
Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet).

- Collection Flow-Chart in Java

<img src="https://static.javatpoint.com/images/java-collection-hierarchy.png" alt="My Image" width="600" height="500">

## 1) List Interface 
The List interface is a part of the Java Collections Framework and extends the Collection interface. It represents an ordered collection, also known as a sequence, and allows for precise control over where elements are inserted. Elements can be accessed by their integer index (position in the list) and searched for within the list.

<strong>Key Characteristics:</strong>
- **Order**: Elements in a list are ordered and can be accessed by their position (index).

- **Duplicates**: A list can contain duplicate elements.

- **Indexing**: Elements in a list are zero-based indexed.

**Functions in the List Interface:**

- void add(int index, E element): Inserts the specified element at the specified position in the list.
- boolean add(E element): Appends the specified element to the end of the list.
- E get(int index): Returns the element at the specified position in the list.
- E set(int index, E element): Replaces the element at the specified position with the specified element.
- E remove(int index): Removes the element at the specified position in the list.
- boolean remove(Object o): Removes the first occurrence of the specified element from the list, if it is present.
- int indexOf(Object o): Returns the index of the first occurrence of the specified element, or -1 if the list does not contain the element.
- int lastIndexOf(Object o): Returns the index of the last occurrence of the specified element, or -1 if the list does not contain the element.
- List<E> subList(int fromIndex, int toIndex): Returns a view of the portion of this list between the specified fromIndex, inclusive, and toIndex, exclusive.

The List interface in Java has three primary and commonly used subclasses (or implementations), which are ArrayList, LinkedList, and Vector. Each of these subclasses provides different features and performance characteristics suited to various use cases.

<h3>🟢ArrayList</h3>
ArrayList is one of the most widely used classes in the Java Collections Framework. It is a resizable array implementation of the List interface, providing the ability to dynamically grow and shrink as elements are added or removed. Unlike standard arrays, which have a fixed size, an ArrayList can automatically adjust its capacity, making it a flexible and powerful tool for handling collections of objects.

**Features**  
- **Resizable Array:** Automatically increases its size when more elements are added.

- **Efficient Random Access:** Ideal for scenarios where you need to frequently access elements by their index.

- **Non-Synchronized:** Not thread-safe unless externally synchronized.

- **Maintains Insertion Order:** Elements are stored in the order they were added.

- **Allows Duplicates:** You can add duplicate elements to the list. 

**When to Use:**

When you need to frequently retrieve elements by index.

When the list size changes infrequently or when elements are mostly added at the end of the list.

---
### Initial State of ArrayList


> [ 0 ] [ 1 ] [ 2 ] [ 3 ] [ 4 ] [ 5 ] [ 6 ] [ 7 ] [ 8 ] [ 9 ]

> [Apple][Banana][Cherry][  ][  ][  ][  ][  ][  ][  ]  // Size = 3, Capacity = 10

---

### After Insertion

> [ 0 ] [ 1 ] [ 2 ] [ 3 ] [ 4 ] [ 5 ] [ 6 ] [ 7 ] [ 8 ] [ 9 ]

> [Apple][Date  ][Banana][Cherry][  ][  ][  ][  ][  ][  ]  // Size = 4, Capacity = 10

---
### After Deleting

> [ 0 ] [ 1 ] [ 2 ] [ 3 ] [ 4 ] [ 5 ] [ 6 ] [ 7 ] [ 8 ] [ 9 ]

> [Apple][Date][Cherry][  ][  ][  ][  ][  ][  ][  ]  // Size = 3, Capacity = 10

---

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        // Initialize ArrayList
        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        
        System.out.println("Initial State of Fruits List:");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size() + ", Capacity = 10 (initially)");

        // After Insertion
        fruits.add(1, "Date"); // Inserting "Date" at index 1
        System.out.println("\nAfter Insertion (Inserting 'Date' at index 1):");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size() + ", Capacity = 10 (no resize needed)");

        // After Deleting
        fruits.remove("Banana"); // Deleting "Banana"
        System.out.println("\nAfter Deleting (Removing 'Banana'):");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size() + ", Capacity = 10 (no resize needed)");

        // Additional Operations
        String firstFruit = fruits.get(0);
        System.out.println("\nFirst fruit: " + firstFruit);

        // Updating a fruit
        fruits.set(1, "Blueberry");
        System.out.println("Updated Fruits List after replacing 'Date' with 'Blueberry': " + fruits);

        // Check if the list contains "Apple"
        boolean hasApple = fruits.contains("Apple");
        System.out.println("Does the list contain Apple? " + hasApple);

        // Size of the list
        int size = fruits.size();
        System.out.println("Size of the Fruits List: " + size);

        // Clear the list
        fruits.clear();
        System.out.println("Fruits List after clearing: " + fruits);
    }
}

```
<h3>🟢LinkedList</h3>
`LinkedList` is another important class in the Java Collections Framework. It implements the List interface as a doubly linked list, which allows for efficient insertion and deletion of elements. Unlike `ArrayList`, which is backed by a resizable array, `LinkedList` uses nodes to store data, making it suitable for scenarios where frequent modifications to the list are necessary.

**Features**

- **Dynamic Size:**  Automatically adjusts its size with the addition or removal of elements.

- **Efficient Insertions/Deletions:**  Insertion and deletion operations are fast (O(1)) when you have a reference to the node.

- **Non-Synchronized:**  Not thread-safe unless externally synchronized.

- **Maintains Insertion Order:**  Elements are stored in the order they were added.

- **Allows Duplicates:**  You can add duplicate elements to the list.

**When to Use:**
- When your application requires frequent insertions and deletions of elements in the middle of the list.

- When you don’t need fast random access to elements by index.

---
## **Initial State of LinkedList**

> [Head] -> [ 0 ] -> [ 1 ] -> [ 2 ] -> [ 3 ] -> [Null]

> [Apple] -> [ Date ] -> [ Banana ] -> [ Cherry ] -> [Null]

---

## Inserting an Element
### Step 1
> [NewNode]
> [Mango] -> [Null]

### Step 2

> [Head] -> [ 0 ] -> [NewNode] -> [ 1 ] -> [ 2 ] -> [ 3 ] -> [Null]

### Step 3
> [Apple] -> [Mango] -> [Date] -> [Banana] -> [Cherry] -> [Null] // Size = 5

---
## Deleting
### Step 1
> [Head] -> [ 0 ] -> [ 1 ] -> [ 2 ] -> [Null]
### Step 2
> [Apple] -> [Mango] -> [Banana] -> [Cherry] // Size = 4
---

```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        // Initialize LinkedList
        LinkedList<String> fruits = new LinkedList<>();
        fruits.add("Apple");
        fruits.add("Date");
        fruits.add("Banana");
        fruits.add("Cherry");
        
        // Display initial state
        System.out.println("Initial State of LinkedList:");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());

        // Inserting an Element (Mango)
        System.out.println("\nInserting an Element (Mango):");

        // Step 1: Create a new node (Mango)
        String newFruit = "Mango";
        // Step 2: Inserting Mango at index 1
        fruits.add(1, newFruit);
        // Step 3: Display updated LinkedList
        System.out.println("After Insertion:");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());

        // Deleting an Element (Date)
        System.out.println("\nDeleting an Element (Date):");
        
        // Step 1: Remove "Date" from the LinkedList
        fruits.remove("Date");
        // Step 2: Display updated LinkedList after deletion
        System.out.println("After Deletion:");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());
    }
}

```
<h3>🟢 Stack</h3> 
`Stack` is a class in the Java Collections Framework that represents a last-in, first-out (LIFO) data structure. It allows for storing and managing a collection of elements, where the most recently added element is the first to be removed. Stacks are useful for scenarios that require tracking previous states or implementing function call management.


**Features**

- LIFO Order: The last element added to the stack is the first to be removed.

- Dynamic Size: Automatically adjusts its size with the addition or removal of elements.

- Non-Synchronized: Not thread-safe unless externally synchronized.

- Maintains Insertion Order: Elements are stored in the order they were added.

- Allows Duplicates: You can add duplicate elements to the stack.


**When to Use:**

- When your application requires tracking of function calls or previous states.

- When implementing undo mechanisms in applications.

- When managing recursive algorithms or backtracking problems.

---
**Initial State of Stack**

> [Top] -> [0] -> [1] -> [2] -> [3] -> [Null]

> [Apple] -> [Banana] -> [Cherry] -> [Null]

---

**Pushing an Element**

Step 1
> [NewElement] [Mango] -> [Null]

Step 2
> [Top] -> [NewElement] -> [0] -> [1] -> [2] -> [3] -> [Null]

Step 3
> [Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null] // Size = 4

---

**Popping an Element**

Step 1
> [Top] -> [0] -> [1] -> [2] -> [Null]

Step 2
> [Apple] -> [Banana] -> [Null] // Size = 3

---

**Peeking at the Top Element**

Step 1
Top Element: Apple (remains unchanged)

Step 2
Stack remains unchanged: [Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null]

---

