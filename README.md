### Derrick Conway G00328406
# Graph-Theory
You are required to design and prototype a Neo4j database for use
in a timetabling system for a third level institute like GMIT. The database
should store information about student groups, classrooms, lecturers, and
work hours – just like the currently used timetabling system at GMIT 


# Reserach for the project
I reserchecd the following to help me do and understand do the project.
* Neo4j - software needed to do the project
* excel - to help with the csv files
* stack overflow - to reserch problems 
* notepad ++ - to creat csv files
* YouTube videos - on how to do relationships with nodes

# Neo4j
### what is Neo4j
Neo4j is a graph database management system developed by Neo Technology, Inc. Described by its developers as an ACID-compliant transactional database with native graph storage and processing, Neo4j is the most popular graph database  

Neo4j is implemented in Java and accessible from software written in other languages using the Cypher Query Language through a transactional HTTP endpoint

The Data Structure of Neo4j is everything is stored in the form of either an edge, a node, or an attribute. Each node and edge can have any number of attributes. Both the nodes and edges can be labelled. Labels can be used to narrow searches. As of version 2.0, indexing was added to Cypher with the introduction of schemas

# Cypher
### What is Cypher
Cypher is a graph query language that allows for efficient querying and updating of the graph store. Cypher is a relatively simple but still very powerful language. Very complicated database queries can easily be expressed through Cypher. This allows you to focus on your domain instead of getting lost in database access.

Cypher is designed to be a nice query language, suitable for both developers. Cypher goal is to make the simple things easy, and the complex things possible.

### Structure

Cypher borrows its structure from SQL.
The queries are built up using various clauses.

Here are a few clauses used to read a graph:

[MATCH]: The graph pattern to match. This is the most common way to get data from the graph.
[WHERE]: Not a clause in its own right, but rather part of [MATCH], [OPTIONAL MATCH] and [WITH]. 
[RETURN]: What to return.

EXMPLE:  
An example would be like here is a query which finds a user called 'John' and 'John’s' friends (though not his direct friends) before returning both 'John' and any friends-of-friends that are found.  

MATCH (john {name: 'John'})-[:friend]->()-[:friend]->(fof)  
RETURN john.name, fof.name  

RESULT:  
+----------------------+  
| john.name | fof.name |  
+----------------------+  
| "John"    | "Maria"  |  
| "John"    | "Steve"  |  
+----------------------+  
2 rows  

## Designing the Timetable

To design my time table i just went to the gmit website and got a copy of the web time table.
And then I justed pick what i thought where the main parts i needed e.g College,Course,Times,Teachers,Class,Room,Days,Groups
In my mind i i had a picture of the ways they could be connected.  

EXP:  
College --> Course --> Teachers --> Group--> Class --> Time+Room  
These would all be connected with nodes and relationships,  
Now to just put them togetter. easer said then done!!

## Making the nodes and relations

In order for this project to work you need to design your nodes and decide witch one hav relations to each other. this touck some thought and effert.
Here I Have the put together what the nodes are and what description are with there Labels and Propertys 

| Node | Description | Label | Property |
| --- | --- | --- | --- |  
| `College` | `GMIT College`| `college` | `gmit` |
| `Course` | `Computing in software development` | `course` |	`Computing in software development`|  
| `Teacher` | `Teachers you will have` | `Teacher` |	`names` |  
| `Class` | `Class studying` | `Class` | `classs` |  
| `Group` | `3 groups A,B,C` | `Group` | `groups` | 
| `Time` | `all the times` | `Time` |	`time` | 
| `Room` | `class room` | `Room` | `room` | 
| `Days` | `days od the week` | `Days` | `day`| 
| `DaysAndTimes ` | `days and times for class` | `DaysAndTimes` | `daysandtimes` |

## relations

| Relationship | Description | Connected Nodes | Label | Property |
| --- | --- | --- | --- | --- | 
| `Has_Class_At` | ` is what group has class at what day and Time` |	`DaysAndTime, Groups` |	`Has_Class_At` | `id,type`|
| `At` | ` iswhich days and what Times` |	`Days, Times` |	`At` |	`id` |
| `Has_Class` |	` iswhich Days for groups` |	`Days,groups` |	`Has_Class` |	`id` |
| `Teaches` |	` is which teacher is teaching what class` | `Class, Teacher` |	`Teaches` |	`id` |
| `Studying` | `is what college and course you are attending` |	`Collage, Course` |	`Studying`	| `type` |

## Queries

In the documentation i was given for the project it states that i needed to come up with interesting queries for the database i have create. the only one i could come with at such short notice but have not tryed them yet cause im out of time with the project.  

NOTE: That I could not be sure if these querie are right cause i can not test them,so im just trying to make queries by just looking at the nodes and relationships have at the moment.  

QUERIE 1
`MATCH` d=(g:Group)-[:Has_Class]->(d:Days)-[a:At]->(t:Times) `RETURN` p  
UNION  
`MATCH` p=(g:Group)-[:Has_Class_At]->(t:Times RETURN p  
QUERIE 2
`MATCH` p=(m:Class)-[:At]->(t:Times)<-[:Has_Class_At]-(g:Group) Where g.group `CONTAINS` "C" return p  
i think the relationship is not right for this to work i should have made a relationship at with DaysAndTimes.

Can't come up with a third one cause i didnt make enough relationships made

## Conclusion

My conclusion on this project is that i did not have much knowledge of the neo4j and cypher, but after testing it and reserching video of neo4j ansd going through the work sheets that the letcher handed out through out the semester war very usefull. The neo4j great pease of software to show and explan to people how the database is connected visually to hundreds of noads.  

Also in my project i would like to have gotten the project finished but i was issues with my software for neo4j and issues with my laptop. like i would do a query and the laptop would just freze for 20mins it was really time consuming stressfull and my laptop would just restart out of nowhere.  

If i had not hade these issues i would have been confident on finishing the project on time with the ReadMe file. but what can ya do thats life these thing happen, no point stressing about it now.

## References

* http://neo4j.com/docs/developer-manual/current/cypher/
* https://en.wikipedia.org/wiki/Neo4j
* https://neo4j.com/developer/guide-neo4j-browser/
* https://neo4j.com/developer/cypher-query-language/
* https://neo4j.com/developer/guide-sql-to-cypher/
* https://www.youtube.com/watch?v=1U6iUTV_Dco
* https://www.youtube.com/watch?v=JhZaCw94r40&t=86s
* https://www.youtube.com/watch?v=GTZ2JD9l5j0&t=542s
* https://www.youtube.com/watch?v=Go3P73-KV30

