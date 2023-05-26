# General enterprise questions


## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

>N-tier architecture (*also known as multi-tier architecture*) is a software architecture pattern that divides an application into multiple logical layers or 
tiers, each with its own specific functionality and responsibilities. The most common n-tier architecture is the three-tier architecture, which includes a 
presentation tier (*user interface*), application tier (*business logic*), and data tier (*database*). This architecture provides several benefits such 
as scalability, maintainability, and separation of concerns.

Visit exactly that [Stackify](https://stackify.com/n-tier-architecture/) for more information.

#### What are microservices? Advantages and disadvantages?
>Microservices is a software development approach that structures an application as a collection of small, independent, and loosely-coupled services. 
Each microservice is designed to perform a specific business function and can be deployed, scaled, and updated independently of the others.

**Advantages of microservices include:** 

* **Scalability:** Microservices can be scaled up or down independently of each other, allowing for more efficient resource usage.

* **Flexibility:** Each microservice can be developed and maintained by a separate team, allowing for faster innovation and experimentation.

* **Resilience:** A failure in one microservice doesn't necessarily affect the whole system, as the others can continue to function.

* **Technology heterogeneity:** Different microservices can use different technologies, allowing developers to choose the best tool for each job.

**Disadvantages of microservices include:**

* **Complexity:** With many small services communicating with each other, the overall system can become more complex to manage.

* **Distributed computing:** With microservices distributed across multiple servers, network latency and other communication issues can arise.

* **Testing and debugging:** Testing and debugging can become more challenging due to the distributed nature of the architecture.

* **Operational overhead:** Managing many independent services can require more effort in deployment, monitoring, and management.


This is [an material](https://tenesys.io/en/the-benefits-of-containers-for-microservices-heres-what-you-need-to-know/?gclid=CjwKCAiAxvGfBhB-EiwAMPakqnszRm6tIg-07Y86EUnk3rjxFqk2pf589jhNWnWqByclFs0QdMxbORoCECcQAvD_BwE
) inline link.

#### What is Separation of Concerns?
>Separation of concerns is a design principle that advocates dividing a software system into distinct and independent modules, 
with each module being responsible for addressing a single, well-defined concern. By separating different concerns into separate modules, 
the overall system becomes easier to develop, maintain, and modify, since changes to one module are less likely to affect others. 
Separation of concerns also makes the system more modular and reusable, enabling developers to more easily repurpose existing code 
to meet new requirements or to integrate with other systems.

#### What is a layered design and why is it important in enterprise applications?
>A layered design is an architectural pattern used in software development that organizes the system into separate layers, each with a specific responsibility and level of abstraction. Typically, a layered design includes a presentation layer, business logic layer, and data access layer.

>The importance of a layered design in enterprise applications is that it allows for better organization and separation of concerns, making it easier to maintain and modify the system over time. By separating the different aspects of the system into different layers, it also enables developers to work on different parts of the system simultaneously without interfering with each other's work. Additionally, a layered design can make the system more scalable and resilient, as each layer can be scaled independently to meet changing demands.

#### What is Dependency Injection?
>Dependency Injection (DI) is a software design pattern used in object-oriented programming that allows objects to receive dependencies from external sources rather than creating them internally. In other words, instead of an object creating its own dependencies, it is given those dependencies by another object or framework, which makes the code more modular, testable, and maintainable.

#### What is the DAO pattern? When and how to implement?

>The DAO (Data Access Object) pattern is a design pattern used to abstract the underlying persistence storage mechanism and provide a layer of abstraction between the business logic and data storage. The DAO pattern separates the data access code from the rest of the code, making it easier to modify the data storage mechanism without affecting the business logic.

>To implement the DAO pattern, you need to define a DAO interface that defines the methods to perform CRUD (Create, Read, Update, Delete) operations on the data. Then, you create an implementation of this interface that provides the actual implementation of the methods, interacting with the underlying data storage mechanism. The DAO implementation should handle all the details of accessing the data, such as connecting to the database, executing SQL queries, and mapping the data to objects.

>You can implement the DAO pattern whenever you need to separate the data access code from the business logic. This can be useful in large and complex applications where different parts of the application need to access the same data. The DAO pattern makes it easier to maintain the code and make changes to the data storage mechanism without affecting the rest of the application. It also helps to improve the overall modularity and testability of the application.

#### What is SOA? When to use?
>SOA stands for Service-Oriented Architecture. It is an architectural pattern used in software development to create modular and loosely coupled systems. In SOA, a system is decomposed into a collection of services that can be invoked independently of each other through well-defined interfaces.

>SOA is typically used in large and complex enterprise applications where the different parts of the system need to communicate with each other in a flexible and scalable manner. By using a service-oriented approach, the different parts of the system can be developed and maintained independently, which can reduce development time and costs. Additionally, SOA can facilitate integration with third-party systems and services, as the services can be exposed through standard protocols and interfaces.

>When deciding whether to use SOA, it's important to consider the complexity and scalability requirements of the system. SOA is typically most beneficial in large and complex systems with many moving parts, where a modular and loosely coupled architecture can help to reduce complexity and increase flexibility. However, in smaller and less complex systems, a simpler architecture may be more appropriate.

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
>Unit test, integration test, system test, regression test, and acceptance test are different types of software testing that are used to ensure that the software meets its requirements and functions correctly.

* **Unit test:** A unit test is a type of testing that focuses on testing individual units or components of the software in isolation, typically at the code level. It verifies the functionality of a specific piece of code, such as a method or function.

* **Integration test:** Integration testing is a type of testing that verifies that different modules or components of the software work together as expected. It involves testing the interactions between different parts of the software, such as testing the interaction between a database and an application.

* **System test:** System testing is a type of testing that verifies that the entire software system meets its functional and non-functional requirements. It involves testing the software as a whole, including its interactions with other systems and external dependencies.

* **Regression test:** Regression testing is a type of testing that is performed to ensure that changes or updates to the software do not introduce new defects or issues. It involves re-running previously passed tests to ensure that the software still works as expected after changes have been made.

* **Acceptance test:** Acceptance testing is a type of testing that is performed to ensure that the software meets the customer's requirements and is ready for release. It involves testing the software in a real-world scenario, typically by the end-users or stakeholders.

**The major differences between these types of testing are:**

>Scope: Unit tests focus on individual code components, while integration tests focus on interactions between components. System tests focus on the entire system, and acceptance tests focus on the system's compliance with customer requirements.

* **Purpose:** Unit tests are designed to catch defects early in the development process and ensure that individual code components work as expected. Integration tests ensure that the different components of the software work together. System tests verify that the entire system meets its functional and non-functional requirements. Regression tests ensure that changes to the software do not introduce new defects, and acceptance tests verify that the software meets the customer's needs.

* **Timing:** Unit tests are typically run by developers as they write code, while integration tests and system tests are run during the testing phase of the software development lifecycle. Regression tests are run after changes have been made to the software, and acceptance tests are run prior to release to ensure that the software meets customer requirements.
#### What is code coverage? Why is it used? How you can measure?
#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?
#### What is a test case? What is an assertion? Give examples!
#### What is TDD? What are the benefits?
#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)
#### What is arrange/act/assert pattern?

### DevOps

#### What is continuous integration? Why is CI important?
#### Why are tests important in the CI workflow?
#### Name some software that help the CI workflow!
#### What is Continuous Delivery?
#### What is Continuous Deployment?
#### What is DevOps?

### Software Methodologies

#### What kind of software-lifecycle models do you know?
>There are several software lifecycle models, each with its own set of phases and activities. Here are some of the most common models:

* **Waterfall Model:** A linear model where each phase must be completed before moving on to the next phase.
* **Agile Model:** An iterative and incremental model that emphasizes flexibility, collaboration, and customer satisfaction.
* **Spiral Model:** An iterative model that combines the ideas of the Waterfall and Prototyping models, with risk analysis and evaluation at each iteration.
* **V-Model:** A variation of the Waterfall model that emphasizes testing and verification at each stage of development.
* **Iterative Model:** A model where each phase is repeated until the desired level of quality is achieved.
* **Prototype Model:** A model where a working prototype is built to demonstrate the requirements and to test design decisions.
>Each model has its own strengths and weaknesses, and the choice of model will depend on the project's specific requirements, timeline, and resources.

#### What is a UML diagram? What kind of diagram types do you know?
#### What is a UML class diagram? What are the typical elements?
>A UML class diagram is a type of diagram used in software engineering to visually represent the classes, interfaces, associations, and dependencies of a system or software application. It provides a high-level overview of the system's structure and relationships between its components.

**The typical elements of a UML class diagram include:**

1. **Class:** A template for creating objects that defines the attributes (data) and methods (behavior) that the objects will have.

2. **Interface:** A collection of methods that define a contract that must be implemented by any class that implements the interface.

3. **Association:** A relationship between two classes that indicates that they are somehow related, such as a "has-a" or "is-a" relationship.

4. **Multiplicity:** A notation used to indicate the number of instances of a class that can be associated with instances of another class.

5. **Inheritance:** A relationship between classes where one class is a subclass of another, inheriting all of its attributes and behaviors.

6. **Dependency:** A relationship between two classes where one class relies on the other in some way, such as by using one of its methods or attributes.

7. **Visibility:** A notation used to indicate the access level of a class's attributes and methods, such as public, private, or protected.

8. **Abstract classes:** Classes that cannot be instantiated on their own but provide a template for creating concrete classes that inherit their attributes and methods.

>Overall, a UML class diagram provides a visual representation of a system's structure and relationships between its components, helping developers to better understand and design the system.
#### What kind of design patterns do you know? Bring at least 3 examples.
#### What is the purpose of the Iterator Pattern?
#### What do you know about the SOLID principles?
>The SOLID principles are a set of five design principles intended to help software developers design systems that are easy to maintain, extend, and refactor. 

**The five principles are:**

1. **Single Responsibility Principle (SRP):** A class should have only one reason to change.

2. **Open-Closed Principle (OCP):** Software entities should be open for extension but closed for modification.

3. **Liskov Substitution Principle (LSP):** Subtypes should be substitutable for their base types.

4. **Interface Segregation Principle (ISP):** Clients should not be forced to depend on interfaces they do not use.

5. **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules; both should depend on abstractions.

>By following these principles, developers can create systems that are easier to test, modify, and extend, with less coupling between different components.

#### How would you separate data storage code and business logic code (which uses stored data) in an application?

## Computer science

### Data Structures
#### What is the difference between Stack and Queue data structure?
#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
#### What are trees? What are binary trees? What are binary search trees?
#### How can you store graphs in programs? What are the advantages/disadvantages per each?
#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?
#### How does dictionary work?
#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

### Algorithms
#### What is QuickSort? Describe the main logic of this sorting algorithm.

## Software design

### Security

#### What is OAuth2?
#### What is Basic Authentication?
#### What is CORS, why it’s needed in browsers?
#### How can you initialize a CSRF attack?
#### What is JWT used for? Where to store it on client side?

### Threaded programming

#### When do you need to use threads in an application?
#### What is a daemon thread?
#### What is the difference between concurrent and parallel execution of code?
#### What is the most important problem developers are faced when using threads?
#### In what kind of situations can deadlocks occur?
#### What are possible ways to prevent deadlocks from occurring?
#### What does critical section or critical region mean in the context of concurrent programming?
