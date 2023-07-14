## Introduction to Hadoop

## What is Hadoop?
* A set of open-source programs and procedures
* Used for processing big data
* Servers run applications on clusters. A Hadoop Cluster is a collection of computers working together to perform tasks.
* Not a database but an ecosystem that handles parallel jobs or processes
* Core components of Hadoop include: ***Hadoop Common***, which is an essential part of the Apache Hadoop Framework that refers to the collection of common utilities and libraries that support other Hadoop modules.
* Storage component - Hadoop Distributed File System, or ***HDFS***. It handles large data sets running on commodity hardware. A commodity hardware is low-specifications industry-grade hardware and scales a single Hadoop cluster to hundreds and even thousands.
* Processing unit of Hadoop - ***MapReduce*** processes data by splitting large amounts of data into smaller units and processes them simultaneously. For a while, MapReduce was the only way to access the data stored in the HDFS. There are now other systems like Hive and Pig.
* The last component is ***YARN***, which is short for “Yet Another Resource Negotiator.” It prepares the RAM and CPU for Hadoop to run data in batch processing, stream processing, interactive processing, and graph processing, with are stored in HDFS.

### Challenges of Hadoop
* Not good for processing transactions due to its lack of random access. 
* Not good when the work cannot be done in parallel or when there are dependencies within the data. Dependencies arise when record one must be processed before record two. 
* Not good for low latency data access. “Low latency” allows small delays, unnoticeable to humans, between an input being processed and the corresponding output providing real time characteristics. This can be especially important for Internet connections utilizing services such as trading, online gaming, and Voice Over IP.
* Not good for processing lots of small files, although there is work being done in this area such as IBM’s Adaptive MapReduce.
* Not good for intensive calculations with little data.

To deal with the shortcomings of Hadoop, new tools like ***Hive*** were built on top of Hadoop. Hive provided SQL-like query and provided users with strong statistical functions. ***Pig*** was popular for its multi query approach to cut down the number of times that the data is scanned.

### MapReduce
* Programming model used in Hadoop for processing Big Data
* Processing technique for distributed computing. Distributed computing is a system or machine with multiple components located on different machines. Each component has its own job, but the components communicate with each other to run as one system to the end user." 
* Consists of Map task and Reduce task
* Can be coded in Java, Python, R

Map takes in an input file and performs some mapping tasks by processing and extracting important data information into a ***key value pairs*** and these are the preliminary output list. Some more reorganization goes on before the preliminary output is sent to the ***Reducer***. The Reducer works with multiple map functions and aggregates the pairs using their keys to produce a final output. MapReduce keeps track of its tasks by creating unique keys to ensure that all the processes are solving the same problem. 

![](MapReduce.PNG?raw=true "How MapReduce Works")

Let us look at the framework visually. First, we have the Map step, which takes a set of data and converts it into another set of data, where individual elements are broken down into key/value pairs. The key is the name, and the value is the content. The input data is a file that is saved in the Hadoop file system called HDFS. Now let’s assume we have an input file that contains names of people, and we would like to do a word count on the unique name occurrences. First, the data is split into the following four files, each of them in key value pair and are worked on separately. For example, for the first split line for Teju and Briana, we have two key value pairs with one occurrence in each file, and it will do the same for all of key value pairs. We then have the reducer; the reducer processes the data that comes from the map. After processing, it produces a new set of outputs, which will be stored in the HDFS. The Reducer starts with shuffling. Shuffling sorts the key and a list of values in a list, for example, you will see the Key Teju and the corresponding list of values from the previous step. We will have Teju [1, 1, 1], This is because the name Teju occurred 3 times in the “Map” step. It does the same for the rest of the names, counting how many times they appeared in the “Map” step. The Reducer layer then aggregates the values in the list and saves them, then the final output is saved in an output file. 

The advantages of MapReduce is its ability to allow for a high level of parallel jobs across multiple nodes. A node is an independent computer used for processing and storing big volumes of data. In Hadoop we have two types of nodes, the ***name node*** and the ***data node***. Map reduce allows for splitting and running independent tasks in parallel by dividing each task which in turn saves time. MapReduce is very flexible and can process data that come in tabular and non-tabular forms. Therefore, MapReduce provides business value to organizations regardless of how their data is structured. It also offers support for different languages and provides a platform for analysis, data warehousing and more. 

### Hadoop Ecosystem (Ingest data -> Store data -> Process & analyze data -> Access data)

#### Ingest data
* Flume - collects aggregates, and trasfers big data
* Sqoop - transfer data between relational database and Hadoop, access database to understand the schema of the data, generate MapReduce application to import or export data

#### Store data
* HBase - a non-relational database that runs on top of HDFS, provides real time wrangling on data, stores data as indexes to allow for random and faster access to data
* Cassandra - NoSQL database desgined to have no single point of failure

#### Analyze data
* Pig - operates on the client side of a cluster, a procedural data flow language
* Hive - Used for creating reports, operates on the server side of a cluster, a declarative programming language

#### Access data 
* Impala
* Hue (Hadoop user experience) - allow you to upload, browse, and query data, run Pig Jobs and workflow, provides SQL editor for several query languages

