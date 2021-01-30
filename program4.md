Program 4
---------
In this assignment, you will implement and experiment with various searching algorithms.

Binary Heap
-----------
Parts of an array backed binary minimum heap have been implemented for you. Complete the
implementation by implementing the following functions:

- `sink(...)`
- `swim(...)`
- `insert(...)`
- `removeMinimum(...)`

Note that this binary heap implementation uses a 1-based array indexing system similar to the type
presented in class. When implementing your binary heap, you can make use of the `resize(...)`
function to grow or shrink the array backing the binary heap to a given capacity. Remember that when
growing the array, we want to double in size. However, when shrinking the array, we only want to do
so when the array is 1/4 used, rather than 1/2 used. This avoids avoid a possible worst case of
repeatedly growing and shrinking as discussed in class.

The file(s) you will need for this exercise are:

- `java/src/edu/berkeley/cs/util/MinHeap.java`

Priority Queues
---------------
Your company builds and operates the world's fastest supercomputer and sells access to top research
firms and universities for them to conduct various experiments (jobs). The company charges a flat
rate per job run. In exchange, the research firms demand full, dedicated access to the entire
supercomputer's resources during the time in which they run their jobs. Although each experiment
takes a different amount of time to complete, it is known roughly how long a job will take to
complete before launching it.

To better understand the problem, we assign some vocabulary to some concepts:

- Job processing time: the time it will take a given job to complete when run on the supercomputer
- Job waiting time: the time a job waits for other jobs to complete before it can run
- Job turnaround time: job processing time + job waiting time
- Total turnaround time: the sum of the turnaround time of all jobs

Regardless of what order the jobs run in, the sum of their processing time will be the same. There
isn't much we can do about that. However, your company can provide a better experience by reducing a
job's waiting time as much as possible, thereby reducing its total turnaround time and getting
results back to the client as fast as possible. The company tasks you with finding the best ordering
of jobs such that job waiting time, and thereby total turnaround time, is kept as small as possible.
You decide to experiment with the following scheduling algorithms to find the best one.

For this task, we can assume that research firms only care that they get their results back at some
point in the future and have no hard deadlines of when their jobs must be completed by. Furthermore,
we can assume that no job depends on another job to be run before it in order to run successfully.

### First In First Out (FIFO)
Jobs are processed in the arriving order. The job at the front of the queue is served until it has
completed. That job is then removed from the queue. The next job at the front of the queue is served
until it has completed and then it is removed from the queue. This process is continued until the
queue is empty.

### Shortest Job First
The job with the shortest processing time is processed first until it has completed. That job is
then removed from the queue. The next job with the smallest processing time is then served until it
has completed and then it is removed from the queue. This process is continued until the queue is
empty.

### Round Robin (RR)
Jobs are processed using a fixed time slice. The jobs are initially kept in a queue based on the
order of arrival. The job at the front of the queue is removed and served similar to the FIFO
algorithm. However, unlike the FIFO algorithm, each job is served up to the predefined slice of
time. If the job can be completed within the allotted time, it is fully served and removed from the
queue. If the job cannot be completed in the allotted time, it is served for the allotted time and
then added to the end of the queue to be served later for the remaining time. This process is
continued until the queue is empty.

The total turnaround time is the total time a job spends in the system: processing time + waiting
time (time spent in the queue). For example, if the workload is 15 units of time, but the job spends
50 units of time in queue, waiting to be processed, then the total turnaround time is equal to 65
units.

Implement each scheduling algorithm in its respective file. The first in first out scheduler can be
implemented with a linked list or a queue. The shortest job first scheduler should be implemented
with a priority queue, and the round robin scheduler should be implemented with a queue. Some of
this data structure selection has been done for you already. The directory you will be working in
 for this exercise is:

- `java/src/edu/berkeley/cs/app/scheduling`

Tree Map
--------
One of the methods to implement a symbol table is to use a binary search tree. Parts of a `TreeMap`
backed by a binary search tree have been implemented for you. Complete the implementation by
implementing the following methods:

- `put(...)`
- `get(...)`
- `min(...)`
- `max(...)`
- `deleteMax(...)`
- `deleteMin(...)`

You may implement these functions either iteratively or recursively. An example recursive
implementation of Hibbard deletion is implemented in `delete(...)`. The same could have been done
iteratively.

The file(s) you will need for this exercise are:

- `java/src/edu/berkeley/cs/util/TreeMapjava`

Summable Tree
-------------
Given a binary search tree of integer keys and a target sum, we want to determine if there is a path
from the root of the tree to a leaf node such that the integers along the path, when summed
together, equal the target sum. For example, suppose we have the following binary search tree as
input.

              ┌───┐
              │ 4 │
              └─┬─┘
         ┌──────┴──────┐
       ┌─┴─┐         ┌─┴─┐
       │ 2 │         │ 6 │
       └─┬─┘         └─┬─┘
      ┌──┴───┐      ┌──┴───┐
    ┌─┴─┐  ┌─┴─┐  ┌─┴─┐  ┌─┴─┐
    │ 1 │  │ 3 │  │ 5 │  │ 7 │
    └───┘  └───┘  └───┘  └───┘

If the target sum were 15, we have a path (4, 6, 5) whose sum equals the target sum. However, if the
target sum were 16 instead, there is no path to a leaf node which equals the target sum. Implement
an algorithm that determines if there is such a path, as defined above, for a given binary search
tree and a target sum. You don't need to return the path itself.

The file(s) you will need for this exercise are:

- `java/src/edu/berkeley/cs/app/SummableTree.java`

Grading
-------
Tests have already been written to help you ensure that your code works. The following commands will
be used to test and grade your code:

    $ bazel test java:program4
