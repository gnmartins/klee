KLEE Symbolic Virtual Machine
=============================

[![Build Status](https://travis-ci.org/klee/klee.svg?branch=master)](https://travis-ci.org/klee/klee)

`KLEE` is a symbolic virtual machine built on top of the LLVM compiler
infrastructure. Currently, there are two primary components:

  1. The core symbolic virtual machine engine; this is responsible for
     executing LLVM bitcode modules with support for symbolic
     values. This is comprised of the code in lib/.

  2. A POSIX/Linux emulation layer oriented towards supporting uClibc,
     with additional support for making parts of the operating system
     environment symbolic.

Additionally, there is a simple library for replaying computed inputs
on native code (for closed programs). There is also a more complicated
infrastructure for replaying the inputs generated for the POSIX/Linux
emulation layer, which handles running native programs in an
environment that matches a computed test input, including setting up
files, pipes, environment variables, and passing command line
arguments.

Coverage information can be found [here](http://vm-klee.doc.ic.ac.uk:55555/index.html).

For further information, see the [webpage](http://klee.github.io/).

## Modifications for assert-p4

This modified version of KLEE includes a new function called klee_print_once which is used to display the symbolic execution results of [assert-p4](https://github.com/gnmartins/assert-p4) in a more user friendly way.

The following files have been changed:

* include/klee/klee.h
* lib/Core/Executor.cpp
* lib/Core/Executor.h
* lib/Core/SpecialFunctionHandler.cpp
* lib/Core/SpecialFunctionHandler.h

The modifications can be found in each of these files directly under ```// assert-p4 changes``` comments. 

The core change is the [implementation of a function handler for klee_print_once](https://github.com/gnmartins/klee/blob/b289b892e8a273ad7423b48bfb839b4a725fa8da/lib/Core/SpecialFunctionHandler.cpp#L208-L225).
