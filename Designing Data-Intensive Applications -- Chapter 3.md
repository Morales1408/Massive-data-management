# Chapter N.3

#### 1. What does the book means by saying the word _log_? 
The word log is often used to refer to applications logs, where an application outputs text that describes what's happening. In the book, "log" is used in the more general sense: an append-only sequence of records. It doesn't have to be human-readable; it might be binary and intended only for the other programs to read. 

#### 2. What is an index? Is it important for databases or analysis? 
An index is an additional structure that is derived from the primary data. Many databases allow you to add and remove indexes, and this doesn't affect the contents of the database; it only affects the performance of queries.
Yes, it is important because, as I just wrote, it affects the performance of the queries. 

#### 3. In a real implementation scenario for a log, what file is it good for databases? CSV is one the most used, is it goo?
CSV is not the best format for a log. It's faster and simpler to use a binary format that first encodes the length of a string in bytes, followed by the raw string (without need for escaping) 

#### 4. What happens to the in-memory has map if the database is restarded? is there anything we can do about it?
If the database is restarted, the in-memory has maps are lost. In principle, you can restore each segment's hash map by reading the entire segment file from beginning to end and nothing the offset of the most recent value for every keys as you go alog. However, that might take along time if the segment files are large, which would make server restars painful. 

#### 5. Why an append-only design turs out to be a reason for?
+ Appending and segment merging are sequential write operations, which are generally much faster than random writes, especially on magnetic spinning-disk hard drives. To some extent sequential writes are also preferable on flash-based solid state drives.
+ Concurrency and crash recovery are much simpler if segment files are append-only of immutable.
+ Merging old segments avoids the problem of data files getting fragmented over time. 

#### 6. What is a hash table? 
In computing, a hash table is a data structure that implements an associative array abstract data type, a structure that can map keys to values.

#### 7. Mention some of the limitations of the has table index: 
+ The hash table must fit in memory, so if you have a very large number of keys, you're out of luck. In principle, you could maintain a hash map on disk, but unfortunately it is difficult to make an on-disk hash map perform well. It requires a lot of random access, it is expensive to grow when it becomes full, and hahs collision require fiddly logic. 
+ Range queries are not efficient.

#### 8. According to the book, would you say HBase and Cassandra are column oriented? 
Cassandra and Hbase have concepts of column families, which they inherited from Bigtable. However, it is very misleading to call them columnoriented. 

#### 9. Name and advantage of sorted order: 
It can help with compression of columns. If the primary sort column does not have many distinct values, then after sorting, it will have long sequences where the same value is repeated many times in a row. 
