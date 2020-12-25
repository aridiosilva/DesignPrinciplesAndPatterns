# Design Principles And Patterns wiki

"Patterns are a cornerstone of object-oriented design, while test-first programming and merciless refactoring are cornerstones of evolutionary 
design. To stop over- or under-engineering, it’s necessary to learn how patterns fit into the new, evolutionary rhythm of software development." - Joshua Kerievsky

"The only software documentation that actually seems to satisfy the criteria of an engeneering design is the source code listings" - Jack Reevis

## UML Relationships among Classes

- **Association** - "is part of association" relationship
- **Generalization (inheritance)** - “is-a” relationship
- **Composition (Dependency)** - one element is dependent on another element -“has-a” relationship 
- **Aggregation (Dependency)** - “has-a” relationship - what distinguishes it from **composition**, that **it doesn't involve owning**
- **Realization** - one model element **implements** the responsibility specified by another model element

## UM Association

**Association** - In UML diagrams, an association class is a class that is part of an association relationship between two other classes. You can attach an association class to an association relationship to provide additional information about the relationship. Association is the semantic relationship between classes that shows how one instance is connected or merged with others in a system. The objects are combined either logically or physically.

![umlassocation](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-association2.png)

Association is the weakest relationship between the three (Association, Generalization and Composition). It isn't a “has-a” relationship, none of the objects are parts or members of another.

Association only means that the objects “know” each other. For example, a mother and her child.

In UML, If the association is unidirectional we mark it with an arrow:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/association_symbol.png)

If the **association is bidirectional**, we can use two arrows, an arrow with an arrowhead on both ends, or a line without any arrowheads:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/association_symbols2.png)

In Java, we can model association the same way as aggregation:

```java
class Child {}

class Mother {
    List<Child> children;
}
```

But wait, how can we tell if a reference means aggregation or association?  Well, we can't. The difference is only logical: whether one of the objects is part of the other or not. Also, we have to maintain the references manually on both ends as we did with aggregation:

```java
class Child {
    Mother mother;
}

class Mother {
    List<Child> children;
}
```
For the sake of clarity, sometimes we want to define the cardinality of a relationship on a UML diagram. We can do this by writing it to the ends of the arrow:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/cardinality-1.png)

Note, that it doesn't make sense to write zero as cardinality, because it means there's no relationship. The only exception is when we want to use a range to indicate an optional relationship:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/cardinality-2.png)

Also note, that since in composition there's precisely one owner we don't indicate it on the diagrams.

Let's see a (little) more complex example!

We'll model a university, which has its departments. Professors work in each department, who also has friends among each other.

Will the departments exist after we close the university? Of course not, therefore it's a composition.

But the professors will still exist (hopefully). We have to decide which is more logical: if we consider professors as parts of the departments or not. Alternatively: are they members of the departments or not? Yes, they are. Hence it's an aggregation. On top of that, a professor can work in multiple departments.

The relationship between professors is association because it doesn't make any sense to say that a professor is part of another one.

As a result, we can model this example with the following UML diagram:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/complex-example_association.png)

And the Java code looks like this:

```java
class University {
    List<Department> department;   
}

class Department {
    List<Professor> professors;
}

class Professor {
    List<Department> department;
    List<Professor> friends;
}
```
Note, that if we rely on the terms **“has-a”**, **“belongs-to”**, **“member-of”**, **“part-of”**, and so on, we can more easily identify the relationships between our objects.

### Constraints of Associations

Since it connects the object of one class to the object of another class, it is categorized as a structural relationship. Following are the constraints applied to the association relationship are enlisted below:

- **{implicit}**: As the name suggests, the implicit constraints define that the relationship is not visible, but it is based on a concept.
- **{ordered}**: It describes that the set of entities is in a particular way at one end in an association.
- **{changeable}**: The changeable constraint ensures that the connections between several objects within a system are added, improved, and detached, as and when required.
- **{addOnly}**: It specifies that any new connection can be added from an object located at the other end in an association.
- **{frozen}**: The frozen constraint specifies that whenever a link is added between objects, it cannot be altered by the time it is activated over the connection or given link.

# UML Generalization (or Inheritance)

In UML modeling, a generalization relationship is a relationship that implements the concept of object orientation called inheritance. The generalization relationship occurs between two entities or objects, such that one entity is the parent, and the other one is the child. The child inherits the functionality of its parent and can access as well as update it.

Generalization relationship is utilized in class, component, deployment, and use case diagrams to specify that the child inherits actions, characteristics, and relationships from its parent.

To meet UML's standard, it necessitates usage of the same types of model elements in the generalization relationship, i.e., generalization relation can either be used between actors or between use cases, but not between an actor and a use case.

The generalization relationship is incorporated to record attributes, operations, and relationships in a parent model element so that it can be inherited in one or more child model elements.

The parent model element can have as many children, and also, the child can have one or more parents. But most commonly, it can be seen that there is one parent model element and multiple child model elements. The generalization relationship does not consist of names. The generalization relationship is represented by a solid line with a hollow arrowhead pointing towards the parent model element from the child model element.

![umlgeneralization_or_inheritance](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-generalization.png)

Let's create a naive example: a base class Person that defines the common fields and methods for a person, while the subclasses Waitress and Actress provide additional, fine-grained method implementations.

Here's the Person class:

```java
public class Person {
    private final String name;

    // other fields, standard constructors, getters
}
```
And these are the subclasses:

