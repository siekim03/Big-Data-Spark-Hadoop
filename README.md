# Introduction to Big Data with Spark and Hadoop

## Big Data
* Generated in huge volumes, could be structured, semi-structured, or unstructured.
* Arrives continuously at enormous speed from multiple sources
* Distributed on the cloud and server farms

### Bits, bytes and more
* Bits = 0 or 1
* 8 Bits = 1 Byte
* 1024 Bytes = 1 Kilobyte (KB)
* 1024 KB = 1 Megabyte (MB)
* 1024 MB = 1 Gigabyte (GB)
* 1024 GB = 1 Terabyte (TB)
* 1024 TB = 1 Petabyte (PB)
* 1024 PB = 1 Exabyte (EB)
* 1024 EB = 1 Zettabyte (ZB)
* 1024 ZB = 1 Yottabyte (YB)

### Five V's of Big Data
* **Velocity**
  * Attributes - Batch, Close to real time, Streaming
  * Drivers - Improved connectivity and hardware 
* **Volume**
  * Attributes - Petabytes and above
  * Drivers - Increase in data sources, higher resolution sensors, scalable infrastructure
* **Variety**
  * Attributes - Data from machines, people and processes, complexity, structure, origin
  * Drivers - Mobile technologies, scalable infrastructure, resilience, fault recovery, efficient storage and retrieval
* **Varacity**
  * Attributes - Consistency and completeness, ambiguity, integrity
  * Drivers - Cost and traceability, robust ingestion, ETL mechanisms
* **Value**

### Parallel processing
***Linear processing*** is the traditional method of computing a problem where the problem statement is broken into a set of instructions that are executed sequentially till all instructions are completed successfully. If an error occurs in any one of the instructions, the entire sequence of instructions is executed from the beginning after the error has been resolved.

***Parallel processing -*** The problem statement is broken down into a set of executable instructions. The instructions are then distributed to multiple execution nodes of equal processing power and are executed in parallel. Since the instructions are run on separate execution nodes, errors can be fixed and executed locally independent of other instructions. Advantages of parallel processing:
* Reduce processing time
* Less memory and compute requirements needed
* Flexibility - execution nodes can be added or removed from the processing network depending on the problem complexity

### Data Scaling
Increasing the capacity of a single node as a means of increasing capacity is called ***scaling up***. A better strategy, or at least the one most people ultimately choose, is to scale out or to ***scale horizontally***. This simply means adding additional nodes with the same capacity until the problem is tractable. The individual nodes arranged in this way are called a ***computing cluster***. Compute clusters can solve problems that are known as “embarrassingly parallel” calculations. These are the kind of workloads that can easily be divided and run independent of one another. If any one process fails, it has no impact on the others and can easily be rerun. 

An example would be to, say, change the date format in a single column of a large dataset that has been split into multiple smaller chunks that are stored in different nodes of the cluster. Sometimes, sorting a large data set adds significant complexity to the process. Now, the multiple computations must coordinate with one another because each process needs to be aware of the state of its peer processes in order to complete the calculation. This requires sending messages across a network to each other or writing them to a file system that is accessible to all processes on the cluster. The level of complexity increases significantly, because you are basically asking a cluster of computers to behave as a single computer. Most calculations in enterprise environments are considered “embarassingly parallel with some not so easy” calculations. While this statement is true to varying degrees it has guided the design of underlying frameworks. 

In the Hadoop ecosystem, the concept of “bringing compute to the data” is a central idea in the design of the cluster. The cluster is designed in a way that computations on certain pieces, or partitions, of the data will take place right at the location of the data when possible. The resulting output will also be written to the same node. Computers break, outages happen, and you need to be prepared. In such cases, fault tolerance comes into play. Fault tolerance refers to the ability of a system to continue operating without interruption when one or more of its components fail. This works for Hadoop primary data storage system (HDFS) and other similar storage systems (like S3 and object storage), a system like the one we showcase here. Consider the first 3 partitions of a data set labelled P1, P2, and P3, which reside on the first node. In this system, copies of each of these data partitions are also stored on other locations or nodes within the cluster. If the first node ever goes down, you can add a new node to the cluster and recover the lost partitions by copying data from one of the other nodes where copies of P1, P2, and P3 partitions are stored. Clearly, this is an extraordinarily complex maintenance process, but the Hadoop filesystem is a robust and time-tested framework. It can be reliable to 5 9s (99.999%). 

### Big Data Tools and Ecosystems


