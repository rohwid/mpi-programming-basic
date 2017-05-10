## Overview of sending and receiving with MPI

MPI's send and receive calls operate in the following manner. First, process A decides a message needs to be sent to process B. Process A then packs up all of its necessary data into a buffer for process B. These buffers are often referred to as envelopes since the data is being packed into a single message before transmission (similar to how letters are packed into envelopes before transmission to the post office). After the data is packed into a buffer, the communication device (which is often a network) is responsible for routing the message to the proper location. The location of the message is defined by the process's rank.

Even though the message is routed to B, process B still has to acknowledge that it wants to receive A's data. Once it does this, the data has been transmitted. Process A is acknowledged that the data has been transmitted and may go back to work.

Sometimes there are cases when A might have to send many different types of messages to B. Instead of B having to go through extra measures to differentiate all these messages, MPI allows senders and receivers to also specify message IDs with the message (known as tags). When process B only requests a message with a certain tag number, messages with different tags will be buffered by the network until B is ready for them.

+ `MPI_Send` sends the exact count of elements

`MPI_Send` example:

    MPI_Send(
        void* data,
        int count,
        MPI_Datatype datatype,
        int destination,
        int tag,
        MPI_Comm communicator)

+ `MPI_Recv` will receive at most the count of elements

`MPI_Recv` example:

    MPI_Recv(
        void* data,
        int count,
        MPI_Datatype datatype,
        int source,
        int tag,
        MPI_Comm communicator,
        MPI_Status* status)

## Elementary MPI datatypes
The `MPI_Send` and `MPI_Recv` functions utilize MPI Datatypes as a means to specify the structure of a message at a higher level. For example, if the process wishes to send one integer to another, it would use a count of one and a datatype of MPI_INT. The other elementary MPI datatypes are listed below with their equivalent C datatypes.

| MPI datatype           | C equivalent           |
|------------------------|------------------------|
| MPI_SHORT	             | short int              |
| MPI_INT                | int                    |
| MPI_LONG               | long int               |
| MPI_LONG_LONG          | long long int          |
| MPI_UNSIGNED_CHAR      | unsigned char          |
| MPI_UNSIGNED_SHORT     | unsigned short int     |
| MPI_UNSIGNED           | unsigned int           |
| MPI_UNSIGNED_LONG      | unsigned long int      |
| MPI_UNSIGNED_LONG_LONG | unsigned long long int |
| MPI_FLOAT              | float                  |
| MPI_DOUBLE             | double                 |
| MPI_LONG_DOUBLE        | long double            |
| MPI_BYTE               | char                   |

## Program explanation

`MPI_Comm_rank` and `MPI_Comm_size` are first used to **determine the world size along with the rank of the process**. Then process zero initializes a number to the value of negative one and sends this value to process one. As you can see in the else if statement, process one is calling `MPI_Recv` to receive the number. It also prints off the received value. Since we are sending and receiving exactly one integer, each process requests that one MPI_INT be sent/received. Each process also uses a tag number of zero to identify the message. The processes could have also used the predefined constant MPI_ANY_TAG for the tag number since only one type of message was being transmitted.