```java
public class Waitress extends Person {

    public String serveStarter(String starter) {
        return "Serving a " + starter;
    }
    
    // additional methods/constructors
}
public class Actress extends Person {
    
    public String readScript(String movie) {
        return "Reading the script of " + movie;
    } 
    
    // additional methods/constructors
}
```
In addition, let's create a unit test to verify that instances of the Waitress and Actress classes are also instances of Person, thus showing that the “is-a” condition is met at the type level:

```java
@Test
public void givenWaitressInstance_whenCheckedType_thenIsInstanceOfPerson() {
    assertThat(new Waitress("Mary", "mary@domain.com", 22))
      .isInstanceOf(Person.class);
}
    
@Test
public void givenActressInstance_whenCheckedType_thenIsInstanceOfPerson() {
    assertThat(new Actress("Susan", "susan@domain.com", 30))
      .isInstanceOf(Person.class);
}
```

It's important to stress here the semantic facet of inheritance. Aside from reusing the implementation of the Person class, we've created a well-defined “is-a” relationship between the base type Person and the subtypes Waitress and Actress. Waitresses and actresses are, effectively, persons.

This may cause us to ask: in which use cases is inheritance the right approach to take?

If subtypes fulfill the *“is-a”* condition and mainly provide additive functionality further down the classes hierarchy, then inheritance is the way to go.

### Stereotypes and their constraints

- **<< implementation >>** - It is used to show that the child is implemented by its parent, such that the child object inherits the structure and behavior of its parent object without disobeying the rules. The implementation of stereotype is mostly used in single inheritance.

In the generalization stereotype, there are two types of constraints that are **complete** and **incomplete** to check if all the child objects are involved or not in the relationship.

Example: As we know, the bank account can be of two types; Savings Account and Credit Card Account. Both the savings and the credit card account inherits the generalized properties from the Bank Account, which is Account Number, Account Balance, etc.

![umlgeneratization_or_inheritance2](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-generalization2.png)

## Inheritance in Design Patterns

While the consensus is that we should favor composition over inheritance whenever possible, there are a few typical use cases where inheritance has its place.

### A) The Layer Supertype Pattern

In this case, we use inheritance to move common code to a base class (the supertype), on a per-layer basis. Here's a basic implementation of this pattern in the domain layer:

```java
public class Entity {
    
    protected long id;
    
    // setters
}
public class User extends Entity {
    
    // additional fields and methods   
}
```
We can apply the same approach to the other layers in the system, such as the service and persistence layers.

### B) The Template Method Pattern

In the template method pattern, we can use a base class to define the invariant parts of an algorithm, and then implement the variant parts in the subclasses:

```java
public abstract class ComputerBuilder {
    
    public final Computer buildComputer() {
        addProcessor();
        addMemory();
    }
    
    public abstract void addProcessor();
    
    public abstract void addMemory();
}
public class StandardComputerBuilder extends ComputerBuilder {

    @Override
    public void addProcessor() {
        // method implementation
    }
    
    @Override
    public void addMemory() {
        // method implementation
    }
}
```

## UML Dependency (Composition)

Dependency depicts how various things within a system are dependent on each other. In UML, a dependency relationship is the kind of relationship in which a client (one element) is dependent on the supplier (another element). It is used in class diagrams, component diagrams, deployment diagrams, and use-case diagrams, which indicates that a change to the supplier necessitates a change to the client. An example is given below:

![umldepedency](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-dependency.png)

In UML, we indicate composition with the following symbol:

![composition symbol](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/symbolOf_composition.png)

Note, that the diamond is at the containing object and is the base of the line, not an arrowhead. For the sake of clarity, we often draw the arrowhead too:

![composition_symbol2](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/symbolOf_composition2.png)

In Java, we can model this with a non-static inner class:

```java
class Building {
    class Room {}   
}
```

Alternatively, we can declare that class in a method body as well. It doesn't matter if it's a named class, an anonymous class or a lambda:

```java
class Building {
    Room createAnonymousRoom() {
        return new Room() {
            @Override
            void doInRoom() {}
        };
    }

    Room createInlineRoom() {
        class InlineRoom implements Room {
            @Override
            void doInRoom() {}
        }
        return new InlineRoom();
    }
    
    Room createLambdaRoom() {
        return () -> {};
    }

    interface Room {
        void doInRoom();
    }
}
```

Note, that it's essential, that our inner class should be non-static since it binds all of its instances to the containing class.

Usually, the containing object wants to access its members. Therefore, we should store their references:

```java
class Building {
    List<Room> rooms;
    class Room {}   
}
```

Note, that all inner class objects store an implicit reference to their containing object. As a result, we don't need to store it manually to access it:

```java
class Building {
    String address;
    
    class Room {
        String getBuildingAddress() {
            return Building.this.address;
        }   
    }   
}
```
### Types of Dependency Relationship

Following are the type of dependency relationships, keywords, or stereotypes given below:

