# MongoDB - Cheat sheet

_Mario Morales_


# What's mongo?
MongoDB is an object-oriented, simple, dynamic, and scalable NoSQL database. It is based on the NoSQL document store model. The data objects are stored as separate documents inside a collection — instead of storing the data into the columns and rows of a traditional relational database.

## Connecting to mongo
There are two ways in which you can connect to mongo, the first one is as easy as write in your shell the folloing command: 

***mongo***

If you do that you'll be connected locally instead to a external server

![](Fotos%20monfo/conectar.jpg)
In the other hand, if you want to connect to an external server, you'll need to write the following command:

***mongo--***+ the server you want to connect to

As an example, I'll connect to the server my professor provide us
![](Fotos%20monfo/conectar%20externo.jpg)
If needed and as you saw in the picture, you'll be asked an user and password

## How to see the databases in the server?
Once you're connected, you can see the databases available by typing 

***show dbs***
![](Fotos%20monfo/show%20bd.jpg)

## How to acces a specific database?

If you've targed the database to access to, you just need to type

***use***+ the name of the dataset 

I'll conect to the database named "test"
![](Fotos%20monfo/use%20.jpg)

## How to know where am I connected to?
If you've lost yourself, you just need to type

***db***

And you'll be shown with the name of the dataset you are in
![](Fotos%20monfo/db.jpg)

## How can I see the collections inside a database? 
This is pretty intuitive. Seeing the collections in a database is as easy as type 
***show collections***

Here I'll show the collections in the "test" database
![](Fotos%20monfo/show%20collections.jpg)

## How to create a database 
There a different ways to do it; nevertheless, the easiest one is to "connect" to the databse you want to crate. When mongo identifies you are trying to connect a database that doesn't exist, it will create a new one named as you please. 
I've shown you how to connect a database, so you just need to use the same command: 

***use*** + the name of your new database 

I'll create a new database named "nueva_prueba". To confirm I'm creating a new one, you can check on the previous images there's no database with that name
![](Fotos%20monfo/create%20database.jpg)
As you can see, I created the database named "nueva_prueba" and then I checked if I'm connected to it

## How to create a new collection 
You need to be careful while doing this, remeber that this collection will be saven in the database you are in. Once you are in the database where you want the collection in, you just need to type 

***db.createCollection("YourCollection")***

I'll create a new colleciton named "nuevacoleccion" in the "nueva_prueba" database 
![](Fotos%20monfo/create%20coleccion.jpg)
As you can see in the picture, I made sure I was in the right database, then, I created the collection. 
Once that was ready, I show the collections in my databse

## How to delete a collection 

Imagine you've created an useless collection or you just one to delete an empty collection; it'll be better to delete it. To do so, you need to run the following line: 
***db.YourCollection.drop()***

Be carefull, keep in mind that you will delete EVERYTHING inside this collection. 
I will delete my new collection named "nuevacolleccion"

###### Disclaimer: Only users with permissions will be able to do this
![](Fotos%20monfo/Eliminar.jpg)
As you see, I deleted it and now there are no collections in my database


# Working with documents 
###### Friendly reminder
MongoDB works on documents, this means that all the data saved in the collections will be a dictionary of the form: 
{entry1:value1,entry2:value2...entry-n:value-n}


## How to insert documents in a collection
You need to be sure you are in the right databse, then, you need to call for the collection for the document to be stored in, finally, you just need to call for the funciont "insert" and then imput the values. 

***db.YourCollection.insert({"entry1":value1})***

I'll add a new document in my collection named "morales" 
![](Fotos%20monfo/insertar.jpg)


## How to see  *all* the documents in a collection
You need to be in the database where the collection is, then, you writhe the following command

***db.YourCollection.find()***
![](Fotos%20monfo/find.jpg)

if you want to show the documents in a more user friendly way, you can add the ".pretty()" command: 
***db.YourCollection.find().pretty()}***
![](Fotos%20monfo/find%20mejor.jpg)


## How to see the first n elements 
You just need to add the funcion "limint" to the previous search. 

***db.YourCollection.find().limit(n).pretty()***

n = the number of documents to be shown 
I'll show the first two elements
![](Fotos%20monfo/limit.jpg)

## How to delete a document in a collection
In that case, what you'd need to do is to write the match on the document that you want to delete, this is:
If you want to delete the document that has the value "Nombre" as "Mario", you'd need to put it that way. The more key-values you write, the more accurate the document to be deleted.


***db.YourCollection.remove({"Entry1":"value1"})***

In my case, I will delete the document that has "Nombre": "Mario"
![](Fotos%20monfo/eliminar%20valor.jpg)
As you can see, I deleted it, therefore, it isn't shown when I show all the documents in mi collection 

