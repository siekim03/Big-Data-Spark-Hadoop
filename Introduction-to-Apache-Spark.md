### Apache Spark Attributes 

* Spark is an open source in-memory application framework for distributed data processing and iterative analysis on massive data volumes. ***In-memory*** here means that operations happen within the memroy or RAM.
* Primarily written in Scala and runs on Java virtual machines (JVMs)
* Supports a computing framework for large sale data processing and analytics
* Provides parallel and distributed processing, scalability and fault tolerance on commodity hardware.
* Enables programming flexibility with easy-to-use Python, Scala, and Java APIs.
* Traditional approach of creating MapReduce jobs for complex jobs, interactive query, and online event-hub processing involves lots of (slow) disk I/O. Apark Spark solved the problem by keeping more data in-memory with a new distributed execution engine

### Distributed Computing
* A group, or cluster, of computers working together to appear as one system to the end user.
* Parallel computing processors access shared memory, whereas distributed computing processors usually have their own private or distributed memory

### Distributed Computing Benefits
* **Scalability** and modular growth - distributed systems are inherently scalable as they work across multiple machines and scale horizontally. A user can add additinal machines to handle the increasing workload instead of repeatedly updating a single system, with virtually no cap for scalability.
* **Fault tolerance and redundancy**

### Spark and Big Data 

|Data Engineering        |Data science and Machine Learning|
|:----------------------:|:---------------------------------:|
|Core Spark engine <br> Clusters and executors <br> Cluster management <br> SparkSQL <br> Catalyst Tungsten DataFrames|SparkML <br> DataFrames <br> Streaming|

### Lambda functions and Spark
* Spark parallelizes computations using the lambda calculus
* All functional Spark programs are inherently parallelizable