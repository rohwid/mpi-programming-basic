As covered in the previous lesson, the `MPI_Recv` operation takes the address of an `MPI_Status` structure as an argument (which can be ignored with `MPI_STATUS_IGNORE`). If we pass an `MPI_Status` structure to the `MPI_Recv` function, it will be populated with additional information about the receive operation after it completes. The three primary pieces of information include:

+ The rank of the sender. The rank of the sender is stored in the `MPI_SOURCE` element of the structure. That is, if we declare an `MPI_Status` stat variable, the rank can be accessed with `stat.MPI_SOURCE`.
+ The tag of the message. The tag of the message can be accessed by the `MPI_TAG` element of the structure (similar to `MPI_SOURCE`).
+ The length of the message. **The length of the message does not have a predefined element in the status structure**. Instead, we have to find out the length of the message with `MPI_Get_count`.

    MPI_Get_count(
        MPI_Status* status,
        MPI_Datatype datatype,
        int* count)

In `MPI_Get_count`, the user passes the `MPI_Status` **structure, the datatype of the message, and count is returned**. The count variable is the total number of datatype elements that were received.

Why would any of this information be necessary? It turns out that `MPI_Recv` can take `MPI_ANY_SOURCE` for the rank of the sender and `MPI_ANY_TAG` for the tag of the message. For this case, the `MPI_Status` **structure is the only way to find out the actual sender and tag of the message**. Furthermore, `MPI_Recv` is not guaranteed to receive the entire amount of elements passed as the argument to the function call. Instead, it receives the amount of elements that were sent to it (and returns an error if more elements were sent than the desired receive amount). The `MPI_Get_count` function is used to determine the actual receive amount.