## How to update the value of an entry in a document
First you need to call the database, then you need to call the collection; finally, use the "update()" function and as parameters you need to write the key-value characteristic of the document to be updated, and then, use the "$set" operator to determine what key you are going to update. Finally, write the new key- value:


#### db.YouCollection.update({"Entry1:Value1},{"$set":{"Entrytochange":newvalue}})

In my example, I will change the update the phone number of the student called "Juan" 
![](Fotos%20monfo/actualizar.jpg)

## How to update multiple documents
Imagine your boss is telling you that in the parameter "sexo" he only want a letter instead of having the entire word "Hombre" or "mujer". How can you change all of the "Hombre" values at the same time so you ended up having just one letter? You'd need to update mutiple documents with the following command: 

#### db.YourCollection.update({"Entry":Thevalueyouwanttochange},{"$set":{"Entry":newvalue}},{"multi":true})

The "multi" paramenter is going to change the value of all the matches.

In my example, I'll change all of the "hombre" values for just one "h"
![](Fotos%20monfo/actualizar%20multi.jpg)

## Update a document's count 
Imagine it's been a year since you took the age of a user, you'll need to add a year to his age. How can you do that? 
You will need to use the "$inc$ operator, it increments field by specified value. 

#### db.YourCollection.update({"Entry":value},{"$inc":{"Entryttobeadded":Figuretobeadded}})

In my example, I'll will increace the age by 1 year of my user named "Pedro"
![](Fotos%20monfo/aumentar.jpg)
In the previous images Pedro had 22 years, now it has 23 in the "edad" field

## How to find for elements with specific characteristics
If you want to see all the elements that matches with an specific characteristic, you'll need to use the "find" with the key-value needed. 

#### db.YourCollection.find({"Entry":value})

In my case, I want to search for all the users that are studyind "Datos"
![](Fotos%20monfo/buscar%20especificio.jpg)

## How to delete fields from the document
Imagine we don't want to know one field that is being represented a lot of times in our collection, we'll need to run the following command:

#### db.morales.update({},{"$unset":{"Entrytodelete":""}},{"multi":true})

In my case, I will delete "Telefono" from all of my users. 
![](Fotos%20monfo/elminar%20field.jpg)

## Creating a document with a document within 
Sometimes it is necessary to create a document that has multiple values in one single field. To do that, you'll need to do it in the following way: 

#### db.morales.insert({"Entry":[value1,value2,value3...value-n]})

I will create one like that in my collection
![](Fotos%20monfo/materias.jpg)

## How to update elements in a array that is in a document 
This is to update an element in an array within a document

#### db.YourCollecion.update({"Entry":value},{"$set":{"Entry.#":"Newvalue"}})

the "#" stands for the number of the element in the array to be updated.
In my example, I will change "Recreo" and I'll put "Descanso"
![](Fotos%20monfo/zz.jpg)

## Updating values in an array without knowing the possition of the element
if you don't know the number of the possition of the element in the array to be changed, you'll need to use "$" operator.

#### db.YourCollecion.update({"Entry":value},{"$set":{"Entry.$":"Newvalue"}})

I will change the "Educacion fisica" data and put "Geografia"
![](Fotos%20monfo/zzz.jpg)

## How to create an embedded document
In case you need it, here's how

#### db.morales.insert({"Entry":{"Subentry":value}})

I will create a sub document myself
![](Fotos%20monfo/zzzz.jpg)

## Finding element that matches certain requierements
In my example, I will find the users that are older than 25 years old

#### db.yourcollection.find({"Entry":{"$gt":25}})
![](Fotos%20monfo/zzzzz.jpg)

# *Keep in mind*

- "$gt$"  = greater than
- "$gte$" = greather than or equal
- "$ne$" = not equal to
- "$lt$" = less than
- "$lte$" = less than or equal to

## How to see specific fields of the documents
Imagine you just want to know the names of your users and not all of the information, here's how 

#### db.morales.find({},{"Nombre":true})

the "{}" funciont stands for "all the documents" 
![](Fotos%20monfo/zzzzzz.jpg)

## How to know the number of documents that matches with my search
If what you want to know the number of documents that matches your search, you just need to run this:

#### db.YourCollection.find({}).count()
![](Fotos%20monfo/zzzzzzz.jpg)

## How to sort numeric values in within the documents
You just need to determine which is going to be the field that will lead the sorting. 

#### db.YourCollection.find().sort({"Numericentry":#})

The "#" operator could be 1 or -1
I will sort my users by their age

# *Disclaimer*
1 stands for ascending order 
-1 stands for descending order

![](Fotos%20monfo/zzzzzzzz.jpg)



































