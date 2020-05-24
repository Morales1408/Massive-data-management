# Chapter N. 3


## _Questions about Apache Thrift_ (1-4)

### 1. _What would be the equivalent of unions and strucrues in graph's theory?_
Unions are useful for representing nodes, strucrs are natural representations of edges and properties use a 
combination of both. 

### 2. _What's would be the definition of a union data type?_
A single value that may have any of several representations.

### 3. _Let's suppose I want to change my schema but I sill want it to be backward compartible with existing data, what are the requirements I need to follow for doing that?_
- Fields may be renamed. 
- A field may be removed, but you must never reuse that field ID.
- Only optional fields can be added to existing structurs.

### 4. _What happens if I change my schema, then I remove a field but I reuse that field ID?_
Thrift would try to deserialize that old data into the new field, which will lead to either invalid or incorrect data.

### 5. _As we already know, we don't have a tool that would let us implement any possible schema funcion; what approaches can we take to work around these limitations with a framework like Apache Thrift?_
+ Wrap your generated code in additional code that checks the additional properties you care about. 
+ Check the extra properties at the very beggining of your batch-processing workflow. 

# Chapter N.4

### 1. -




