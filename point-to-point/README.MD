## Parallelization of the random walking problem

Step:
+ Splitting the domain across processes.
+ The random walk problem has a **one-dimensional domain of size Max - Min + 1** (since Max and Min are inclusive to the walker).
+ Assuming that walkers can only take integer-sized steps, we can easily partition the domain into near-equal-sized chunks across processes.
+ For example, if Min is 0 and Max is 20 and we have four processes.
+ The first three processes own five units of the domain while the last process takes the last five units plus the one remaining unit.
+ The first three processes own five units of the domain while the last process takes the last five units plus the one remaining unit.
+ Once the domain has been partitioned, the application will initialize walkers.
+ As explained earlier, a walker will take S walks with a random total walk size.
+ For example, if the walker takes a walk of size six on process zero (using the previous domain decomposition), the execution of the walker will go like this:
  * The walker starts taking incremental steps. When it hits value four, however, it has reached the end of the bounds of process zero. Process zero now has to communicate the walker to process one.
  * Process one receives the walker and continues walking until it has reached its total walk size of six. The walker can then proceed on a new random walk.
