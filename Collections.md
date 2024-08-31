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

<h1>### **ArrayList**</h1>
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
