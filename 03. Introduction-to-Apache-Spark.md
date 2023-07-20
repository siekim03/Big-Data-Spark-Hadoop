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

### Resilient Distributed Dataset
* Spark primary data abstraction
* A fault-tolerant collection of elements
* Partitioned across the nodes of the cluster
* Capable of accepting parallel operations
* Immutatable (always recoverable)
* Supported files types: Text, SequenceFiles, Avro, Parquet, Hadoop input formats
* Supported file formats: Local, Cassandra, HBase, HDFS, Amazon S3, and others, SQL and NoSQL
* Can persist or cache datasets in memory across operations, which speeds iterative operations

## Creating an RDD in Spark
* Use an external or local file from Hadoop-supported file system
* Create a RDD from list in Python / Scala
`data = [1, 2, 3, 4, 5]`
`disData = sc.parallelize(data)`
* Apply a transformation on an existing RDD to create a new RDD
  
### RDD and Parallel Programming
* We can create an RDD by parallelizing an array of objects, or by splitting a dataset into partitions
* Spark runs one task for each partition of the cluster

### Scale out / Data Parallelism in Apache Spark
Apache Spark components: 
* Data storage, HDFS, and other formats
* Compute interface, API: Scala, Java, Python
* Management distributed computing standalone, Mesos, YARN, and Kubernetes

![](SparkArchitecture.PNG?raw=true)
![](SparkScaleUp.PNG?raw=true)

### Summary
* Apache Spark architecture consists of three main pieces components data, compute input, and management. 
* The fault-tolerant Spark Core base engine performs large-scale parallel and distributed data processing, manages memory, schedules tasks, and houses APIs that define RDDs.
* The Spark driver program communicates with the cluster and then distributes RDDs among worker nodes.

### Spark SQL and DataFrames
* SparkSQL is a Spark module for structured data processing.
* Spark SQL provides a programming abstraction called DataFrames and can also act as a distributed SQL query engine.
* DataFrames are conceptually equivalent to a table in a relational database or a data frame in R/Python, but with richer optimizations.

![](SparkSQL_DFAPI.PNG?raw=true)
