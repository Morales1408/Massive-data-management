# Chapter N.6 
----------------

### 1. _How does the name "partition" changes according to the technology you are using?_
What the book names "partition" is challed _shard_ in MongoDB, Elastichsearch, and SolrCloud; it's known as a _region_ in HBase, a _tablet_ in Bigtable, a _vnode_ in Cassandra and Riak, and a _vBucket_ in Couchbase. 

### 2. _Mention the main reason for wanting to partition data_
The main reason for wanting to partition data is _scalability_. Different partitions can be placed on different nodes in a shared-nothing cluster. Thus, a large dataset can be distributed across many disks, and the query load can be distributed across many processors. 

### 3. _What's the difference between systems that are designed for transactional workload and the ones that are designed for analytics?_
The difference affects how the system is tuned, but the fundamentals of partitioning apply to both kinds of workloads. 

### 4. _What's te reason for partitioning to be combined with replication?_
So that copies for ach partition are stored in multiple nodes. This means that, even though each record belongs to exactly one partition, it may still be stored on several different nodes for fault tolerance. 

### 5. _What's the aim of partitioning and how this affects the performance?_ 
THe goal with partitioning is to spread the data and the query load evenly across nodes. If every node takes a fair share, then -in theory- 10 noes should be able to handle 10 times as much data and 10 times the read and write throughtput of a single node.

### 6. _Why many distributed datastores use a hash function to determine the partition for a given key?_
The main reasn behind that is because of the risk of skew and hot spots. 

### 7. _What does a good has function does?_
A good hash function takes skewed data and makes it uniformly distributed.

### 8. _What is consistent hashing?_ 
Consistent hashing is a way of evenly distribuiting load across an internet-wide system of caches such as a content delivery network. 

### 9. _Why some key-value stores have started adding secondary indexes?_
Because they are so useful for data modeling. And finally, secondary indexes are the reason of existing of search servers such as Solr and Elastichsearch. 

### 10. _What's the advantage of a global index over a document-partitioned intex?_
Is that it can make reads more efficient: Rather than doing scatter/gather over all partitions, a client only needs to make a request to the partition containing the term that it wants.
