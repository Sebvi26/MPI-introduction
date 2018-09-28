# MPI-introduction
this is a parallelization introduction with MPI

first, we got to download the MPI library
if you work on ubuntu you can type on terminal:
`sudo apt-get install libcr-dev mpich mpich-doc
`
now you are ready to start.

1. why parallelize?

when you write a programme, a code, a script, etc. as usual, when you execute it, each one of the instructions you made are executed one after another. even though your machin have 8 cores, the 8 at the same time are working on just one instruction.

the first step is to analyze your code,decompose your code into tasks that can be executed concurrently
