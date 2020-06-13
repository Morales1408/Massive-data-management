# Chapter N.2 
-------------------------------------------
### 1. _Why is it that creating something "NoSQL" was seen as something necesssary before its existince?_
There are several driving forces behind the adoption of NoSQL databases, including:
+ A need for greater scalability than relational databases can easily achieve, including very large datasets or very high write throughput 
+ A widespread preference for free and open source software over commercial database products
+ Frustration with the restrictiveness of relational schemas, and a desire for more dynamic and expressive data model

### 2. _Imagine you are working on a SQL database and you cannot migrate to another type of database, how would you represent a one-to-may relationship from the user to some item?_
+ In the traditional SQL the most common normalized representation is to put these items in seperate tables, with foreign key reference to the corresponded table. 
+ Later versions of the SQL standard added support for structured datatypes and XML data; this allowed multi-valued data to be stored with a sibgle row, with support for query and indexing inside those documents

### 3. _What are the advantages of using an ID regardless the type of databases?_
The advantage of using an ID is that becuase it has no meaning to humans, it never needs to change; the ID can remain the same, even if the information it identifies changes. Anything that is meaningful to humans may need to change sometime in the future, but the ID. 

### 4. _Explain a bit about the characteristics of the relational databases (make emphasis on the contrast it has between the non-relational ones)_
What a relational database does in contrast is to lay out all the data in the open: a relation (table) is simply a collection of tuples (rows), and that's it. There are no labyrnthine nested structures, no complicated access paths to follow if you want to look at the data. You can read a particular row by designating some colmns as a key and matching on those. You can insert a new row into any table without worrying about foreing key relationship to and from other tables. 

### 5. _If I want to represent many-to-one and many-to-many relationships, what should I use? a relational database or a document database?_
When it comes to representing many-to-one and may-to-many relationships, rational and document databases are not fundamentally different: In both cases, the related item is referenced by a unique identifier, which is called a _foreign key_ in the raltional model and a _document fererence_ in the document model.

### 6. _When does the "storage locally" advantage applies?_
The locally advantage only applies if you need large parts of the document at the same time, otherwise, you will having lacks on the latency. 

### 7. _Why isn't advisable to use storage locally queries if you will only use a small part of the dataset?_
When updating or opening, it needs to rewrite and load the ENTIRE document respectevely, so if you are not using a large part of the document, it is a waste of time and memory. 

### 8. _Describe the characteristics of a graph-like database and mention three typical examples of its usage_

A graph consists of two kinds of objects: _vertices_ (also known as nodes or entities) and edges (also known as relationships or arcs). Many kinds of data can be mdeled as a graph. Typical examples include: 
- Social graphs:
  - Vertices are people, and edges indicate which people know each other. 
- The web graph
  - Vertices are web pages, and edges indicate HTML links to other pages. 
- Roead or rail networks
  - Vertices are junctions, and edges represent the roads or railway lines between them

### 9. _When is it advisable to use graph-like models?_
The relational model can handle simple cases of many-to-many relationships, but as the concections within your data become more complex, it becomes more natural to start modeling your daa as a graph. 

