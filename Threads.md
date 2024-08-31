# Threads
A Thread in Java is the smallest unit of execution within a process. It enables parallelism by allowing multiple sequences of operations to run concurrently within a single program. This ability to run multiple parts of a program simultaneously is crucial for creating responsive and efficient applications, particularly in environments where multiple tasks need to be performed at the same time.


### **Why Use Threads?**
- **Parallelism:** Threads enable the parallel execution of tasks. For instance, a server can handle multiple client requests concurrently, or a desktop application can perform background operations like file downloading while keeping the user interface responsive.

- **Efficiency:** Threads share the same memory space and resources of the process they belong to, which makes them more efficient than creating multiple processes. This shared memory model allows threads to communicate and share data easily.

- **Resource Management:** Since threads share the same memory and resources, they use less memory and are easier to manage than processes, which have their own separate memory space. This makes threads particularly useful for applications that need to perform multiple tasks simultaneously without a significant overhead.

- **Responsiveness:** In user-centric applications, threads ensure that time-consuming tasks like loading data, processing files, or performing calculations do not block the user interface, thereby keeping the application responsive.

- **Utilization of Multi-Core Processors:** Modern processors have multiple cores, and threads allow programs to utilize these cores effectively. By running multiple threads in parallel, you can maximize the performance benefits of multi-core processors.

# Table of Contents