- **<< derive >>** -It is a constraint that specifies the template can be initialized by the source at the target location utilizing given parameters.
- **<< derive >>** -It represents that the source object's location can be evaluated from the target object.
- **<< friend >>** -It states the uniqueness of the source in the target object.
- **<< instanceOf >>** -It states that an instance of a target classifier is the source object.
- **<< instantiate >>** -It defines the capability of the source object, creating instances of a target object.
- **<< refine >>** -It states that the source object comprises of exceptional abstraction than that of the target object.
- **<< use >>** -When the packages are created in UML, the use of stereotype is used as it describes that the elements of the source package can also exist in the target package. It specifies that the source package uses some of the elements of the target package.
- **<< substitute >>** -The substitute stereotype state that the client can be substituted at the runtime for the supplier.
- **<< access >>** -It is also called as private merging in which the source package accesses the element of the target package.
- **<< import >>** -It specifies that target imports the source package's element as they are defined within the target. It is also known as public merging.
- **<< permit >>** -It describes that the source element can access the supplier element or whatever visibility is provided by the supplier.
- **<< extend >>** -It states that the behavior of the source element can be extended by the target.
- **<< include >>** -It describes the source element, which can include the behavior of another element at a specific location, just like a function call in C/C++.
- **<< become >>** -It states that target is similar to the source with distinct roles and values.
- **<< call >>** -It specifies that the target object can be invoked by the source.
- **<< copy >>** -It states that the target is an independent replica of a source object.
- **<< parameter >>** -It describes that the supplier is a parameter of the client's actions.
- **<< send >>** -The client act as an operation, which sends some unspecified targets to the supplier.

# UML Aggregation (Dependency) 

Aggregation is also a **“has-a” relationship**. What distinguishes it from **composition**, that **it doesn't involve owning**. As a result, the lifecycles of the objects aren't tied: every one of them can exist independently of each other.

For example, a car and its wheels. We can take off the wheels, and they'll still exist. We can mount other (preexisting) wheels, or install these to another car and everything will work just fine.

Of course, a car without wheels or a detached wheel won't be as useful as a car with its wheels on. But that's why this relationship existed in the first place: to assemble the parts to a bigger construct, which is capable of more things than its parts.

Since aggregation doesn't involve owning, a member doesn't need to be tied to only one container. For example, a triangle is made of segments. But triangles can share segments as their sides.

Aggregation is very similar to composition. The only logical difference is aggregation is a weaker relationship.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/aggregation_symbol1.png)

For cars and wheels, then, we'd do:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/aggregation_symbol2.png)

In Java, we can model aggregation with a plain old reference:

```java
class Wheel {}

class Car {
    List<Wheel> wheels;
}
```
    
The member can be any type of class, except a non-static inner class.  

In the code snippet above both classes have their separate source file. However, we can also use a static inner class:

class Car {
    List<Wheel> wheels;
    static class Wheel {}
}
Note that Java will create an implicit reference only in non-static inner classes. Because of that, we have to maintain the relationship manually where we need it:

```java
class Wheel {
    Car car;
}

class Car {
    List<Wheel> wheels;
}
```

# UML Realization

In UML modeling, the realization is a relationship between two objects, where the client (one model element) implements the responsibility specified by the supplier (another model element). The realization relationship can be employed in class diagrams and components diagrams.  The realization relationship does not have names. It is mostly found in the interfaces. It is represented by a dashed line with a hollow arrowhead at one end that points from the client to the server.

## Interface Realization

Interface realization is a kind of specialized relation between the classifier and the interface. In interface realization relationship, realizing classifiers conforms to the contract defined by the interface.

A classifier implementing an interface identifies the objects that conform to the interface and any of its ancestors. A classifier can execute one or more interfaces. The set of interfaces that are implemented by the classifier are its given interfaces. The given interfaces are the set of services offered by the classifiers to its clients.

The interface realization relationship does not contain names, and if you name it, then the name will appear beside the connector in the diagram.

The interface realization relationship is represented by a dashed line with a hollow arrowhead, which points from the classifier to the given interface.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-realization.png)

## 
next →← prev
UML-Realization
In UML modeling, the realization is a relationship between two objects, where the client (one model element) implements the responsibility specified by the supplier (another model element). The realization relationship can be employed in class diagrams and components diagrams.

The realization relationship does not have names. It is mostly found in the interfaces. It is represented by a dashed line with a hollow arrowhead at one end that points from the client to the server.

Interface Realization
Interface realization is a kind of specialized relation between the classifier and the interface. In interface realization relationship, realizing classifiers conforms to the contract defined by the interface.


A classifier implementing an interface identifies the objects that conform to the interface and any of its ancestors. A classifier can execute one or more interfaces. The set of interfaces that are implemented by the classifier are its given interfaces. The given interfaces are the set of services offered by the classifiers to its clients.

The interface realization relationship does not contain names, and if you name it, then the name will appear beside the connector in the diagram.

The interface realization relationship is represented by a dashed line with a hollow arrowhead, which points from the classifier to the given interface.

## Types of Realization

1. **Canonical form**: In UML, the canonical form realizes the interfaces across the system. An interface stereotype is used for creating an interface, and a realization relationship is employed to realize (implement) a specific interface. In this, the realization relationship is represented by a dashed line with a hollow arrowhead, and the interface is implemented using an object.

From the diagram given below, it can be seen that the object Account Business Rules realizes the interface Iruleagent.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-realization2.png)

1. **Elided form**: It is that kind of realization relationship in which the interface is represented by a circle, also known as a lollipop notation. When an interface is realized employing anything present in the system, then an elided structure is created.

Here the interface Iruleagent is denoted by an elided form, which is realized by acctrule.dll.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-realization3.png)

# COHESION

