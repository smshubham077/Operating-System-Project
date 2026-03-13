Producer–Consumer Synchronization Simulation
Project Overview

This project simulates a real-world Producer–Consumer scenario in a multi-threaded environment. Multiple producer threads generate data and place it into a bounded buffer, while multiple consumer threads retrieve and process the data.

To ensure safe and efficient communication between threads, the system uses synchronization mechanisms such as Semaphores or Monitors. These mechanisms control access to the shared buffer and prevent common concurrency issues.

The implementation demonstrates how operating systems manage concurrent processes, ensuring that producers do not add data when the buffer is full and consumers do not remove data when the buffer is empty.

**Objectives**

Simulate a real-world producer–consumer model

Implement multi-threading

Use semaphores or monitors for synchronization

Manage a bounded buffer

Prevent race conditions

Maintain data consistency

Demonstrate safe concurrent access

**Key Concepts**

Producer Thread – Generates data and places it into the buffer

Consumer Thread – Retrieves and processes data from the buffer

Bounded Buffer – Shared memory structure with limited capacity

Semaphore / Monitor – Synchronization tools to control thread access

Mutex – Ensures mutual exclusion for the critical section

**Synchronization Mechanism**

The system uses three synchronization controls:

Mutex – Provides exclusive access to the buffer

Empty Semaphore – Tracks available empty slots

Full Semaphore – Tracks available items for consumption

These mechanisms ensure that:

Producers wait when the buffer is full

Consumers wait when the buffer is empty

Only one thread accesses the critical section at a time

**Features**

Multiple producers and consumers

Thread-safe bounded buffer

Demonstrates synchronization using semaphores/monitors

Prevents race conditions

Illustrates operating system concurrency concepts

**Applications**

Operating System synchronization studies

Multi-threaded system design

Concurrent programming learning

Real-world resource sharing problems
