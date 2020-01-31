# Threads in java

## The Producer-Consumer problem
[Producer Consumer Full Explanation and Solution](https://dzone.com/articles/the-evolution-of-producer-consumer-problem-in-java)

![Producer-Consumer-Queue_buffer](https://interviewsansar.com/wp-content/uploads/2014/09/blocking-queue-1024x256.png)

### The problem

There are two processes, a producer and a consumer, that share a common buffer with a limited size.  
The producer “produces” data and stores it in the buffer, and the consumer “consumes” the data, removing it from the buffer.  
Having two processes that run in parallel, we need to make sure that the producer will not put new data in the buffer when the buffer is full and the consumer won’t try to remove data from the buffer if the buffer is empty.

 