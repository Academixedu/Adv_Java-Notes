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
`Stack` is a class in the Java Collections Framework that represents a last-in, first-out (LIFO) data structure.
It allows for storing and managing a collection of elements, where the most recently added element is the first to be removed. Stacks are useful for scenarios that require tracking previous states or implementing function call management.



### **Features**

- LIFO Order: The last element added to the stack is the first to be removed.

- Dynamic Size: Automatically adjusts its size with the addition or removal of elements.

- Non-Synchronized: Not thread-safe unless externally synchronized.

- Maintains Insertion Order: Elements are stored in the order they were added.

- Allows Duplicates: You can add duplicate elements to the stack.


### **When to Use:**

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

``` java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        // Initialize Stack
        Stack<String> fruits = new Stack<>();
        fruits.push("Apple");
        fruits.push("Banana");
        fruits.push("Cherry");
        
        System.out.println("Initial State of Fruits Stack:");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());

        // Pushing an Element
        fruits.push("Mango");
        System.out.println("\nAfter Pushing (Adding 'Mango'):");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());

        // Popping an Element
        String poppedFruit = fruits.pop(); // Removing the top element
        System.out.println("\nAfter Popping (Removed: " + poppedFruit + "):");
        System.out.println(fruits);
        System.out.println("Size = " + fruits.size());

        // Peeking at the Top Element
        String topFruit = fruits.peek(); // Get the top element without removing it
        System.out.println("\nTop Element (After Peek): " + topFruit);
        System.out.println("Stack remains unchanged: " + fruits);
        
        // Checking if the stack is empty
        boolean isEmpty = fruits.isEmpty();
        System.out.println("\nIs the stack empty? " + isEmpty);
        
        // Clearing the stack
        fruits.clear();
        System.out.println("\nFruits Stack after clearing: " + fruits);
        System.out.println("Size = " + fruits.size());
    }
}
```
## **2) Set Interface**
The Set interface is a part of the Java Collections Framework and extends the Collection interface. It represents a collection that does not allow duplicate elements. Sets are used to model mathematical set abstractions and provide a means to store unique elements.

### **Key Characteristics:**

- **Uniqueness:** A set does not allow duplicate elements. If you try to add a duplicate element, the set remains unchanged.

- **No Order:** The elements in a set are unordered, meaning they do not have a specific position or index.

- **Performance:** Sets generally provide faster operations for add, remove, and contains methods compared to lists.

### **Functions in the Set Interface:**
- boolean add(E element): Adds the specified element to the set if it is not already present.

- boolean remove(Object o): Removes the specified element from the set if it is present.

- boolean contains(Object o): Returns true if the set contains the specified element.

- int size(): Returns the number of elements in the set.

- boolean isEmpty(): Returns true if the set contains no elements.

- Iterator<E> iterator(): Returns an iterator over the elements in the set.

- Object[] toArray(): Returns an array containing all elements in the set.

- boolean containsAll(Collection<?> c): Returns true if the set contains all elements in the specified collection.

- boolean addAll(Collection<? extends E> c): Adds all elements in the specified collection to the set.

- boolean retainAll(Collection<?> c): Retains only the elements in the set that are contained in the specified collection.

- boolean removeAll(Collection<?> c): Removes from the set all of its elements that are contained in the specified collection.

### **Common Subclasses of the Set Interface:**

- **HashSet:**
Implements the Set interface using a hash table.
Provides constant-time performance for basic operations (add, remove, contains) on average.
Does not maintain the order of elements.

- **LinkedHashSet:**Extends HashSet and maintains a linked list of the entries to preserve the insertion order.
    Provides predictable iteration order.

- **TreeSet:**Implements the Set interface using a red-black tree.
Maintains elements in a sorted order.
Provides logarithmic time performance for the basic operations (add, remove, contains).

<h3>🟢HashSet</h3>
HashSet is part of the Java Collections Framework and implements the Set interface.
It represents a collection that does not allow duplicate elements and does not maintain any particular order.