- Is the force thad binds together the code responsible to a single actor.
- Is a measure of how related the functions within a single module are.
- Refers to the degree to which the elements of a module belong together.
- Is a measure of how strongly-related or focused the responsabilities of a single module are.
- High Cohesion is the goal in design of classes, modules and other software artifacts.
- Low Cohesion is bad practice in design of classes, modules and other software artifacts.

## Component Cohesion Principles

Which classes belong in which components? This is an important decision, and requires guidamce from good software engineering principles. So, the three principle that helps this decision are:

- **REP** - Reuse/Release Equivalence Principle
- **CCP** - Common Closure Principle
- **CRP** - Common Reuse Principle

# COUPLING or DEPENDENCY

- Refers to the interdependencies between software artifacts
- Is the degree to which each module relies on each one of the the modules.
- High coupling means several dependencies between software artifacts and it is a ba practice of design
- Low Coupling means small dependencies and this is the goal in the design of software artifacts

## Summary of Good Practices of Design

- **SoC**   - Separation of Concerns
- **KISS**  - Keep it Simple
- **DRY**   - Don´t Repeat Yourself
- **TDA**   - Tell Don´t Ask
- **LoD**   - Law of Demeter - Each Unit Should have only limited knowledge about other units 
- **YAGNI** - You aren´t gonna need it

## Summary of the Principles of Object-Oriented Design

"The Source Code is the Design" (Uncle Bob C. Martin)

## = SOLID PRINCIPLES - Principles of Class Design

- ***SRP - Single Responsability Principle***  -  A class should have only one reason to change
- ***OCP - Open-Closed Principle*** - Classes should be open for extension, but closed for modification
- ***LSP - Liskov Substitution Principle*** - Subtypes must be substitutable for their base types
- ***ISP - Interface Segregation Principle*** - Clients should not be forced to depend upon methods that they do no use. Interfaces belong to clients, not do hierarchies.
- ***DIP - Depedency Inversion Principle*** - Abstractions should not depend upon details. Details should depend upon abstractions.

## = COMPONENT COHESION PRINCIPLES (Package Cohesion Principles)

- ***REP - Release - Reuse Equivalency Principle*** - The granule of reuse is the granule of release
- ***CCP - Common Closure Principle*** - The classes in a package should be closed together against the same kinds of changes. A change that affects a closed package affects all the classes in that package no other packages.
- ***CRP - Common Reuse Principle*** - The classes in a package are reused together. If you reuse one of the classes in a package, you reuse them all.

## = COMPONENT COUPLINP PRINCIPLES  (Coupling Between Packages Principles)

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

 - *describe what is to be computed;*
 - *organise the computation sequencing into small steps;*
 - *organise memory management during the computation.*
 
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

Design patterns are not about designs such as linked lists and hash tables that can be encoded in classes and reused as is. Nor are they complex, domain-specific designs for an entire application or subsystem. The design patterns in this book are descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context.

A design pattern names, abstracts, and identifies the key aspects of a common design structure that make it useful for creating a reusable object-oriented design. The design pattern identifies the participating classes and instances, their roles and collaborations, and the distribution of responsibilities. Each design pattern focuses on a particular object-oriented design problem or issue. It describes :

- when it applies, 
- whether it can be applied in view of other design constraints, and 
- the consequences and trade-offs of its use. 

## Advantage of Factory Design Pattern

- Factory Method Pattern allows the sub-classes to choose the type of objects to create.
- It promotes the loose-coupling by eliminating the need to bind application-specific classes into the code. That means the code interacts solely with the resultant interface or abstract class, so that it will work with any classes that implement that interface or that extends that abstract class.

## Usage of Factory Design Pattern

- When a class doesn't know what sub-classes will be required to create
- When a class wants that its sub-classes specify the objects to be created.
- When the parent classes choose the creation of objects to its sub-classes.

# Gang of Four - 23 Design Patterns (to help Fix Design Object-Oriented Problems)

## (GoF) What is a Design Pattern?

"Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice"  - Christopher Alexander

## (GoF) Elements of a Pattern

In general, a pattern has four essential elements:

1. The **pattern name** is a handle we can use to describe a design problem, its solutions, and
consequences in a word or two. Naming a pattern immediately increases our design vocabulary. It
lets us design at a higher level of abstraction. Having a vocabulary for patterns lets us talk about them
with our colleagues, in our documentation, and even to ourselves. It makes it easier to think about
designs and to communicate them and their trade-offs to others. Finding good names has been one of
the hardest parts of developing our catalog.

1. The **problem** describes when to apply the pattern. It explains the problem and its context. It might
describe specific design problems such as how to represent algorithms as objects. It might describe
class or object structures that are symptomatic of an inflexible design. Sometimes the problem will
include a list of conditions that must be met before it makes sense to apply the pattern.

1. The **solution** describes the elements that make up the design, their relationships, responsibilities, and
collaborations. The solution doesn't describe a particular concrete design or implementation, because
a pattern is like a template that can be applied in many different situations. Instead, the pattern
provides an abstract description of a design problem and how a general arrangement of elements
(classes and objects in our case) solves it.

1. The **consequences** are the results and trade-offs of applying the pattern. Though consequences are
often unvoiced when we describe design decisions, they are critical for evaluating design alternatives
and for understanding the costs and benefits of applying the pattern. The consequences for software
often concern space and time trade-offs. They may address language and implementation issues as
well. Since reuse is often a factor in object-oriented design, the consequences of a pattern include its
impact on a system's flexibility, extensibility, or portability. Listing these consequences explicitly
helps you understand and evaluate them.

