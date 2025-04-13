# 📚 Introduction to Operating Systems: Processes

## 🖥️ What is an Operating System?

An **Operating System (OS)** is a system software that manages computer hardware, software resources, and provides services for computer programs. It acts as an intermediary between users and the computer hardware.

---

## ⚙️ What is a Process?

A **process** is an instance of a program **in execution**. It is not just the program code (which is called the **text section**), but also includes:

- **Program Counter**: Indicates the current instruction the process is executing.
- **Registers**: Hold variables and intermediate data.
- **Stack**: Contains temporary data like function parameters, return addresses, and local variables.
- **Heap**: Used for dynamic memory allocation.
- **Data Section**: Contains global variables.

Each process is assigned a **unique identifier** called the **Process ID (PID)**.

---

## 🧾 Process vs Program

| Concept  | Description |
|----------|-------------|
| Program  | A passive collection of instructions stored on disk (e.g., `.exe`, `.out` files). |
| Process  | A dynamic execution of a program; it has a lifecycle, allocated resources, and state. |

A single program can create **multiple processes**. For example, opening two instances of a text editor launches two separate processes of the same program.

---

## 📊 Data Associated with a Process

Each process has several data elements that the OS uses to manage it:

### 1. **Process Control Block (PCB)**

A PCB is a data structure maintained by the OS. It contains:

- PID (Process ID)
- Process state (e.g., running, ready, waiting)
- CPU registers
- CPU scheduling information
- Memory management info (e.g., page tables)
- I/O status
- Accounting info (e.g., CPU used, time limits)

### 2. **Memory Layout**

### 3. **State of Process**
The actual state of the program, that includes the value of the CPU records, the program counter and other details that allow the OS to suspend and resume the process execution at a given time.

### 4. **Assigned resources**
This includes resources like memory, CPU, execution time and in/out devices that the process can use while its executed. Assigned resources can never be bigger than the amount specified by the kernel.

---
## 🔄 Process Statuses in Operating Systems

A **process status** (or state) describes the current condition or activity of a process. These statuses help the operating system manage multitasking and resource allocation.

## 📌 Common Process States

1. **New** 🐣  
   The process is being created but is not yet ready to run.

2. **Ready** ⏳  
   The process is prepared to run and waiting for CPU time.

3. **Running** ⚡  
   The process is currently being executed on the CPU.

4. **Waiting (or Blocked)** 💤  
   The process is waiting for some event (like I/O completion) before it can proceed.

5. **Terminated** ❌  
   The process has completed execution and is being removed from the system.

---

These states form the core of **process lifecycle management**, allowing the OS to efficiently schedule and control multiple processes.

---

## 🔁 Transitions Between States

- **New ➝ Ready**: After creation, when the process is fully initialized.
- **Ready ➝ Running**: When the scheduler assigns CPU time.
- **Running ➝ Waiting**: If the process needs to wait for an event.
- **Running ➝ Ready**: If the process is preempted (interrupted to let another process run).
- **Waiting ➝ Ready**: When the awaited event completes.
- **Running ➝ Terminated**: Upon completion or error.

---

## 🧠 Summary

- The lifecycle is controlled by the OS to manage multitasking.
- Transitions are triggered by the OS, hardware events, or the process itself.
- Managing this cycle efficiently is crucial for system performance.

---
## 🛠️ Summary: Process Creation in Operating Systems

The creation of a new process involves a series of actions that can be grouped into **two main stages**:

## 🔧 Stages of Process Creation

1. **Creation of administrative data structures**  
   The OS prepares the necessary structures (like the Process Control Block) to manage the new process.

2. **Allocation of address space**  
   The OS assigns memory that the process will use during its execution.

---

## 🧾 Reasons for Process Creation

Process creation can occur for various reasons, depending on the system type:

- 📦 **Batch Systems**  
  A new process is created when a job is submitted for execution.

- 👤 **Interactive Systems**  
  A new process is created when a user logs in or starts a session.

- 🖨️ **System Services**  
  The OS may create a process to provide a service (e.g., printing a file), allowing the requesting process to continue execution.

- 🔁 **Process Generation**  
  A running process can create another to execute tasks in parallel.  
  - The creator is called the **parent process**.  
  - The newly created one is the **child process**.

This establishes a **hierarchy** between processes.

> 🔍 Note:  
> In the first three cases, the OS initiates the process creation, which is **transparent to user processes**.  
> In the last case, a **user process explicitly** requests the creation of another process.