### **Key Features of HashSet**
- **Dynamic Size:** Automatically adjusts its size as elements are added or removed.
- **Non-Synchronized:** Not thread-safe unless externally synchronized.
- **Allows Null Elements:** You can add null to the set.
- **No Duplicates:** Automatically prevents the addition of duplicate elements.

### **Internal Mechanism of HashSet**

**Hashing:**
- When an object is added to a HashSet, the hashCode() method of the object is called to compute its hash code. This hash code is used to determine the bucket (or index) where the object will be stored.
- The HashSet uses this hash code to quickly locate the bucket corresponding to that object.

**Bucket Storage:**
- Each bucket can store multiple elements, typically in a linked list or tree structure (in case of many collisions).
- The index of the bucket is computed as hashCode() % numberOfBuckets.

**Collision Handling:**
- If two different objects produce the same hash code (a collision), the HashSet uses the equals() method to differentiate between the two objects.
- If the equals() method returns true for two objects, the HashSet will not add the new object since it considers it a duplicate.

---
### Initial State of HashSet
> HashSet: []
---
### Adding an Element
- New Element: Mango
- The hashCode() method of Mango is called, and an index is calculated.
---
### **HashSet after addition:**
> [Mango] -> [Null] // Size = 1
- Adding More Elements

**Step 1**
- Adding: Apple, Banana, Cherry
- The hashCode() for each new element is calculated and placed in the appropriate bucket.

**Step 2**
**HashSet after additions:**
>[Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null] // Size = 4
---

### **Adding a Duplicate Element**

**Step 1**
Attempting to add: Apple (already exists)
The hashCode() for Apple is computed, and it points to the same bucket as the existing Apple.

**Step 2**
The equals() method is called to check for duplicates. Since it finds an existing Apple, the set remains unchanged:
> [Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null] // Size = 4

---
### **Removing an Element**

**Step 1**
Removing: Banana
The hashCode() of Banana is calculated, leading to its bucket.

**Step 2**
**HashSet after removal:**
> [Mango] -> [Apple] -> [Cherry] -> [Null] // Size = 3
---

### **Checking for Containment**
**Step 1**
- Checking if HashSet contains: Apple
- The hashCode() of Apple is calculated, and it points to the correct bucket.

**Step 2**
- The equals() method is called, confirming that Apple exists:
Does the set contain Apple? Yes
---

### **Clearing the Set**

**Step 1**
- Clear all elements from the HashSet.

**Step 2**
- HashSet after clearing:
[] (Empty Set) // Size = 0

```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        // Initialize HashSet
        HashSet<String> fruits = new HashSet<>();

        // Initial state of HashSet
        System.out.println("Initial State of HashSet: " + fruits);

        // Adding an Element
        String newElement = "Mango";
        fruits.add(newElement);
        System.out.println("After adding " + newElement + ": " + fruits + " // Size = " + fruits.size());

        // Adding More Elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        System.out.println("After adding Apple, Banana, Cherry: " + fruits + " // Size = " + fruits.size());

        // Adding a Duplicate Element
        String duplicateElement = "Apple";
        boolean added = fruits.add(duplicateElement);
        System.out.println("Attempting to add duplicate " + duplicateElement + ": " + (added ? "Added" : "Not Added"));
        System.out.println("HashSet remains unchanged: " + fruits + " // Size = " + fruits.size());

        // Removing an Element
        String elementToRemove = "Banana";
        fruits.remove(elementToRemove);
        System.out.println("After removing " + elementToRemove + ": " + fruits + " // Size = " + fruits.size());

        // Checking for Containment
        String elementToCheck = "Apple";
        boolean containsElement = fruits.contains(elementToCheck);
        System.out.println("Does the set contain " + elementToCheck + "? " + (containsElement ? "Yes" : "No"));

        // Clearing the Set
        fruits.clear();
        System.out.println("After clearing the HashSet: " + fruits + " // Size = " + fruits.size());
    }
}
```
---
### **Person Class(User Class)**
Overrriding HashCode() and Equals() Method to our Class

