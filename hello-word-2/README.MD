## MPI_INIT()

+ During `MPI_Init`, all of MPI's global and internal variables are constructed. For example, a communicator is formed around all of the processes that were spawned, and unique ranks are assigned to each process. Currently, MPI_Init takes two arguments that are not necessary, and the extra parameters are simply left as extra space in case future implementations might need them.
+ `MPI_Comm_size` returns the size of a communicator.
+ `MPI_Comm_rank` returns the rank of a process in a communicator. Each process inside of a communicator is assigned an incremental rank starting from zero. The ranks of the processes are primarily used for identification purposes when sending and receiving messages.
+ `MPI_COMM_WORLD` (which is constructed for us by MPI) encloses all of the processes in the job, so this call should return the amount of processes that were requested for the job.
+ `MPI_Get_processor_name` obtains the actual name of the processor on which the process is executing.
+ `MPI_Finalize` is used to clean up the MPI environment. No more MPI calls can be made after this one.
