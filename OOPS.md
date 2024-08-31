# Object-Oriented Programming Concepts (OOPs) in Java

Object-Oriented Programming (OOP) is a programming paradigm that organizes software design based on objects, which act as representations of real-world entities. It emphasizes the creation of reusable code by encapsulating both data and behavior within these objects, making it easier to manage and develop complex applications.

**Objects:** Instances of classes that contain both data (attributes) and methods (functions) that operate on that data.

**Classes:** Blueprints for creating objects, defining their properties and behaviors. A class encapsulates data and provides methods to manipulate that data.

**Encapsulation:** The practice of bundling data and methods within a class while restricting direct access to some components. This helps protect an object's integrity by exposing only what is necessary.

**Inheritance:** A mechanism that allows one class to inherit attributes and methods from another class. This promotes code reuse and establishes a hierarchical relationship between classes.

**Polymorphism:** The ability for different classes to be treated as instances of the same class through a common interface. This includes method overloading (using the same method name with 
different parameters) and method overriding (a subclass redefining a method from its parent class).

**Abstraction:** The concept of hiding complex implementation details while exposing only the essential features of an object. This can be achieved through abstract classes and interfaces.


## **Classes and Objects**

**1. Classes**
- A class is a blueprint or template for creating objects. It defines a data type by bundling data (attributes) and methods (functions) that operate on that data.
- Classes provide a way to structure code and represent real-world entities.
- Example: In a Car class, you might define attributes like color and model, and methods like drive() and stop().

**2. Objects**
- An object is an instance of a class. It is created based on the class definition and represents a specific entity.
- Objects encapsulate data and behavior, allowing them to manage their state and perform operations.
- Example: Car myCar = new Car(); creates an object myCar of the Car class.

**3. Attributes**
- Attributes (or fields) are variables defined in a class that hold the state of an object.
- They can have various access modifiers (private, protected, public) to control visibility and accessibility.
- Example: In the Car class, attributes might include color, model, and year.

**4. Methods**
- Methods are functions defined in a class that describe the behaviors or actions an object can perform.
- Methods can manipulate the object's attributes and may return values.
- Example: Methods like start(), accelerate(), and brake() define what actions a Car object can perform.

**5. Instantiation**
- Instantiation is the process of creating an object from a class using the new keyword.
- Example: Car myCar = new Car(); creates an object named myCar based on the Car class.

**6. Access Modifiers**
- Access modifiers control the visibility of classes, attributes, and methods.
- public: Accessible from anywhere.
- private: Accessible only within the class.
- protected: Accessible within the class and subclasses.

```java
public class Basics {
    public int id=2;
    public String name;
    public double sal;
    public String desg;
    
    //void function 
    public void m1(){
        this.desg="Dev";
        this.sal=34000;
        this.name="rohith";
        System.out.println(id+""+name+" "+sal+" "+desg);
    }
    // void function with Paramaters
    public void m2(int a,int b){
        System.out.println(a+b);
    }
    // int function with Paramaters
    public int m3(int a,int b){
        return a*b;
    }
    // static function with void as return
    public static void m4(String name){
        System.out.println("(Void) Name is "+name);
    }
    // static function with String as return
    public static String m5(String name){
        return name;
    }
    public static void main(String[] args) {
        Basics b=new Basics();
        // Initalizing varible
        b.id=3;
        System.out.println(b);
        // Calling Void Function
        b.m1();
        // Calling Func with Paramaters
        b.m2(3, 4);
        // Calling Return Function With Paramaters
       int ret= b.m3(5, 6);
    //    Printing the Value Which was Recieved
       System.out.println(ret);
    //    Static void function
       m4("Chanakya");
    //    static return function calling and printing 
       System.out.println(m5("Chaanakya")+"---- Hello Java");

    }
}

```
## Encapsulation
Encapsulation is one of the fundamental concepts of Object-Oriented Programming (OOP). It refers to the bundling of data (attributes) and methods (functions) that operate on the data into a single unit, known as a class. It restricts direct access to some of an object's components and can prevent the accidental modification of data.

### **Key Characteristics:**

**Data Hiding:**
- Encapsulation allows the internal state of an object to be hidden from the outside world.
- Access to the internal state is restricted, typically using private access modifiers.

**Public Methods:**
- Public methods (getters and setters) are provided to access and modify the private fields. This controls how the fields are accessed and modified, allowing validation or modification of data before it is stored.

**Increased Security:**
- By restricting access to certain components of an object, encapsulation enhances security and reduces the risk of unintended interference.

**Maintainability:**
- Changes to the internal implementation of a class can be made without affecting external code that uses the class, as long as the public interface remains consistent.

**Flexibility and Reusability:**
- Encapsulation promotes flexibility in code design. Classes can be reused in different contexts without exposing their internal workings.
  
Example Program of Encapsulation

```java

public class Student {
private int sid;
private String sname;
private double page;
public int getSid() {
    return sid;
}
public void setSid(int sid) {
    this.sid = sid;
}
public String getSname() {
    return sname;
}
public void setSname(String sname) {
    this.sname = sname;
}
public double getPage() {
    return page;
}
public void setPage(double page) {
    this.page = page;
}
public Student(int sid, String sname, double page) {
    this.sid = sid;
    this.sname = sname;
    this.page = page;
}

}
```
1. Getters
**Definition:**
Getters are public methods that allow access to private fields (attributes) of a class.

**Purpose:**
- Provide controlled access to the class's private data.
- Allow read-only access to certain fields when no setter is provided.

```java
Syntax:
public <DataType> get<FieldName>() {
    return fieldName; // Returns the value of the private field
}
```

Example:
```java
public int getSid() {
    return sid; // Returns the value of the private field sid
}
```

2. Setters
**Definition:**
Setters are public methods that allow modification of private fields of a class.

**Purpose:**
- Provide controlled modification of the class's private data.
- Implement validation logic before updating the field value.

Syntax:
```java
public void set<FieldName>(<DataType> fieldName) {
    this.fieldName = fieldName; // Sets the value of the private field
}
```
Example:

```java
public void setSid(int sid) {
    this.sid = sid; // Sets the value of the private field sid
}
```
3. Constructor
**Definition:**
- A constructor is a special method called when an object of a class is created. It initializes the newly created object and can accept parameters to set initial values for the object's fields.

**Purpose:**
- Initialize the object’s state (i.e., its fields).
- Ensure that the object is in a valid state upon creation.

Syntax:

```java
public <ClassName>(<ParameterTypes>) {
    // Initialization code
}
```
Example:

```java
public Student(int sid, String sname, double page) {
    this.sid = sid;    // Initialize sid field with parameter value
    this.sname = sname; // Initialize sname field with parameter value
    this.page = page;   // Initialize page field with parameter value
}
```
3)Two String

toString() method is a special method in Java that is used to provide a string representation of an object. It is defined in the Object class, and all classes in Java inherit this method. When you print an object or convert it to a string, the toString() method is called implicitly.

**Purpose of toString()**

- **Readable Output:** It provides a human-readable string representation of an object, which is helpful for debugging and logging.
- **Custom Representation:** By overriding the toString() method in your class, you can define how the object should be represented as a string, making it easier to understand the state of the object at a glance.

Syntax
To override the toString() method, you define it in your class like this:

```java
@Override
public String toString() {
    // Return a string representation of the object
    return "ClassName { field1=value1, field2=value2, ... }";
}
```
Example

```java
@Override
public String toString() {
    return "Student [sid=" + sid + ", sname=" + sname + ", page=" + page + "]";
}
```