```java
public class Person{
    private int pid;
    private String name;
    private double sal;
    private String desg;
    public int getPid() {
        return pid;
    }
    public void setPid(int pid) {
        this.pid = pid;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public double getSal() {
        return sal;
    }
    public void setSal(double sal) {
        this.sal = sal;
    }
    public String getDesg() {
        return desg;
    }
    public void setDesg(String desg) {
        this.desg = desg;
    }
    public Person(int pid, String name, double sal, String desg) {
        this.pid = pid;
        this.name = name;
        this.sal = sal;
        this.desg = desg;
    }
    public Person(){

    }
    @Override
    public String toString() {
        return "Person [pid=" + pid + ", name=" + name + ", sal=" + sal + ", desg=" + desg + "]";
    }
    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + pid;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        long temp;
        temp = Double.doubleToLongBits(sal);
        result = prime * result + (int) (temp ^ (temp >>> 32));
        result = prime * result + ((desg == null) ? 0 : desg.hashCode());
        return result;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Person other = (Person) obj;
        if (pid != other.pid)
            return false;
        if (name == null) {
            if (other.name != null)
                return false;
        } else if (!name.equals(other.name))
            return false;
        if (Double.doubleToLongBits(sal) != Double.doubleToLongBits(other.sal))
            return false;
        if (desg == null) {
            if (other.desg != null)
                return false;
        } else if (!desg.equals(other.desg))
            return false;
        return true;
    }
   
    
}
```
---
### **HashCode() and Equals()**
```java
@Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + pid;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        long temp;
        temp = Double.doubleToLongBits(sal);
        result = prime * result + (int) (temp ^ (temp >>> 32));
        result = prime * result + ((desg == null) ? 0 : desg.hashCode());
        return result;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Person other = (Person) obj;
        if (pid != other.pid)
            return false;
        if (name == null) {
            if (other.name != null)
                return false;
        } else if (!name.equals(other.name))
            return false;
        if (Double.doubleToLongBits(sal) != Double.doubleToLongBits(other.sal))
            return false;
        if (desg == null) {
            if (other.desg != null)
                return false;
        } else if (!desg.equals(other.desg))
            return false;
        return true;
    }
```
---
### **HashSet Implementation**

```java
import java.util.HashSet;
import java.util.Iterator;

public class HashSet1 {
    public static void main(String[] args) {

    HashSet<Person> h3=new HashSet<>();
  
    h3.add(new Person(1, "Chanakya", 3445, "Dev"));
    h3.add(new Person(2, "Abhishek", 77683482, "Dev"));
    h3.add(new Person(1, "Chanakya", 3445, "Dev"));
    for (Person person : h3) {
        System.out.println(person);
    }
            }
}

```

<h3>🟢LinkedHashSet</h3> 
`LinkedHashSet` is part of the Java Collections Framework and implements the Set interface. It represents a collection that does not allow duplicate elements and maintains a predictable iteration order based on the order of insertion.

### **Key Features of LinkedHashSet**

- **Dynamic Size:** Automatically adjusts its size as elements are added or removed.
- **Non-Synchronized:** Not thread-safe unless externally synchronized.
- **Allows Null Elements:** You can add null to the set.
- **No Duplicates:** Automatically prevents the addition of duplicate elements.
- **Ordered Iteration:** Maintains the order of elements based on their insertion sequence.

### **Internal Mechanism of LinkedHashSet**
**Hashing:**
- When an object is added to a LinkedHashSet, the hashCode() method of the object is called to compute its hash code. This hash code is used to determine the bucket (or index) where the object will be stored.
- The LinkedHashSet uses this hash code to quickly locate the bucket corresponding to that object.

**Bucket Storage:**
- Each bucket can store multiple elements, typically in a linked list or tree structure (in case of many collisions).
In addition to the hash table, a LinkedHashSet maintains a doubly linked list of entries to preserve the insertion order.
Collision Handling:

