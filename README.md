# Dangling Pointer Bug in Rust
This repository demonstrates a common error in Rust involving dangling pointers.  The code attempts to iterate over a vector's elements after the vector's memory has been deallocated, resulting in undefined behavior.

## The Bug
The `bug.rs` file contains the buggy code.  The core issue is using `v.clear()` which deallocates the vector's memory, but then the code continues to dereference the raw pointer `ptr`.  This pointer now points to invalid memory, causing undefined behavior.

## The Solution
The `bugSolution.rs` file provides a corrected version of the code.  Instead of using a raw pointer and `v.clear()`, it iterates safely through the vector's elements using a safer method before clearing the vector or using another method that preserves the data before clearing. 

## How to Reproduce
1. Clone this repository.
2. Navigate to the repository's directory.
3. Compile and run `bug.rs` (expect undefined behavior or a crash).
4. Compile and run `bugSolution.rs` (expect correct output).

## Lessons Learned
This example highlights the importance of memory management in Rust, especially when dealing with raw pointers.  Using safe abstractions provided by Rust's standard library is highly encouraged to prevent dangling pointers and data races.