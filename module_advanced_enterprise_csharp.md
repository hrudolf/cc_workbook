# Enterprise module (C# branch)

## ASP.NET Core

### What Is the difference between .NET Core and .NET Standard? How do they relate to the "classic" .NET Framework?

.NET Standard: is the specification that defines the set of APIs that all .NET implementations must provide. It is only used to develop class libraries. .NET Standard is a successor of the portable class library. A .NET Standard library can be used to share code between different .NET implementations (.NET Core, .NET Framework).
<br>
.NET Framework: original implementation of .NET to build Web and Desktop application for Windows (in C#, F#, VB). <br>
Two components: CLR Common language runtime that handles the execution of application. <br>
BCL Base Class Library: provides a library of tested and reusable code that developers can use in their application.<br>
Code is compiled into Intermediate Language and stored in assembly files with .dll or .exe extensions. When the application runs, CLR turns the assembly into machine code with a process called JIT (just in time) compilation. The .NET Framework provides memory management, common type system, language interoperability.<br>
<br>
.NET Core: New framework to run on other OS also. Written from scratch, dropping backwards compatibility, making it much faster. It is open source, cross-platform implementation of .NET. It also has class libraries, CLR, compilers, languages, application frameworks. Supports multiple architectures, x64, x86, ARM.<br>

### What is ASP.NET MVC?

It is an open source software from Microsoft. MVC stands for Model View Controller, it is a design pattern / architecture used to achieve separation of concerns of User Interface (View), Data (Model) and Application logic (Controller). It separates an application into 3 main logical components.

### Can you explain Model, Controller and View in MVC?

They are the three main logical components of the MVC pattern. Each of these are built to handle specific development aspects of an application.

https://www.tutorialspoint.com/mvc_framework/mvc_framework_introduction.htm

![MVC Diagram](https://developer.mozilla.org/en-US/docs/Glossary/MVC/model-view-controller-light-blue.png)

The Model component corresponds to all the data-related logic that the user works with. This can represent either the data that is being transferred between the View and Controller components or any other business logic-related data. E.g. a Customer object will retrieve the customer information from the database, manipulate it and update the data back to the DB or use it to render data.

The View component is used for all the UI logic of the app. E.g. the Customer view will include all the UI components that the user interacts with.

The Controllers act as an interface between Model and View components to process all the business logic and incoming requests, manipulate data using the Model component and interact with the Views to render the final output. E.g the Customer controller will handle all the interactions and inputs from the Customer View and update the database using the Customer Model. The same controller will be used to view the Customer data.

### Explain the request lifecycle of ASP.NET Core.

https://www.c-sharpcorner.com/article/asp-net-core-mvc-request-life-cycle/

The ASP.NET Core MVC Request Life Cycle is a sequence of events, stages or components that interact with each other to process an HTTP request and generate a response that goes back to the client.

![ASP.NET Core MVC Request Life Cycle](https://f4n3x6c5.stackpathcdn.com/article/asp-net-core-mvc-request-life-cycle/Images/Picture1.png)

Middlewares: They form the basic building block of application HTTP pipeline. These are a series of components that are combined to form a request pipeline in order to handle any incoming request.

The request is first routed. The routing middleware decides how an incoming request can be mapped to Controllers and action methods.

Then the initialization and execution of controllers take place. Controllers are responsible for handling incoming requests. The controller selects the appropriate action method.

The selected action method is executed and return a view which contains Html document to be returned as response to the browser.

### What is Razor View Engine?

https://www.c-sharpcorner.com/article/learn-about-razor-view-engine/

Razor View Engine is a markup syntax which helps write HTML and server-side code in web pages using C# or VB.NET. It is server-side markup language and not a prog language.

Razor is a templating engine and ASP.NET MVC has implemented a view engine which allows us to use Razor inside of an MVC application to produce HTML.

Razor Syntax is compact, but easy to learn.

### What you mean by Routing in ASP.NET Core?

Routing is the process of directing HTTP requests to the right controller. The middleware must decide whether a request should go to the controller for processing or not. The midware makes the decision based on the URL and some config info. This is known as convention based routing. https://www.simplilearn.com/tutorials/asp-dot-net-tutorial/asp-dot-net-core

### What is Layout in ASP.NET MVC?

Layouts are used in MVC to provide a consistent look and feel on all the pages of our application. https://www.tutorialspoint.com/mvc_framework/mvc_framework_layouts.htm

### What are the three possible lifecycles for an object created by the ASP.NET Dependency Injection module? 

https://www.c-sharpcorner.com/article/differences-between-scoped-transient-and-singleton-service/

The DI container has to decide whether to return a new object of the service or consume an existing instance. The lifetime of a Service depends on how we instantiate the dependency. We define the lifetime when we register the service.

Three types:
- Scoped: with every HTTP request we create one new instance, the same instance is provided for the entire scope of that request.

- Transient: a new instance is created for each object (!) in the HTTP request. Good for multithreading, because these instances are independent of each other. It can cause more memory and resouce usage, so can be negative for performance. It should be utilized for services with little or no state.

- Singleton: only one service instance is created throughout the lifetime, the same instance is reused in the future, wherever the service is required. Watch out for memory leaks, but it is memory efficient.

### What is wwwroot folder in ASP.NET Core?

https://www.tutorialsteacher.com/core/aspnet-core-wwwroot

The wwwroot folder is treated as a web root folder. Static files can be stored here (and its subfolders, but only in ASP.NET, not Core) and accessed with a relative path. Middleware is needed to serve these static files. It can be renamed, but has to be renamed in Program.cs by .UseWebRoot("FolderName").

### What’s the usage of [InternalsVisibleTo] attribute? What are pros and cons of it?

It provides information about the internal state of a class to members of a different, specified assembly. For example it lets a test project see state of "internal" members (not private) of a class.

http://grabbagoft.blogspot.com/2007/10/double-edged-sword-of.html

Pros:
- allows test libraries to access internal classes and methods for additional testing and coverage,
- keeps your public API limited to what you want to publish,
- provides greater flexibility for internal refactoring and backwards compatibility.

Cons:
- easily abused -> "internal" instead of "private",
- potential loss of encapsulation,
- decision about what should be public could be wrong,
- two levels of "public" visibility that have to be managed,
- enforces bi-directional dependencies between assemblies.



## Object Relational Mapping, Entity Framework

### What is an ORM? What are benefits, when to use?

https://www.freecodecamp.org/news/what-is-an-orm-the-meaning-of-object-relational-mapping-database-tools/

ORM stands for Object Relational Mapping, it is a technique used in creating a bridge between object-oriented programs and relational databases. ORM is a layer that connects OOP to relational databases. ORM tools help simplify the interaction between relational databases and different OOP languages by performing CRUD operation on the database and the programmer not having to write database queries themselves (SQL commands managed by the ORM Tool).

Advantages of using an ORM Tools:
- speeds up dev time,
- decreases cost of dev,
- handles the logic required to interact with DB,
- improves security - ORM tools are built to eliminate the possibility of SQL injection attacks,
- having to write less code.

Disadvantages of using ORM Tools:
- learning to use ORM Tool is time consuming,
- performance likely lower for complex queries,
- generally slower than pure SQL.

### What is Entity Framework? What are the advantages, limitations?

https://www.entityframeworktutorial.net/what-is-entityframework.aspx

Entity Framework is an open source ORM framework for .NET applications to enable developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write.

![Alt text](https://www.entityframeworktutorial.net/images/basics/ef-in-app-architecture.png)

Features:
- cross-platform,
- Modelling: EF creates an EDM (entity data model) based on POCO (Plain Old CLR Object) entities with get/set properties of different data types. It uses this model when querying or saving entity data to the underlaying databse,
- Querying: EF allows the use of LINQ queries to retrieve data from the DB, LINQ query will be translated to database-specific query. Raw SQL query execution is also possible,
- Change tracking: EF keeps track of changes made to instances of your entities which need to be submitted to the DB,
- Saving: EF executes INSERT, UPDATE, DELETE commands to the DB based on the changes occured to your entities when SaveChanges() or SaveChangesAsync() methods are called.
- Concurrency: EF uses Optimistic Concurrency to protect overwriting changes made by another user since data was fetched from the DB.
- Caching: First level caching out of the box. Repeated querying will return data from the cache instead of the DB.
- Conventions over configuration, many defaults.
- Configurations possible
- Migrations: EF provides a set of migration commands that can be executed in the Console to create or manage underlying database Schema.

Advantages:
- provides auto generated code,
- reduce dev time, cost,
- code first database modeling,
- using LINQ on Objects, etc

Disadvantages:
- Lazy loading,
- Complicated syntax (?),
- Does not handle all relational database management systems,
- Data handling is "non-traditional".

### What is lazy loading?

https://www.tutorialspoint.com/entity_framework/entity_framework_lazy_loading.htm

Lazy loading is the process when an entity or collection of entities is automatically loaded from the database not when a query is made, but when the result of the query is used.

When using POCO (Plain Old CLR Object) entity types, lazy loading is achieved by creating instances of derived proxy types and hten overriding virtual properties to add the loading hook.

https://dotnettutorials.net/lesson/lazy-loading-vs-eager-loading-in-entity-framework/

It is the default in Entity Framework, but can be modified. Lazy loading is not done if a property is not defined as virtual. (Property must be virtual for EF to use lazy loading).

### What is the difference between code first and DB first approach?

https://www.chubbydeveloper.com/code-first-vs-database/

Code First:
In Code First approach, entities or classes are created first with the primary focus on the domain of an application. You can start creating classes and required properties, without designing the database that matches the entities. Then the Entity Framework creates the tables and database accordingly and when the code is run, the database is created.

Advantages: 
- db and tables are created from classes,
- recommended for small apps that do not involve extensive data processing,
- collections for eager loading and serialization can be specified,
- modifications can be done easily in the code.

Disadvantages:
- code is needed for creating the db,
- at db change, the app has to be changed,
- relatively difficult to manage the db through code, not recommended for data extensive applications

Database first:
In Database First approach, database and the related tables are created first. After that, you can create an entity data models based on the database. It is easier to create a database, as there are multiple options are available by using graphical user interfaces.

Advantages:
- GUI for db and table creation,
- preferred for large and data-driven apps,
- easier to create keys and relationships without writing extra code for it,
- when a DB already exists

Disadvantages:
- If there is a change, model class needs to be updated,
- creating and managing of keys and relationships requires more coding

### What is a migration script?

https://docs.xperience.io/xp/developers-and-admins/ci-cd/ci-cd-database-migration-scripts

A migration script allows you to alter a database by modifying its schema. This alteration can be as simple as adding or removing a column, or a complex refactoring task such as splitting tables or changing column properties in a way that could affect the stored data.

### What is a navigation property?

https://learn.microsoft.com/en-us/ef/ef6/fundamentals/relationships

Navigation properties provide a way to navigate an association between two entity types. Every object can have a navigation property for every relationship in which it participates. Navigation properties allow you to navigate and manage relationships in both directions, returning either a reference object (if the multiplicity is either one or zero-or-one) or a collection (if the multiplicity is many). You may also choose to have one-way navigation, in which case you define the navigation property on only one of the types that participates in the relationship and not on both.

It is recommended to include properties in the model that map to foreign keys in the database. With foreign key properties included, you can create or change a relationship by modifying the foreign key value on a dependent object. This kind of association is called a foreign key association. Using foreign keys is even more essential when working with disconnected entities. Note, that when working with 1-to-1 or 1-to-0..1 relationships, there is no separate foreign key column, the primary key property acts as the foreign key and is always included in the model.

### Name 3 different attributes used in EF Core, what can they do for you?

https://www.learnentityframeworkcore.com/configuration/data-annotation-attributes

- `[DatabaseGenerated]`: specifies how the db generates values for a property,
- `[ForeignKey]`: specifies the property is used as a foreign key in a relationship,
- `[Key]`: identifies one or more properties as a Key,
- `[Required]`: Specifies that a property's value is required,
- `[MaxLength]`: Sets the maximum allowed length of the property value (string or array),
- `[StringLength]`: Sets the max allowed length of the property value (string or array)