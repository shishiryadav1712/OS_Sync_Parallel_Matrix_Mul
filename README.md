# Parallel Matrix Multiplication

**LAB 2**

This assignment involves implementing both serial and parallel matrix multiplication using Pthreads in C. The program multiplies two randomly generated \( N X N) matrices and compares the results of the serial and parallel computations to verify correctness.

---

## Prerequisites

Before proceeding, ensure you have the following:


- **Development Environment**: A Unix-like environment with GCC, Make, and Pthreads library installed.
- **Project Files**: Ensure all project files (`prog_Assign2.c`, `Makefile`) are present in the designated directory on the server.

---

## Features

### Serial Matrix Multiplication

- Computes the product of two \( N \times N \) matrices using a serial algorithm.
- Uses exactly **three loops** for the computation, as required.

### Parallel Matrix Multiplication

- Implements parallel matrix multiplication using POSIX threads (Pthreads).
- Dynamically allocates tasks to threads; each thread computes elements of the result matrix.
- Ensures proper synchronization using mutexes to prevent race conditions.

### Dynamic Task Allocation

- Threads fetch tasks at runtime instead of having tasks statically assigned.
- Uses a shared counter with mutex protection to assign tasks to threads safely.

### Result Verification

- Compares the serial and parallel results to verify correctness.
- Displays messages indicating whether the results match.

### Logging and Tracking

- Logs which thread computes each element of the result matrix.
- Tracks and displays the number of tasks completed by each thread.

---

## Connecting to the Server

To begin, you'll need to connect to the provided server using SSH. Follow these steps:

1. **Open Terminal**: Launch your terminal application.

2. **Connect via SSH**:

   Use the following command to connect to the server. Replace `username` with your actual username.

   ```bash
   ssh username@serverURL
   ```

3. **Enter Password**:

   When prompted, enter your password. 

4. **Successful Connection**:

   Upon successful authentication, you will be logged into the server and presented with a shell prompt similar to:

   ```bash
   username@server:~$
   ```

---

## Navigating to the Project Directory

Once connected to the server, navigate to the root directory. In my case the project is located in `Assignment/Assignment 2`, follow these steps:

1. **Change Directory**:

   Use the `cd` command to navigate to your project directory. If your directory name contains spaces, escape them using a backslash (`\`) or enclose the path in quotes.

   ```bash
   cd Assignment/Assignment\ 2
   ```

2. **Verify Location**:

   Confirm you're in the correct directory by listing its contents:

   ```bash
   ls
   ```

   Expected output:

   ```
   Makefile  prog_Assign2  prog_Assign2.c  prog_Assign2.o
   ```

---

## Compilation and Execution

To compile the parallel matrix multiplication program, utilize the provided `Makefile`. This simplifies the build process and ensures all necessary flags and dependencies are correctly handled.

1. **Compile the Program**:

   ```bash
   make
   ```

   **Expected Output**:

   ```
   gcc -Wall -Wextra -pthread -lm -c prog_Assign2.c -o prog_Assign2.o
   gcc -Wall -Wextra -pthread -lm -o prog_Assign2 prog_Assign2.o
   ```

   This compiles `prog_Assign2.c` into an object file `prog_Assign2.o` and then links it to create the executable `prog_Assign2`.

2. **Running the Program**:

   After successful compilation, run the program using the `make run` command:

   ```bash
   make run
   ```

   Alternatively, you can execute the program directly:

   ```bash
   ./prog_Assign2
   ```

---

## Using the Program

Once the program is running, you can utilize its functionalities as follows:

1. **Enter Matrix Size and Number of Threads**:

   The program will prompt you to enter the size of the matrices (`N`) and the number of threads.

   ```bash
   Enter the size of the matrices (N):
   ```

   Enter a positive integer for `N` (e.g., `6`).

   ```bash
   Enter the number of threads:
   ```

   Enter a positive integer for the number of threads (e.g., `3`).

2. **Program Execution**:

   The program will then:

   - Display the randomly generated input matrices `B` and `C`.
   - Perform serial and parallel matrix multiplication.
   - Log which thread is computing each element.
   - Display the result matrices.
   - Compare the results to verify correctness.
   - Display the number of tasks completed by each thread.

   **Example Output**:

   ```
   Matrix B:
       6.00     9.00     5.00     9.00     8.00     8.00
       ...

   Matrix C:
       5.00     4.00     4.00     6.00     7.00     1.00
       ...

   Thread 0 is computing cell [0][0]
   Thread 0 is computing cell [0][1]
   ...
   The serial and parallel results match.

   Number of tasks completed by each thread:
   Thread 0 completed 14 tasks.
   Thread 1 completed 19 tasks.
   Thread 2 completed 3 tasks.
   ```

3. **Exiting the Program**:

   The program will exit automatically after execution.

---

## Notes

- **Matrix Size**: For large values of `N`, displaying the entire matrices may produce a lot of output. Consider using smaller values of `N` for testing.

- **Workload Distribution**: Due to dynamic task allocation, the number of tasks completed by each thread may vary.

- **Random Seed**: The random number generator is seeded with the current time to produce different matrices on each run.

- **Thread Synchronization**: The program uses mutexes to synchronize access to shared variables, preventing race conditions.


---

## Contents of the Assignment 2 Directory

- **Makefile**: Automates the compilation, execution, and cleanup processes.
- **prog_Assign2.c**: The main C source code file containing the implementation.
- **prog_Assign2**: The compiled executable program (after running `make`).
- **prog_Assign2.o**: The object file generated during compilation.

---

## Cleaning Up

To remove the compiled executable and object files, run:

```bash
make clean
```

This command deletes `prog_Assign2` and `prog_Assign2.o`.

---

## Sample Test Cases

You can test the program with various inputs to verify its correctness and behavior. Here are some sample test cases:

1. **Test Case 1**:

   - **Matrix Size**: `3`
   - **Number of Threads**: `2`

2. **Test Case 2**:

   - **Matrix Size**: `5`
   - **Number of Threads**: `4`

3. **Test Case 3**:

   - **Matrix Size**: `10`
   - **Number of Threads**: `5`

For each test case, observe the output to ensure that the serial and parallel results match and that the threads are computing the elements as expected.

---



