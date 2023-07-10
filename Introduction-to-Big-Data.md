# Introduction to Big Data with Spark and Hadoop

## Big Data
* Generated in huge volumes, could be structured (SQL, spreadsheets), semi-structured (XML, JSON), or unstructured.
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
#### Categories of Big Data tooling
1. **Data Technologies** - Hadoop, HDFS, Spark, MapReduce, Cloudera, and Databricks
2. **Analytics and Visualization** - Tableau
3. **Business intelligence** - Cognos, Oracle, PowerBI, Buiness Objects
4. **Cloud Providers** - AWS, IBM, GCP, Oracle
5. **NoSQL Databases** - Store information in JSON documents instead of relational tables. Include pure document databases, key-value stores, wide-column databases, and graph databases. Examples include MongoDB, CouchDB, Cassandra, Redis
6. **Programming tools** - R, Python, SQL, Scala

### Open source in Big Data 
The biggest component of big data is, by far, the **_Hadoop_** project and its three main components: ***MapReduce***, ***The Hadoop File System (HDFS)***, and ***The resource manager (YARN)***. MapReduce is a framework that allows code to be written to run at scale on a Hadoop cluster. It is still used, but not as much as more modern Big Data computation frameworks like ***Apache Spark***. HDFS is the file system that stores and manages Big Data files. It manages all of the issues around large and distributed datasets, including resilience and partitioning. It is still a mainstay of the industry. 70% of the world’s Big Data resides on HDFS. More modern approaches to distributed storage, such as S3 and object storage, are coming into use, but they are based on the design principles of HDFS. YARN is the resource manager that comes with Hadoop, and it is the default resource manager for many Big Data applications, including HIVE and Spark. It is one of the most robust resource managers in use today, but more modern container-based resource managers (like Kubernetes) are slowly becoming the new de facto standards. Concluding, these are the main components of the Hadoop ecosystem, and most big data applications are built on top of them. 

The array of big data applications available to the user is dizzying. They all build upon the basic Hadoop framework or interact with it in some way, however. Frameworks like Hive and Spark support lots of ETL (Extract, Transform, Load) and computation tasks on Hadoop systems. Some systems that integrate tightly with the Hadoop ecosystem are: Apache Hbase, which is a large NoSQL datastore. It manages storage and computation resources outside of the Hadoop ecosystem but often resides on the same cluster. Open-source packages like the Hortonworks Data Platform (HDP) provide a set of big data tools that are already configured to work together, and include most of the important open source packages (Hadoop, Spark, Hive, Hbase, and others).

## Summary 
* Personal assistants like Siri, Alexa and Google Now, use Big Data and IoT to gather data and devise answers.
* Big Data Analytics helps companies gain insights from the data collected by IoT devices.
* Big Data requires parallel processing on account of massive volumes of data that are too large to fit on any one computer.
* "Embarrassingly parallel” calculations are the kinds of workloads that can easily be divided and run independently of one another. If any single process fails, that process has no impact on the other processes and can simply be re-run.
* Open-source projects, which are free and completely transparent, run the world of Big Data and include the Hadoop project and big data tools like Apache Hive and Apache Spark.
* The Big Data tool ecosystem includes the following six main tooling categories: data technologies, analytics and visualization, business intelligence, cloud providers, NoSQL databases, and programming tools.


