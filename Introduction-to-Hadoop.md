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

Let us look at the framework visually. First, we have the Map step, which takes a set of data and converts it into another set of data, where individual elements are broken down into key/value pairs. The key is the name, and the value is the content. The input data is a file that is saved in the Hadoop file system called HDFS. Now let’s assume we have an input file that contains names of people, and we would like to do a word count on the unique name occurrences. First, the data is split into the following four files, each of them in key value pair and are worked on separately. For example, for the first split line for Teju and Briana, we have two key value pairs with one occurrence in each file, and it will do the same for all of key value pairs. We then have the reducer; the reducer processes the data that comes from the map. After processing, it produces a new set of outputs, which will be stored in the HDFS. The Reducer starts with shuffling. Shuffling sorts the key and a list of values in a list, for example, you will see the Key Teju and the corresponding list of values from the previous step. We will have Teju [1, 1, 1], This is because the name Teju occurred 3 times in the “Map” step. It does the same for the rest of the names, counting how many times they appeared in the “Map” step. The Reducer layer then aggregates the values in the list and saves them, then the final output is saved in an output file. The advantages of MapReduce is its ability to allow for a high level of parallel jobs across multiple nodes. A node is an independent computer used for processing and storing big volumes of data. In Hadoop we have two types of nodes, the name node and the data node. Map reduce allows for splitting and running independent tasks in parallel by dividing each task which in turn saves time. MapReduce is very flexible and can process data that come in tabular and non-tabular forms. Therefore, MapReduce provides business value to organizations regardless of how their data is structured. It also offers support for different languages and provides a platform for analysis, data warehousing and more. MapReduce has a couple of use cases and here we have some of them displayed. MapReduce can be used for social media platforms like LinkedIn and Instagram to analyze who visited, viewed, and interacted with your profile posts. Map reduce is used by Netflix to recommend movies based on what you have watched in the past by using the user's interests. It is also used in financial institutions like banks and credit card companies to flag and detect anomalies in user transactions. It can also be used in the advertisement industry to understand a user’s behavior by how they engage with ads. Google ads work by using MapReduce to understand the engagement of users with an ad.