## (GoF) Describing Design Patterns

How do we describe design patterns? Graphical notations, while important and useful, aren't sufficient. They simply capture the end product of the design process as relationships between classes and objects. To reuse the design, we must also record the decisions, alternatives, and trade-offs that led to it. Concrete examples are important too, because they help you see the design in action. The Gang of Four describe design patterns using a consistent format. Each pattern is divided into sections according to the following template. The template lends a uniform structure to the information, making design patterns easier to learn, compare, and use.

- **Pattern Name and Classification**  -  The pattern's name conveys the essence of the pattern succinctly. A good name is vital, because it will become part of your design vocabulary. The pattern's classification reflects the scheme we introduce in Section 1.5.

- **Intent ** - A short statement that answers the following questions: What does the design pattern do? What is its rationale and intent? What particular design issue or problem does it address?

- **Also Known As** - Other well-known names for the pattern, if any.

- **Motivation** - A scenario that illustrates a design problem and how the class and object structures in the pattern solve the problem. The scenario will help you understand the more abstract description of the pattern that follows.

- **Applicability** - What are the situations in which the design pattern can be applied? What are examples of poor designs that the pattern can address? How can you recognize these situations?

- **Structure** - A graphical representation of the classes in the pattern using a notation based on the Object Modeling Technique (OMT) [RBP+91]. We also use interaction diagrams [JCJO92, Boo94] to illustrate sequences of requests and collaborations between objects. Appendix B describes these notations in detail.

- **Participants** - The classes and/or objects participating in the design pattern and their responsibilities.

- **Collaborations** - How the participants collaborate to carry out their responsibilities.

- **Consequences** - How does the pattern support its objectives? What are the trade-offs and results of using the pattern? What aspect of system structure does it let you vary independently?

- **Implementation** - What pitfalls, hints, or techniques should you be aware of when implementing the pattern? Are there language-specific issues?

- **Sample Code** - Code fragments that illustrate how you might implement the pattern in C++ or Smalltalk.

- **Known Uses** - Examples of the pattern found in real systems. We include at least two examples from different domains.

- **Related Patterns** - What design patterns are closely related to this one? What are the important differences? With which other patterns should this one be used?

## (GoF) Diagram of the Design Patterns Relationships

![design patterns relationships](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Fig1-1-Gof-DesignPatternsRelationships-23Patterns.jpg)

## (GoF) The Catalog of  Gang of Four 23 Design Patterns

The catalog beginning on page 79 contains 23 design patterns. Their names and intents are listed next to give you an overview. The number in parentheses after each pattern name gives the page number for the pattern (a convention we follow throughout the book).

- **Abstract Factory (87)** - Provide an interface for creating families of related or dependent objects without specifying their concrete classes. Yield objects whose only responsibilities are creating other objects.

- **Adapter (139)** - Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

- **Bridge (151)** - Decouple an abstraction from its implementation so that the two can vary independently. Yield objects whose only responsibilities are creating other objects.

- **Builder (97)** - Separate the construction of a complex object from its representation so that the same construction process can create different representations.

- **Chain of Responsibility (223)** - Avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chain the receiving objects and pass the request along the chain until an object handles it.

- **Command (233)** - Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.  Yield objects whose only responsibilities are to implement a request on another object or group of objects.

- **Composite (163)**- Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly. introduces an abstraction for treating objects uniformly that doesn't have a physical counterpart.

- **Decorator (175)** - Attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.

- **Facade (185)** - Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use. It describes how to represent complete subsystems as objects.

- **Factory Method (107)** - Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

- **Flyweight (195)** - Use sharing to support large numbers of fine-grained objects efficiently. It describes how to support huge numbers of objects at the finest granularities.

- **Interpreter (243)** - Given a language, define a represention for its grammar along with an interpreter that uses the representation to interpret sentences in the language.

- **Iterator (257)** - Provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation.

- **Mediator (273)** - Define an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently.

- **Memento (283)** - Without violating encapsulation, capture and externalize an object's internal state so that the object can be restored to this state later. It describes how to encapsulate and save the internal state of an object so that the object can be restored to that state later. The pattern stipulates that Memento objects must define two
interfaces: a restricted one that lets clients hold and copy mementos, and a privileged one that only the original object can use to store and retrieve state in the memento.

- **Observer (293)** - Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

- **Prototype (117)** - Specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.

- **Proxy (207)** - Provide a surrogate or placeholder for another object to control access to it.

- **Singleton (127)** - Ensure a class only has one instance, and provide a global point of access to it.

- **State (305)** - Allow an object to alter its behavior when its internal state changes. The object will appear to change its class.

- **Strategy (315)** - Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it. Describes how to implement interchangeable families of algorithms.

- **Template Method (325)** - Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.

- **Visitor (331)** - Represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.  Yield objects whose only responsibilities are to implement a request on another object or group of objects.

## Gang of Four - Design Patterns Space

![design pattern space](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/table-1-1-GOF_DesignPatternsSpace.jpg)

the Gang of Four classify design patterns by two criteria shown in Table 1.1 above.

A) The first criterion, called purpose, reflects what a pattern does. Patterns can have either creational, structural, or behavioral purpose. 

   - **Creational patterns** concern the process of object creation. 
   - **Structural patterns** deal with the composition of classes or objects. 
   - **Behavioral patterns** characterize the ways in which classes or objects interact and distribute responsibility.
   