- If two different objects produce the same hash code (a collision), the LinkedHashSet uses the equals() method to differentiate between the two objects.
If the equals() method returns true for two objects, the LinkedHashSet will not add the new object since it considers it a duplicate.
---
### **Initial State of LinkedHashSet**

- LinkedHashSet: [ ]
---
### **Adding an Element**
- New Element: Mango
- The hashCode() method of Mango is called, and an index is calculated.
---
### **LinkedHashSet after addition:**
> [Mango] -> [Null] // Size = 1

- Adding More Elements
**Step 1**
- Adding: Apple, Banana, Cherry
- The hashCode() for each new element is calculated and placed in the appropriate bucket while maintaining the insertion order.

**Step 2 LinkedHashSet after additions:**
> [Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null] // Size = 4
---
### **Adding a Duplicate Element**
**Step 1** Attempting to add: Apple (already exists) The hashCode() for Apple is computed, and it points to the same bucket as the existing Apple.

**Step 2** The equals() method is called to check for duplicates. Since it finds an existing Apple, the set remains unchanged:

> [Mango] -> [Apple] -> [Banana] -> [Cherry] -> [Null] // Size = 4
---
### **Removing an Element**
**Step 1 Removing:** 
- Banana The hashCode() of Banana is calculated, leading to its bucket.

**Step 2 LinkedHashSet after removal:**

> [Mango] -> [Apple] -> [Cherry] -> [Null] // Size = 3
---
### **Checking for Containment**
**Step 1**
- Checking if LinkedHashSet contains: Apple
- The hashCode() of Apple is calculated, and it points to the correct bucket.

**Step 2**
- The equals() method is called, confirming that Apple exists: Does the set contain Apple? Yes
---
### **Clearing the Set**

**Step 1**
- Clear all elements from the LinkedHashSet.

**Step 2**
- LinkedHashSet after clearing: [] (Empty Set) // Size = 0
---

```java
import java.util.LinkedHashSet;

public class LinkedHashSetExample {
    public static void main(String[] args) {
        // Creating a LinkedHashSet
        LinkedHashSet<String> fruits = new LinkedHashSet<>();

        // Initial State of LinkedHashSet
        System.out.println("LinkedHashSet: " + fruits); // Output: []

        // Adding an element
        fruits.add("Mango");
        System.out.println("After adding Mango: " + fruits); // Output: [Mango]

        // Adding more elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        System.out.println("After adding Apple, Banana, Cherry: " + fruits); // Output: [Mango, Apple, Banana, Cherry]

        // Attempting to add a duplicate element
        boolean isAdded = fruits.add("Apple");
        System.out.println("Attempt to add duplicate Apple: " + isAdded); // Output: false
        System.out.println("LinkedHashSet remains unchanged: " + fruits); // Output: [Mango, Apple, Banana, Cherry]

        // Removing an element
        fruits.remove("Banana");
        System.out.println("After removing Banana: " + fruits); // Output: [Mango, Apple, Cherry]

        // Checking for containment
        boolean containsApple = fruits.contains("Apple");
        System.out.println("Does the set contain Apple? " + containsApple); // Output: true

        // Clearing the set
        fruits.clear();
        System.out.println("After clearing the set: " + fruits); // Output: []
    }
}
```
---
### **Person Class(User Class)**
Overrriding HashCode() and Equals() Method to our Class

