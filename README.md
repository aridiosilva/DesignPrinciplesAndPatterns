# Design Principles And Patterns wiki

"Patterns are a cornerstone of object-oriented design, while test-first programming and merciless refactoring are cornerstones of evolutionary 
design. To stop over- or under-engineering, it’s necessary to learn how patterns fit into the new, evolutionary rhythm of software development." - Joshua Kerievsky

"The only software documentation that actually seems to satisfy the criteria of an engeneering design is the source code listings" - Jack Reevis

## UML Relationships among Classes

- Association
- Inheritance
- Dependency (Composition)

## COHESION

- Is the force thad binds together the code responsible to a single actor.
- Is a measure of how related the functions within a single module are.
- Refers to the degree to which the elements of a module belong together.
- Is a measure of how strongly-related or focused the responsabilities of a single module are.
- High Cohesion is the goal in design of classes, modules and other software artifacts.
- Low Cohesion is bad practice in design of classes, modules and other software artifacts.

## COUPLING or DEPENDENCY

- Refers to the interdependencies between software artifacts
- Is the degree to which each module relies on each one of the the modules.
- High coupling means several dependencies between software artifacts and it is a ba practice of design
- Low Coupling means small dependencies and this is the goal in the design of software artifacts

## Summary of Good Practices of Design

- KISS - Keep it Simple
- DRY - Don´t Repeat Yourself
- TDA - Tell Don´t Ask
- LoD - Law of Demeter - Each Unit Should have only limited knowledge about other units 
- YAGNI - You aren´t gonna need it

## Summary of the Principles of Object-Oriented Design

"The Source Code is the Design" (Uncle Bob C. Martin)

= SOLID PRINCIPLES

- ***SRP - Single Responsability Principle***  -  A class should have only one reason to change
- ***OCP - Open-Closed Principle*** - Classes should be open for extension, but closed for modification
- ***LSP - Liskov Substitution Principle*** - Subtypes must be substitutable for their base types
- ***ISP - Interface Segregation Principle*** - Clients should not be forced to depend upon methods that they do no use. Interfaces belong to clients, not do hierarchies.
- ***DIP - Depedency Inversion Principle*** - Abstractions should not depend upon details. Details should depend upon abstractions.

= COMPONENT COHESION PRINCIPLES

- ***REP - Release - Reuse Equivalency Principle*** - The granule of reuse is the granule of release
- ***CCP - Common Closure Principle*** - The classes in a package should be closed together against the same kinds of changes. A change that affects a closed package affects all the classes in that package no other packages.
- ***CRP - Common Reuse Principle*** - The classes in a package are reused together. If you reuse one of the classes in a package, you reuse them all.

= COMPONENT COUPLINP PRINCIPLES

- ***ADP - Acyclic Deependencies Principle*** - Allow no cycles in the package dependency graph.
- ***SDP Stable Dependencies Principle*** - Depend in the direction of stability.
- ***SAP - Stable Abstraction Principle*** - A package should be as abstract as it is stable.
 
# SOLID Principles

The text in this Wiki is writeen based on the following Books:

- Book Agile Software Development: Principles, Patterns, and Practices by Uncle Bob C. Martin and published in 2002
- Book Clean Architecture - A Handbook of Agile Software Craftsmanship by Uncle Bob C. Marting and published in 2017

## SRP - Single Responsability Principle

A classe should have one, and only one, reason to change. In the context of the SRP, a responsability is "a reason to change". If there are more than one motive for changing a class, then that class has more than one responsability, in this case is violating the SRP Principle.

- One class shoudl have one and only one responsability over the application´s functionality;
- We should write, change and maintain a class only for one purpose;
- A module should have one, and only one, reason to change;
- A module should be responsible to one, only one, user or stakeholder;
- A module should be responsible to one, and only one, actor;
- Considre Module as just a source file in the above definitions;
- The best way to understand this principle is by looking at the symptoms of vilating it;
- Cohesion is the force thar binds together the code responsible to a single actor;
- Single Responsability is about methods and classes. At the component level it becomes the COMMON CLOSURE PATTERN;
- We should design each class to attend just only one actor - this way we can be sure that we are not violating the SRP Principle;

## OCP - Open-Closed Principle

Software systems to be easy to change, hey must be designed to allow the behavior of those systems to be changing by adding new code, rather than changinh existing one.

