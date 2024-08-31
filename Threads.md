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
- [Wait&Notify](#Wait)
- [Yield & Join](#YnJ)
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
