# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
   N-tier architecture (also known as multi-tier architecture) is a software architecture pattern that divides an application into multiple logical layers or 
tiers, each with its own specific functionality and responsibilities. The most common n-tier architecture is the three-tier architecture, which includes a 
presentation tier (user interface), application tier (business logic), and data tier (database). This architecture provides several benefits such 
as scalability, maintainability, and separation of concerns.

* https://stackify.com/n-tier-architecture/


#### What are microservices? Advantages and disadvantages?
   Microservices is a software development approach that structures an application as a collection of small, independent, and loosely-coupled services. 
Each microservice is designed to perform a specific business function and can be deployed, scaled, and updated independently of the others.

Advantages of microservices include:

* Scalability: Microservices can be scaled up or down independently of each other, allowing for more efficient resource usage.

* Flexibility: Each microservice can be developed and maintained by a separate team, allowing for faster innovation and experimentation.

* Resilience: A failure in one microservice doesn't necessarily affect the whole system, as the others can continue to function.

* Technology heterogeneity: Different microservices can use different technologies, allowing developers to choose the best tool for each job.

Disadvantages of microservices include:

* Complexity: With many small services communicating with each other, the overall system can become more complex to manage.

* Distributed computing: With microservices distributed across multiple servers, network latency and other communication issues can arise.

* Testing and debugging: Testing and debugging can become more challenging due to the distributed nature of the architecture.

* Operational overhead: Managing many independent services can require more effort in deployment, monitoring, and management.

https://tenesys.io/en/the-benefits-of-containers-for-microservices-heres-what-you-need-to-know/?gclid=CjwKCAiAxvGfBhB-EiwAMPakqnszRm6tIg-07Y86EUnk3rjxFqk2pf589jhNWnWqByclFs0QdMxbORoCECcQAvD_BwE

#### What is Separation of Concerns?
   Separation of concerns is a design principle that advocates dividing a software system into distinct and independent modules, 
with each module being responsible for addressing a single, well-defined concern. By separating different concerns into separate modules, 
the overall system becomes easier to develop, maintain, and modify, since changes to one module are less likely to affect others. 
Separation of concerns also makes the system more modular and reusable, enabling developers to more easily repurpose existing code 
to meet new requirements or to integrate with other systems.

#### What is a layered design and why is it important in enterprise applications?
#### What is Dependency Injection?
#### What is the DAO pattern? When and how to implement?
#### What is SOA? When to use?

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
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
There are several software lifecycle models, each with its own set of phases and activities. Here are some of the most common models:

* Waterfall Model: A linear model where each phase must be completed before moving on to the next phase.
* Agile Model: An iterative and incremental model that emphasizes flexibility, collaboration, and customer satisfaction.
* Spiral Model: An iterative model that combines the ideas of the Waterfall and Prototyping models, with risk analysis and evaluation at each iteration.
* V-Model: A variation of the Waterfall model that emphasizes testing and verification at each stage of development.
* Iterative Model: A model where each phase is repeated until the desired level of quality is achieved.
* Prototype Model: A model where a working prototype is built to demonstrate the requirements and to test design decisions.
Each model has its own strengths and weaknesses, and the choice of model will depend on the project's specific requirements, timeline, and resources.

#### What is a UML diagram? What kind of diagram types do you know?
#### What is a UML class diagram? What are the typical elements?
#### What kind of design patterns do you know? Bring at least 3 examples.
#### What is the purpose of the Iterator Pattern?
#### What do you know about the SOLID principles?
The SOLID principles are a set of five design principles intended to help software developers design systems that are easy to maintain, extend, and refactor. 
The five principles are:

* Single Responsibility Principle (SRP): A class should have only one reason to change.
* Open-Closed Principle (OCP): Software entities should be open for extension but closed for modification.
* Liskov Substitution Principle (LSP): Subtypes should be substitutable for their base types.
* Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use.
* Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules; both should depend on abstractions.
By following these principles, developers can create systems that are easier to test, modify, and extend, with less coupling between different components.

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