B) The second criterion, called scope, specifies whether the pattern applies primarily to classes or to objects.

- **Class patterns** 
    
   - deal with relationships between classes and their subclasses. T
   - these relationships are established through inheritance, so they are static—fixed at compile-time. 
       
- **Object patterns** 
      
    - deal with object relationships, which can be changed at run-time and are more dynamic. 
    
- Almost all patterns use inheritance to some extent. 
- So the only patterns labeled "class patterns" are those that focus on class relationships. 
- Note that most patterns are in the Object scope.

# (GoF) How Design Patterns Solve Design Problems

Design patterns solve many of the day-to-day problems object-oriented designers face, and in many different ways. Here are several of these problems and how design patterns solve them. 

# (GoF) P1 - Finding Appropriate Objects

Object-oriented programs are made up of objects. An **object** packages both data and the procedures that operate on that data. The procedures are typically called methods or **operations**. An object performs an operation when it receives a **request** (or message) from a client. **Requests** are the only way to get an object to execute an operation. **Operations** are the only way to change an object's internal data (state). Because of these restrictions, the **object's internal state** is said to be **encapsulated**; it cannot be accessed directly, and its representation is invisible from outside the object.  

The hard part about object-oriented design is **decomposing a system into objects**. The task is difficult because many factors come into play: *encapsulation,  granularity, dependency, flexibility, performance, evolution, reusability, and  on and on*. They all influence the **decomposition**, often in conflicting ways. Object-oriented design methodologies favor many different approaches:

- *You can write a problem statement, single out the nouns and verbs, and create corresponding classes and operations, or*
- *You can focus on the collaborations and responsibilities in your system, or*
- *You can model the real world and translate the objects found during analysis into design.*

There will always be disagreement on which approach is best. 

Many objects in a design come from the **analysis model**. But object-oriented designs often end up with *classes* that have no counterparts in the real world. Some of these are **low-level classes** like arrays. Others are much **higher-level**. For example, the **Composite (163) pattern** introduces an abstraction for treating objects uniformly that doesn't have a physical counterpart. *Strict modeling of the real world leads to a system that reflects today's realities but not necessarily tomorrow's*. The **abstractions** that emerge during design are key to making a design flexible.

Design patterns help you identify **less-obvious abstractions** and the objects that can capture them. For example, objects that represent a **process** or **algorithm** don't occur in nature, yet they are a crucial part of flexible designs. 

- The **Strategy (315) pattern** describes how to implement interchangeable families of algorithms. 
- The **State (305) pattern** represents each state of an entity as an object. 

These objects are seldom found during analysis or even the early stages of design; they're discovered later in the course of making a design more flexible and reusable.

## (GoF) P2 - Determining Object Granularity

-  Note: Granularity = the scale or level of detail present in a set of data or other phenomenon.

Objects can vary tremendously in size and number. They can represent everything down to the hardware or all the way up to entire applications. How do we decide what should be an object?

Design patterns address this issue as well. 

- The **Facade (185) pattern** describes how to represent complete subsystems as objects, and 
- the **Flyweight (195) pattern** describes how to support huge numbers of objects at the finest granularities.

Other design patterns describe specific ways of decomposing an object into smaller objects. 

- **Abstract Factory (87)** and **Builder (97)** yield objects whose only responsibilities are creating other objects.
- **Visitor (331)** and **Command (233)** yield objects whose only responsibilities are to implement a request on another object or group of objects.

## (GoF) P3 - Specifying Object Interfaces

Every operation declared by an object specifies the operation's name, the objects it takes as parameters, and the operation's return value. This is known as the **operation's signature**. The set of all signatures defined by an object's operations is called the **interface to the object**. An object's interface characterizes the complete set of requests that can be sent to the object. Any request that matches a **signature** in the object's interface may be sent to the object.

A *type* is a name used to denote a particular interface. We speak of an object as having the type "Window" if it accepts all requests for the operations defined in the interface named "Window." An object may have many types, and widely different objects can share a type. Part of an object's interface may be characterized by one type, and other parts by other types. Two objects of the same type need only share parts of their interfaces. Interfaces can contain other interfaces as subsets. We say that a **type** is a *subtype* of another if its interface contains the interface of its supertype. Often we speak of a subtype inheriting the interface of its *supertype**.

**Interfaces** are fundamental in object-oriented systems. Objects are known only through their interfaces. There is no way to know anything about an object or to ask it to do anything without going through its interface. An object's interface says nothing about its implementation—different objects are free to implement requests differently. That means two objects having completely different implementations can have identical interfaces.

When a request is sent to an object, the particular operation that's performed depends on both the request and the receiving object. Different objects that support identical requests may have different implementations of the operations that fulfill these requests. The run-time association of a request to an object and one of its operations is known as **dynamic binding**.

Dynamic binding means that issuing a request doesn't commit you to a particular implementation until runtime. Consequently, you can write programs that expect an object with a particular interface, knowing that any object that has the correct interface will accept the request. Moreover, dynamic binding lets you substitute objects that have identical interfaces for each other at run-time. This substitutability is known as **polymorphism**, and it's a key concept in object-oriented systems. It lets a client object make fewassumptions about other objects beyond supporting a particular interface. Polymorphism simplifies the definitions of clients, decouples objects from each other, and lets them vary their relationships to each other at run-time.

