###How do JDBC, JPA and Hibernate fit into SpringBoot

So now that you've got your SpringBoot application set up, and you want to be able to interact with your relational database of choice, how would you go about that? This is where JDBC, JPA and Hibernate come in. 

![SpringJPAHibernateDiagram](https://github.com/thidoo/thidoo.github.io/blob/master/images/SpringJPAHibernate.jpg)

Let's explore the concepts on the above diagram

**JDBC - Java Database Connectivity**

* JDBC is a Java API for **connecting** to a database directly and running SQL against it.
	* It provides methods to query and update data in a database, and is oriented towards relational databases
* In SpringBoot, to create this connection, you can configure it in your *application.properties* file:
	
	```
	spring.datasource.url=jdbc:postgresql://localhost:5432/your_dbname
spring.datasource.username=your_username
spring.datasource.password=your_password
	```

**Object Relational Mapping**

* Our Java application contains Java objects, which are designed using Object Oriented Programming System
* Our relational database is designed with Tables and Relations

Object Relational Mapping allows for the mapping from a particular table in your relational database to a particular object in your application.

**Java Persistence API (JPA)**

JPA allows for the **mapping** between objects in your Java application to tables in your relational database. Let's examine the following terms that are central to the operations of JPA:

* **Entity Manager**: once the mappings are defined, the Entity Manager can manage your entities (here, entities refer to the Java objects and tables that have been mapped to each other). It handles all interactions with the database.
	* To do the mapping in SpringBoot, we annotate the Java class with:
	
	```
	@Entity
	@Table(name="table_name")
	public class JavaObject {}
	```
	
* **JPQL (Java Peristence Query Language)**: used to write queries to execute searches against entities
	* These queries are different to SQL queries
	* JPQL queries already understand the mappings that are defined between entities
* **Criteria API**: defines a Java based API to express a JPQL query, in order to execute searches against databases

**JPA and Hibernate**

* JPA is an API
* Hibernate is one of the popular implementations of JPA. It comes as the default implementation for JPA in SpringBoot
	* Hibernate understands the mappings between objects and tables
	* It ensures data is stored and retrieved from the database based on the mappings
	* It also provides additional features on top of JPA. However, depending on these additional features would mean a lock into Hibernate, which means you cannot move to other JPA implementations.

**JPARepository**

* To handle interactions with the database within our Java application, we often create a simple repository interface (e.d. UserRepository) to access information about a particular object such as User.
	* This repository interface should extend the JpaRepository

		```
		@Repository
		public interface UserRepository extends JpaRepository<User, Long> {
		
		}
		```

* JpaRepository extends PagingAndSortingRepository, which in turn extends CrudRepository interface
	* PagingAndSortingRespository has methods:
		
		```
		public abstract Iterable findAll(Sort arg0);
  		public abstract Page findAll(Pageable arg0);
		``` 
	* CrudRepository has methods such as:
	
		```
		save(S entity)
		findOne(ID primaryKey)
		findAll()
		delete()
		```
* Creating your own repository interface which extends JpaRepository allows one to utilise its inherited methods to do basic CRUD operations without having to write those oneself. Other more complex operations or queries can be added to the newly created interface as needed.

**SUMMARY**

* Java application establishes a connection with the database using **JDBC** 
* **JPA** allows for mappings between Java objects and tables in the relational database
	* **Hibernate** is an implementation of JPA
* **JPQL** is the query language used to query entities (mapped objects and tables)
	* **Criteria API** defines the standard for JPQL queries

Hopefully, this post has helped you get a better understanding of the different components that come into play between your SpringBoot application and your relational database. Below is that diagram again to help you visualise where they stand.

![SpringJPAHibernateDiagram](https://github.com/thidoo/thidoo.github.io/blob/master/images/SpringJPAHibernate.jpg)

-----

###REFERENCES

* [Integrating Hibernate and JPA with SpringBoot](http://www.springboottutorial.com/hibernate-jpa-tutorial-with-spring-boot-starter-jpa)
* [Java Database Connectivity](https://en.wikipedia.org/wiki/Java_Database_Connectivity)



