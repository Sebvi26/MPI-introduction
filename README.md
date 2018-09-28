# MPI-introduction
this is a parallelization introduction with MPI

first, we got to download the MPI library
if you work on ubuntu you can type on terminal:

`sudo apt-get install libcr-dev mpich mpich-doc
`
now you are ready to start.

1. why parallelize?

when you write a programme, a code, a script, etc. as usual, when you execute it, each one of the instructions you made are executed one after another. even though your machin have 8 cores, the 8 at the same time are working on just one instruction.

the first step is to analyze your code,decompose your code into tasks that can be executed concurrently. for example:

![fig9](https://user-images.githubusercontent.com/29667047/46233080-04720900-c337-11e8-97f8-dfb9887dcdf5.png)


in this case, we can calculate the area under the curve till any t. normally we do it in just one procces, using all our cores. but if we divide our exercise in 8 diferent integral, ofcourse the end of the first is the start of second ,and send each integral to each core and then bunch our processes results,we can execute it many times faster. 


### program-1 

```
#include <stdlib.h>
#include <stdio.h>
#include <mpi.h>
//libraries
int main(int argc, char * argv[] ){

  int rank, procs_size;
//procs_size is the number of processes in which i divide my program
// rank is the name of each proces, kind of a count: 0, 1, 2, 3 (if i have 4 processes)
  MPI_Init( &argc, &argv );

  // This function returns the number of processes in my communicator MPI_COMM_WORLD
  MPI_Comm_size( MPI_COMM_WORLD, &procs_size );
  // This function returns the ID of a given process in the MPI_COMM_WORLD comm
  MPI_Comm_rank( MPI_COMM_WORLD, &rank );

  fprintf( stderr, "\nHello World! I am %d of %d processes", rank, procs_size );

  MPI_Finalize();
  return 0;
}
