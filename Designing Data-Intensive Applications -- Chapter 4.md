# Chapter 4 
--------------

#### 1. How can you distinguish between _Relational databases_ and Schema-on-read databases?
Relational databases generally assume that all data in the database conforms to one schema: Although that schema can be changed there is exactly one schema in force at any one point in time. By constrasts, schema-on-read ("Schemaless") databases don't enforce a schema, so the database can contain a mixture of older and newer data formats written at different times. 

#### 2. What happens with my code if I change my schema? 
It is very likely that you will need to apply some changes. However, in a large applications, code changes often cannot happen instantaneously: 

#### 3. Continuing with the previous answer, what happens if you cannot apply the changes in your code instantaneously? 
+ With server-side applications you may want to perform a _rolling upgrade_, deploying the new version to a few nodes at a time, checking whether the new version is running smoothly, and gradually working your way through all the nodes. This allows new versions to be deployed without service downtime, and thus encourages more frequent releases and better envolvability.
+ With client-side applications you're at the mercy of the user, who may not install the upgrade for some time.

#### 4. Why are encoding libraries convenient? Mention some examples of encoding libraries. 
Encoding libraries are very convenient because they allow in-memory objects to be saved and restored with minimal additional code. 
Jus for mentioning some examples, Ruby has Marshal and Python has pickle. 

#### 5. Are there any problems with encoding libraries? 
Yes, they have numerous deep problems: 
+ The encoding is often tied to a particular programming language, and reading the data in another language is very difficult. If you store or transmit data in such an encoding, you are committing yourself to your current programming language for potentially a very long time, and precluding integrating your systems with those of other organizations. 
+ In order to restore data in the same object tpes, the decoding process needs to be able to instatiate arbitrary classes. This is frequently a source of security problems:
  + If an attacker can get your application to decode and arbritary byte sequence, they can instantiate arbitrary classes, which in turn often allows them to do terrible things such as remotely executing arbitrary code.
+ Versioning data is often an afterthought in these libraries: as they are intended for quick and easy encoding of data, they ofthen neglect the inconvenient problems of forward and backward compatibility
* Efficiency is also often an afterthought. For example, Java's built-in serialization is notorious for its bad performance and bloated encoding.

#### 6. What are the most common and used formats for data storage? Are those perfect langauges or do they have problems? 
JSON, XML and CSV are textual formats, and thus somewhat human-readable. Besides the superficial syntactic issue, they also have some subtle problems: 
+ There is a lot of ambiguity around the encoding of numbers
+ JSON and XML have good supports for Unicode character strings, but they don't support binary strings. Binary strings are useful feature, so people get around this limitation by encoding the binary data as text using Base64. The schema is then used to indicate that the value should be interpreted as Base64-encoded. 

#### 7. Can you change the datatypes on your schema? is it advisable? 
Thay may be possble, but there is a risk that values will lse precision or get truncated. 

#### 8. Following the previous answer, name an situation where it is risky to alter datatypes in an schema
Let's say you change a 32-bit integer into a 64-bit integer. New code can easily read data written by old vode, because the parser can fill in any missing bits with zeros. However, if old code reads data written by new code, the old code is still using a 32-bit variable to hold the alue. If the decoded 64-bit value won't fit in 32 bits, it will be truncated. 

#### 9. What is Apache Avro? 
Apache Avro is another binary encoding format that is interestingly different from Protocol Buffers and Thrift. It was started in 2009 as subproject of Hadoop, as a result of Thrift not being a good fit for Hadoop's use cases

#### 10. What happens with the data in Avro when the user wants to encode it? 
With Avro, when an application wants to encode some data, it encodes the data using whatever version of the schema it knows about. For example, that schema may be compiled into the application. This is known as the writer's schema.

#### 11. What it is that the book called _data outlives code_?
When you deploy a new version of your application, you may entirely replace the old version with the new version within a few minutes. The same is not true of database contents: The five-year-old data will still be there, in the original encoding, unless you have explicity rewritten it since then. That observation is summed up as _data outlives code_.


