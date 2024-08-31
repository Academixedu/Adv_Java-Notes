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


