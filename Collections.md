### Collections in Java 
- The Collection in Java is a framework that provides an architecture to store 
and manipulate the group of objects,Java Collections can achieve all the operations that you perform on a data 
such as searching, sorting, insertion, manipulation, and deletion. 

- Java Collection means a single unit of objects. Java Collection framework 
provides many interfaces (Set, List, Queue, Deque) and classes (ArrayList, 
Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet).

- Collection Flow-Chart in Java

<img src="https://static.javatpoint.com/images/java-collection-hierarchy.png" alt="My Image" width="500" height="500">

## 1) List Interface 
The List interface is a part of the Java Collections Framework and extends the Collection interface. It represents an ordered collection, also known as a sequence, and allows for precise control over where elements are inserted. Elements can be accessed by their integer index (position in the list) and searched for within the list.

<strong>Key Characteristics:</strong>
Order: Elements in a list are ordered and can be accessed by their position (index).
Duplicates: A list can contain duplicate elements.
Indexing: Elements in a list are zero-based indexed.
Main Methods in the List Interface:
void add(int index, E element): Inserts the specified element at the specified position in the list.
boolean add(E element): Appends the specified element to the end of the list.
E get(int index): Returns the element at the specified position in the list.
E set(int index, E element): Replaces the element at the specified position with the specified element.
E remove(int index): Removes the element at the specified position in the list.
boolean remove(Object o): Removes the first occurrence of the specified element from the list, if it is present.
int indexOf(Object o): Returns the index of the first occurrence of the specified element, or -1 if the list does not contain the element.
int lastIndexOf(Object o): Returns the index of the last occurrence of the specified element, or -1 if the list does not contain the element.
List<E> subList(int fromIndex, int toIndex): Returns a view of the portion of this list between the specified fromIndex, inclusive, and toIndex, exclusive.
Common Implementations of the List Interface:
ArrayList<E>:

Description: A resizable array implementation of the List interface.
Use Case: Best for applications where you need fast random access to elements and where the size of the list changes infrequently.
Performance:
Fast for random access (O(1)).
Slower for insertions and deletions in the middle of the list (O(n)).
LinkedList<E>:

Description: A doubly-linked list implementation of the List and Deque interfaces.
Use Case: Ideal for applications that involve frequent insertions and deletions from the middle of the list.
Performance:
Slower for random access (O(n)).
Faster for insertions and deletions in the middle of the list (O(1)).
Vector<E>:

Description: A synchronized, resizable array implementation of the List interface.
Use Case: Suitable for applications where thread safety is required.
Performance: Generally slower than ArrayList due to synchronization overhead.
Stack<E>:

Description: A subclass of Vector that implements a last-in, first-out (LIFO) stack.
Use Case: Used for stack operations where elements are accessed in a LIFO manner.
Performance: Inherits the same performance characteristics as Vector.