- The **Memento (283) pattern** is a good example. It describes how to encapsulate and save the internal state of an object so that the object can be restored to that state later. The pattern stipulates that Memento objects must define two interfaces: a restricted one that lets clients hold and copy mementos, and a privileged one that only the original object can use to store and retrieve state in the memento.

Design patterns also specify **relationships between interfaces**. In particular, they often require some classes to have similar interfaces, or they place constraints on the interfaces of some classes. For example, both **Decorator (175)** and **Proxy (207)** require the interfaces of Decorator and Proxy objects to be identical to the decorated and proxied objects. In **Visitor (331)**, the Visitor interface must reflect all classes of objects that visitors can visit.

Design patterns help you define interfaces by identifying their key elements and the kinds of data that get sent across an interface. A design pattern might also tell you what not to put in the interface. 

# (GoF) P4 - Specifying Object Implementations

So far we've said little about how we actually define an object. An object's implementation is defined by its **class**. The class specifies the object's internal data and representation and defines the operations the object can perform.

Objects are created by instantiating a class. The object is said to be an instance of the class. The process of instantiating a class allocates storage for the object's internal data (made up of **instance variables**) and associates the operations with these data. Many similar instances of an object can be created by instantiating a class.

New classes can be defined in terms of existing classes using **class inheritance**. When a **subclass** inherits from a **parent class**, it includes the definitions of all the data and operations that the parent class defines. Objects that are instances of the subclass will contain all data defined by the subclass and its parent classes, and they'll be able to perform all operations defined by this subclass and its parents.

An **abstract class** is one whose main purpose is to define a common interface for its subclasses. An abstract class will defer some or all of its implementation to operations defined in subclasses; hence an abstract class cannot be instantiated. The operations that an abstract class declares but doesn't implement are called **abstract operations**. Classes that aren't abstract are called **concrete classes**.

Subclasses can refine and redefine behaviors of their parent classes. More specifically, a class may **override** an operation defined by its parent class. Overriding gives subclasses a chance to handle requests instead of their parent classes. Class inheritance lets you define classes simply by extending other classes, making it easy to define families of objects having related functionality.

A **mixin class** is a class that's intended to provide an optional interface or functionality to other classes. It's similar to an abstract class in that it's not intended to be instantiated. Mixin classes require **multiple inheritance**.

# (GoF) P5 - Class versus Interface Inheritance

It's important to understand the difference between an object's **class** and its **type**.

An object's class defines how the object is implemented. The class defines the object's internal state and the implementation of its operations. In contrast, an object's type only refers to its interface—the set of requests to which it can respond. An object can have many types, and objects of different classes can have the same type.

Of course, there's a close relationship between class and type. Because a class defines the operations an object can perform, it also defines the object's type. When we say that an object is an instance of a class, we imply that the object supports the interface defined by the class.

Languages like C++ and Eiffel use classes to specify both an object's type and its implementation. Smalltalk programs do not declare the types of variables; consequently, the compiler does not check that the types of objects assigned to a variable are subtypes of the variable's type. Sending a message requires checking that the class of the receiver implements the message, but it doesn't require checking that the receiver is an instance of a particular class.

It's also important to understand the difference between class inheritance and interface inheritance (or subtyping). Class inheritance defines an object's implementation in terms of another object's implementation. In short, it's a mechanism for code and representation sharing. In contrast, interface inheritance (or subtyping) describes when an object can be used in place of another. 

It's easy to confuse these two concepts, because many languages don't make the distinction explicit. In languages like C++ and Eiffel, inheritance means both interface and implementation inheritance. The standard way to inherit an interface in C++ is to inherit publicly from a class that has (pure) virtual member functions. Pure interface inheritance can be approximated in C++ by inheriting publicly from pure abstract classes. Pure implementation or class inheritance can be approximated with private inheritance. In Smalltalk, inheritance means just implementation inheritance. You can assign instances of any class to a variable as long as those instances support the operation performed on the value of the variable. 

Although most programming languages don't support the distinction between interface and implementation inheritance, people make the distinction in practice. Smalltalk programmers usually act as if subclasses were subtypes (though there are some well-known exceptions [Coo92]); C++ programmers manipulate objects through types defined by abstract classes.

  - [Cpp02] William R. Cook. Interfaces and specifications for the Smalltalk-80 collection classes. In Object-Oriented Programming Systems, Languages, and Applications Conference Proceedings, pages 1–15, Vancouver, British Columbia, Canada, October 1992. ACM Press.

Many of the design patterns depend on this distinction. For example, objects in a Chain of Responsibility (223) must have a common type, but usually they don't share a common implementation. In the Composite (163) pattern, Component defines a common interface, but Composite often defines a common implementation. **Command (233)**, **Observer (293)**, **State (305)**, and **Strategy (315)** are often implemented with abstract classes that are pure interfaces.

# (GoF) P5 - Programming to an Interface, not an Implementation

Class inheritance is basically just a mechanism for extending an application's functionality by reusing functionality in parent classes. It lets you define a new kind of object rapidly in terms of an old one. It lets you get new implementations almost for free, inheriting most of what you need from existing classes.

However, implementation reuse is only half the story. Inheritance's ability to define families of objects with identical interfaces (usually by inheriting from an abstract class) is also important. Why? Because polymorphism depends on it.

