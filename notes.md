Why databases?

Because before now, in the past when we created files and read from them, we would go through the entire file whenever we wanted to do anything with them, ie when creating data, we replace the entire content in the file with new content, when reading, it always read all of it, when updating, it read the entire thing, finds the content to update and replaces, and when deleting again it went through the entire content, found the thing to delete, and so on. This is not HORRIBLY TERRIBLE for very veyr small files and projects, but for anything _at scale_ it becomes an annoying nightmare that is HORRIBLY TERRIBLE veyr quickly. Before we continue by the way, Creating, Reading, Updating, and Deleting are comonly referred together as CRUD operations
Another nightmare that could occur with big files like we had, is that in the future say, we could have multiple concurrent users accessing the file and uopdating at the same time, creating conflicts and fuicking everytihg up

ENTER DATABASES - Database Management Systems (DBMS)
These are software systems ahtat are optimized for data storage tasks.While ultimately they do store data in files, they do it in a much more efficient way and also much easier for us to deal with. They help with optimizing simultaneous read/write access, data storage and retrieval, and data querying (queries with filters and conditions)

There are 2 main kinds of systems:
Relational Database Management Systems (RDBMS / SQL Databases)
Non-Relational Database Management Systems (NoSQL Databases)

SQL databases typically store normalized data across multiple tables
An example for this, would be for airports and flights, We would create two different tables, for airports and flights, and give them IDs, cities, and countries for airports, and ID, start, and destination for flights. We would relate the start and dest from the flight to the ID of the airport (whihc would be JFK, TFGRN etc) AS SHOWN IN DATABASE RELATIONS.JPG ![alt text](database-relations.jpg "Title")
Something to note about normalized data, is that there are no nested values. Each cell contains just its own data. IE Airport ID only holds the ID of one airport, etc

Sopemthing also to note, is that these tables have clearly defined schemas and data types
![alt text](database-schema.jpg "Title")
Note that the types are all defined BEFORE you popualte them with data, ie with IDs you know they should all be unique strings ETC
uniqueness is an important feature, because it ensures that each row has a unique ideinfier which is important in relational databases, since you need to establish relations between tables with such unique IDs. Without unique IDs this is not possible

In such databases, you can also QUERY the data, and related data. For example, you could go into the database and search for all flights that start in Munich for wexmaple, and then you could return that, and the destination value and the ID of the fligth. You can also do this acrros multiuple tables. You could for example, do the same, getting all flights that start in munich, and then get the related airport data, IE relating to the munich airport using the ID

NoSQL Databases ar emuch different.
In NoSQL databases you typically only work with a few tables, like a single Flights table that contains documents with all the data we want to stroe, in a json type format rather than with columns and rows
![alt text](database-NoSQL.jpg "Title")
In some ways this is worse, but in others it is fine. There is a lot of data duplication as we can see, but this isnt always a problem. If we are duplicating data that isnt changing a lot, suhc as airport data (being as they dont tend to move or whatveeR) then this can be fine. In such a case, storing a bnunch of information in files like this means that you can store more info in less files, which means you can get more data with less queries. Like if you grabbed the flightcode there, you could also grab the start and dest without having to link tables or anyrthing like that. Remember, storing big amounts of data isnt necessarily the problem, but often times it is the querying of data, which can be simplified with nosql databases.

In this examplke here too you notice, there is no set schema, no predefined data types etc. They _can_ all have different structures if you so wish

Now which to choosE?

Thjere is no be all end all for every situation. Often time it comes down to personal preferenc. however you should think about the queries you will typically be running for it and choose accordingly In bigger websites you could even use both types for different things depending on what is needed then. However

SQL Dbs have more structure and rules, which can be helpful for being strict and sleek, however as the project or wahtever grows, the schema could be outpaced and not work as well at scale if its differen from how you originally intended it to be

NoSQL Dbs however can be more flexible, and reduce the amount of required queries, and especially with gigantic websites with millions of entries, SQL tends to have a scalibility issue
