# C++ Engineering Skills

A collection of specialized AI skills for C++ backend, performance engineering, numerical linear algebra, and Git workflow.

These skills are designed for C++ projects that require more than basic code generation, especially projects involving:

* Linux
* C++17 / C++20 / C++23
* CMake
* gRPC
* Multithreading
* NUMA
* CPU affinity
* BLAS / LAPACK
* MKL
* AOCL
* BLIS
* OpenBLAS
* SuiteSparse
* Sparse matrices
* High-performance computing (HPC)

---

## Directory Structure

Recommended project layout:

```text
.agents/
└── skills/
    ├── cpp-backend/
    │   └── SKILL.md
    │
    ├── cpp-performance/
    │   └── SKILL.md
    │
    ├── linear-algebra/
    │   └── SKILL.md
    │
    └── git-commit/
        └── SKILL.md
```

Each skill focuses on a specific engineering domain.

---

# 1. C++ Backend

Path:

```text
.agents/skills/cpp-backend/SKILL.md
```

## Purpose

Provides guidance for designing, implementing, reviewing, and debugging production-quality C++ backend systems.

Typical areas include:

* C++ architecture
* Linux services
* CMake
* gRPC
* HTTP/2
* ZeroMQ
* Multithreading
* Thread safety
* Resource lifetime
* RAII
* Error handling
* Logging
* Configuration
* Networking
* Service architecture
* ABI and deployment
* Testing

## Example Usage

```text
Design a high-performance gRPC server in C++.
```

```text
Review this C++ server implementation for thread-safety issues.
```

```text
Help me design the architecture of a C++ backend with gRPC and multiple worker threads.
```

```text
Check whether this CMake configuration is suitable for a production Linux service.
```

Use this skill when the main question is:

> How should I design or implement this C++ backend?

---

# 2. C++ Performance

Path:

```text
.agents/skills/cpp-performance/SKILL.md
```

## Purpose

Provides a systematic approach to performance analysis and optimization.

The core principle is:

> Measure first, identify the bottleneck, optimize second.

It covers:

* CPU profiling
* `perf`
* Cache behavior
* Memory bandwidth
* SIMD
* Compiler optimization
* GCC / Clang / AOCC
* Thread scaling
* Thread affinity
* NUMA
* False sharing
* Lock contention
* Atomics
* OpenMP
* Nested parallelism
* CPU topology
* Real-time Linux
* Benchmark design
* Latency analysis
* P50 / P95 / P99
* Performance regression analysis

## Example Usage

```text
Why is my program slower with 12 threads than with 8 threads?
```

```text
Analyze this perf report and find the bottleneck.
```

```text
Help me benchmark the scaling from 1 to 64 threads.
```

```text
Why does running two processes make each process slower?
```

```text
Analyze the NUMA and CPU affinity behavior of this application.
```

Use this skill when the main question is:

> Why is it slow, and what is the actual bottleneck?

---

# 3. Linear Algebra

Path:

```text
.agents/skills/linear-algebra/SKILL.md
```

## Purpose

Provides expertise in numerical linear algebra and high-performance matrix computation.

It focuses on both mathematical algorithms and their high-performance implementations.

Covered technologies include:

### Dense Linear Algebra

* BLAS
* LAPACK
* GEMM
* GEMV
* TRSM
* TRSV
* LU
* QR
* Cholesky
* SVD
* Eigenvalue problems

### BLAS Implementations

* Intel MKL
* AMD AOCL
* BLIS
* OpenBLAS

### Sparse Linear Algebra

* CSR
* CSC
* COO
* BSR
* SpMV
* SpMM
* CSRMM
* Sparse triangular solve

### Sparse Solvers

* SuiteSparse
* KLU
* UMFPACK
* CHOLMOD
* SPQR
* PARDISO
* AOCL-Sparse
* PETSc

### Numerical Issues

