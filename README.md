# Combining-Distribution-and-Multithreading

Processes and Threads are the Fundamental blocks of distributed computing:
Within a process you can create multiple threads (JVM is one process)

Multithreaded Servers:
As an extension to the servers that we studied in client-server programming. As a motivating example, we studied the timeline for  a single request sent to a standard sequential server, which typically consists of four steps :
A) accept the request.
B) ectract the necessary information from the request.
C) Read the file.
D) Send the file.

In practice step c) is usually the most time consuming step in this sequence. However threads  can be used to reduce this bottleneck.
In particular, after step A) is performed, a new thread can be created to process step B) C) and D) for a given request. In this way, it is possible to process multiple requests simultaneously because they are executing in different threads.


One challenge of following this approach literally is that there is a significant overhead in creating and starting a java thread.
However, since there is usually an upper bound on the number of threads that can be efficiently utilized within a node(often linited by number of cores or hardware context), it is wasteful to create more threads than that number. There are two approaches that are commonly taken to address this challenge in java applications. One is to use a thread pool, so that threads can be reused acroos multiple requests instead of creating new thread for each request. Another is to use lightweight tasking (e.g. as in Java ForkJoin framework) which execute on a thread pool with a bounded number of threads, and offer the advantage that the overhead of task creation is significantly smaller than that of thread creation. 
