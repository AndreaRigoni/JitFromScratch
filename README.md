# JitFromScratch
Collection of examples from my talks in the [LLVM Social Berlin](https://www.meetup.com/de-DE/LLVM-Social-Berlin/) and [C++ User Group Berlin](https://www.meetup.com/de-DE/berlincplusplus/) that showcase techniques for implementing various aspects of a JIT compiler built with the LLVM 4.0 ORC libraries.

All examples are tested on Linux Mint 18, Mac OS X 10.12 and Windows 10. The repository follows a *perfect history* policy to foster traceability and understanding.

## Structure

The [jit-basics](https://github.com/weliveindetail/JitFromScratch/commits/jit-basics) establish a common code base for all further examples by demonstrating how to compile the code for a simple function at runtime:

```
template <size_t sizeOfArray>
int *integerDistances(const int (&x)[sizeOfArray], int *y) {
  int items = arrayElements(x);
  int *results = customIntAllocator(items);

  for (int i = 0; i < items; i++) {
    results[i] = abs(x[i] - y[i]);
  }

  return results;
}
```

## Table of Contents

* general topics
  * [jit-basics](https://github.com/weliveindetail/JitFromScratch/commits/jit-basics) — step by step guide for a basic minimal JIT
  * [jit-optimization](https://github.com/weliveindetail/JitFromScratch/commits/jit-optimization) — applying selected optimizations to JITed code

* calling external functions from JITed code
  * [jit-function-calls/explicit](https://github.com/weliveindetail/JitFromScratch/commits/jit-function-calls/explicit) — explicit run-time name/address mapping
  * [jit-function-calls/implicit-extern-c](https://github.com/weliveindetail/JitFromScratch/commits/jit-function-calls/implicit-extern-c) — implicit compile-time binding to C functions
  * [jit-function-calls/implicit-mangled](https://github.com/weliveindetail/JitFromScratch/commits/jit-function-calls/implicit-mangled) — implicit compile-time binding to C++ functions

* debugging JIT compiled code
  * [jit-debug/gdb-interface](https://github.com/weliveindetail/JitFromScratch/commits/jit-debug/gdb-interface) — implement the GDB JIT-interface
