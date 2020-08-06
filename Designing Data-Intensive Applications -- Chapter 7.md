# Chapter N.7 

#### 1. _Mention some of the most common problems in harsd reality of a data system (according to the book)_
+ The database software or hardware may fail at any time (including in the middleof a write operation)
+ The  application  may  crash  at  any  time  (including  halfway  through  a  series  ofoperations)
+ A client may read data that doesn’t make sense because it has only partially beenupdated

#### 2. _What is a transaction?_
is  a  way  for  an  application  to  group  several  reads  and  writestogether into a logical unit

#### 3. _What does ACID stand for?_
Atomicity, Consistency, Isolation, and Durability

#### 4. _What does atomicity mean?_ 
In general, atomic refers to something that cannot be broken down into smaller parts.The word means similar but subtly different things in different branches of comput‐The Slippery Concept of a Transaction | 223
ing.  For  example,  in  multi-threaded  programming,  if  one  thread  executes  an  atomicoperation, that means there is no way that another thread could see the half-finishedresult of the operation. 

#### 5. _What is the main idea behind applying ACID?_
The  idea  of  ACID  consistency  is  that  you  have  certain  statements  about  your  data(invariants) that must always be true

#### 6. _Mention one example where writes to several different objects need to be coordinated (open question)_
In  databases  with  secondary  indexes  (almost  everything  except  pure  key-valuestores), the indexes also need to be updated every time you change a value. Theseindexes are different database objects from a transaction point of view: for exam‐ple, without transaction isolation, it’s possible for a record to appear in one indexbut not another, because the update to the second index hasn’t happened yet.

#### 7. _What are the two guarantees that makes the "read committed"?_
+ When reading from a database, you will only see data that has been committed 
+ When writing to the database, you will only overwrite data that has ben comitted

#### 8. _How wold you index work in a multi-version database?_
One  option  is  to  have  the  indexsimply point to all versions of an object and require an index query to filter out anyobject  versions  that  are  not  visible  to  the  current  transaction