```java
public class Person{
    private int pid;
    private String name;
    private double sal;
    private String desg;
    public int getPid() {
        return pid;
    }
    public void setPid(int pid) {
        this.pid = pid;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public double getSal() {
        return sal;
    }
    public void setSal(double sal) {
        this.sal = sal;
    }
    public String getDesg() {
        return desg;
    }
    public void setDesg(String desg) {
        this.desg = desg;
    }
    public Person(int pid, String name, double sal, String desg) {
        this.pid = pid;
        this.name = name;
        this.sal = sal;
        this.desg = desg;
    }
    public Person(){

    }
    @Override
    public String toString() {
        return "Person [pid=" + pid + ", name=" + name + ", sal=" + sal + ", desg=" + desg + "]";
    }
    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + pid;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        long temp;
        temp = Double.doubleToLongBits(sal);
        result = prime * result + (int) (temp ^ (temp >>> 32));
        result = prime * result + ((desg == null) ? 0 : desg.hashCode());
        return result;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Person other = (Person) obj;
        if (pid != other.pid)
            return false;
        if (name == null) {
            if (other.name != null)
                return false;
        } else if (!name.equals(other.name))
            return false;
        if (Double.doubleToLongBits(sal) != Double.doubleToLongBits(other.sal))
            return false;
        if (desg == null) {
            if (other.desg != null)
                return false;
        } else if (!desg.equals(other.desg))
            return false;
        return true;
    }
   
    
}
```
---
### **HashCode() and Equals()**
```java
@Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + pid;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        long temp;
        temp = Double.doubleToLongBits(sal);
        result = prime * result + (int) (temp ^ (temp >>> 32));
        result = prime * result + ((desg == null) ? 0 : desg.hashCode());
        return result;
    }
    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null)
            return false;
        if (getClass() != obj.getClass())
            return false;
        Person other = (Person) obj;
        if (pid != other.pid)
            return false;
        if (name == null) {
            if (other.name != null)
                return false;
        } else if (!name.equals(other.name))
            return false;
        if (Double.doubleToLongBits(sal) != Double.doubleToLongBits(other.sal))
            return false;
        if (desg == null) {
            if (other.desg != null)
                return false;
        } else if (!desg.equals(other.desg))
            return false;
        return true;
    }
```
---
### **LinkedHashSet Implementation**

```java

import java.util.LinkedHashSet;

public class LinkedHashSet1 {
    public static void main(String[] args) {
         LinkedHashSet<Person> h3=new LinkedHashSet<>();
  
    h3.add(new Person(1, "Chanakya", 3445, "Dev"));
    h3.add(new Person(2, "Abhishek", 77683482, "Dev"));
    h3.add(new Person(1, "Chanakya", 3445, "Dev"));
    for (Person person : h3) {
        System.out.println(person);
    }
    }
}

```
<h3>🟢TreeSet</h3> 
`TreeSet` is part of the Java Collections Framework and implements the `NavigableSet` interface, which extends the `SortedSet` interface. It represents a collection that does not allow duplicate elements and maintains a sorted order of its elements.

### **Key Features of TreeSet**
**Sorted Order:** Automatically sorts elements in their natural ordering or according to a specified comparator.
**Dynamic Size:** Adjusts its size automatically as elements are added or removed.
**Non-Synchronized:** Not thread-safe unless externally synchronized.
**No Duplicates:** Automatically prevents the addition of duplicate elements.

### **Internal Mechanism of TreeSet**

**Tree Structure:**
- TreeSet is implemented using a red-black tree, a self-balancing binary search tree.
Each node in the tree contains a value, and nodes are arranged in a way that allows for efficient searching, inserting, and deleting.
Sorted Storage:

- Elements are stored in sorted order based on their natural ordering or by a comparator provided at set creation.
The tree structure allows for O(log n) time complexity for basic operations like add, remove, and contains.
No Duplicates:

