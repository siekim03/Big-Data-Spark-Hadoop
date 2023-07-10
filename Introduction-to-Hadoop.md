## Introduction to Hadoop

## What is Hadoop?
* A set of open-source programs and procedures
* Used for processing big data
* Servers run applications on clusters. A Hadoop Cluster is a collection of computers working together to perform tasks.
* Not a database but an ecosystem that handles parallel jobs or processes
* The core components of Hadoop include: Hadoop Common, which is an essential part of the Apache Hadoop Framework that refers to the collection of common utilities and libraries that support other Hadoop modules.
* There is a storage component called Hadoop Distributed File System, or ***HDFS***. It handles large data sets running on commodity hardware. A commodity hardware is low-specifications industry-grade hardware and scales a single Hadoop cluster to hundreds and even thousands. The next component is MapReduce which is a processing unit of Hadoop and an important core component to the Hadoop framework.
* ***MapReduce*** processes data by splitting large amounts of data into smaller units and processes them simultaneously. For a while, MapReduce was the only way to access the data stored in the HDFS. There are now other systems like Hive and Pig.
* The last component is ***YARN***, which is short for “Yet Another Resource Negotiator.” YARN is a very important component because it prepares the RAM and CPU for Hadoop to run data in batch processing, stream processing, interactive processing, and graph processing, with are stored in HDFS.

### Challenges of Hadoop
* Not good for processing transactions due to its lack of random access. 
* Not good when the work cannot be done in parallel or when there are dependencies within the data. Dependencies arise when record one must be processed before record two. 
* Not good for low latency data access. “Low latency” allows small delays, unnoticeable to humans, between an input being processed and the corresponding output providing real time characteristics. This can be especially important for Internet connections utilizing services such as trading, online gaming, and Voice Over IP.
* Not good for processing lots of small files, although there is work being done in this area such as IBM’s Adaptive MapReduce.
* Not good for intensive calculations with little data.

To deal with the shortcomings of Hadoop, new tools like ***Hive*** were built on top of Hadoop. Hive provided SQL-like query and provided users with strong statistical functions. Pig was popular for its multi query approach to cut down the number of times that the data is scanned. In this video you learned that: Hadoop is an open-source frame framework for Big Data The core components of Hadoop are HDFS, MapReduce, YARN, and Hadoop Common The drawbacks of Hadoop outweighed the benefits.
