## Program explanation

This example is meant to be executed with only two processes. The processes first determine their partner with some simple arithmetic. A `ping_pong_count` is initiated to zero and it is incremented at each ping pong step by the sending process. As the `ping_pong_count` is incremented, the processes take turns being the sender and receiver. Finally, after the limit is reached (ten in my code), the processes stop sending and receiving.
