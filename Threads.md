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

### Creating a Thread by Extending the Thread Class in Java

In Java, one way to create a new thread is by extending the Thread class. This method involves creating a subclass of Thread and overriding its run() method. The run() method contains the code that will be executed when the thread is started.

- **Create a Class that Extends Thread:**   To create a new thread, you define a class that extends the Thread class and override the run() method. The code inside the run() method is what will be executed by the new thread.

- **Override the run() Method:**   The run() method contains the code that represents the task or job that the thread will perform when it's running.

- **Create an Instance of the Subclass:**    After defining your thread class, you create an instance of it.

- **Start the Thread:**   Call the start() method on the instance to begin the execution of the thread. This causes the run() method to be executed in a new thread.
