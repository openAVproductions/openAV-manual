###########
Programming
###########

.. note::
  If you have no interest in software development, then please ignore this chapter!

This section of the OpenAV manual is intended for those interested in
programming computers, or more specifcally real-time audio applications.
The following parts detail how OpenAV uses specific tools to test and
verify audio software.

The chapters are broken down into topics, and each topic will use various
tools for that specific problem. The most commonly used C debugging tools
are gdb and valgrind, so some familiarity with them is expected.


Memory
======
This guide explains how to use Valgrind to profile cache and memory usage
using the **callgrind** and **cachegrind** tools.

The Problem
-----------
The issue we are trying to minimize is that memory reads are expensive and
slow. This means that in order to achieve optimal performance, we *must*
ensure that memory reads and writes are optimal.

First we should profile L3 Cache Misses, providing information on
*how often* cache misses are taking place. Only if this number is
concidered too high we should find out *where* the cache misses are
being caused, which can be done using the *cachegrind* tool.

What happens
------------
The following is a quick description of how memory accesses work:

1. When we use the array for the first time, a "cold miss" occurs. This means that the array has not been used recently, and that it must be loaded from main memory. Sometimes also called a "compulsary miss", as it cannot be avoided.

2. A cache line is loaded, bringing the memory where the array is being accessed into L3 cache. Since 1 full cache line is loaded, the next item in the array is probably also in cache now.

3. Access the next item in the array and a "cache hit" occurs. Cache hits are good, as it means that the memory needed was already loaded in cache, and performance is very fast.

Finding the Problem
-------------------
This section introduces the tools available, and how to make them provide
useful information to debug why cache misses are occuring.

Callgrind
~~~~~~~~~
Valgrind provides a tool which profiles cache hits and misses. The tool is
called ``callgrind``. Example of profiling a file ``main.c`` as follows:

``gcc -g main.c -o main # Build with debug symbols``
``valgrind --tool=callgrind --cache-sim=yes --branch-sim=yes ./main``

The option ``--cache-sim=yes`` ensures that the cache and MMU are
simulated which provides the cache miss info, while ``--branch-sim=yes``
allows us to see how well branch prediction is performing.

The output of callgrind gives an overview of the memory operations that
took place during the profiling run. The total event counts are not very
helpful - they depend almost entirely on the unit test. Percent values
are much more useful, as they give an insight into how the code uses the
cache.

.. NOTE:: Callgrind has an annotation tool just like CacheGrind does:
  its called ``callgrind_annotate``
 
Analysing memory usage is not extremely difficult - it requires a unit test
to be available, and compilation with debug symbols. Valgrind's callgrind 
takes care of the profiling itself, printing results of the profiling run.

With the information gathered from ``callgrind``, we should now run
``cachegrind`` in order to find out where in the source code any expensive
memory thrashing is being caused.


CacheGrind
~~~~~~~~~~
Valgrind provides a tool which profiles cache hits and misses. The tool is
called ``cachegrind``. Example of profiling a file ``main.c`` as follows:

``gcc -g main.c -o main # Build with debug symbols``
``valgrind --tool=cachegrind --cachegrind-out-file=cg.out ./main``

This generates the ``cg.out`` file, which contains cache profile information
that can later be viewed or analysed.

Valgrind provides a tool to analyse the output file that it generates
with the `--cachegrind-out-file=<name>` option. The tool is called
``cg_annotate``, an example invocation here:

``cg_annotate --auto=yes cg.out main.c``

This provides detailed output of which lines in the code are causing what
memory I/O operations. If certain lines have a suspiciously large number,
it provides a good point to start looking to optimize.


Conclusion
~~~~~~~~~~
Analysing memory usage is not extremely difficult - it requires a unit test
to be available, and compilation with debug symbols. Valgrind's cachegrind
takes care of the profiling itself, and the results it produces can be
viewed alongside the source code using the annotation tool.

This guide should provide a starting point to get insight into what code
is causing the most memory thrashing, and where to look for optimizing.