### HDFS 
* Storage layer of Hadoop
* Splits the files into blocks, creates replicas of the blocks, and stores them on different machines
* Provides access to streaming data. Streaming means that HDFS provides a constant bitrate when transferring data rather than having the data being transferred in waves.
* Uses a command line interface to interact with Hadoop
* Key features
  * Cost efficient - storage hardware is not expensive
  * Large amounts of data - store up to petabytes of data 
  * Replication - make copies of the data on multiple machines 
  * Fault tolerant - if one machine crashes, a copy of the data can be found somewhere else and work continues
  * Scalable - one cluster can be scaled into hundreds of nodes
  * Portable - easily move accross multiple platform
* Block - minimum amount of data that can be read or written, default size is 64 MB or 128 MB.
* Node - single system which is responsible to store and process data
  * Primary node (name node)- regulates file access to the clients and maintains, manages, and assigns tasks to the secondary node
  * Secondary node (data node) - actual workers in the HDFS system and take instructions from the primary nodes
* ***Rack awareness*** - choosing data node racks that are closest to each other. A rack is the collection of about 40 to 50 data nodes using the same network switch. Improves cluster performance by reducing the network traffic. Name node keeps the rack ID information. Replication can be done through rack awareness.
* ***Replication*** - creating a copy of data block. Replication factor: number of times the data block was copied.
* 
![](Replication.PNG?raw=true)
![](Replication2.PNG?raw=true)

* HDFS allows “write once, read many” operations. This means that you cannot edit files that are already stored in HDFS, but you can append new data to them. Let us start with how the read operation works. Assuming we have a text file, the client will send a request to the primary node, which is the name node, to get the location of the data nodes containing blocks. The name node will verify that the client has the correct privileges and provide the client with the locations. A client in HDFS interacts with the primary and secondary nodes to fulfill a user's request. The client will then send a request to the closest data nodes through an FS Data Input stream object by calling the read method to read all the files. And when the client is done, the client will use the close method to end the session. Next, we will see how the write operation works. Just like in the read operation, the name node confirms that the client has the right privileges. The name node makes sure to check that the file doesn’t exist in the system. If the file already exists, the client will receive an IO exception. If the file doesn’t exist, the client receives a write permission together with the data nodes. Once the client is done, the data nodes start creating replicas and sends a confirmation to the client. Hadoop follows the concept of a primary/secondary node architecture. The primary node is the name node. The architecture is such that per cluster, there is one name node and multiple data nodes, which are the secondary nodes. Internally, a file is split into one or more blocks and these blocks are stored in a set of data nodes. The name node oversees opening, closing, renaming file operations, and mapping file blocks to the data node. The data nodes are responsible for read and write requests from the client and perform the creation, replication, and deletion of file blocks based on instructions from the name node. 

![](HDFS_Architecture.PNG?raw=true)

### Hive 
* A data warehouse software within Hadoop that is designed for reading, writing, and managing tabular-type datasets and data analysis.
* HiveQL is inspired by SQL
* Supports data cleansing and filtering depending on users' requirements

### Hive and tradisional RDBMS compared

| Traditional RDBMS        | Hive           |
|--------------------------|----------------|
|Used to maintain a Database and uses SQL|Used to maintain a data warehouse using Hive query language|
|Suited for real-time/dynamic data analysis like data sensors|Suited for static data analysis like a txt file containing names|
|Designed to read and write as many times as it needs|Designed on the methodology of write once, read many|\
|Maximum data size it can handle is terabytes|Maximum data size it can handle is petabytes|
|Enforces that the schema must verify loading data before it can proceed|Doesn't enforce the schema to verify loading data|
|Mya not always have built-in for support data partitioning|Supports partitioning (dividing the table into parts based on the values of a particular column such as date or city)|

![](Hive_Architecture.PNG?raw=true)

### HBASE
* Column-oriented non-relational database management system
* Runs on top of HDFS
* Provides a fault-tolerant way of storing sparse datasets
* Works well with real-time data and random read and write access to Big Data
* USed ofr write-heavy applications
* Linearly and modularly scalable
* Backup support for MapReduce jobs
* Provides consistent reads and writes
* Has no fixed column schema
* Easy-to-use Java API for client access
* Provides data replication across clusters

### Differences between HBase and HDFS

| HBase        | HDFS           |
|--------------------------|----------------|
|Stores data in the form of columns and rows in a table|Stores data in distributed manner across different nodes on that network|
|Allows dynamic changes|Has a rigid architecture that doesn't allow changes|
|Suitable for random writes and reads of data stores in HDFS|Suited for write once and read many times|
|Allows for storing and processing of Big Data| For storing only|

## Summary and Highlights
* Hadoop is an open-source framework for Big Data that faced challenges when encountering dependencies and low-level latency.
* MapReduce, a parallel computing framework used in parallel computing, is flexible for all data types, addresses parallel processing needs for multiple industries and contains two major tasks, “map” and “reduce.”
* The four main stages of the Hadoop Ecosystem are Ingest, Store, Process and Analyze, and Access.
* Key HDFS benefits include its cost efficiency, scalability, data storage expansion and data replication capabilities. Rack awareness helps reduce the network traffic and improve cluster performance. HDFS enables “write once, read many” operations.
* Suited for static data analysis and built to handle petabytes of data, Hive is a data warehouse software for reading, writing, and managing datasets. Hive is based on the “write once, read many” methodology, doesn’t enforce the schema to verify loading data and has built-in partitioning support.
* Linearly scalable and highly efficient, HBase is a column-oriented non-relational database management system that runs on HDFS and provides an easy-to-use Java API for client access. HBase architecture consists of HMaster, Region servers, Region, Zookeeper and HDFS. A key difference between HDFS and HBase is that HBase allows dynamic changes compared to the rigid architecture of HDFS.
