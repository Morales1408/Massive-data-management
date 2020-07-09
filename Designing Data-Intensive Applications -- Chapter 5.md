# Chapter N.5 
-----------

### 1. _Mention some good reasons you might have for replicating your data_
+ To keep data geographically close to your users
+ To allow the system to continue working even if some of its parts have failed
+ To scale out the number of machines that can serve read queries

### 2. _Mention the two ways of distributing data across multiple nodes_
+ Partitioning: Splitting a big database into smaller subsets called partitions, to that different partitions can be assigned to different nodes.
+ Replication: Keeping a copy of the same data on several different nodes, potentially in different locations.

### 3. _What are the main three algorithms discussed in the book for replicating changes between nodes?_
Single-leader, multi-leader and leaderless replication. 

### 4. _What is the solution that guarantees that all the data ends up on all the replicas?_
+ One of the replicas is designated the _leader_. When clients want to write to the database, they must send their requests to the leader, which first writes the nre data to its local storage. 
+ The other replicas are known as _followers_. Whenever the leader writes new data to its local storage, it also sends the data change to all of its followers as part of a replication log or change stream. Each followwer takes the log from the leader and updates its local copy of the database accordingly, b applying all writes in the same order as they were processed on the leader. 
+ When a client wants to read from the database, it can query either the leader or any of the followers. Howeber, writes are only accepted on the leader. 

### 5. _Describe the synchronous and asynhronous replication_
**Synchronous:** The leader waits until the follower 1 has confirmed that it received the write before reporting success to the user, and before making the write visible to other clients. 

**Asynchronous:** The leader sends the message, but doesn't wait for a response from the follower. 

### 6. _Metion one advantage and one disadvantage of syncronous replication_
The  advantage  of  synchronous  replication  is  that  the  follower  is  guaranteed  to  havean  up-to-date  copy  of  the  data  that  is  consistent  with  the  leader.  If  the  leader  sud‐denly  fails,  we  can  be  sure  that  the  data  is  still  available  on  the  follower.  

The  disad‐vantage is that if the synchronous follower doesn’t respond, the write cannot be processed. The leader must block all writes and wait until the synchronous replica is available again.


### 7. _It is true that synchronous replication could improve your system's reliability, but let's talk about real-world cases... is synchronous replication used in practice?_
Yes, but with a slightly difference... it is impractical for all followers to be synchronous: any one node outage would cause the whole system to grind to a halt. In practice, if you ensable synchronous replication on a database, it usually means that **one** of the followers is syncronous, and the others are asynchronous. 

### 8. _What is the algorithm to follow in case of a leader failure (failover)?_
+ Determining that the leader has failed
+ Choosing a new leader
+ Reconfiguring the system to use the new leader 


### 9. _What is a logical log?_
An alternative is to use different log formats for replication and for the storage engine, which allows the replication log to be decoupled from the storage engine internals. This kind of replication log is called a logical log, to distinguish it from the storage engine's data representation. 

### 10. _What does monotomic reads mean?_
When you read data, you may see an old value; monotonic reads only means that if one user makes several reads in sequence, they will not see time go backward, i.e.; they will not read older data after having previously read newer data. 



