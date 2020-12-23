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

- SoC - Separation of Concerns
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

# SoC - Separation of Concerns

## What is SoC?

In Software Engineering, Sseparation of concerns (SoC) is a design principle for separating a computer program into distinct sections such that each section addresses a separate concern. A concern is a set of information that affects the code of a computer program. A concern can be as general as "the details of the hardware for an application", or as specific as "the name of which class to instantiate". A program that embodies SoC well is called a modular[1] program. Modularity, and hence separation of concerns, is achieved by encapsulating information inside a section of code that has a well-defined interface. Encapsulation is a means of information hiding.[2] Layered designs in information systems are another embodiment of separation of concerns (e.g., presentation layer, business logic layer, data access layer, persistence layer).[3]

Separation of concerns results in more degrees of freedom for some aspect of the program's design, deployment, or usage. Common among these is increased freedom for simplification and maintenance of code. When concerns are well-separated, there are more opportunities for module upgrade, reuse, and independent development. Hiding the implementation details of modules behind an interface enables improving or modifying a single concern's section of code without having to know the details of other sections and without having to make corresponding changes to those other sections. Modules can also expose different versions of an interface, which increases the freedom to upgrade a complex system in piecemeal fashion without interim loss of functionality.[citation needed]

Separation of concerns is a form of abstraction. As with most abstractions, separating concerns means adding additional code interfaces, generally creating more code to be executed. So despite the many benefits of well-separated concerns, there is often an associated execution penalty.[citation 

# Origin of The Separation of Concerns Concept

The term separation of concerns was probably coined by Edsger W. Dijkstra in his 1974 paper "On the role of scientific thought".[6]

 - Let me try to explain to you, what to my taste is characteristic for all intelligent thinking. It is, that one is willing to study in depth an aspect of one's subject matter in isolation for the sake of its own consistency, all the time knowing that one is occupying oneself only with one of the aspects. We know that a program must be correct and we can study it from that viewpoint only; we also know that it should be efficient and we can study its efficiency on another day, so to speak. In another mood we may ask ourselves whether, and if so: why, the program is desirable. But nothing is gained —on the contrary!— by tackling these various aspects simultaneously. It is what I sometimes have called "the separation of concerns", which, even if not perfectly possible, is yet the only available technique for effective ordering of one's thoughts, that I know of. This is what I mean by "focusing one's attention upon some aspect": it does not mean ignoring the other aspects, it is just doing justice to the fact that from this aspect's point of view, the other is irrelevant. It is being one- and multiple-track minded simultaneously.

Fifteen years later, it was evident the term Separation of Concerns was becoming an accepted idea. In 1989, Chris Reade wrote a book titled "Elements of Functional Programming"[7] that describes separation of concerns:

The programmer is having to do several things at the same time, namely,

 - describe what is to be computed;
 - organise the computation sequencing into small steps;
 - organise memory management during the computation.
 
 Reade continues to say,

- Ideally, the programmer should be able to concentrate on the first of the three tasks (describing what is to be computed) without being distracted by the other two, more administrative, tasks. Clearly, administration is important, but by separating it from the main task we are likely to get more reliable results and we can ease the programming problem by automating much of the administration.

- The separation of concerns has other advantages as well. For example, program proving becomes much more feasible when details of sequencing and memory management are absent from the program. Furthermore, descriptions of what is to be computed should be free of such detailed step-by-step descriptions of how to do it, if they are to be evaluated with different machine architectures. Sequences of small changes to a data object held in a store may be an inappropriate description of how to compute something when a highly parallel machine is being used with thousands of processors distributed throughout the machine and local rather than global storage facilities.

- Automating the administrative aspects means that the language implementor has to deal with them, but he/she has far more opportunity to make use of very different computation mechanisms with different machine architectures.
 
## Examples of Separation of Concerns (Soc)

### Internet protocol stack

Separation of concerns is crucial to the design of the Internet. In the Internet Protocol Suite, great efforts have been made to separate concerns into well-defined layers. This allows protocol designers to focus on the concerns in one layer, and ignore the other layers. The Application Layer protocol SMTP, for example, is concerned about all the details of conducting an email session over a reliable transport service (usually TCP), but not in the least concerned about how the transport service makes that service reliable. Similarly, TCP is not concerned about the routing of data packets, which is handled at the Internet Layer.

### HTML, CSS, JavaScript

HyperText Markup Language (HTML), Cascading Style Sheets (CSS), and JavaScript (JS) are complementary languages used in the development of web pages and websites. HTML is mainly used for organization of webpage content, CSS is used for definition of content presentation style, and JS defines how the content interacts and behaves with the user. Historically, this was not the case: prior to the introduction of CSS, HTML performed both duties of defining semantics and style.

### Subject-oriented programming

Subject-oriented programming allows separate concerns to be addressed as separate software constructs, each on an equal footing with the others. Each concern provides its own class-structure into which the objects in common are organized, and contributes state and methods to the composite result where they cut across one another. Correspondence rules describe how the classes and methods in the various concerns are related to each other at points where they interact, allowing composite behavior for a method to be derived from several concerns. Multi-dimensional Separation of Concerns allows the analysis and composition of concerns to be manipulated as a multi-dimensional "matrix" in which each concern provides a dimension in which different points of choice are enumerated, with the cells of the matrix occupied by the appropriate software artifacts.

### Aspect-oriented programming

Aspect-oriented programming allows cross-cutting concerns to be addressed as primary concerns. For example, most programs require some form of security and logging. Security and logging are often secondary concerns, whereas the primary concern is often on accomplishing business goals. However, when designing a program, its security must be built into the design from the beginning instead of being treated as a secondary concern. Applying security afterwards often results in an insufficient security model that leaves too many gaps for future attacks. This may be solved with aspect-oriented programming. For example, an aspect may be written to enforce that calls to a certain API are always logged, or that errors are always logged when an exception is thrown, regardless of whether the program's procedural code handles the exception or propagates it.[8]

### Levels of analysis in artificial intelligence

In cognitive science and artificial intelligence, it is common to refer to David Marr's levels of analysis. At any given time, a researcher may be focusing on (1) what some aspect of intelligence needs to compute, (2) what algorithm it employs, or (3) how that algorithm is implemented in hardware. This separation of concerns is similar to the interface/implementation distinction in software and hardware engineering.

### Normalized systems

In normalized systems separation of concerns is one of the four guiding principles. Adhering to this principle is one of the tools that helps reduce the combinatorial effects that, over time, get introduced in software that is being maintained. In Normalized Systems separation of concerns is actively supported by the tools.

### SoC via partial classes

Separation of concerns can be implemented and enforced via partial classes.[9]

- SoC via partial classes in Ruby

## Gang of Four - Design Patterns 


```Ruby
bear_hunting.rb
class Bear
  def hunt
    forest.select(&:food?)
  end
end
bear_eating.rb
class Bear
  def eat(food)
    raise "#{food} is not edible!" unless food.respond_to? :nutrition_value
    food.nutrition_value
  end
end
bear_hunger.rb
class Bear
  attr_accessor :hunger
  def monitor_hunger
    if hunger > 50
      food = hunt
      hunger -= eat(food)
    end
  end
end
```

## Implementation

The mechanisms for modular or object-oriented programming that are provided by a programming language are mechanisms that allow developers to provide SoC.[4] For example, object-oriented programming languages such as C#, C++, Delphi, and Java can separate concerns into objects, and architectural design patterns like MVC or MVP can separate content from presentation and the data-processing (model) from content. Service-oriented design can separate concerns into services. Procedural programming languages such as C and Pascal can separate concerns into procedures or functions. Aspect-oriented programming languages can separate concerns into aspects and objects.

Separation of concerns is an important design principle in many other areas as well, such as urban planning, architecture and information design.[5] The goal is to more effectively understand, design, and manage complex interdependent systems, so that functions can be reused, optimized independently of other functions, and insulated from the potential failure of other functions.

Common examples include separating a space into rooms, so that activity in one room does not affect people in other rooms, and keeping the stove on one circuit and the lights on another, so that overload by the stove does not turn the lights off. The example with rooms shows encapsulation, where information inside one room, such as how messy it is, is not available to the other rooms, except through the interface, which is the door. The example with circuits demonstrates that activity inside one module, which is a circuit with consumers of electricity attached, does not affect activity in a different module, so each module is not concerned with what happens in the other.

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

# Gang of Four - 23 Design Patterns to hekp Fix Design Object-Oriented Problems

## Diagram of the Design Patterns Relationships

{design pattern relationships](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Fig1-1-Gof-DesignPatternsRelationships-23Patterns.jpg)