- The OCP is the driving forces behind the architecture of systems" (Uncle Bob C. Martin)
- If a component A should be protected from changes in component B, then component B should depend on component A (
- A software artifact should be open extension but closed for modification;
- the goal of OCP is to mmake the system easy ti extend without incurring a high impact of change
- This goal is accomplished by partitioning the system into compoenents, and arranging thos components into a dependency hierarchy that protects higher-level components from changes in lower-level components;

## LSP - Liskov Substitution Principle

To build software systems from interchangeable parts, those parts must adhere to a contract that allows those parts to be substituted one for another.

- Derived classes must be substitutable for their base classes.
- Subtypers must be substitutable for their base types.
- Supposing object S is a subtype of object T, then objects of type T may be replaced with objects of type S without altering any of the desirable properties of T.

 -  Don’t change the behavior of the parent or base class in derived classes

The Liskov Substitution Principle (LSP) is a concept in Object Oriented Programming and one of the SOLID principles that was initially introduced by Barbara Liskov in a 1987. This principle states that if a class inherits from a Base class, then the reference to the Base class should be able to be replaced by a Derived class without affecting the functionality of the program. If we inherit from a class, creating a child class, we must make sure that the new derived class only extends functionality without replacing or modifying any of the functionality of the base class. Otherwise the new class could produce undesired effects. In other words you should never modify the behavior of the parent or base class from within derived classes.

In dynamic languages like Ruby, the Liskov principle (LSP) works slightly differently because Ruby less rigidly enforces how types work (so-called “Duck Typing”) as opposed to a language like Java, where type safety is enforced by the compiler. This means that LSP winds up applying more to the messages an object responds to rather than its type.

We should remember that inheritance should be used for specialization. Specialization means creating new subclasses from an existing class so the subclasses can share some behaviour. 

The first consequence of not using LSP is that class hierarchies become a mess. If the class hierarchy grows, it will become more and more complicated to know about the behaviour of the child classes. Secondly, unit tests for the superclass would never succeed for the subclass. The code that uses your type will have to have explicit knowledge of the internal workings of derived types to treat them differently. This tightly couples your code and generally makes the implementation harder to use consistently, and also more difficult to change. In the worst case scenario, LSP violations will introduce bugs in your system because you can’t rely anymore in derived classes. LSP is very easy to break if we don’t pay attention to our derived classes, and this can cause a lot of trouble in the feature. As we can see, there are plenty of things that can go wrong when breaking the LSP, so pay attention to your derived classes and try to avoid breaking the LSP.


### ISP - Interface Segregation Principle

The ISP states that no cliente should be forced to depend on methods it does not use.

- Avoid depending on things that you don´t use.
- Make fine-grained interfaces that are client specific.

- The ISP guides us to create many small interfaces with coherent functionalities instead of a few big interfaces with lots of different methods. When we apply the ISP, class and their dependencies communicate using focused interfaces, minimizing dependencies. Smaller interfaces are easier to implement, improving flexibility and the possibility of reuse.

### DIP - Dependency Inversion Principle

The code that implement high-level policy should not depend on the code that implements low-level details. Rather, details should depend on policies.

- Depend on abstraction, not on concretion.

# Component Cohesion Principles

Which classes belong in which components? This is an important decision, and requires guidamce from good software engineering principles. So, the three principle that helps this decision are:

- REP - Reuse/Release Equivalence Principle
- CCP - Common Closure Principle
- CRP - Common Reuse Principle




# Classification of Programming Languages

![classification](https://github.com/aridiosilva/TDD_ITA/blob/main/DynamicxStatic%20x%20Strng%20x%20Waek%20-%20classification%20of%20programming%20languages.png)

# FACTORY DESIGN PATTERN

The only thing that we can be sure in software development is that the change in the requirements of applications will occur inevitably. So, the business requirements change over time. New product launches, new regulations, effect of competitors, new markets needs, economic factors, adn  so on: there are lots of potential causes for business software to need updating. From those observations we can infer that the code they write is going to change, but not what those changes will be or when they will happen. Writing code in such a way that it can be easily adapted is a skill that takes years to master. How you code your application has a big impact on how easy it is to adapt to meet new requirements. As weprogress through our career, we learn techniques that make adapting code easier. Once we've grasped fundamentals of object-oriented programming we wonder how we ever did without it!

## What is Factory Design Pattern ?

A Factory Pattern or Factory Method Pattern says that just define an interface or abstract class for creating an object but let the subclasses decide which class to instantiate. In other words, subclasses are responsible to create the instance of the class.

The Factory Method Pattern is also known as Virtual Constructor.

The Factory Method pattern is useful when you need to abstract the creation of an object away from its actual implementation. Let’s say the factory will be building a “MobileDevice” product type. A mobile device could be made up of any number of components, some of which can and will change later, depending on advances in technology.

## What is the Factory Pattern used for?

The Factory Method pattern is a design pattern used to define a runtime interface for creating an object. It's called a factory because it creates various types of objects without necessarily knowing what kind of object it creates or how to create it.

## Advantage of Factory Design Pattern

- Factory Method Pattern allows the sub-classes to choose the type of objects to create.
- It promotes the loose-coupling by eliminating the need to bind application-specific classes into the code. That means the code interacts solely with the resultant interface or abstract class, so that it will work with any classes that implement that interface or that extends that abstract class.

## Usage of Factory Design Pattern

- When a class doesn't know what sub-classes will be required to create
- When a class wants that its sub-classes specify the objects to be created.
- When the parent classes choose the creation of objects to its sub-classes.
