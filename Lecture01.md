## Flat file:     
such as comma-separated value (CSV) files  
problems:
+ data integrity: validity, same values, removal
+ implementation: efficiency, cocurrency
+ durability: crash, replicate  

从 flat file 在存储,使用上的问题引出 DBMS 存在的必要

## Database management system (DBMS):
a software that allows applications to store and analyze information in a database  
purpose: allow the definition, creation, querying, update, and administration of databases

提到了sqlite，运行在移动端的数据库，是数量最多的数据库

## Relational model
Proposed in 1970 by Ted Codd  
"A Relational Model of Data for Large Shared Data Banks"  
关系模型开山之作

## Data models
1. data model:  
a collection of concepts for describing the data in a database
2. schema (模式):  
a description of a particular collection of data, using a given data model

schema和catalog的理解 [来源](https://www.zhihu.com/question/20355738/answer/1241628708):  
+ 在关系型数据库中，分三级：database.schema.table。即一个数据库下面可以包含多个schema，一个schema下可以包含多个数据库对象，比如表、存储过程、触发器等。但并非所有数据库都实现了schema这一层，比如mysql直接把schema和database等效了，PostgreSQL、Oracle、SQL server等的schema也含义不太相同。
+ 所以说，关系型数据库中没有catalog的概念。但在一些其它地方（特别是大数据领域的一些组件）有catalog的概念，也是用来做层级划分的，一般是这样的层级关系：catalog.database.table。

## Catagory
1. Relational: Most DBMSs
2. NoSQL: Key/Value, Graph, Document, Column-family
3. Machine Learning: Array/Matrix
4. Obsolete/Legacy/Rare: Hierarchical, Network, Multi-Value  

几类常见的数据库，NoSQL同样需要学习，也很重要

## Concepts about relational model
1. Components:
    + Structure: The definition of the database's relations and their contents.
    + Integrity: Ensure the database's contents satisfy constraints.
    + Manipulation: Programming interface for accessing and modifying a database's contents.
2. Relation:  
an unordered set that contain the relationship of attributes that represent entities
3. Tuple (元组):  
    + a set of attribute values (also known as its domain 域) in the relation.  
    + values are normally atomic/scalar (原子化/标量).
    + NULL is a member of every domain.
    + n-ary Relation (n元关系) = Table with n columns
4. Primary keys (主键):
    + uniquely identifies a single tuple
    + random or increment values
5. Foreign keys (外键):
    + specifies that an attribute from one relation has to map to a tuple in another relation
    + e.g. ArtistAlbum(artist_id, album_id) has two foreign keys for Artist(id, name, year, country) and Album(id, name, artists, year)

## Data manipulation languages (DML)
Methods to store and retrieve information from a database.  
包含三个层面: SQL 关系代数 关系演算
1. Procedural:
    + Relational Algebra (关系代数)
    + The query specifies the (high-level) strategy the DBMS should use to find the desired result.
    + 一步步规定好查询的每个步骤
2. Non-Procedural (Declarative):
    + Relational Calculus (关系演算)
    + The query specifies only what data is wanted and not how to find it.
    + 只是指明想要查找到的数据是什么，实现交给DBMS

## Relational algebra
1. Fundamental operators:
    + Each operator takes one or more relations as its inputs and ouputs a new relation
    + Select: 按条件(合取 析取)选择
    + Projection: 改变顺序，修改值(b_id-100)
    + Union
    + Intersection
    + Difference
    + Product: 笛卡尔积
    + Join (自然连接): 两个关系都有的属性只取一个
2. Extra operators:  
Rename, Assignment, Duplicate Elimination, Aggregation, Sorting, Division
3. 关系代数仍然定义了如何计算一个查询的高层次步骤, 而更好的方法是向DMBS陈述你想要计算的高层次查询结果
4. Relational algebra defines the primitives (理解为原型) for processing queries on a relational database.

## Queries
The relational model is independent of any query language implementation, while SQL is the de facto standard (many dialects).
