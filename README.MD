# MPI (Message-Passing Interface)

## Library Installation

This project refer to the chapter 3 in [An Introduction to Parallel Programming](https://www.elsevier.com/books/an-introduction-to-parallel-programming/pacheco/978-0-12-374260-5) book by Peter Pacheco.

Installing MPI package:

    $ ./install_mpi

## Core of MPI Programming

During `MPI_Init`, all of MPI's global and internal variables are constructed. For example, a communicator is formed around all of the processes that were spawned, and unique ranks are assigned to each process. Currently, `MPI_Init` takes two arguments that are not necessary, and the extra parameters are simply left as extra space in case future implementations might need them.

`MPI_Init` example:

    MPI_Init(
        int* argc,
        char*** argv)

`MPI_Comm_size` returns the size of a communicator.

`MPI_Comm_size` example:

    MPI_Comm_size(
        MPI_Comm communicator,
        int* size)

`MPI_Comm_rank` returns the rank of a process in a communicator. Each process inside of a communicator is assigned an incremental rank starting from zero. The ranks of the processes are primarily used for identification purposes when sending and receiving messages.

`MPI_Comm_rank` example:

    MPI_Comm_rank(
        MPI_Comm communicator,
        int* rank)

`MPI_COMM_WORLD` (which is constructed for us by MPI) encloses all of the processes in the job, so this call should return the amount of processes that were requested for the job.

`MPI_Get_processor_name` obtains the actual name of the processor on which the process is executing.


`MPI_Comm_rank` example:

    MPI_Get_processor_name(
        char* name,
        int* name_length)

`MPI_Finalize` is used to clean up the MPI environment. No more MPI calls can be made after this one.

    MPI_Finalize()

## Compile project

To compile this prjoect:

    $ make all

To clean compilation project:

    $ make clean

## Run

To run the project and set the number of processes:

    $ ./exec

To run the project in multiple nodes and set the number of processes. You must follow this [step first](http://mpitutorial.com/tutorials/running-an-mpi-cluster-within-a-lan/), to setup the NFS and synchronize all the nodes.

+ Copy executable file (ex: hello_word) to nfs directory (ex: cloud) to sync with all nodes:

        $ cp hello_word ~/cloud
        $ ./exec-multi hello_word

then the response in the number of processes or `MPI_Comm_size`.

## Main key to remember
+ **Process = world_rank**
+ **Location = world_size**

## My Log

Ignore this, this section only common knowledge about what i've found when search this topic.

+ [OpenMPI vs Mpich](http://stackoverflow.com/questions/2427399/mpich-vs-openmpi).
+ [MPI (Parallel Computing) and AMQP (Distributed Computing)](http://stackoverflow.com/questions/3842300/can-message-oriented-middleware-be-used-instead-of-mpi-to-coordinate-distributed).
+ [Analyze your needs](http://stackoverflow.com/questions/6756630/python-openmpi-vs-rabbitmq).