When inheritance is used carefully (some will say properly), all classes derived from an abstract class will share its interface. This implies that a subclass merely adds or overrides operations and does not hide operations of the parent class. All subclasses can then respond to the requests in the interface of this abstract class, making them all subtypes of the abstract class.

There are two benefits to manipulating objects solely in terms of the interface defined by abstract classes:

1. Clients remain unaware of the specific types of objects they use, as long as the objects adhere to the interface that clients expect.
1. Clients remain unaware of the classes that implement these objects. Clients only know about the
abstract class(es) defining the interface. 

This so greatly reduces implementation dependencies between subsystems that it leads to the following principle of reusable object-oriented design: 

 - *Program to an interface, not an implementation*.

Don't declare variables to be instances of particular concrete classes. Instead, commit only to an interface defined by an abstract class. You will find this to be a common theme of the design patterns in the book´s Gang of Four.

You have to instantiate concrete classes (that is, specify a particular implementation) somewhere in your system, of course, and the creational patterns (**Abstract Factory (87)**, **Builder (97)**, **Factory Method (107)**, **Prototype (117)**, and **Singleton (127)** let you do just that. By abstracting the process of object creation, these patterns give you different ways to associate an interface with its implementation transparently at instantiation. Creational patterns ensure that your system is written in terms of interfaces, not implementations.

# (GoF) P6 - Putting Reuse Mechanisms to Work

Most people can understand concepts like objects, interfaces, classes, and inheritance. The challenge lies in applying them to build flexible, reusable software, and design patterns can show you how.

## (GoF) Inheritance versus Composition

The two most common techniques for reusing functionality in object-oriented systems are class inheritance and object composition. As we've explained, class inheritance lets you define the implementation of one class in terms of another's. Reuse by subclassing is often referred to as white-box reuse. The term "whitebox" refers to visibility: With inheritance, the internals of parent classes are often visible to subclasses.

Object composition is an alternative to class inheritance. Here, new functionality is obtained by assembling or composing objects to get more complex functionality. Object composition requires that the objects being composed have well-defined interfaces. This style of reuse is called black-box reuse, because no internal details of objects are visible. Objects appear only as "black boxes."

Inheritance and composition each have their advantages and disadvantages. Class inheritance is defined statically at compile-time and is straightforward to use, since it's supported directly by the programming language. Class inheritance also makes it easier to modify the implementation being reused. When a subclass overrides some but not all operations, it can affect the operations it inherits as well, assuming they call the overridden operations.

But class inheritance has some disadvantages, too. First, you can't change the implementations inherited from parent classes at run-time, because inheritance is defined at compile-time. Second, and generally worse, parent classes often define at least part of their subclasses' physical representation. Because inheritance exposes a subclass to details of its parent's implementation, it's often said that "inheritance breaks encapsulation" [Sny86]. The implementation of a subclass becomes so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change.

Implementation dependencies can cause problems when you're trying to reuse a subclass. Should any aspect of the inherited implementation not be appropriate for new problem domains, the parent class must be rewritten or replaced by something more appropriate. This dependency limits flexibility and ultimately reusability. One cure for this is to inherit only from abstract classes, since they usually provide little or no implementation.

Object composition is defined dynamically at run-time through objects acquiring references to other objects. Composition requires objects to respect each others' interfaces, which in turn requires carefully designed interfaces that don't stop you from using one object with many others. But there is a payoff. Because objects are accessed solely through their interfaces, we don't break encapsulation. Any object can be replaced at runtime by another as long as it has the same type. Moreover, because an object's implementation will be written in terms of object interfaces, there are substantially fewer implementation dependencies.

Object composition has another effect on system design. Favoring object composition over class inheritance helps you keep each class encapsulated and focused on one task. Your classes and class hierarchies will remain small and will be less likely to grow into unmanageable monsters. On the other hand, a design based on object composition will have more objects (if fewer classes), and the system's behavior will depend on their interrelationships instead of being defined in one class.

That leads us to our second principle of object-oriented design: 

 - *Favor object composition over class inheritance.*

Ideally, you shouldn't have to create new components to achieve reuse. You should be able to get all the functionality you need just by assembling existing components through object composition. But this is rarely the case, because the set of available components is never quite rich enough in practice. Reuse by inheritance makes it easier to make new components that can be composed with old ones. Inheritance and object composition thus work together. 

Nevertheless, our experience is that designers overuse inheritance as a reuse technique, and designs are often made more reusable (and simpler) by depending more on object composition. You'll see object composition applied again and again in the design patterns. 

## (GoF) Delegation

Delegation is a way of making composition as powerful for reuse as inheritance [Lie86, JZ91]. In
delegation, two objects are involved in handling a request: a receiving object delegates operations to its delegate. This is analogous to subclasses deferring requests to parent classes. But with inheritance, an inherited operation can always refer to the receiving object through the this member variable in C++ and self in Smalltalk. To achieve the same effect with delegation, the receiver passes itself to the delegate to let the delegated operation refer to the receiver.

For example, instead of making class Window a subclass of Rectangle (because windows happen to be
rectangular), the Window class might reuse the behavior of Rectangle by keeping a Rectangle instance variable and delegating Rectangle-specific behavior to it. In other words, instead of a Window being a Rectangle, it would have a Rectangle. Window must now forward requests to its Rectangle instance explicitly, whereas before it would have inherited those operations.

The following diagram depicts the Window class delegating its Area operation to a Rectangle instance.

