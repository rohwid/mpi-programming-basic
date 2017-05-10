# MPI (Message-Passing Interface)

## Library Installation

This project refer to the chapter 3 in [An Introduction to Parallel Programming](https://www.elsevier.com/books/an-introduction-to-parallel-programming/pacheco/978-0-12-374260-5) book by Peter Pacheco.

Installing MPI package:

    $ ./install_mpi

## Compile project

To compile this prjoect:

    $ make all

To clean compilation project:

    $ make clean

## Run

To run this project and set the number of processes:

    $ ./exec

## Main key
+ **Process = world_rank**
+ **Location = world_size**

## My Log

Ignore this, this section only common knowledge about what i've found when search this topic.

+ [OpenMPI vs Mpich](http://stackoverflow.com/questions/2427399/mpich-vs-openmpi).
+ [MPI (Parallel Computing) and AMQP (Distributed Computing)](http://stackoverflow.com/questions/3842300/can-message-oriented-middleware-be-used-instead-of-mpi-to-coordinate-distributed).
+ [Analyze your needs](http://stackoverflow.com/questions/6756630/python-openmpi-vs-rabbitmq).