- [Thread Life Cycle](#LifeCycle)
- [Creating Thread](#Create)
- [Thread Functions](#Functions)
- [synchronization](#synchronize)
- [Inter-Thread-Communication](Inter-Thread-Communication)
- [Yield&Join](#Yield&Join)
- [Deadlock](#DeadLock)

## LifeCycle 
In Java, a thread goes through several states during its life cycle. These states represent the various stages a thread can be in, from creation to termination. Understanding the thread life cycle is crucial for effective multithreading programming, as it helps in managing and controlling thread execution.

<img src="https://javatrainingschool.com/wp-content/uploads/2021/09/image-13-1024x477.png" alt="My Image" width="800" height="500">


### **New:**
The thread is created but not yet started. In this state, the thread object is instantiated, but the start() method has not been called yet.

### **Runnable:**
Once the start() method is called, the thread enters the Runnable state. In this state, the thread is ready to run and is waiting for CPU time to execute. However, it may not be running immediately depending on the availability of the CPU.

### **Running:**
When the thread scheduler selects the thread from the Runnable state, it enters the Running state. In this state, the thread is actively executing its task.

### **Wait()/Blocked/Sleep:**
During execution, a thread can enter this state if it is waiting for another thread to perform a specific action, waiting for I/O operations to complete, or simply put to sleep using sleep() or wait(). The thread remains in this state until the condition that caused it to wait is met or until the specified time has elapsed.

### **Dead:**
A thread enters the Dead state once its execution is complete, either by returning from the run() method or by being terminated. Once a thread is in this state, it cannot be restarted.

---
## Create

### 1) Creating a Thread by Extending the Thread Class in Java

In Java, one way to create a new thread is by extending the Thread class. This method involves creating a subclass of Thread and overriding its run() method. The run() method contains the code that will be executed when the thread is started.

- **Create a Class that Extends Thread:**   To create a new thread, you define a class that extends the Thread class and override the run() method. The code inside the run() method is what will be executed by the new thread.

- **Override the run() Method:**   The run() method contains the code that represents the task or job that the thread will perform when it's running.

- **Create an Instance of the Subclass:**    After defining your thread class, you create an instance of it.

- **Start the Thread:**   Call the start() method on the instance to begin the execution of the thread. This causes the run() method to be executed in a new thread.

Example Code to Create a Thread using "extends" keyword

```java
public class Threads2 extends Thread {
    public void run(){
        for(int i=1;i<=2;i++){
            System.out.println("Hello"+Thread.currentThread().getName());
        }
    }
    public static void main(String[] args) {
        Threads2 t=new Threads2();
        t.start();
        t.yield();
        Threads2 t1=new Threads2();
        t1.start();
    }
}
```
### 2)Creating a Thread by Implementing the Runnable Interface in Java
Another way to create a thread in Java is by implementing the Runnable interface. This approach is often preferred because it allows the class to inherit from another class if needed while still enabling multithreading.

### **Steps and Procedure**

**Implement the Runnable Interface:**
- To create a new thread, a class must implement the Runnable interface and provide an implementation for the run() method. The code inside the run() method defines the task that will be executed by the thread.

**Override the run() Method:**
- The run() method contains the code that will be executed when the thread starts.

**Create an Instance of the Runnable Implementation:**
- After defining the class, create an instance of the class that implements Runnable.

**Create a Thread Object:**
- Pass the Runnable instance to the Thread constructor to create a Thread object.
Start the Thread:

**Call the start() method on the Thread object to begin the execution of the thread.**

```java
public class Threads1 implements Runnable{

    public void run(){
        for(int i=0;i<4;i++){
            try {
                Thread.sleep(100);
                System.out.println("Hello "+Thread.currentThread().getName());
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }    
            
                    }
    }
    public static void main(String[] args) {
        Threads1 t1=new Threads1();
        Thread t=new Thread(t1);
        t.start();
        t.interrupt();

        Thread t2=new Thread(t1);
        t2.start();

        }
}
```

### 3)Creating a Thread Using an Anonymous Class in Java

In Java, you can create a thread using an anonymous class, which provides a more concise way to define and start a thread without the need to create a separate class. An anonymous class is an unnamed implementation of an interface or extension of a class, defined and instantiated all at once.

### **Steps and Procedure:**

**Create an Anonymous Class Implementing Runnable:**
- You can create an anonymous class that implements the Runnable interface and overrides the run() method directly where you need the thread.

**Pass the Anonymous Class Instance to a Thread Object:**
- Once the anonymous class is defined, pass it as an argument to a Thread object.
Start the Thread:

**Call the start() method on the Thread object to initiate the thread's execution.**

```java
public class Anomous {
public static void m1(){
    for(int i=1;i<=3;i++){
        System.out.println(Thread.currentThread().getName()+" : "+i);
    }
}
    public static void main(String[] args) {
        Thread t=new Thread(){
            @Override
            public void run(){
                m1();
            }
        };t.start();

        Thread t1=new Thread(){
            public void run(){
                m1();
            }
        };t1.start();
    }
}
```
---
## Functions

**start()**

- **Description:** This method starts the thread, invoking the run() method in a new thread of execution.
- **Usage:** Must be called to begin thread execution.

> Thread t = new Thread();
> t.start();

**run()**

- **Description:** This method contains the code that is executed when the thread is started. It can be overridden to define the thread's task.
- **Usage:** Typically overridden in a subclass of Thread.

> public void run() {
>   // Code to be executed by the thread
> }

**join()**

- **Description:** This method waits for the thread to die (complete execution). It can take an optional timeout parameter.
- **Usage:** Useful when you need to wait for another thread to finish before continuing execution.

> t.join(); // Waits for thread t to finish

**sleep(long millis)**

- **Description:** Static method that causes the currently executing thread to sleep for a specified number of milliseconds.
- **Usage:** Can be used to pause the thread's execution temporarily.

> Thread.sleep(1000); // Sleeps for 1 second

**interrupt()**

- **Description:** This method interrupts a thread, setting its interrupted status. It does not forcibly stop the thread but signals it to stop if it checks for interruptions.
- **Usage:** Can be used to gracefully stop a thread.

> t.interrupt(); // Interrupts thread t

**isAlive()**

- **Description:** This method checks if the thread is still alive (running or has not finished).
- **Usage:** Can be used to determine the state of a thread.

> if (t.isAlive()) {
>    // Thread is still running
> }

**setPriority(int priority)**

- **Description:** This method sets the priority of the thread. Priorities are integers between Thread.MIN_PRIORITY (1) and Thread.MAX_PRIORITY (10).

- **Usage:** Affects the order in which threads are scheduled by the thread scheduler.

> t.setPriority(Thread.MAX_PRIORITY); // Set highest priority

**getPriority()**

- **Description:** This method returns the priority of the thread.
- **Usage:** Can be used to retrieve the current priority of the thread.

> int priority = t.getPriority(); // Get the thread's priority

**setName(String name)**

- **Description:** This method sets the name of the thread.
- **Usage:** Useful for identifying threads.

> t.setName("MyThread");

**getName()**

- **Description:** This method returns the name of the thread.
- **Usage:** Can be used to retrieve the thread's name.
> String name = t.getName(); // Get the thread's name

## synchronize

Synchronization in Java is a mechanism that ensures that two or more concurrent threads do not simultaneously execute specific sections of code, preventing data inconsistency and ensuring thread safety. It is essential in multi-threaded programming when multiple threads access shared resources.

**Why Synchronization is Needed**

- **Data Consistency:** When multiple threads modify shared resources (like variables, objects, or data structures), inconsistencies can occur if threads read or write data at the same time.
- **Prevent Race Conditions:** A race condition occurs when two or more threads attempt to modify shared data concurrently, leading to unpredictable results.

**Types of Synchronization**

**Method Synchronization:**
- We can synchronize an entire method by using the synchronized keyword in its declaration. Only one thread can execute that method for a given instance at a time.

```java
 public synchronized void synchronizedMethod() {
     // Critical section code
 }
```

**Block Synchronization:**
- Instead of synchronizing an entire method, you can synchronize a block of code within a method. This allows for finer control over what gets synchronized.

```java
public void someMethod() {
    synchronized (this) {
        // Critical section code
    }
}
```
Example Code 

```java
public class Synchronisation {
    public  synchronized void m1(){
        for(int i=1;i<=5;i++){
            System.out.println("Static "+Thread.currentThread().getName());
        }
    }
 
    public static void main(String[] args) {
    Synchronisation s =new Synchronisation();
    Thread t=new Thread(){
        public void run(){
           s.m1();
        }
    }; 
    t.start();
    
    Thread t1=new Thread(){
        public void run(){
           s.m1();
        }
    }; 
    t1.start(); 
    }
}
```
**Static Synchronization in Java**

Static synchronization in Java is used when you want to synchronize access to a static method across all instances of a class. This means that if one thread is executing a static synchronized method, no other thread can execute any static synchronized method of the same class until the first thread completes its execution.

**Why Use Static Synchronization?**

- **Class-Level Locking:** Static synchronization locks the class itself rather than an instance of the class, ensuring that all threads are synchronized on the class level.
- **Shared Resources:** It is particularly useful when dealing with shared resources that are not tied to a specific instance of a class but are shared among all instances.

```java
public class Synchronisation {
    
    public static synchronized void m2(){
        for(int i=1;i<=5;i++){
            System.out.println("Static"+Thread.currentThread().getName());
        }
    }
    public static void main(String[] args) {
    // Synchronisation s =new Synchronisation();
    Thread t=new Thread(){
        public void run(){
           m2();
        }
    }; 
    t.start();
    Synchronisation s1 =new Synchronisation();
    Thread t1=new Thread(){
        public void run(){
           m2();
        }
    }; 
    t1.start(); 
    }
}
```
## Inter-Thread-Communication

Inter-thread communication in Java allows threads to communicate with each other, enabling coordination and synchronization between their execution. The primary methods used for inter-thread communication are wait(), notify(), and notifyAll(), which are defined in the Object class.

**Key Concepts:**

- **Wait and Notify Mechanism:** This mechanism helps manage the communication between threads, especially when one thread needs to wait for a condition to be met before proceeding, while another thread can notify it when the condition has changed.

- **Monitors:** Each object in Java has a monitor, which is a synchronization mechanism that allows threads to lock the object. The wait(), notify(), and notifyAll() methods must be called from within a synchronized block or method to ensure thread safety.

### **The wait() Method:**
**Purpose:** The wait() method causes the current thread to wait until another thread invokes notify() or notifyAll() on the same object.
Releases Lock: When a thread calls wait(), it releases the lock on the object, allowing other threads to access it.
**Usage:** It can be used when a thread is waiting for some condition to be met.

### **The notify() Method:**
- **Purpose:** The notify() method wakes up a single thread that is waiting on the object's monitor.
- **Lock Retained:** The thread that calls notify() does not release the lock immediately; it retains it until the current synchronized block or method completes.

### **The notifyAll() Method:**
- **Purpose:** The notifyAll() method wakes up all the threads that are waiting on the object's monitor.
- **Lock Retained:** Similar to notify(), the lock is retained until the current synchronized block or method completes.

Example Code
```java
public class Bank {
    public static double Balance=3000;
    public synchronized void Deposit(double Dep){
        Balance=Balance+Dep;
        System.out.println("Balance after Deposit :"+Balance);
    notify();
    }
    public synchronized void Withdrawl(double WD){
        if(Balance>=WD){
            System.out.println("Balance after Withdrawl :"+(Balance-=WD));
        }
        else{
            System.out.println("Processing Amount");
            try {
                wait();
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
            if(Balance>=WD){
                System.out.println("Balance after Deducting "+(Balance-=WD));
            }else{
                System.out.println("Insufficient Funds");
            }
        }
    }
    public static void main(String[] args) {
       Bank b=new Bank();
        Thread t=new Thread(){
            public void run(){
                b.Deposit(3000);
            }
        };
        t.start();
        t.setPriority(1);

        Thread t1=new Thread(){
            public void run(){
                b.Withdrawl(5000);
            }
        };
        t1.start();
        t1.setPriority(10);
    }
}
```
### Example Execution Flow
- Thread t1 (withdrawal thread) starts and attempts to withdraw 5000:
- It checks the balance (3000) and finds it insufficient.
- It prints "Processing Amount" and calls wait(), pausing execution.
- Thread t (deposit thread) starts and deposits 3000:
- It updates the balance to 6000 and prints "Balance after Deposit: 6000".
- It calls notify(), waking up the waiting withdrawal thread.
- Thread t1 resumes:
- After being notified, it checks the balance again (now 6000).
- It successfully withdraws 5000 and prints "Balance after Deducting: 1000".
  ---
## Yield&Join
### **yield()**
- **Definition:** A method in the Thread class that causes the currently executing thread to temporarily pause and allow other threads to execute.
- **Purpose:** To improve the responsiveness of applications by giving other threads a chance to run.
- **Behavior:** It does not guarantee immediate switching to another thread; it is a suggestion to the thread scheduler.

### **join()**
- **Definition:** A method in the Thread class that allows one thread to wait for another thread to complete its execution.
- **Purpose:** To ensure that the current thread pauses until the specified thread finishes.
- **Behavior:** It can be called with a timeout parameter to limit the wait duration; if the specified thread completes before the timeout, the current thread continues execution.

### **Key Differences**
- **Yield:** Suggests that the thread yield its execution; does not wait for completion.
- **Join:** Waits for the specified thread to finish before continuing execution.
