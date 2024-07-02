# Neo4j Learning Guide

## This Time We Learn Neo4j

### What is Neo4j?
1. Neo4j is a graph-based database.
2. It has a query language called Cypher.
3. It is written in Java.
4. it is approprate for that' data is not important beacese each time it can be change but the relation is very important for us
### <img src="./img/image1.png" width="50">
*cilcle in image call Node
* ----> call relation or edges<edg>
all the edges are One way.
me found the keyboard and keyboard not dound me
### Why is it Good?
1. Neo4j is ideal for handling irregular data with strong relationships.

### Where is it Useful?
Neo4j can be particularly useful in scenarios such as:

- **E-commerce**: On a shopping website, if you're browsing for a keyboard and close all your tabs, you might then see a targeted advertisement when you visit a dictionary site.
- **Social Networks**: On LinkedIn, you might see that "Mmd" follows someone you also follow, even though you don't know "Mmd" personally. This common connection is an example of how Neo4j can analyze and display relationships between users.
### <img src="./img/images2.jpeg" width="50">
## wbsit 
# cypher
1. developmet > documation > cypher
* Clauses has basi query.
* Syntax

## Getting Started

### Prerequisites
- Java Development Kit (JDK)
- Neo4j Community Edition
## sql and eo4js:
1. in sql we have to join but in neo4js we traverse 
* join in sql is very heavy and complect and lower our code but traverse is quickly and not effect on the speed querycode.
2. Top use Case:
our data vary each time and so it do not good use sql

### <img src="./img/image3.png" width="50">

## waht is lable?
each category we have we call lable like the picture we have jobs and person that they are our lables.
### <img src="./img/image4.png" width="50">
### <img src="./img/image5.png" width="50">


## 
* a or  or n or .. not effeict in our code and just like varibales
1. Create
   #
   1.Node
      ```
       Create(nameNode)
   2.Create Node with lable person and devlopers with value {name:'afshin', age:90}
    ```
      CREATE(a:person:developer {name:'afshin',age:50})
      CREATE(b:person:devops {name:'jack',age:41})
      CREATE(n:person:cto {name:'ali',age:80}) return b

2. match<find>
   #
   1. return all data

      ```
      MATCH(x) return x;
      ```
   2.where on the properties
      ```
         MATCH(n) where x.name = 'afshin' return n
      ```
   3.Match with lable and properties
      ```
      #lable
      MATCH(b:developer) return b.age
      #properties
      MATCH(a {name:'saeid'}) return a
      ```
   4.match that a person has labael devloper and relation with a person and it was devekoper   
      ```
      MATCH (a:developer) -- (:developer) return a
      // that has realtion arrow
         MATCH (a:person) --> (:developer) return a
      // realtion with name
      MATCH(a:person) -[r]-> (:developer) return type(r) #is_freiend 
      MATCH(a:person) -[:is_freiend]-> (:developer) return a    
      ```
3. realation
   #
   1. create relation between two node afshin is freind with jack but jack doesn't frien with afshin
   ```
      MATCH (a:person),(b:person) 
      where a.name='afshin' and b.name='jack'
      create (a)-[:is_freiend]->(b)  
4.DELETE<for node and relation> 
   ```
   #not relation
   match(x{name:'afshin'}) delete x
   #if we have relation
   1. delete relation: match(x{name:'afshin'}) -[r:is_friend]->() delete r

   #delete all data from db
   match(n) detach delete n
5.REMOVE<for properties>
   ``` 
   #properties
   match(n{name:'saeid'}) remove n.age return n
   #lable
   match(n{name:'saeid'}) remove n:person return n
 
 2.where on the properties
    ```
    MATCH(n) where x.name = 'afshin' return n  
6.set<for add or update and delete properties>
   ```
   match(n{name:'afshin'}) set n.name = 'mehdi' return n
   #delete
   match(n{name:'afshin'}) set n.name = true return n
   #each afshin has pour on seaid
   match(a:developer),(b:cto) set b=a
7.merge<create + match> 
* create and if one node is exist do not create this again
   ```
   MERGE(n:person) return n
   #if was set
   MERGE(n:person) ON MAtCH SET n.age =90

8.ORDER By , skip , limit
   ```
      orderby
      match(n) return n order y n.age asc[desc]
      #skip  
      match(n) return n skip 2
      #limit  
      match(n) return n limit 2

  ```    
## Function String
1) left(n.name,3) ==> return just 3 world of the text.
2) ltrim() => delete whitespece.
3) replace ==> l to r.
4) right ==> return from right world.
5) split.
6) substring ==> his name is afshin ,,==> name.
7) Tolower.
## list
you can store a lot of data with one key
```
MATCH(n:cto{name:['amir','afshin']})
```
## index 
fast query  searching , copy from a spesfic properties
```
create index person_index for(n:person) on(n.age)
:schema
```
### Installation

1. **Install Neo4j**:
   - Download and install the Neo4j Community Edition from the [official website](https://neo4j.com/download/).
   
2. **Start Neo4j**:
   - Open the Neo4j application and start the database.

3. **Connect to Neo4j**:
   - Use the default username and password (usually `neo4j` and `neo4j`).

### Usage

1. **Open Neo4j Browser**:
   - Access the Neo4j Browser at `http://localhost:7474`.

2. **Run Cypher Queries**:
   - Example query to create a node:
     ```cypher
     CREATE (n:Person {name: 'John Doe', age: 30})
     ```
   - Example query to find nodes:
     ```cypher
     MATCH (n:Person) RETURN n
     ```
3. Shell docker
   ```
   sudo docker exec -it neo4j cypher-shell -u neo4j -p pass 
   create();
   match(n) return n;
### Learning Resources
- [Neo4j Documentation](https://neo4j.com/docs/)
- [Cypher Query Language](https://neo4j.com/developer/cypher/)
- [Neo4j Tutorials](https://neo4j.com/developer/neo4j-tutorials/)

## Contributing

If you want to contribute to this project, please fork the repository and use a feature branch. Pull requests are warmly welcome.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