* Numerical stability
* Conditioning
* Pivoting
* Scaling
* Residuals
* Floating-point precision
* LP64 / ILP64
* C / C++ / Fortran ABI

## Example Usage

```text
Which is faster for this GEMM workload: MKL, AOCL BLIS, or OpenBLAS?
```

```text
Why is AOCL-Sparse SpMM slower than my own CSR implementation?
```

```text
Which SuiteSparse solver should I use for this sparse matrix?
```

```text
Should I use KLU, UMFPACK, or PARDISO for this matrix?
```

```text
How should I benchmark SpMV across different sparse matrix formats?
```

```text
Explain why this matrix gets much more fill-in during LU factorization.
```

Use this skill when the main question is:

> Which numerical algorithm or linear algebra library should I use, and how can I make it fast?

---

# 4. Git Commit

Path:

```text
.agents/skills/git-commit/SKILL.md
```

## Purpose

Analyzes Git changes and produces clear, consistent commit messages.

It can work with:

```bash
git status
git diff
git diff --cached
git log
```

The skill can determine whether a change is primarily:

* `feat`
* `fix`
* `perf`
* `refactor`
* `test`
* `build`
* `ci`
* `docs`
* `style`
* `chore`
* `revert`

It also considers the repository's existing commit-message conventions.

## Example Usage

```text
Help me write a commit message for my current changes.
```

```text
Analyze the staged changes and generate a Conventional Commit message.
```

```text
Should this change be feat, fix, perf, or refactor?
```

```text
Review my current diff and suggest how to split it into multiple commits.
```

Typical output:

```text
perf(spmm): reuse temporary buffers
```

or:

```text
fix(csr): correct zero-based index handling
```

Use this skill when the main question is:

> How should I describe this Git change clearly and consistently?

---

# 5. Combining Skills

The skills are independent, but they can be used together.

This is particularly useful for high-performance C++ projects.

For example:

```text
C++ Backend
      │
      ├── cpp-backend
      │
      ├── cpp-performance
      │
      └── linear-algebra
```

A real-world problem may require several skills simultaneously.

## Example

Suppose an application performs sparse matrix multiplication through a gRPC service.

The question is:

```text
Why does the gRPC service become slower when the number of
worker threads increases from 8 to 16?
```

The analysis may involve:

```text
cpp-backend
      ↓
gRPC worker architecture
      ↓
cpp-performance
      ↓
thread scaling / perf / cache / NUMA
      ↓
linear-algebra
      ↓
SpMM / AOCL-Sparse / CSR
```

This produces a much more complete analysis than looking at the C++ code alone.

---

# 6. Recommended Workflow

For performance-sensitive C++ development, use the following workflow.

```text
              ┌─────────────────┐
              │   C++ Backend   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  Benchmarking   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │   Profiling     │
              │  perf / cache   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Linear Algebra  │
              │ BLAS / Sparse   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Optimization    │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ A/B Benchmark   │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │   Git Commit    │
              └─────────────────┘
```

The important principle is:

> Do not optimize based on intuition alone.

Measure the baseline, identify the bottleneck, make a controlled change, and benchmark again.

---

# 7. Typical Commands

## Backend Development

```text
Implement this feature.
Review this class.
Find potential lifetime problems.
Design a gRPC service.
Review this CMake configuration.
```

## Performance Analysis

```text
Analyze this benchmark.
Analyze this perf output.
Find the CPU bottleneck.
Explain poor thread scaling.
Investigate NUMA effects.
Compare two implementations.
```

## Linear Algebra

```text
Analyze this matrix.
Choose a sparse solver.
Compare KLU and PARDISO.
Compare AOCL and MKL.
Optimize SpMV.
Optimize SpMM.
Choose CSR vs CSC vs COO.
```

## Git

```text
Write a commit message for this diff.
Analyze the staged changes.
Suggest commit splitting.
Use Conventional Commits.
Follow the repository's existing commit style.
```

---

# 8. Performance Investigation Example