- When an object is added, TreeSet uses the compareTo() method (or the comparator's compare() method) to check for duplicates.
If an attempt is made to add a duplicate, the set remains unchanged.

### **Comparable and Comparator in TreeSet**

### **Comparable Interface:**

- The Comparable interface is used to define the natural ordering of the objects.
Classes that implement this interface must override the compareTo(T o) method, which is used for comparison in TreeSet.

```java
class Fruit implements Comparable<Fruit> {
    String name;

    Fruit(String name) {
        this.name = name;
    }

    @Override
    public int compareTo(Fruit other) {
        return this.name.compareTo(other.name); // Sorts fruits alphabetically
    }

    @Override
    public String toString() {
        return name;
    }
}

TreeSet<Fruit> fruits = new TreeSet<>();
fruits.add(new Fruit("Mango"));
fruits.add(new Fruit("Apple"));
fruits.add(new Fruit("Banana"));
System.out.println(fruits); // Output: [Apple, Banana, Mango]
```
### **Comparator Interface:**

- The Comparator interface is used to define custom ordering for objects that may not have a natural ordering or when multiple sorting strategies are needed.
Implementing a Comparator allows for sorting based on different criteria.

```java
import java.util.Comparator;

class Fruit {
    String name;
    int price;

    Fruit(String name, int price) {
        this.name = name;
        this.price = price;
    }

    @Override
    public String toString() {
        return name + " (" + price + ")";
    }
}

// Comparator to sort fruits by price
Comparator<Fruit> byPrice = new Comparator<Fruit>() {
    @Override
    public int compare(Fruit f1, Fruit f2) {
        return Integer.compare(f1.price, f2.price); // Sorts fruits by price
    }
};

TreeSet<Fruit> fruitsByPrice = new TreeSet<>(byPrice);
fruitsByPrice.add(new Fruit("Mango", 60));
fruitsByPrice.add(new Fruit("Apple", 30));
fruitsByPrice.add(new Fruit("Banana", 40));
System.out.println(fruitsByPrice); // Output: [Apple (30), Banana (40), Mango (60)]
```
---
### **Initial State of TreeSet**
- TreeSet: []
---
### **Adding an Element**
New Element: Mango
The element is added, and the TreeSet automatically maintains the sorted order.
---
### **TreeSet after addition:**
> [Mango] // Size = 1

- Adding More Elements

**Step 1**
- Adding: Apple, Banana, Cherry
- Each element is added, and the TreeSet adjusts to keep elements sorted.

**Step 2**
- TreeSet after additions:
> [Apple, Banana, Cherry, Mango] // Size = 4
---
### **Adding a Duplicate Element**

**Step 1**
- Attempting to add: Apple (already exists)
- The TreeSet checks for duplicates using the compareTo() method.
**Step 2**
- The TreeSet remains unchanged since Apple already exists:
> [Apple, Banana, Cherry, Mango] // Size = 4
---

### **Removing an Element**

**Step 1**
- Removing: Banana
- The TreeSet locates the element using its sorted structure.

**Step 2**
- TreeSet after removal:
> [Apple, Cherry, Mango] // Size = 3

### **Checking for Containment**

**Step 1**
- Checking if TreeSet contains: Apple
- The TreeSet efficiently checks for existence using its sorted structure.

**Step 2**
- The result confirms that Apple exists: Does the set contain Apple? Yes
--- 

### **Clearing the Set**

**Step 1**
- Clear all elements from the TreeSet.

**Step 2**
- TreeSet after clearing:
> [] (Empty Set) // Size = 0

```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        // Creating a TreeSet to store Fruit names
        TreeSet<String> fruits = new TreeSet<>();

        // Adding elements to the TreeSet
        fruits.add("Mango");
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");

        // Displaying the TreeSet
        System.out.println("TreeSet after additions: " + fruits); // Output: [Apple, Banana, Cherry, Mango]

        // Attempting to add a duplicate element
        boolean isAdded = fruits.add("Apple");
        System.out.println("Attempt to add 'Apple': " + (isAdded ? "Added" : "Already exists")); // Already exists

        // Removing an element from the TreeSet
        fruits.remove("Banana");
        System.out.println("TreeSet after removing 'Banana': " + fruits); // Output: [Apple, Cherry, Mango]

        // Checking if the TreeSet contains a specific element
        boolean containsApple = fruits.contains("Apple");
        System.out.println("Does the TreeSet contain 'Apple'? " + (containsApple ? "Yes" : "No")); // Yes

        // Clearing the TreeSet
        fruits.clear();
        System.out.println("TreeSet after clearing: " + fruits); // Output: []
    }
}
```
--- 

### **User Approach in Tree Set**

**Person Class**

```java
public class Person implements Comparable<Person>{
    private int pid;
    private String name;
    private double sal;
    private String desg;
    public int getPid() {
        return pid;
    }
    public void setPid(int pid) {
        this.pid = pid;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public double getSal() {
        return sal;
    }
    public void setSal(double sal) {
        this.sal = sal;
    }
    public String getDesg() {
        return desg;
    }
    public void setDesg(String desg) {
        this.desg = desg;
    }
    public Person(int pid, String name, double sal, String desg) {
        this.pid = pid;
        this.name = name;
        this.sal = sal;
        this.desg = desg;
    }
    public Person(){

    }
    @Override
    public String toString() {
        return "Person [pid=" + pid + ", name=" + name + ", sal=" + sal + ", desg=" + desg + "]";
    }
    @Override
    public int compareTo(Person o) {
       return Integer.compare(this.pid, o.pid);
    }
    
    
}
```
---
### **For Sorting Order Based on Name(Comparator)**
```java
import java.util.Comparator;

public class BasedonName implements Comparator<Person>{

    @Override
    public int compare(Person o1, Person o2) {
      return o1.getName().compareTo(o2.getName());
    }
    
}
```
---
### **For Sorting Order Based on Salary(Comparator)**

```java
import java.util.Comparator;

public class BasedonSal implements Comparator<Person> {

    @Override
    public int compare(Person o1, Person o2) {
        return Double.compare(o1.getSal(), o2.getSal());
    }
    
}
```
### **To Implement User Approach While Getting Data**
- Creating Comparator Object Based On User's Request

```java
import java.util.Comparator;
import java.util.Scanner;
import java.util.TreeSet;

public class Sets {
    public static void main(String[] args) {
       
Scanner in=new Scanner(System.in);
        Comparator<Person> p=null;
        System.out.println("1. Based on Name");
        System.out.println("2 .Based on Salary");
        int id=in.nextInt();
        if(id==1){
            p=new BasedonName();
        }
        else if(id==2){
            p=new BasedonSal();
        }

        
        TreeSet<Person> t1=new TreeSet<>(p);
        t1.add(new Person(1, "Chanakya", 23, "Dev"));
        t1.add(new Person(2, "Balu", 34, "Dev"));
        for (Person person : t1) {
            System.out.println(person);
        }
    }
}
```
## **Map Interface**
The Map interface is a part of the Java Collections Framework and represents a collection that maps unique keys to values. It allows for the storage of key-value pairs, where each key is associated with a specific value. Maps are used for efficiently retrieving values based on keys.

### **Key Characteristics:**
**Key-Value Pair:** A map consists of key-value pairs, allowing easy access to values via their corresponding keys.

**Uniqueness of Keys:** Each key in a map must be unique. If you attempt to add a duplicate key, the existing value is replaced.

**Dynamic Size:** Maps automatically adjust their size as elements are added or removed.

### **Functions in the Map Interface:**
**V put(K key, V value):** Adds the specified key-value pair to the map. If the key already exists, the value is updated.

**V get(Object key):** Returns the value associated with the specified key, or null if the key does not exist.

**V remove(Object key):** Removes the key-value pair for the specified key if it is present.

**boolean containsKey(Object key):** Returns true if the map contains the specified key.

**boolean containsValue(Object value):** Returns true if the map maps one or more keys to the specified value.

**int size():** Returns the number of key-value pairs in the map.

**boolean isEmpty():** Returns true if the map contains no key-value pairs.

**Set<K> keySet():** Returns a set view of the keys contained in the map.

**Collection<V> values():** Returns a collection view of the values contained in the map.

**Set<Map.Entry<K, V>> entrySet():** Returns a set view of the mappings contained in the map.

### **Common Subclasses of the Map Interface:**

**HashMap:** Implements the Map interface using a hash table. Provides constant-time performance for basic operations (put, remove, contains) on average.

**LinkedHashMap:** Extends HashMap and maintains a linked list of the entries to preserve the insertion order. Provides predictable iteration order.

TreeMap: Implements the Map interface using a red-black tree. Maintains the keys in a sorted order. Provides logarithmic time performance for basic operations (put, remove, contains).
