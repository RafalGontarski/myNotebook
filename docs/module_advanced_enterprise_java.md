# Enterprise module (Java branch)

#### Error vs. exceptions
#### How to create an instance of a public nonstatic internal class outside of its containing class?
#### JRE vs JDK vs JVM?
#### What are the differences between a shallow copy and a deep copy?
#### What does "volatile" keyword means?
#### What is a Dependency Injection?
#### What is a Java Bean?
#### What is a nested class?
#### What is an annonymous class?
#### What is String Pool?
#### What is the difference between static and non static internal class?
#### Why should we override hashCode() method when we override equals() method?
#### What are the differences between Stream methods `findFirst` and `findAny`?
#### What are the differences between Stream methods `map` and `flatMap`?
#### What are the differences between Stream methods `reduce` and `collect`?
#### What do the ... dots in the method parameters mean?

[//]: # (### Java Enterprise and Spring)

[//]: # ()
[//]: # (#### What are the possible uses of reflection?)

[//]: # (#### What is Spring?)

[//]: # (>Spring is an open-source framework for building enterprise-level Java applications. It provides a comprehensive programming and configuration model for modern Java-based enterprise applications, covering a wide range of areas such as web applications, security, data access, and more.)

[//]: # ()
[//]: # (>The Spring framework is based on several core principles, including dependency injection, aspect-oriented programming, and inversion of control. These principles help to promote modularity, testability, and maintainability in the application development process.)

[//]: # ()
[//]: # (>Spring also provides a wide range of modules and extensions, such as Spring MVC for web application development, Spring Security for authentication and authorization, and Spring Data for working with databases. Additionally, Spring integrates with many third-party libraries and frameworks, making it a versatile and flexible tool for enterprise application development.)

[//]: # ()
[//]: # (>Overall, Spring is a popular and powerful framework for developing enterprise-level Java applications, with a strong community and extensive documentation and support.)

[//]: # (#### What is Spring Boot?)

[//]: # (>Spring Boot is a framework built on top of the Spring framework that simplifies the process of building and deploying standalone, production-ready Spring applications. It provides an opinionated approach to application configuration and setup, eliminating the need for developers to manually configure and manage many of the underlying technologies and frameworks.)

[//]: # ()
[//]: # (**Spring Boot provides several key features that make it an attractive option for developers, including:**)

[//]: # ()
[//]: # (1. **Autoconfiguration:** Spring Boot provides a wide range of default configurations for many common technologies and frameworks, such as embedded web servers, databases, and security, which can be easily customized or extended as needed.)

[//]: # ()
[//]: # (2. **Embedded servers:** Spring Boot includes an embedded web server, such as Tomcat or Jetty, which makes it easy to develop and test web applications without the need for an external server.)

[//]: # ()
[//]: # (3. **Developer tools:** Spring Boot includes several tools and features that make it easy to develop and test applications, such as hot reloading, which automatically refreshes the application when changes are made.)

[//]: # ()
[//]: # (4. **Production-ready features:** Spring Boot includes several production-ready features, such as health checks, metrics, and distributed tracing, which make it easier to monitor and manage applications in production environments.)

[//]: # ()
[//]: # (>Overall, Spring Boot simplifies the process of building and deploying production-ready Spring applications, allowing developers to focus on building high-quality features and functionality.)

[//]: # (#### What is the major difference between the Standard edition &#40;JSE&#41; and Enterprise edition &#40;JEE&#41;? You can choose Spring &#40;Spring Boot&#41; instead of JavaEE. Focus on comparing them.)

[//]: # (#### What are the advantages of the Spring Framework? Focus on the Core part.)

[//]: # (#### What is a servlet? What is the purpose of DispatcherServlet in Spring?)

[//]: # (#### When do you use RestControllers, when just simple Controllers?)

[//]: # (#### What is Spring Application Context?)

[//]: # (#### What are the main ways to define a bean in the Application Context?)

[//]: # (#### Difference between .jar and .war files.)

[//]: # (#### What are the major differences between Maven, Ant and Gradle?)

[//]: # (#### What is Maven used for?)

[//]: # (#### What does a pom.xml file contains in Maven?)

[//]: # (### Object Relational Mapping, JPA)

[//]: # ()
[//]: # (#### What is an ORM? What are the benefits, when to use?)

[//]: # (>ORM stands for Object-Relational Mapping. It is a programming technique that allows developers to interact with a relational database using an object-oriented paradigm.)

[//]: # ()
[//]: # (**The benefits of using an ORM include:**)

[//]: # ()
[//]: # (* **Improved productivity:** ORMs can significantly reduce the amount of code needed to interact with a database, which can increase productivity.)

[//]: # ()
[//]: # (* **Portability:** ORMs provide a level of abstraction between the application and the database, which can make it easier to switch between different database management systems.)

[//]: # ()
[//]: # (* **Security:** ORMs can help prevent SQL injection attacks by properly escaping special characters in user input.)

[//]: # ()
[//]: # (* **Maintainability:** ORMs provide a standardized way of accessing and manipulating data, which can make it easier to maintain and update an application over time.)

[//]: # ()
[//]: # (>When to use an ORM depends on the specific requirements of the project. ORMs can be a good choice for applications that need to interact with a database frequently or that require complex queries. However, for simple applications or those with very specific performance requirements, using raw SQL may be more appropriate.)

[//]: # (#### What is the difference between JDBC and JPA? Which are the advantages and disadvantages of each? Give a general overview.)

[//]: # (>JDBC &#40;Java Database Connectivity&#41; is a Java API for connecting and interacting with relational databases, whereas JPA &#40;Java Persistence API&#41; is a higher-level abstraction on top of JDBC that provides a standardized way of mapping Java objects to database tables.)

[//]: # ()
[//]: # (**Advantages of JDBC include:**)

[//]: # ()
[//]: # (* **Flexibility:** JDBC provides fine-grained control over database interactions, allowing developers to optimize queries for specific use cases.)

[//]: # ()
[//]: # (* **Performance:** JDBC can be faster than using a higher-level abstraction like JPA, especially for complex queries or large datasets.)

[//]: # ()
[//]: # (* **Familiarity:** JDBC is a widely-used API that many Java developers are already familiar with.)

[//]: # ()
[//]: # (**Disadvantages of JDBC include:**)

[//]: # ()
[//]: # (* **Complexity:** JDBC can be complex to use, especially for developers who are not familiar with SQL or relational database concepts.)

[//]: # ()
[//]: # (* **Boilerplate code:** JDBC code can be verbose and require a lot of boilerplate code to handle database interactions.)

[//]: # ()
[//]: # (**Advantages of JPA include:**)

[//]: # ()
[//]: # (* **Productivity:** JPA can significantly reduce the amount of code needed to interact with a database, increasing productivity.)

[//]: # ()
[//]: # (* **Portability:** JPA provides a level of abstraction between the application and the database, making it easier to switch between different database management systems.)

[//]: # ()
[//]: # (* **Maintainability:** JPA provides a standardized way of accessing and manipulating data, making it easier to maintain and update an application over time.)

[//]: # ()
[//]: # (**Disadvantages of JPA include:**)

[//]: # ()
[//]: # (* **Performance:** JPA can be slower than using a lower-level API like JDBC, especially for complex queries or large datasets.)

[//]: # ()
[//]: # (* **Limited control:** JPA abstracts away many details of database interactions, which can make it difficult to optimize queries for specific use cases.)

[//]: # ()
[//]: # (>In general, JDBC is a good choice for applications with specific performance requirements or complex queries, while JPA can be a good choice for applications where productivity and maintainability are the primary concerns.)

[//]: # (#### What is Hibernate? What are the advantages, limitations?)

[//]: # (>Hibernate is a popular Object-Relational Mapping &#40;ORM&#41; framework for Java that provides a way to map Java objects to relational database tables and vice versa. It simplifies the task of developing database-driven applications by abstracting away many of the low-level details of JDBC &#40;Java Database Connectivity&#41; code.)

[//]: # ()
[//]: # (**Advantages of using Hibernate include:**)

[//]: # ()
[//]: # (* **Saves time and effort:** Hibernate reduces the amount of JDBC code that needs to be written, making it faster and easier to develop database applications.)

[//]: # ()
[//]: # (* **Object-oriented approach:** Hibernate allows developers to work with objects and classes instead of tables and SQL, which makes the code more readable and easier to maintain.)

[//]: # ()
[//]: # (* **Database independence:** Hibernate provides a layer of abstraction between the application and the database, which makes it possible to switch between different databases without changing the code.)

[//]: # ()
[//]: # (* **Cache management:** Hibernate has built-in caching mechanisms that improve the performance of database access.)

[//]: # ()
[//]: # (>Supports lazy loading: Hibernate supports lazy loading of objects, which means that objects are loaded into memory only when needed, reducing memory usage and improving performance.)

[//]: # ()
[//]: # (**Limitations of using Hibernate include:**)

[//]: # ()
[//]: # (* **Steep learning curve:** Hibernate has a complex API, which can take some time to learn and master.)

[//]: # ()
[//]: # (* **Performance issues:** Hibernate's caching mechanisms can cause performance issues if not used properly, and lazy loading can result in a large number of database queries if not optimized correctly.)

[//]: # ()
[//]: # (* **Overhead:** Hibernate adds an extra layer of abstraction between the application and the database, which can result in some overhead and potentially slow down the application.)

[//]: # ()
[//]: # (>Vendor lock-in: Hibernate may limit the choice of databases, as not all databases are fully supported.)

[//]: # (#### Name 3 different annotations used in JPA, what can they do for you?)

[//]: # (#### What is object-relational impedance mismatch?)

[//]: # (#### What is a JpaRepository? What are the 2 main methods to define queries in them?)

[//]: # (#### Why is the Set preferred over List when we want to store OneToMany relations?)

[//]: # (#### What kind of inheritance strategies are available? Which annotations are used to solve this?)