For a slow numerical kernel, a good investigation should look like:

```text
1. Establish baseline
       ↓
2. Inspect matrix characteristics
       ↓
3. Identify algorithm
       ↓
4. Check library implementation
       ↓
5. Check thread count
       ↓
6. Check CPU affinity
       ↓
7. Check NUMA
       ↓
8. Run perf
       ↓
9. Check cache / memory bandwidth
       ↓
10. Test alternative implementation
       ↓
11. Benchmark
       ↓
12. Compare results
```

For example:

```text
User:
AOCL-Sparse SpMM is slower than my implementation.
```

A useful analysis should not immediately conclude:

```text
AOCL-Sparse is slower.
```

Instead investigate:

```text
Matrix dimensions
NNZ
Row distribution
Index type
Data type
CSR layout
RHS columns
Thread count
CPU affinity
NUMA
Memory bandwidth
Library version
```

Then benchmark both implementations under identical conditions.

---

# 9. Git Workflow Example

After completing an optimization:

```text
1. Implement optimization
2. Run correctness tests
3. Run benchmark
4. Compare before/after
5. Inspect git diff
6. Generate commit message
```

For example:

```text
Before:
12.4 ms

After:
9.1 ms
```

A suitable commit may be:

```text
perf(spmm): reuse temporary buffers
```

If the benchmark evidence is part of the project's commit convention, the body can include it.

---

# 10. Design Philosophy

These skills follow several principles.

### Evidence over intuition

```text
Measure → Hypothesis → Experiment → Result
```

### Correctness before performance

A faster incorrect result is not an optimization.

### Algorithm before micro-optimization

Prefer:

```text
better algorithm
```

over:

```text
more aggressive compiler flags
```

### Reproducibility

Performance results should record:

```text
CPU
OS
Compiler
Compiler flags
Library version
Matrix
Thread count
Affinity
Environment
```

### Hardware awareness

Performance depends on the actual machine.

Consider:

```text
CPU topology
Cache
NUMA
Memory bandwidth
ISA
Thread placement
```

### Repository consistency

Git commit messages should follow the existing project's conventions whenever possible.

---

# 11. When to Use Which Skill

| Task                 | Skill             |
| -------------------- | ----------------- |
| C++ architecture     | `cpp-backend`     |
| gRPC service         | `cpp-backend`     |
| CMake                | `cpp-backend`     |
| Thread safety        | `cpp-backend`     |
| CPU profiling        | `cpp-performance` |
| `perf` analysis      | `cpp-performance` |
| NUMA                 | `cpp-performance` |
| CPU affinity         | `cpp-performance` |
| Thread scaling       | `cpp-performance` |
| SIMD                 | `cpp-performance` |
| BLAS                 | `linear-algebra`  |
| LAPACK               | `linear-algebra`  |
| MKL                  | `linear-algebra`  |
| AOCL                 | `linear-algebra`  |
| OpenBLAS             | `linear-algebra`  |
| BLIS                 | `linear-algebra`  |
| SuiteSparse          | `linear-algebra`  |
| KLU / UMFPACK        | `linear-algebra`  |
| SpMV / SpMM          | `linear-algebra`  |
| Sparse solvers       | `linear-algebra`  |
| Git commit message   | `git-commit`      |
| Commit splitting     | `git-commit`      |
| Conventional Commits | `git-commit`      |

---

# 12. Recommended Skill Set

For a high-performance C++ project, the recommended baseline is:

```text
cpp-backend
cpp-performance
linear-algebra
git-commit
```

For projects involving numerical simulation, sparse matrices, or HPC, these skills provide a useful engineering stack:

```text
C++ Backend
     +
Performance Engineering
     +
Numerical Linear Algebra
     +
Git Engineering Workflow
```

The goal is not simply to generate code.

The goal is to build software that is:

```text
Correct
Maintainable
Observable
Portable
Numerically reliable
High-performance
Reproducible
```
