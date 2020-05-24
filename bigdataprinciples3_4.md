# Chapter N. 3


## _Questions about Apache Thrift_ (1-4)

### 1. _What would be the equivalent of unions and strucrues in graph's theory?_
Unions are useful for representing nodes, strucrs are natural representations of edges and properties use a 
combination of both. 

### 2. _What would be the definition of a union data type?_
A single value that may have any of several representations.

### 3. _Let's suppose I want to change my schema but I sill want it to be backward compartible with existing data, what are the requirements I need to follow for doing that?_
- Fields may be renamed. 
- A field may be removed, but you must never reuse that field ID.
- Only optional fields can be added to existing structurs.

### 4. _What happens if I change my schema, then, I remove a field but I reuse that field ID?_
Thrift would try to deserialize that old data into the new field, which will lead to either invalid or incorrect data.

### 5. _As we already know, we don't have a tool that would let us implement any possible schema funcion; what approaches can we take to work around these limitations with a framework like Apache Thrift?_
+ Wrap your generated code in additional code that checks the additional properties you care about. 
+ Check the extra properties at the very beggining of your batch-processing workflow. 

# Chapter N.4

### 1. _Write and explain the requirements for the master dataset_
  + Write: Efficient appeds of new data. The only write operation is to add new pieces of data, so it mustb be easy and efficient to append a new set of data objects to the master dataset. 
  + Read: Scalable storage. The batch layer stores the complete dataset-potentially terabytes or petabytes of data. It myst therefore be easy to scale the storage as your dataset grows. 
  + Both: Tunable storage and processing costs; Enforceable immutability. It's critical that you're able to enforce the immutability property on your master dataser. Of course, computers by ther very nature are mutale, so there will always be a way to mutate the data you're storing. The best you can do is put checks in place to disallow mutable oprations. There checks shuld prevent bugs or other random errors from trampling over existing data.
  
### 2. _What's the problem with regular filesystem technologies and how could you solve it?_
The problem with a regular filesystem is that it exists on just a single machine, so you can only scale to the storage limits and processing power of that one machine. You could sove this issue by applying a distributed filesystem technology. 

### 3. _Define the "distributed filesystem" technology_
The difference with the typical filesystems is that they spread their storage across a cluster of computers. They scale by adding more machines to the cluster. Distributed filesystems are designed to that you have fault tolereance when a machine goes down, meaning that if you lose one machine, all your files and data will still be accessible.

### 4. _Explain what happens when you uploead a file to a distributed filesystem (HDFS in this case)_ 
The file is is first chunked into blocks of a fixed size, typically between 64 MB and 256 MN. Each block is then replicated across multiple datanodes (typically three) that are chosen at random. The namenode keeps track of the file-to-bloc mapping and where each block is located.

![](Fotos%20monfo/libro.png)

### 5. _which requirements does a master dataset storage need to fulfill?_
  + Write: Efficient appends of new data & Scalable storage
  + Read: Support for parallel processing
  +Both: Tuneable storage and processing cost & Enforceable immutability
  
### 6. _Give an example of vertical partioning_
You may have a computation thah only requires informatino collected during the past two weeks. The batch storage should allow you to partition your data a function only accesses data relevant to is computation. 
