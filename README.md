# OS Lab Assignment 6 — Deadlock Avoidance and Detection

This repository contains the implementation of **Operating Systems Lab Assignment 6** using the **xv6 operating system**.

The assignment focuses on deadlock avoidance, deadlock detection, deadlock prevention, and multi-resource process synchronization.

## Contents

### Q1 — Banker's Algorithm

**File:** `user/bankers.c`

Implements the Banker's Algorithm for deadlock avoidance using:

* Allocation matrix
* Maximum demand matrix
* Available resource vector
* Need matrix
* Safety Algorithm
* Resource Request Algorithm

The program checks whether the initial system state is safe and generates a valid safe sequence.

It also tests:

* A resource request that can be safely granted.
* A resource request that must be rejected because it would result in an unsafe state.

---

### Q2 — Deadlock Detection using Resource Allocation Graph

**File:** `user/deadlockdetect.c`

Implements deadlock detection using a Resource Allocation Graph (RAG) and Wait-For Graph.

The program:

* Represents resource allocation and process requests.
* Constructs the corresponding wait-for graph.
* Uses DFS-based cycle detection.
* Determines whether a deadlock exists.
* Prints the cycle of processes when a deadlock is detected.

Two scenarios are tested:

* A system with no deadlock.
* A system containing a circular wait involving three or more processes.

---

### Q3 — Deadlock Prevention using Resource Ordering

**File:** `user/resourceorder.c`

Demonstrates deadlock prevention using **Hierarchical Resource Ordering**.

Two shared resources are used to demonstrate the problem of circular wait. In the first case, processes attempt to acquire the resources in different orders, which can result in deadlock.

The program then applies a fixed global ordering in which all processes acquire resources in the same order.

This prevents circular wait and allows the processes to complete successfully.

The program uses step markers to show resource acquisition, waiting, work, and completion.

---

### Q4 — Multi-Resource Synchronization and Deadlock Avoidance

**File:** `user/syncdeadlock.c`

Implements a multi-resource synchronization problem involving:

* 5 worker processes
* 2 Printers
* 1 Scanner
* 2 Disks

Each process requires two different resource types to perform its work.

The program uses synchronization mechanisms to control access to the limited resource instances and applies **Hierarchical Resource Ordering** as the deadlock-prevention strategy.

The resources are assigned the following order:

```text
Printer = 0
Scanner = 1
Disk    = 2
```

Each process acquires its required resources in increasing order. This prevents circular wait and ensures that the processes can complete their work without entering a deadlock state.

Multiple execution cycles are performed to demonstrate correct resource sharing and synchronization.

---

## Deadlock Prevention Strategy

The resource-ordering technique is based on assigning every resource type a unique global priority.

A process must always request resources according to this ordering. Therefore, a process holding a higher-ordered resource cannot wait for a lower-ordered resource.

This eliminates the **circular wait** condition, which is necessary for a deadlock to occur.

---

## Output Logs

The `output_logs` directory contains execution logs for the different programs and test scenarios.

The logs demonstrate:

* Safe and unsafe system states.
* Safe and rejected resource requests.
* Wait-for graph construction.
* Deadlock detection and cycle identification.
* Deadlock caused by inconsistent resource ordering.
* Successful execution using consistent resource ordering.
* Multi-process resource synchronization.
* Completion of multiple execution cycles without deadlock.

---

## Project Structure

```text
.
├── kernel/
├── user/
│   ├── bankers.c
│   ├── deadlockdetect.c
│   ├── resourceorder.c
│   ├── syncdeadlock.c
│   ├── user.h
│   └── usys.pl
├── output_logs/
├── Makefile
└── README.md
```

## Environment

* Operating System: xv6
* Programming Language: C
* Build System: xv6 Makefile
* Execution Environment: xv6

## Learning Objectives

This assignment provides practical implementation of:

* Deadlock avoidance
* Deadlock detection
* Deadlock prevention
* Banker's Algorithm
* Safety Algorithm
* Resource Request Algorithm
* Resource Allocation Graphs
* Wait-For Graphs
* DFS-based cycle detection
* Circular wait
* Resource ordering
* Process synchronization
* Multi-resource allocation
* Inter-process coordination
