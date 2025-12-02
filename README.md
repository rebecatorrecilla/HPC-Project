# HPC Project: Scalability & Energy Efficiency Analysis

## Project Overview
This project was conducted for the "Parallelism and Distributed Systems" course at the **Universitat Politècnica de Catalunya (UPC)**. The primary objective is to evaluate the performance, scalability, and energy consumption of high-performance computing applications running on a supercomputing cluster (utilizing the **MN5** environment).

The study focuses on hybrid parallelization strategies, comparing the trade-offs between **MPI** (Message Passing Interface) processes and **OpenMP** threads.

## Benchmarks & Workload
The project utilizes the **NAS Parallel Benchmarks (NPB) Multi-Zone**, specifically Class D of the following kernels:
*   **bt-mz:** Block Tri-diagonal solver.
*   **sp-mz:** Scalar Pentadiagonal solver.
*   **lu-mz:** Lower-Upper Gauss-Seidel solver.

Additionally, a separate analysis is performed on **TensorFlow** workloads running on GPU partitions.

## Methodology
The analysis is divided into four main sections:

### 1. Scalability Analysis (CPU)
Execution of the three kernels on the **GPP partition** using 4, 6, and 8 nodes.
*   **Configurations:** Tested "Extreme" cases (Pure MPI vs. Pure OpenMP) and "Intermediate" hybrid configurations.
*   **Metrics:** Calculation of Speedup and Parallel Efficiency (aiming for >70% efficiency).
*   **Goal:** Determine the optimal balance between MPI processes and OpenMP threads for each kernel.

### 2. Energy Consumption Analysis
Using the **EAR (Energy Awareness Runtime)** toolset (`eacct`, `ear-user-db`) to gather power metrics.
*   **Calculations:** Total Energy (Joules), Power (Watts), and Estimated Cost (€).
*   **Analysis:** Correlation between hardware resource usage (up to 700W per node limit) and operational costs.

### 3. Hardware Counters Performance
Evaluation of low-level performance metrics for the different configurations on 4, 6, and 8 nodes:
*   **CPI:** Cycles Per Instruction.
*   **Memory Bandwidth:** Analysis of memory bottlenecking in relation to the number of processes.

### 4. GPU Energy Analysis
Repetition of the energy and power analysis for **TensorFlow** applications running on the **ACC (Accelerator) partition**, considering the theoretical max power of 700W per GPU.

## Tools Used
*   **Hardware:** MareNostrum 5 (MN5) Supercomputer Nodes.
*   **Software/Libraries:** MPI, OpenMP, EAR (Energy Management), TensorFlow.
*   **Scripting:** Bash (Slurm workload manager).
