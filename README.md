# Design Principles And Patterns in Object-Oriented Design (OOD)

*"Patterns are a cornerstone of object-oriented design, while test-first programming and merciless refactoring are cornerstones of evolutionary 
design. To stop over- or under-engineering, it’s necessary to learn how patterns fit into the new, evolutionary rhythm of software development."* - Joshua Kerievsky

*"The only software documentation that actually seems to satisfy the criteria of an engeneering design is the source code listings"* - Jack Reevis

* [Coupling and Cohesion](#coupling-and-cohesion )

  - [Coupling or Dependency](#coupling-or-dependency)
  - [Cohesion](#cohesion)

* [Summary of Good Practices of Design](#summary-of-good-practices-of-design) 
* [Summary of the Principles of Object-Oriented Design](#summary-of-the-principles-of-object-oriented-design)
* [SOLID Principles](#solid-principles)

   - [SRP Single Responsability Principle](#srp-single-responsability-principle)
   - [OCP Open-Closed Principle](#ocp-open-closed-principle)
   - [LSP Liskov Substitution Principle](#lsp-liskov-substitution-principle)
   - [ISP Interface Segregation Principle](#isp-interface-segregation-principle)
   - [DIP Dependency Inversion Principle](#dip-dependency-inversion-principle)

* [Summary of Good Practices of Design](#summary-of-good-practices-of-design)

   - [SoC Separation of Concerns](#soc-separation-of-concerns)
   - [KISS Keep It Simple Principle](#kiss-keep-it-simple-principle)
   - [Keep things DRY](#keep-things-dry)
   - [YAGNI Principle](#yagni-principle)
   - [LoD Law of Demeter Principle](#lod-law-of-demeter-principle)
   - [TDA Tell Do not Ask](#tda-tell-do-not-ask)

* Other Good Practices in Design 

   - [Do The Simplest Thing That Could Possibly Work](#do-the-simplest-thing-that-could-possibly-work)
   - [Hide Implementation Details](#hide-implementation-details)
   - [Encapsulate What Changes](#encapsulate-what-changes)
   - [Code For The Maintainer](#code-for-the-maintainer)
   - [Component Cohesion Principles](#component-cohesion-principles)
   - [Composition Over Inheritance Principle](#composition-over-inheritance-principle)
   - [Orthogonality Principle](#orthogonality-principle)
   - [Robustness Principle](#robustness-principle)
   - [IC Inversion of Control](#ic-inversion-of-control)
   - [Command Query Separation Principle](#Command-query-separation-principle)

* [Classification of Programming Languages](#classification-of-programming-languages)

* [Gang of Four 23 Design Patterns to help Fix Design Object-Oriented Problems](#gang-of-four-23-design-patterns-to-help-fix-design-object-oriented-problems)

   - [GoF What is a Design Pattern](#gof-what-is-a-design-pattern)
   - [GoF Elements of a Pattern](#gof-elements-of-a-pattern)
   - [GoF Describing Design Patterns](#gof-describing-design-patterns)
   - [GoF Diagram of the Design Patterns Relationships](#gof-diagram-of-the-design-patterns-relationships)
   - [GoF The Catalog of Gang of Four 23 Design Patterns](#gof-the-catalog-of-gang-of-four-23-design-patterns)
   - [GoF How Design Patterns Solve Design Problems](#gof-how-design-patterns-solve-design-problems)
   - [GoF P1 Finding Appropriate Objects](#gof-p1-finding-appropriate-objects)
   - [GoF P2 Determining Object Granularity](#gof-p2-determining-object-granularity)
   - [GoF P3 Specifying Object Interfaces](#gof-p3-specifying-object-interfaces)
   - [GoF P4 Specifying Object Implementations](#gof-p4-specifying-object-implementations)
   - [GoF P5 Class versus Interface Inheritance](#gof-p5-class-versus-interface-inheritance)
   - [GoF P6 Programming to an Interface, not an Implementation](#gof-p6-programming-to-an-interface-not-an-implementation)
   - [GoF P7 Putting Reuse Mechanisms to Work](#gof-p7-putting-reuse-mechanisms-to-work)
   - [GoF Inheritance versus Composition](#gof-inheritance-versus-composition)
   - [GoF Delegation](#gof-delegation)
   - [GoF P8 Inheritance versus Parameterized or Generic Types](#gof-p8-inheritance-versus-parameterized-or-generic-types)
   - [GoF P9 Relating Run Time and Compile Time Structures](#gof-p9-relating-run-time-and-compile-time-structures)
   - [GoF P10 Designing for Change](#gof-p10-designing-for-change)
   - [GoF P11 Application Programs](#gof-p11-application-programs)
   - [GoF P12 Toolkits](#gof-p12-toolkits)
   - [GoF P13 Frameworks](#gof-p13-frameworks)
   - [FACTORY DESIGN PATTERN](#factory-design-pattern)

* [UML Relationships among Classes](#uml-relationships-among-classes)

   - [UML Association or Using Relationship](#uml-association-or-using-relationship)
   - [UML Composition](#uml-composition)
   - [UML Aggregation or Has a Relationship](#uml-aggregation-or-has-a-relationship)
   - [UML Generalization or Inheritance](#uml-generalization-or-inheritance)
   - [UML Realization](#uml-realization)
   - [Interface Realization](#interface-realization)
   
* [# Creational Design Patterns](#creational-design-patterns)

   - [DCP1 Factory Method](#dcp1-factory-method)
   - [Model View Controller Pattern](#model-view-controller-pattern)

# Coupling and Cohesion 

Note: the definitons below is based on the book Timothy Budd's An Introduction to Object-Oriented Programming  

# Coupling or Dependency

- Refers to the interdependencies between software artifacts
- Is the degree to which each module relies on each one of the the modules.
- High coupling means several dependencies between software artifacts and it is a ba practice of design
- Low Coupling means small dependencies and this is the goal in the design of software artifacts

"**Coupling**" describes the relationships between modules, and "**cohesion**" describes the relationships within them. A reduction in interconnectedness between modules (or classes) is therefore achieved via a reduction in coupling. On the other hand, well-designed modules (or classes) should have some purpose; all the elements should be associated with a single task. This means that in a good design, the elements within a module (or class) should have internal cohesion.

**Coupling** between modules can arise for different reasons, some of which are more acceptable, or desirable, than others. A ranked list [from least desirable to most desirable] might look something like the following:

* **Internal data coupling** - one module modifying the internals of another;
* **Global data coupling** -modules sharing global data;
* **Control or sequence coupling** - one module controlling the sequence of events in another;
* **Parameter coupling** - one module passing information to another through parameters;
* **Subclass coupling** - one module inheriting from another;

As with **coupling**, **cohesion** can be ranked on a scale of the **weakest (least desirable)** to the **strongest (most desirable)* as follows:

* **Coincidental cohesion** -elements are in the same module for no particular reason;
* **Logical cohesion** - elements perform logically related tasks;
* **Temporal cohesion** - elements must be used at approximately the same time;
* **Communication cohesion** - elements share I/O;
* **Sequential cohesion** - elements must be used in a particular order;
* **Functional cohesion** - elements cooperate to carry out a single function;
* **ata cohesion** - elements cooperate to present an interface to a hidden data structure;

One can often estimate the **degree of cohesion** within a module by writing a brief statement of the module's purpose.... The following tests are suggested by Constantine:

>1. If the sentence that describes the purpose of the module is a compound sentence containing a comma or more than one verb, the module is probably performing more than one function; therefore, it probably has sequential or communicational binding *or even less: temporal, logical, or coincidental*;
>
>1. If the sentence contains words relating to time, such as "first," "next," "then," "after," "when," or "start," the module probably has sequential or temporal binding. An example is "Wait for the instant teller customer to insert a card, then prompt for the personal identification number.";
>
>1. If the predicate of the sentence does not contain a single, specific object following the verb, the module is probably logically bound. For example, "Edit all data" has logical binding; Edit source data may have functional binding;
>
>1. If the sentence contains words such as "Initialize" or "Clean up," the module probably has temporal binding;

# Cohesion

- Is the force thad binds together the code responsible to a single actor.
- Is a measure of how related the functions within a single module are.
- Refers to the degree to which the elements of a module belong together.
- Is a measure of how strongly-related or focused the responsabilities of a single module are.
- High Cohesion is the goal in design of classes, modules and other software artifacts.
- Low Cohesion is bad practice in design of classes, modules and other software artifacts.

# Maximize Cohesion

Cohesion of a single module/component is the degree to which its responsibilities form a meaningful unit; higher cohesion is better.

### Why Maximize Cohesion

* Increased difficulty in understanding modules.
* Increased difficulty in maintaining a system, because logical changes in the domain affect multiple modules, and because changes in one module require changes in related modules.
* Increased difficulty in reusing a module because most applications won’t need the random set of operations provided by a module.

### How to Maximize Cohesion

* Group related functionalities sharing a single responsibility (e.g. in a class).

# Minimise Coupling

Coupling between modules/components is their degree of mutual interdependence; lower coupling is better. In other words, coupling is the probability that code unit "B" will "break" after an unknown change to code unit "A".

### Why Minimize Coupling

* A change in one module usually forces a ripple effect of changes in other modules.
* Assembly of modules might require more effort and/or time due to the increased inter-module dependency.
* A particular module might be harder to reuse and/or test because dependent modules must be included.
* Developers might be afraid to change code because they aren't sure what might be affected.

### How Minmimize Coupling

* Eliminate, minimise, and reduce complexity of necessary relationships.
* By hiding implementation details, coupling is reduced.
* Apply the Law of Demeter.

# Component Cohesion Principles

Which classes belong in which components? This is an important decision, and requires guidamce from good software engineering principles. So, the three principle that helps this decision are:

- **REP** - Reuse/Release Equivalence Principle
- **CCP** - Common Closure Principle
- **CRP** - Common Reuse Principle

# Summary of Good Practices of Design

- **SoC**   - Separation of Concerns
- **KISS**  - Keep it Simple
- **DRY**   - Don´t Repeat Yourself
- **TDA**   - Tell Don´t Ask
- **LoD**   - Law of Demeter - Each Unit Should have only limited knowledge about other units 
- **YAGNI** - You aren´t gonna need it

# Summary of the Principles of Object-Oriented Design

"The Source Code is the Design" (Uncle Bob C. Martin)

## A- SOLID PRINCIPLES - Principles of Class Design

- ***SRP - Single Responsability Principle***  -  A class should have only one reason to change
- ***OCP - Open-Closed Principle*** - Classes should be open for extension, but closed for modification
- ***LSP - Liskov Substitution Principle*** - Subtypes must be substitutable for their base types
- ***ISP - Interface Segregation Principle*** - Clients should not be forced to depend upon methods that they do no use. Interfaces belong to clients, not do hierarchies.
- ***DIP - Depedency Inversion Principle*** - Abstractions should not depend upon details. Details should depend upon abstractions.

## B - Component Cohesion Principles (Package Cohesion Principles)

- ***REP - Release - Reuse Equivalency Principle*** - The granule of reuse is the granule of release
- ***CCP - Common Closure Principle*** - The classes in a package should be closed together against the same kinds of changes. A change that affects a closed package affects all the classes in that package no other packages.
- ***CRP - Common Reuse Principle*** - The classes in a package are reused together. If you reuse one of the classes in a package, you reuse them all.

## C - Component Coupling Principles (Coupling Between Packages Principles)

- ***ADP - Acyclic Deependencies Principle*** - Allow no cycles in the package dependency graph.
- ***SDP Stable Dependencies Principle*** - Depend in the direction of stability.
- ***SAP - Stable Abstraction Principle*** - A package should be as abstract as it is stable.

# SOLID Principles

The text in this Wiki is writeen based on the following Books:

- Book Agile Software Development: Principles, Patterns, and Practices by Uncle Bob C. Martin and published in 2002
- Book Clean Architecture - A Handbook of Agile Software Craftsmanship by Uncle Bob C. Marting and published in 2017

# SRP Single Responsability Principle

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

### Why to Apply SRP

Maintainability: changes should be necessary only in one module or class.

### How to Apply SRP

Curly's Law - Curly's Law is about choosing a single, clearly defined goal for any particular bit of code: Do One Thing.

>* [link to Article about Apply Curly's Law](https://java-design-patterns.com/principles/#curlys-law)
>* [kinto to Article Curly's Law: Do One Thing](https://blog.codinghorror.com/curlys-law-do-one-thing/)
>* [The Rule of One or Curly’s Law](http://grsmentor.com/blog/the-rule-of-one-or-curlys-law/)

### Resources About SRP 

[link to Single responsibility principle in Wikipedia](https://en.wikipedia.org/wiki/Single_responsibility_principle)

# OCP Open-Closed Principle

Software systems to be easy to change, they must be designed to allow the behavior of those systems to be changed by adding new code, rather than changing existing one.

- The OCP is the driving forces behind the architecture of systems" (Uncle Bob C. Martin);
- If a *component A* should be protected from changes in *component B*, then *component B should depend on component A*;
- A software artifact should be *open extension but closed for modification*;
- the *goal of OCP* is to *make the system easy to extend without incurring an high impact of change* - This goal is accomplished by *partitioning the system into components, and arranging those components into a dependency hierarchy that protects higher-level components from changes in lower-level components*;

A software entities (classes) should be open for extension, but closed for modification. I.e. such an entity can allow *its behavior to be modified without altering its source code*.

Of all the *principles of object oriented design (OOD)*, this is the most important. It originated from the work of *Bertrand Meyer*. It means simply this: *We should write our modules so that they can be extended, without requiring them to be modified*. In other words, *we want to be able to change what the modules do, without changing the source code of the modules*.

This may sound contradictory, but there are *several techniques* for achieving the OCP on a large scale. All of these techniques are based upon *abstraction*. Indeed, *abstraction is the key to the OCP*. Some of these techniques are, for example:

> **A) Dynamic Polymorphism**
> **B) Static Polymorphism**

## Dynamic Polymorphism Technique Used to Implement Open-Closed Principle (OCP)

Consider the source code below. the *logOn method* must be changed every time a *new kind of modem is added to the software*. Worse, since each *different type of modem* depends upon the *modemType enumeration*, each modem must be recompiled every time a new kind of modem is added:

```java
public class Modem {
	private int modemStatus;
	public enum modemType {
		HAYES, COURRIER, ERNIE;
	}
	public voi logOn (modemType m, String pno, String user, String pw) {
		switch (m) {
		case HAYES:
			dialHayes( m.HAYES, pno);
			break;
		case COURRIER:
			dialCourrier( m.COURRIER, pno);
			break;
		case ERNIE:
			dialErnie (m.HAYES, pno);
			break;
		default:
			break;
		}
		// ...you get the idea
	}
}
```
Of course this is not the worst attribute of this kind of design. Programs that are designed this way tend to be littered with similar *if/else* or *switch statement*. Every time anything needs to be done to the *Modem Class*, a *switch statement* or *if/else chain* will need to select the proper methods to use. When *new modems* are added, or *modem policy changes*, the code must be scanned for all these *selection statements*, and each must be appropriately *modified*.

Worse, programmers may use *local optimizations that hide the structure of the selection statements*. For example, it might be that the method is exactly the same for *HAYES* and *COURRIER* modems. Thus we might see code like this:

```java

if (m.ERNIES)
    sendErnie(m.ERNIES, c);
else
    dendHayes(m.HAYERS, c);

```

Clearly, *such structures make the system much harder to maintain*, and are *very prone to error*. 

As an example of the OCP, consider code shown in the following *UML Diagram*. Here the *logOn method* depends only upon the *Modem interface*. Additional modems will not cause the *logOn method* to change. Thus, we have created a module that *can be extended, with new modems, without requiring modification*. See the the following *UML Diagram* showing such design:

![OCP_Principle_UML_Diagram_Example013_CleanCodeBook](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/OCP_Principle_UML_Diagram_Example013_CleanCodeBook.jpg)

We have *two options* in *Java Programming Language* to implement the *model* shown in the *UML diagram* above. The **first optin** is through *abstract class* via use of *inheritance mechanism*, and the **second option** is through the use of *interface and its implementation by concrete classes*. In both cases the *method LogOn* will be *open for extension and closed for modification* as states the *OCP Principle*:

## Dynamic Polymorphism Technique Applied Through Abstract Classes and Inheritance

```java
public abstrac class Modem {

    public abstract void dial(String pno);
    public abstract void send(String s);
    public abstract String recv();
    public abstract void hangUp();

    public void logOn(modemType m, String pno, String user, String pw) {
         m.dial(pno);
         ...
    }
    ...
}
```

```java

public class ModemHayes extends Modem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

```java
public class ModemErnie extends Modem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

```java
public class ModemCourrier extends Modem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

## Dynamic Polymorphism Technique Applied Through Interface´s Implementation

```java
public interface IModem {

    public void dial(String pno);
    public void send(String s);
    public String recv();
    public void hangUp();

    public void logOn(ModemType m, String pno, String user, String pw) {
         m.Dial(pno);
         ...
    }
    ...
}
```

```java

public class ModemHayes implements IModem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

```java
public class ModemErnie implements IModem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

```java
public class ModemCourrier implements IModem {
    @Overrides
    public void dial(String pno) { ... }
    @Overrides
    public void send(String s) { ... }
    @Overrides
    public String recv()  { ... }
    @Overrides
    public void hangUp() { ... }
}
```

## Static Polymorphism Technique to Implement Open-Closed Principle (OCP)

Another technique for conforming to the OCP is through the use of **generics** or **parametric classes** in *Java* and **templates** in *C++*, that let us implement static polymorphims to conform the Open-Close Principle requirements.

The following *C++ source code* example shows how this is done. The *logOn method* can be extended in the future in this way with many different types of modems without requiring modification.

```c++

template <typename MODEM>

void logOn(MODEM& m, string& pno, string& user, string& pw) {

    m.dial(pno);
}

````

The following *Java source code* example below shows how we can use *Generic Type* (named also *Parameterized Type*) to get the way where the *logOn method* can be extended with many different types of modems without requiring modification:

```java
public class Modem< M > {

    private  M  modemType;  
    
    public void dial(String pno, String user, String pw) { ... }
    public void send(String s) { ... }
    public String recv() { ... }
    public void hangUp() { ... }
    public void logOn(Modem<M> m, String pno, String user, String pw) {    	
         m.dial(pno, user, pw);
         ...
    }
}
```

## Architectural Goals of the OCP Principle

By using these techniques to conform to the OCP, we can create modules that are extensible, without being changed. This means that, with a little forethought, we can add new features to existing code, without changing the existing code and by only adding new code. This is an ideal that can be difficult to achieve, but you will see it achieved, several times, using those techniques described in th previous sections.

Even if the OCP cannot be fully achieved, even *partial OCP compliance* can make dramatic improvements in the structure of an application. It is always better if changes *do not propogate into existing code that already works*. If you *don’t have to change working code*, you *aren’t likely to break it*.

### Why Apply OCP Principle

Improve maintainability and stability by minimizing changes to existing code.

### How to Apply OCP Principle

* Write classes that can be extended (as opposed to classes that can be modified) through the us of the dynamic and static polimorphysm;
* Expose only the moving parts that need to change, hide everything else;

### Resources Aboiut OCP Principle

>* [link to Open Closed Principle in Wikipedia](https://en.wikipedia.org/wiki/Open/closed_principle)
>* [Link to Article Explaining The Open Closed Principle](https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html)

# LSP Liskov Substitution Principle

## Introduction 

>
>    *Subclasses should be substitutable for their base classes.*
>    *or*  
>    *If type X extends type Y then an object of type X can always be used wherever an object of type Y is expected.*
>

This principle was coined by *Barbar Liskov* in her work regarding *data abstraction* and *type theory*. It also derives from the concept of *Design by Contract (DBC)* by
Bertrand Meyer. 

The concept, as stated above, is depicted in Figure below, where *Derived classes should be substitutable for their base classes*. That is, a user of a *base class* should continue to function properly if a *derivative* of that *base class* is passed to it.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/UML_Diagram_Liskov_Substitution_Principle_LSP_001.jpg)

In other words, if some method User takes an argument ot type Base, then as shown in Listing below, it should be legal to pass in an instance of Derived to that
method.

```java
public Class Base { ... }
public class Derived extends Base { ... }
public class App {
  private Derived d;
  public void User(Base b) { ... } 
  ...
  User(d);
  ...
}
```

This may seem obvious, but there are subtleties that need to be considered. The canonical example is the Circle/Ellipse dilemma.

### The Circle/Ellipse Dilemma. 

Most of us learn, in high school math, that a circle is just a degenerate form of an ellipse. All circles are ellipses with coincident foci.  This is-a relationship tempts us to model circles and ellipses using inheritance as shown in the following UML Diagram:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/UML_Diagram_Circle_Elipse_Dillema_LCP_Principle_001.jpg)

While this satisfies our *conceptual model*, there are certain difficulties. A closer look at the *declaration of Ellipse in Figure above* begins to expose them. Notice that
Ellipse has three data elements. The first two are the *foci*, and the last is the *length of the major axis*. If *Circle inherits from Ellipse*, then it will *inherit these data variables*. This is unfortunate since *Circle* really only needs *two data elements*, a *center point* and a *radius*.

```java
package designpatterns;

public class Ellipse {

	private double _itsFocusA;    // x axis
	private double _itsFocusB;    // y axis
	private double _itsMajorAxis;
	
	public double circumference() {
          double a = _itsFocusA, b = _itsFocusB;
	  return 2*3.14*Math.sqrt((Math.pow(a,2)+Math.pow(b,2))/2);	
	}
	public double area(){
           return 3.142 * _itsFocusA * _itsFocusB;
	}
	public double getFocusA() {
	   return _itsFocusA;
	}
	public double getFocusB() {
	   return _itsFocusB;
	}
	public double getMajorAxis() {
	   return _itsMajorAxis;
	}
	public double getMinorAxis () {
	   return _itsMajorAxis;
	}
	public void setFoci ( double a, double b) {
	   _itsFocusA = a;
	   _itsFocusB = b;
	}
	public void setMajorAxis (double a) {
	   _itsMajorAxis = a; 
	}
	public void f (Ellipse e) {
	    double a = -1; 
	    double b = 1;  
	    e.setFoci(a,b);
	    e.setMajorAxis(3);
            assert(e.getFocusA() == a);
	    assert(e.getFocusB() == b);
	    assert(e.getMajorAxis() == 3);    	    
	}
}
```

Still, if we ignore the slight overhead in space, we can make *Circle* behave properly by *overriding its SetFoci method* to ensure that both *foci* are kept at the *same value*. See Listing shown below. Thus, either *focus* will act as the *center of the circle*, and the *major axis* will be its *diameter*.

```java
// Keeping the Circle Foci coincident

public class Circle extends Ellipse {

   public void setFoci(double a, double b)    {
       
       double itsFocusA = a;
       double itsFocusB = a;
   }
   ...
}
```

## Clients Ruin Everything

Certainly the *model* we have created is *self consistent*. An *instance of Circle* will obeys all the *rules of a circle*. There is nothing you can do to it to make it violate those rules. So too for *Ellipse*. The *two classes* form a nicely consistent *model*, even if *Circle has one too many data elements*.

However, *Circle* and *Ellipse* do not live alone in a universe by themselves. They cohabit that universe with many *other entities*, and provide their *public interfaces*
to those *entities*. Those *interfaces* imply a *contract*. The *contract may not be explicitly stated*, but *it is there nonetheless*. For example, users of *Ellipse* have the
right to expect the following *code fragment* to succeed: 

```java

public void f (Ellipse e) {
   double a = -1, b = 1;
   e.setFoci(a,b);
   e.setMajorAxis(3);
   assert(e.getFocusA() == a);
   assert(e.getFocusB() == b);
   assert(e.getMajorAxis() == 3);
}

```

In this case the method expects to be working with an *Ellipse*. As such, it expects to be able to set the *foci*, and *major axis*, and then verify that they have been properly set. If we pass an *instance of Ellipse* into this method, it will be quite happy. However, if we pass an *instance of Circle* into the method, it will fail rather badly.

If we were to make the *contract of Ellipse explicit*, we would see a *postcondition* on the *setFoci method* that guaranteed that the input values got copied to the *member variables*, and that the *major axis variable was left unchanged*. Clearly *Circle violates this guarantee* because it ignores the *second input variable of setFoci*.

## Design by Contract

Restating the *LSP (Liskov Substitution Principle)*, we can say that, *in order to be substitutable, the contract of the base class must be honored by the derived class*. Since *Circle* does not honor the implied *contract of Ellipse*, it is *not substitutable and violates the LSP*.

Making the *contract explicit* is an avenue of research followed by *Bertrand Meyer*. He has invented a language named *Eiffel* in which *contracts are explicitly stated for each method, and explicitly checked at each invocation*. Those of us who are not using *Eiffel*, *have to make do with simple assertions and comments*.

**To state the contract of a method**, we *declare what must be true before the method is called*. This is called the **precondition**. If the *precondition fails*, the *results of the method are undefined*, and the *method ought not be called*. We also declare what the *method guarantees will be true once it has completed*. This is called the *postcondition*. A *method that fails its postcondition should not return*. 

Restating the LSP once again, this time in *terms of the contracts*, a *derived class is substitutable for its base class if*:

> 1. Its *preconditions* are **no stronger** than the *base class method*.
> 2. Its *postconditions* are **no weaker** than the *base class method*.

Or, in other words, *derived methods* should *expect no more and provide no less*.

## Repercussions of LSP Violation

Unfortunately, LSP violations are difficult to detect until it is too late. In the Circle/Ellipse case, everything worked fine until some client came along and discovered that the implicit contract had been violated.

If the design is heavily used, the cost of repairing the LSP violation may be too great to bear. It might not be economical to go back and change the design, and then rebuild
and retest all the existing clients. Therefore the solution will likely be to put into an if/else statement in the client that discovered the violation. This if/else statement checks to be  sure that the Ellipse is actually an Ellipse and not a Circle. See the following source code fragment:

**Ugly fix for LSP violation**

```java
	public void f (Ellipse e) throws Exception {
	   if ( e instanceof Ellipse ) 
		 throw new Exception (" Not an Ellipse(e) ");	
           else {    		
		double a = -1; 
		double b = 1;  
		e.setFoci(a,b);
		e.setMajorAxis(3);
		assert(e.getFocusA() == a);
		assert(e.getFocusB() == b);
		assert(e.getMajorAxis() == 3);    	    
	  }
	}
```

Careful examination of source code fragment above will show **it to be a violation of the OCP**. Now, whenever some new derivative of Ellipse is created, this function will have to be checked to see if it should be allowed to operate upon it. Thus, **violations of LSP are latent violations of OCP.**

## Resources About LSP Principle

>* [link to Article of Liskov substitution principle in Wikipedia](https://en.wikipedia.org/wiki/Liskov_substitution_principle)
>* [Link to Article Explaining The Liskov Substitution Principle](http://www.blackwasp.co.uk/lsp.aspx)

# ISP Interface Segregation Principle

The ISP states that no cliente should be forced to depend on methods it does not use.

- Avoid depending on things that you don´t use.
- Make fine-grained interfaces that are client specific.

- The ISP guides us to create many small interfaces with coherent functionalities instead of a few big interfaces with lots of different methods. When we apply the ISP, class and their dependencies communicate using focused interfaces, minimizing dependencies. Smaller interfaces are easier to implement, improving flexibility and the possibility of reuse.

Reduce fat interfaces into multiple smaller and more specific client specific interfaces. An interface should be more dependent on the code that calls it than the code that implements it.

### Why Apply ICP

* If a class implements methods that are not needed the caller needs to know about the method implementation of that class. For example if a class implements a method but simply throws then the caller will need to know that this method shouldn't actually be called.

### How to Apply ICP

* Avoid fat interfaces. Classes should never have to implement methods that violate the Single responsibility principle.

### Resources About ICP

>* [linto to Interface segregation principle in Wikipedia](https://en.wikipedia.org/wiki/Interface_segregation_principle)

# DIP Dependency Inversion Principle

## Introduction

The *Dependency Inversion Principke (DIP)* tell us that the most flexible applications are those in which source *code dependenciesrefer only to abstraction, not to concretions*. 

In a *statically typed language*, like *Java*, this means that the *use*, *import*, and *include* statements should refere only to source modules constaining *interfaces*, *abstract classes*, or *some kind of abstractions*.  Nothing concrete shoul be depended on.

The same *rule* applies for *dynamically type languages*, like *Python* and *Ruby*. Source *code dependencies* **should not refer to** *concrete modules*. However, in these languages it is a bit harder to define what a concrete module is. In particular, it is any module in which the functions being called are implemented.

## The Rule of DIP

The code that implement high-level policy should not depend on the code that implements low-level details. Rather, details should depend on policies.

- Depend on abstraction, not on concretion.

In object-oriented design, the dependency inversion principle is a specific form of decoupling software modules. When following this principle, the conventional dependency relationships established from high-level, policy-setting modules to low-level, dependency modules are reversed, thus rendering high-level modules independent of the low-level module implementation details. The principle states:[1]

> *1.  High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g., interfaces).*
> *1.  Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions.*

By dictating that both *high-level* and *low-level objects* must depend on the *same abstraction*, this design principle inverts the way some people may think about object-oriented programming.

The idea behind points "1" and "2" above of this principle is that when designing the interaction between a high-level module and a low-level one, the interaction should be thought of as an abstract interaction between them. This not only has implications on the design of the high-level module, but also on the low-level one: the low-level one should be designed with the interaction in mind and it may be necessary to change its usage interface.

In many cases, thinking about the interaction in itself as an abstract concept allows the coupling of the components to be reduced without introducing additional coding patterns, allowing only a lighter and less implementation-dependent interaction schema.

When the discovered abstract interaction schema(s) between two modules is/are generic and generalization makes sense, this design principle also leads to the following dependency inversion coding pattern.

In conventional application architecture, lower-level components (e.g., Utility Layer) are designed to be consumed by higher-level components (e.g., Policy Layer) which enable increasingly complex systems to be built. In this composition, higher-level components depend directly upon lower-level components to achieve some task. This dependency upon lower-level components limits the reuse opportunities of the higher-level components.

![traditional layers pattern](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Traditional_Layers_Pattern001.png)

### How to Implement Dependency Injection Principle 

The goal of the dependency inversion pattern is to avoid this highly coupled distribution with the mediation of an abstract layer, and to increase the re-usability of higher/policy layers.

With the addition of an abstract layer, both high- and lower-level layers reduce the traditional dependencies from top to bottom. Nevertheless, the "inversion" concept does not mean that lower-level layers depend on higher-level layers. Both layers should depend on abstractions that draw the behavior needed by higher-level layers.

![dip layers](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/DIPLayersPattern002A.png)

In a direct application of dependency inversion, the abstracts are owned by the upper/policy layers. This architecture groups the higher/policy components and the abstractions that define lower services together in the same package. The lower-level layers are created by inheritance/implementation of these abstract classes or interfaces.[1]

The inversion of the dependencies and ownership encourages the re-usability of the higher/policy layers. Upper layers could use other implementations of the lower services. When the lower-level layer components are closed or when the application requires the reuse of existing services, it is common that an Adapter mediates between the services and the abstractions.

### Dependency inversion Principle generalization

In many projects the dependency inversion principle and pattern are considered as a single concept that should be generalized, i.e., applied to all interfaces between software modules. There are at least two reasons for that:

>a) It is simpler to see a good thinking principle as a coding pattern. Once an abstract class or an interface has been coded, the programmer may say: "I have done the job of abstraction".
>b) Because many unit testing tools rely on inheritance to accomplish mocking, the usage of generic interfaces between classes (not only between modules when it makes sense to use generality) became the rule.

If the mocking tool used relies only on inheritance, it may become necessary to widely apply the dependency inversion pattern. This has major drawbacks:

>1. Merely implementing an interface over a class isn't sufficient to reduce coupling; only thinking about the potential abstraction of interactions can lead to a less coupled design.
>2. Implementing generic interfaces everywhere in a project makes it harder to understand and maintain. At each step the reader will ask themself what are the other implementations of this interface and the response is generally: only mocks.
>3. The interface generalization requires more plumbing code, in particular factories that generally rely on a dependency-injection framework.
>4. Interface generalization also restricts the usage of the programming language.

### Generalization restrictions of Dependency Injection Principle 

The presence of interfaces to accomplish the Dependency Inversion Pattern (DIP) has other design implications in an object-oriented program:

>* All member variables in a class must be interfaces or abstracts.
>* All concrete class packages must connect only through interface or abstract class packages.
>* No class should derive from a concrete class.
>* No method should override an implemented method.
>* All variable instantiation requires the implementation of a creational pattern such as the factory method or the factory pattern, or the use of a dependency-injection framework.

### Interface mocking restrictions with Dependency Injection Principle

Using inheritance-based mocking tools also introduces restrictions:

>* Static externally visible members should systematically rely on dependency injection making them far harder to implement.
>* All testable methods should become an interface implementation or an override of an abstract definition.

### Example of DIP applyed using Abstract Class instead of Interface

![DIPRealCase001](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/RealCaseOfDIPUUsingAbstractClassInteadOfInterface.jpg)

```java
public class Rental {
	private Movie _movie;
	private int _daysRented;

	public Rental(Movie movie, int daysRented) {
		_movie = movie;
		_daysRented = daysRented;
	}
	public int getDaysRented() {
		return _daysRented;
	}
	public Movie getMovie() {
		return _movie;
	}
	public int getFrequentRenterPoints() {
		
		int daysRented = getDaysRented();
		return _movie.getFrequentRenterPoints(daysRented);
	}
	public double getAmount() {
		
		int daysRented = getDaysRented();
		return _movie.getAmount(daysRented);
	}
}
```

```java
public abstract class Movie {
	
	public static final int CHILDRENS = 2;	
	public static final int REGULAR = 0;
	public static final int NEW_RELEASE = 1;
	private String _title;

        public static Movie factoryMovie(String title, int typeOfMovie) throws Exception {
		
		//  Factory Method Pattern 
		if (typeOfMovie == REGULAR)
			return new RegularMovie (title);
		if (typeOfMovie == CHILDRENS)
			return new ChildrensMovie (title);	
		if (typeOfMovie == NEW_RELEASE)
			return new NewReleaseMovie (title);	
		
		throw new Exception("Nao Existe Este tipo de Filme - Os tipos Atuais sao REGULAR, CHILDRENS e NEW-RELEASE");
	}
	public Movie(String title) {
		_title = title;
	}
	public String getTitle() {
		return _title;
	}
	public abstract double getAmount(int daysRented);

	public abstract int getFrequentRenterPoints(int daysRented);
}
```

```java
public class RegularMovie extends Movie {
	public RegularMovie(String title) {
		super(title);
	}
	public double getAmount(int daysRented) {
		double thisAmount = 2;
		if (daysRented > 2)
			thisAmount += (daysRented - 2) * 1.5;
		return thisAmount;
	}
	public int getFrequentRenterPoints(int daysRented) {
		return 1;
	}
}
```
```java
public class ChildrensMovie extends Movie {
	public ChildrensMovie(String title) {
		super(title);
	}
	public double getAmount(int daysRented) {
		double thisAmount = 1.5;
		if (daysRented > 3)
			thisAmount += (daysRented - 3) * 1.5;
		return thisAmount;
	}
	public int getFrequentRenterPoints(int daysRented) {
        return 1;
	}
}
```
```java
public class NewReleaseMovie extends Movie {
	public NewReleaseMovie(String title) {
		super(title);
	}
	public double getAmount(int daysRented) {
		double thisAmount = 0;
		thisAmount += daysRented * 3;
		return thisAmount;
	}
	public int getFrequentRenterPoints(int daysRented) {
		if (daysRented > 1)
			return 2;  else  return 1;
	}
}
```

# Summary of Good Practices of Design

- **SoC**   - Separation of Concerns
- **KISS**  - Keep it Simple
- **DRY**   - Don´t Repeat Yourself
- **TDA**   - Tell Don´t Ask
- **LoD**   - Law of Demeter - Each Unit Should have only limited knowledge about other units 
- **YAGNI** - You aren´t gonna need it
- **TDA**   - Tell, Don´t Ask

# SoC Separation of Concerns

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

### a) Internet protocol stack

Separation of concerns is crucial to the design of the Internet. In the Internet Protocol Suite, great efforts have been made to separate concerns into well-defined layers. This allows protocol designers to focus on the concerns in one layer, and ignore the other layers. The Application Layer protocol SMTP, for example, is concerned about all the details of conducting an email session over a reliable transport service (usually TCP), but not in the least concerned about how the transport service makes that service reliable. Similarly, TCP is not concerned about the routing of data packets, which is handled at the Internet Layer.

### b) HTML, CSS, JavaScript

HyperText Markup Language (HTML), Cascading Style Sheets (CSS), and JavaScript (JS) are complementary languages used in the development of web pages and websites. HTML is mainly used for organization of webpage content, CSS is used for definition of content presentation style, and JS defines how the content interacts and behaves with the user. Historically, this was not the case: prior to the introduction of CSS, HTML performed both duties of defining semantics and style.

### c) Subject-oriented programming

Subject-oriented programming allows separate concerns to be addressed as separate software constructs, each on an equal footing with the others. Each concern provides its own class-structure into which the objects in common are organized, and contributes state and methods to the composite result where they cut across one another. Correspondence rules describe how the classes and methods in the various concerns are related to each other at points where they interact, allowing composite behavior for a method to be derived from several concerns. Multi-dimensional Separation of Concerns allows the analysis and composition of concerns to be manipulated as a multi-dimensional "matrix" in which each concern provides a dimension in which different points of choice are enumerated, with the cells of the matrix occupied by the appropriate software artifacts.

### d) Aspect-oriented programming

Aspect-oriented programming allows cross-cutting concerns to be addressed as primary concerns. For example, most programs require some form of security and logging. Security and logging are often secondary concerns, whereas the primary concern is often on accomplishing business goals. However, when designing a program, its security must be built into the design from the beginning instead of being treated as a secondary concern. Applying security afterwards often results in an insufficient security model that leaves too many gaps for future attacks. This may be solved with aspect-oriented programming. For example, an aspect may be written to enforce that calls to a certain API are always logged, or that errors are always logged when an exception is thrown, regardless of whether the program's procedural code handles the exception or propagates it.[8]

### e) Levels of analysis in artificial intelligence

In cognitive science and artificial intelligence, it is common to refer to David Marr's levels of analysis. At any given time, a researcher may be focusing on (1) what some aspect of intelligence needs to compute, (2) what algorithm it employs, or (3) how that algorithm is implemented in hardware. This separation of concerns is similar to the interface/implementation distinction in software and hardware engineering.

### f) Normalized systems

In normalized systems separation of concerns is one of the four guiding principles. Adhering to this principle is one of the tools that helps reduce the combinatorial effects that, over time, get introduced in software that is being maintained. In Normalized Systems separation of concerns is actively supported by the tools.

## Implementation

The mechanisms for modular or object-oriented programming that are provided by a programming language are mechanisms that allow developers to provide SoC.[4] For example, object-oriented programming languages such as C#, C++, Delphi, and Java can separate concerns into objects, and architectural design patterns like MVC or MVP can separate content from presentation and the data-processing (model) from content. Service-oriented design can separate concerns into services. Procedural programming languages such as C and Pascal can separate concerns into procedures or functions. Aspect-oriented programming languages can separate concerns into aspects and objects.

Separation of concerns is an important design principle in many other areas as well, such as urban planning, architecture and information design.[5] The goal is to more effectively understand, design, and manage complex interdependent systems, so that functions can be reused, optimized independently of other functions, and insulated from the potential failure of other functions.

Common examples include separating a space into rooms, so that activity in one room does not affect people in other rooms, and keeping the stove on one circuit and the lights on another, so that overload by the stove does not turn the lights off. The example with rooms shows encapsulation, where information inside one room, such as how messy it is, is not available to the other rooms, except through the interface, which is the door. The example with circuits demonstrates that activity inside one module, which is a circuit with consumers of electricity attached, does not affect activity in a different module, so each module is not concerned with what happens in the other.

# KISS Keep It Simple Principle

Most systems work best if they are kept simple rather than made complex.

### Why Apply KISS

* Less code takes less time to write, has less bugs, and is easier to modify.
* Simplicity is the ultimate sophistication.
* It seems that perfection is reached not when there is nothing left to add, but when there is nothing left to take away.

### Resources about KISS

>* [KISS principle](https://en.wikipedia.org/wiki/KISS_principle)
>* [Keep It Simple Stupid (KISS)](http://principles-wiki.net/principles:keep_it_simple_stupid)

# Keep things DRY

Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

Each significant piece of functionality in a program should be implemented in just one place in the source code. Where similar functions are carried out by distinct pieces of code, it is generally beneficial to combine them into one by abstracting out the varying parts.

### Why Apply DRY Principle

Duplication (inadvertent or purposeful duplication) can lead to maintenance nightmares, poor factoring, and logical contradictions.
A modification of any single element of a system does not require a change in other logically unrelated elements.
Additionally, elements that are logically related all change predictably and uniformly, and are thus kept in sync.

### How to Apply DRY Principle

Put business rules, long expressions, if statements, math formulas, metadata, etc. in only one place.
Identify the single, definitive source of every piece of knowledge used in your system, and then use that source to generate applicable instances of that knowledge (code, documentation, tests, etc).
Apply the Rule of three.

### Resources about DRY Principle

>* [Dont Repeat Yourself](http://wiki.c2.com/?DontRepeatYourself)
>* [Don't repeat yourself](https://en.wikipedia.org/wiki/Don't_repeat_yourself)
>* [DRY Principle: Its Benefit and Cost with Examples](https://thevaluable.dev/dry-principle-cost-benefit-example/)

### Related

* [Abstraction principle](https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming))
* [Once And Only Once](http://wiki.c2.com/?OnceAndOnlyOnce)] - is a subset of DRY (also referred to as the goal of refactoring).
* [Single Source of Truth](https://en.wikipedia.org/wiki/Single_Source_of_Truth)
* A violation of DRY is [WET (Write Everything Twice)]](http://thedailywtf.com/articles/The-WET-Cart)
* [Be careful with the code metric "duplicated lines"](https://rachelcarmena.github.io/2018/02/27/duplication-you-are-welcome.html)

# YAGNI Principle

YAGNI stands for "you aren't gonna need it": don't implement something until it is necessary.

### Why Apply YAGNI 

Any work that's only used for a feature that's needed tomorrow, means losing effort from features that need to be done for the current iteration.
It leads to code bloat; the software becomes larger and more complicated.

### How to Apply YAGNI

Always implement things when you actually need them, never when you just foresee that you need them.

### Resources About YAGNI

>* [You Arent Gonna Need It](http://c2.com/xp/YouArentGonnaNeedIt.html)
>* [You’re NOT gonna need it!](https://ronjeffries.com/xprog/articles/practices/pracnotneed/)(
>* [You aren't gonna need it](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)

#  Lod Law of Demeter Principle

The present description is bases on Robert Brautigam article mixed qith other sources. The original article of Robert Brautigam is:

- [original article of Robert Brautigam ](https://javadevguy.wordpress.com/2017/05/14/the-genius-of-the-law-of-demeter/)

## Introduction

This a simple programming language rule, named as the Law of Demeter, which encodes the ideas of encapsulation and modularity in an easy to follow form for the object-oriented programming. Can be get the following benefits when we follow the Law of Demeter while minimizing simultaneously *code duplication*, the *number of method arguments* and the *number of methods per class*: 

- Easier software maintenance, 
- less coupling between your methods, 
- better information hiding, 
- narrower interfaces, 
- methods which are easier to reuse, and 
- easier correct.ness proofs using structural induction. 

The point is *how any object-oriented program can be transformed to satisfy the Law fo Demeter.*

## Why Should We Obey the Law of Demeter?

There are well-known *abstract concepts* in *Object-Oriented programming*, like **encapsulation**, **cohesion**, and **coupling**, that could be theoretically used to generate *clear designs and good code*. While these are all very important concepts, they are just not pragmatic enough to be directly useful for development. One has to interpret these concepts, and with that, they become somewhat subjective and start to depend on people’s experience and knowledge.

The same can be said for other concepts like the *Single Responsibility Principle*, or the *Open/Closed Principle*, etc. These allow a very wide margin for interpretation, so the practicality, the direct usefulness, is therefore diminished.

The beauty of the *Law of Demeter* comes from the *succinct and exact definition*, which allows for a direct application when writing code, while at the same time almost automatically guaranteeing proper *encapsulation, cohesion, and loose coupling*. The authors of the Law managed to take these *abstract concepts* and distil the essence of them into a clear *set of rules* that are universally applicable to Object-Oriented coding.

## What does The Law of Demeter state?

The Law, in its *original form*, is stated in the following way:

> **For all classes C, and for all methods M attached to C, all objects to which M sends a message must be instances of classes associated with the following classes:**
>
> **1. The argument classes of M (including C).**
> **2. The instance variable classes of C.**
> 
> **(Objects created by M, or by functions or methods which M calls, and objects in global variables are considered as arguments of M.)**

## Considerations about Law of Demeter

In the early days of Object-Orientation, *objects* were supposed to *“send messages” to each other*. That is how they communicated. So the term *“objects to which M sends a message”* roughly translates to *“objects used by M,”* or in a more practical definition *“objects on which M calls a method on.”*

You might have noticed that there are some very important additional points made in parentheses after the two rules. They seem like clarifications mentioned just in passing, but they are actually additional rules. So let’s reformulate the whole Law so all points stand independently:

For all *classes C*, and for all *methods M* attached to *C*, all *objects* to which *M* sends a message must be:

* Rule 1. **self** (**this** in *Java*)
* Rule 2. M’s argument objects
* Rule 3. Instance variable objects of C
* Rule 4. Objects created by M, or by functions or methods which M calls
* Rule 5. Objects in global variables (**static** fields in Java)

## What Does It Mean?

The law formulates what we are allowed to do in any given *ethod M* So, let’s work backward and find out *hat it is exactly what this law prohibits*

**Rule #4** states, that all *objects* created during the *call to M*, either directly or indirectly, are allowed. So the prohibition must be among objects that already existed when the call began.

These already existing objects must have a *reference* to them, otherwise, nobody would be able to access them. Therefore these *objects* must be *referenced* from fields (variables) of other *objects*. **Rule #5** allows *global objects*, so that leaves us with *objects* in *instance variables*.

**Rules #1, #2, and #3** further allows “self”, *M’s parameters* and all *objects* in *instance variables of C*.

That means that *the Law prohibits “sending a message” to any already existing object that is held in instance variables of other classes*, unless it is also held by our *class* or passed to us as *method parameters*.

Let’s look at some examples of the Law in action:

**Example 1:**

```java
public final class NetworkConnection {

	public void close() {
	
		sendShutdownMessage(); // Allowed?
	}
	private void sendShutdownMessage() {
		...
	}
}
```

The *method call sendShutdownMessage()* is obviously allowed, because it is covered by **Rule #1 ( The argument classes of M (including C)**.  Any method can be called on the current object.

**Example 2:**

```java

public final class NetworkConnection {
	
	private Socket socket;
	
	public void close() {
		
		socket.close(); // Allowed?
	}
}
```

That is also allowed, because of **Rule #3 -  Instance variable objects of C** (as *socket* is an *instance variable* of this *class*).

**Example 3:**

```java
public final class NetworkConnection {
	
	public void send(Person person) {
		
		sendBytes(person.getName().getBytes());
		
		sendBytes(person.getPhoto().getBytes();
		
		...
	}
}
```

This is a **violation of the Law of Demeter**. The *method* received the *parameter person*, so all *method calls* on this *object* are allowed. However, calling any *methods* (in this case *getBytes()*) on the *object returned* by either *getName()* or *getPhoto()* is **not allowed**. Assuming *standard getters*, these *objects* are already *existing objects* in *other objects’ instance variables*, therefore they are exactly the *kind of objects* this *method* **should not have access to**.

**Example 4 - Chain Calls:**  

Some explanations of the Law concentrate on so-called “chain calls”, that is, expressions which contain multiple dereferencings. Or stated plainly, multiple “dots”, like the following example:

```java
    car.getOwner().getAddress().getStreet();
```

This is almost certainly a **violation of the Law**, since *all those objects (owner, address) are presumably already-existing instance variable values, to which the Law prohibits access.*  However, **it is not* the *chain-calling* that makes the above a **violation**, but the *access to certain objects*. The following “refactored” code still violates the Law:

```java
   Owner owner = car.getOwner();
   Address ownerAddress = owner.getAddress();
   Street ownerStreet = ownerAddress.getStreet();
```

As above, the objects in *owner* , *ownerAddress* , and *ownerStreet* are still **not covered by any of the rules*, therefore *no methods should be called on them*. 

**Example 4 - Fluent APIs**

Some interpretations of the Law argue that since chain-calls are not allowed, fluent APIs are also forbidden. Fluent APIs are created to allow syntactically easy usage of a library or set of classes. They look like the following example:

```java
Report report = new ReportBuilder()
                .withBorder(1)
                .withBorderColor(Color.black)
                .withMargin(3)
                .withTitle("Law of Demeter Report")
                .build();
```

To determine whether such a construct is allowed, we just *have to check each method call to see whether it is specifically allowed*. The *ReportBuilder object* is created in this *method* right now, so the first *method* call *withBorder(1)* is on a *freshly created object*. This is *explicitly allowed by* **Rule #4**.

All the following *method calls*, including the last *build() call* are all using the *returned objects* from the *previous call*. What is the *return value* of all these *methods*? Well, most of the *fluent APIs* just return the *same object* over and over again. That is still covered by **Rule #4** because the *builder* is an *object* that was created in this code. Some *fluent PIs* use *immutable objects* and return a *new object* every time. But even if this is the case, **Rule #4** still applies to *indirectly created objects too*. So the *Law of Demeter* **does not prohibited** *fluent APIs*.

Ecample 5 - “Wrapper” Methods**

Some, including the [Wikipedia Article on the Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter), argue that the Law implies the usage of *“Wrapper” methods* to get around *calling methods* on *foreign objects*, like the following example:

```java

  car.getOwner().getAddress().getStreet(); // This is a violation

  car.getOwnerAddressStreet();             // This is a proposed "solution

```

There are a couple of problems with this approach. For example: How is *getOwnerAddressStreet()* implemented? Presumably like the following:

```java
public final class Car {
	
	private final Owner owner;
	
	public Street getOwnerAddressStreet() {
		
		return owner.getAddressStreet();
	}
	...
}
```
So two new methods are introduced, but there was no real structural or design change. One could argue that while the Law was technically followed, the spirit of the Law was still violated. 

The structure is still visible in the method name, and we all know that the caller wants to get the street of the address of the owner of the car. 

The question is: Why does the caller want that, and how does he/she even know that this information exists at this point? This is when applying the Law blends together with Object-Oriented Design. Obviously, the purpose of the Law is not to roll additional hurdles in our way and make our lives more difficult. The same way that our job is not to make sure that we technically follow all the rules without thinkinh about our overall design.

What the Law is quite clearing saying is that you shouldn’t access the Street in this structure. As in, you shouldn’t even know it’s there. Don’t trick the definition by introducing wrapper methods! There is a deeper design isseu here that needs to be addressed (no pun intended)!

**Example 6 - Pure "Data Strcutures"**

In his book Clean Code, Robert C. Martin has a short section on the Law of Demeter, where he makes two interesting points. One is that perhaps by using direct access to variables, the Law could be circumvented. So instead of this...
 
```java
   car.getOwner().getAddress().getStreet();
 ```
 
...which is not acceptable, it could be transformed into the following, which complies with the Law,
since it doesn’t involve method calls:

```java
  .owner.address.street; // Using direct access to fields
  ```
  
  There are two arguments against this line of reasoning. One is that it still just tries to work around the
Law instead of heeding its advice. And the second is that direct access to fields arguably still qualifies as "sending a message", since it is still just communicating between two objects.

There is a more nuanced point made by Uncle Bob regarding the aboce - that the Law of Demeter should not apply to pure data structures anyway.

Pure data structures ("objects" that gave no behavior, just data) are integral building blocks of a procedural, functional or a mixed paradigm approach. As such, they are of course exempt from having to comply with the Law of Demeter, which is a Law for Object-Oriented development.

**Example 7 - Getters**

Most, if not all of the *negative examples* for the *Law of Demeter* given involve *“getter” methods*. These
are *methods* like the following:

```java
public final class Car {
	
	private final Owner owner;
	
	public Owner getOwner() {
		
		return owner;
	}
}
```
It is not a coincidence that this is the case. Let’s imagine another *method*, which uses this *getter*:

```java
public final class Garage {
	
	public void isAllowed(Car car) {
		
		Owner owner = car.getOwner(); // Allowed?
		...
	}
}
```

Is the above call even allowed? Well, technically yes. The car object is a direct parameter to the method, so I may call methods on this object.

However, let’s think about what can be done with the result of this call. The method returns an owner object, which is neither a parameter nor an object that the Garage has direct access to. Therefore there can be no further method calls on this object. Not toString() , not hashCode() , nothing!
 
This might be considered unexpected. So that means while calling the getter itself might be technically legal, we can’t actually use the result. It seems getter methods violate the Law of Demeter almost by design.

As previously said, this is neither a coincidence nor is it unintentional. In the Object-Oriented paradigm, objects are supposed to tell other objects what to do — delegate, instead of querying data from others and doing everything themselves.

## When to Apply

There are some opinions in blog posts and other articles expressing that the Law of Demeter is less
of a “law” and only a “suggestion” or a “guideline.” Or that it is fine in theory, but *the Law od Demeter does not apply to* 
certains objects, like:

- *data structures,*
- *Java Beans,* 
- *entities,*
- *business objects,* 
- *value objects,*
- *data transfer objects,* or
- *objects for presentation or persistence.*

An Object-Oriented developer should be aware that more often than not, these opinions come from a background of different programming paradigms, in which the Law of Demeter might very well have a different weight or even interpretation than in Object-Orientation.

The Law of Demeter is the law of the land in Object-Oriented development. As the original paper itself calls it, it is the Law of Good Style. Complying with the Law technically and in spirit everywhere is the minimum required to produce proper, well designed Object-Oriented code.

## The Motivation and Explanation

The motivation behind this Law is to ensure that the software is as modular as possible. Any method written to obey this Law will only know about the immediate structure of the class to which it is attached. The structure of the arguments and the sub-structure of C are hidden from M. Therefore, should a change to the structure of the class C be necessary we need only to look at those methods attached to C and its subclasses for possible conflicts. The Law effectively reduces the occurrences of certain nested message sendings (generic method calls) and simplifies the methods. The Law prohibits the nesting of generic accessor method calls, which return objects that are not instance variable objects. It allows the nesting of constructor function calls. An accessor method is a method which returns an object which did exist before the method is called. A constructor method returns an object which did not exist before the method is called.

The Law of Demeter has many implications regarding widely known software engineering principles. Below there are many of the proven principles of software design into a single statement which can easily be used by the object-oriented programmer and which can be easily checked at compile-time. 

Some of the inter-related principles covered by the Law are the following:

### Coupling control

It is a well-known principle of software design to have minimal coupling between abstractions (e.g. procedures, modules, methods) [3]. The coupling can be along several links. An important link for methods is the “uses” link (or call/return link) which is established when one method calls another method. The Law of Demeter effectively reduces the methods we can call inside a given. a method and therefore limits the coupling of methods with respect to the “uses” relation. The Law therefore facilitates reusability of methods and the abstraction level of the software.

### Information hiding

The Law of Demeter enforces one kind of information hiding: structure hiding. In general, the Law prevents a method from directly retrieving  a subpart of an object which lies deep in that object’s “part-of” hierarchy. Instead, intermediate methods must be used to traverse the “part-of” hierarchy in controlled small steps. In some object-oriented systems, the user can protect some of the instance variables or methods of a class from outside access by making them private. This important feature complements the Law to increase modularity but is orthogonal to it. Our Law promotes the idea that the instance variables and methods which are public should be used in a restricted way.

###  Information restriction

Our work is related to the work by Parnas et al. on the modular structure of complex systems. To reduce the cost of software changes in their operational flight program for the A-7E aircraft, the use of modules that provide information that is subject to change is restricted. We take this point of view seriously in our objectoriented programming and assume that any class could change. Therefore we restrict the use of message seendings (generic function calls) by the Law of Demeter. Information restriction complements information hiding. Instead of hiding certain methods, we make them public but we restrict their use. 

### Localization of information

The importance of localizing information is stressed in many software engineering texts. The Law of Demeter focusses on localizing type information When we study a method we only have to be aware of types which are very closely related to the class to which the method is attached. We can effectively be ignorant (and independent) of the rest of the system and as the old proverb goes: “Ignorance is bliss”. This is an important aspect which helps to reduce the complexity of programming. Prom another point of view related to localization, the Law controls the visibility of message names. In a given method we can only use message names which are in the signatures of the instance variable types and argument types.

### Narrow interfaces

The maintenance of narrow interfaces between interacting entities is also important. A method ihould have access to only as much information as it needs to do its job. If a method gets too much information, it has to destructure this information (via many nested sends) which the Law of Demeter discourages. Therefore The Law promotes narrow interfaces between methods. 

### Structural induction

The Law of Demeter is related to the fundamental thesis of Denotational Semantics. That is, “The meaning of a phrase is a function of the meanings of its immediate constituents”. This goes back to Prege’s work on the principle of compositionality in his Begriffsschrift [S]. The main motivation behind the compositionality principle
is that it facilitates structural induction proofs.

## The Trade-off 

Writing programs which follow the the Law of Demeter decreases the occurrences of nested message sending and decreases the complexity of the methods, but it increases the number of methods. The latter is related to the problem outlined in [12] which is that there can be too many operations in a type. In this case the abstraction may be less comprehensible, and implementation and maintenance are more difficult. There might also be an increase in the number of arguments passed to some methods.

One way of correcting this problem is to organize all the methods associated with a particular functional (or algorithmic) task sSo the functional abstraction is no longer a method but a module which will hide the lower-level methods which caused the original confusion.

## Summary of How to Apply LoD

A method of an object may only call methods of:

>* The object itself.
>* An argument of the method.
>* Any object created within the method.
>* Any direct properties/fields of the object.

## Final Considerations about Law of Demeter

The Law of Demeter is a very well-defined set of rules for Object-Oriented development. Following these rules in letter a

Furthermore, it produces clear signals if the code is deviating from the Object-Oriented path, therefore it is an invaluable tool to keep our designs and code style on the right track.

### Resources about LoD

* [Link to Law of Demeter in Wikipedia](https://en.wikipedia.org/wiki/Law_of_Demeter)
* [Link to Articl About The Law of Demeter Is Not A Dot Counting Exercise](https://haacked.com/archive/2009/07/14/law-of-demeter-dot-counting.aspx/)
* [Law of Demeter](http://wiki.c2.com/?LawOfDemeter)

# TDA Tell Do not Ask

## What is TDA?

Tell-Don't-Ask is a principle that helps people remember that object-orientation is about bundling data with the functions that operate on that data. It reminds us that rather than asking an object for data and acting on that data, we should instead tell an object what to do. This encourages to move behavior into an object to go with the data.

Many people find tell-don't-ask to be a useful principle. One of the fundamental principles of object-oriented design is to combine data and behavior, so that the basic elements of our system (objects) combine both together. This is often a good thing because this data and the behavior that manipulates them are tightly coupled: changes in one cause changes in the other, understanding one helps you understand the other. Things that are tightly coupled should be in the same component. Thinking of tell-don't-ask is a way to help programmers to see how they can increase this co-location.

**Note:** *Accessors are methods that let you read and write the value of an instance variable of an object. They are also known as setters and getters. Public accessors indicate that the data and the behavior of a class are not kept together. This is seen as a an indication of higher coupling and lower coherence. Are public accessors are considered CodeSmell*  

## Should We Get Rid of all Accessors (the Getters and Setters) ?

As stated by Martin Fowler in his article about TDA in his blog site, he doesn´t use tell-dont-ask. He does looks to co-locate data and behavior, which often leads to similar results.  One thing he finds troubling about tell-dont-ask is that he've seen it encourage people to become GetterEradicators, seeking to get rid of all query methods.  But there are times when objects collaborate effectively by providing information. A good example are objects that take input information and transform it to simplify their clients, such as using EmbeddedDocument.  As stated by Martin Fowler, he've seen code get into convolutions of only telling where suitably responsible query methods would simplify matters . For him, tell-don't-ask is a stepping stone towards co-locating behavior and data, but he doesn't find it a point worth highlighting.

## Java Code Example that doesn´t follow the TDA Principle

The example below shows just the opposite of what is enforced by TDA principle:

```java
public class Monitor {

  private int value;
  private int limit;
  private boolean isTooHigh;
  private String name;
  private Alarm alarm;

  public AskMonitor (String name, int limit, Alarm alarm) {
    this.name = name;
    this.limit = limit;
    this.alarm = alarm;
  }
  public int getValue() {
      return value;
  }
  public void setValue(int arg) {
      value = arg; 
  }
  public int getLimit() {
      return limit;
  }
  public String getName()  {
      return name;
  }
  public Alarm getAlarm() {
      return alarm;
  }
}
```

As we can see above, this approach violates the object-oriented principles of information and implementation hiding, due to the fact that, instead of tell what to do, the classes will ask private data from Monitor Class, through the use of its accessors methods (getters), This wide spread style of coding gives external access to private data of the Monitor Class. To do that, the external classes must know the types of data that they are asking for. This approach creates tightly coupling between classes, making the maintenance hard, because any minor change in the types of datas contained inside of the classe Monitor will propagate and spread those changes to all objects that instantiate and use the Monitor Class.

In the code example above, we have, in the Monitor class, data plus getters methods and with no behavior working and transforming the data. So, the behavior that works over the data will be, instead, outside and spread over all objects that ask and use the private data of Monitor Class. This is bad approach generates side-effects when maintaingn the original class.

## How to Externalize Data Without Violating Encapsulation and Information Hiding

- This is very close to the question answered by the Memento Pattern.

- [Link to Memento Pattern](http://wiki.c2.com/?MementoPattern)
- [Memento Pattern - Wikipedia](https://en.wikipedia.org/wiki/Memento_pattern)

## References about the TDA and Problems Related 

- [Accessors Are Evil](http://wiki.c2.com/?AccessorsAreEvil)
- [Tell Don´t Ask - MArtin Fowler](https://martinfowler.com/bliki/TellDontAsk.html)
- [Getter Eradicator - Martin Fowler](https://martinfowler.com/bliki/GetterEradicator.html)
- [Why Getter and Setter Methods are Evil - Part 1](https://www.infoworld.com/article/2073723/why-getter-and-setter-methods-are-evil.html?pag=1)
- [Why Getter and Setter Methods are Evil - Part 2](https://www.infoworld.com/article/2073723/why-getter-and-setter-methods-are-evil.html?pag=2)
- [Avoid getters and setters whenever possible](https://dev.to/scottshipp/avoid-getters-and-setters-whenever-possible-c8m)

# Do The Simplest Thing That Could Possibly Work

### Why Do The Simplest Thing That Could Possibly Work

* Real progress against the real problem is maximized if we just work on what the problem really is.

### How Do The Simplest Thing That Could Possibly Work

* Ask yourself: "What is the simplest thing that could possibly work?"

### Resources

>* [Do The Simplest Thing That Could Possibly Work](http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html)

# Hide Implementation Details

A software module hides information (i.e. implementation details) by providing an interface, and not leak any unnecessary information.

### Why Hide Implementation Details

* When the implementation changes, the interface clients are using does not have to change.

### How to Hide Implementation Details

* nMinimize accessibility of classes and members.
* Don’t expose member data in public.
* Avoid putting private implementation details into a class’s interface.
* Decrease coupling to hide more implementation details.

### Resources about Hide Implementation Details

>* [Information hiding](https://en.wikipedia.org/wiki/Information_hiding)

# Encapsulate What Changes

A good design identifies the hotspots that are most likely to change and encapsulates them behind an API. When an anticipated change then occurs, the modifications are kept local.

### Why Encapsulate What Changes

* To minimize required modifications when a change occurs

### How to Encapsulate What Changes

* Encapsulate the concept that varies behind an API
* Possibly separate the varying concept into its own module

### Resources about Encapsulate What Changes

>* [Encapsulate the Concept that Varies](http://principles-wiki.net/principles:encapsulate_the_concept_that_varies)
>* [Encapsulate What Varies](https://blogs.msdn.microsoft.com/steverowe/2007/12/26/encapsulate-what-varies/)
>* [Information hiding](https://en.wikipedia.org/wiki/Information_hiding)

# Code For The Maintainer

### Why 

* Maintenance is by far the most expensive phase of any project.

### How

* Be the maintainer.
* Always code as if the person who ends up maintaining your code is a violent psychopath who knows where you live.
* Always code and comment in such a way that if someone a few notches junior picks up the code, they will take pleasure in reading and learning from it.
* [Don't make me think.](http://www.sensible.com/dmmt.html)
* Use the [Principle of Least Astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment)

### Resources

>* [Code For The Maintainer]()
>* [The Noble Art of Maintenance Programming/()

# Composition Over Inheritance Principle

### Why Composition Over Inheritance

* Less coupling between classes.
* Using inheritance, subclasses easily make assumptions, and break LSP.

### How Apply Composition instead of Inheritance

* Test for LSP (substitutability) to decide when to inherit.
* Compose when there is a "has a" (or "uses a") relationship, inherit when "is a".

### Resources about Composition Over Inheritance

>* [Favor Composition Over Inheritance](https://blogs.msdn.microsoft.com/thalesc/2012/09/05/favor-composition-over-inheritance/)

# Orthogonality Principle

The basic idea of orthogonality is that things that are not related conceptually should not be related in the system.

Source: [Be Orthogonal](https://www.artima.com/intv/dry3.html)

It is associated with simplicity; the more orthogonal the design, the fewer exceptions. This makes it easier to learn, read and write programs in a programming language. The meaning of an orthogonal feature is independent of context; the key parameters are symmetry and consistency.

Source: [Orthogonality](https://en.wikipedia.org/wiki/Orthogonality_(programming))

# Robustness Principle

Be conservative in what you do, be liberal in what you accept from others

Collaborating services depend on each others interfaces. Often the interfaces need to evolve causing the other end to receive unspecified data. A naive implementation refuses to collaborate if the received data does not strictly follow the specification. A more sophisticated implementation will still work ignoring the data it does not recognize.

### Why Apply Robustness Principle

* In order to be able to evolve services you need to ensure that a provider can make changes to support new demands while causing minimal breakage to their existing clients.

### How to Apply Robustness Principle

* Code that sends commands or data to other machines (or to other programs on the same machine) should conform completely to the specifications, but code that receives input should accept non-conformant input as long as the meaning is clear.

### Resources about Robustness Principle

>* [Robustness Principle in Wikipedia](https://en.wikipedia.org/wiki/Robustness_principle)
>* [Tolerant Reader](https://martinfowler.com/bliki/TolerantReader.html)

# IC Inversion of Control

Inversion of Control is also known as the Hollywood Principle, "Don't call us, we'll call you". It is a design principle in which custom-written portions of a computer program receive the flow of control from a generic framework. Inversion of control carries the strong connotation that the reusable code and the problem-specific code are developed independently even though they operate together in an application.

### Why Apply Inversion of Control (IC)

Inversion of control is used to increase modularity of the program and make it extensible.
To decouple the execution of a task from implementation.
To focus a module on the task it is designed for.
To free modules from assumptions about how other systems do what they do and instead rely on contracts.
To prevent side effects when replacing a module.

### How to Apply Inversion of Control (IC)

* Using Factory pattern
* Using Service Locator pattern
* Using Dependency Injection
* Using contextualized lookup
* Using Template Method pattern
* Using Strategy pattern

### Sources About Inversion of Control (IC)

>* [link to Inversion of Control in Wikipedia](https://en.wikipedia.org/wiki/Inversion_of_control)
>* [link to Article of Martin Fowler about Inversion of Control Containers and the Dependency Injection pattern](https://www.martinfowler.com/articles/injection.html)

# Command Query Separation Principle

The Command Query Separation principle states that each method should be either a command that performs an action or a query that returns data to the caller but not both. Asking a question should not modify the answer.

With this principle applied the programmer can code with much more confidence. The query methods can be used anywhere and in any order since they do not mutate the state. With commands one has to be more careful.

### Why Command Query Separation Principle

* By clearly separating methods into queries and commands the programmer can code with additional confidence without knowing each method's implementation details.

### How to apply Command Query Separation Principle

* Implement each method as either a query or a command
* Apply naming convention to method names that implies whether the method is a query or a command

### Resources about Command Query Separation Principle

>* [Command Query Separation in Wikipedia](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation) 
>* [Command Query Separation by Martin Fowler/(https://martinfowler.com/bliki/CommandQuerySeparation.html)

# Classification of Programming Languages

![classification](https://github.com/aridiosilva/TDD_ITA/blob/main/DynamicxStatic%20x%20Strng%20x%20Waek%20-%20classification%20of%20programming%20languages.png)

## Type Checking 

The process of verifying and enforcing the constraints of types . Type Checking may occur either at compile-time (a static check) or at run-time (dynamic check).

Type checking is all about ensuring that the program is **type-safe**, minimizing the possibility of **type errors**. For example — type error could be a situation where an operation is performed on a data of type integer with the intent that it is a float, or even something such as adding a string and an integer together.

Despite of the fact that in many languages both strings and integers can make use of the + operator, this would often result in a type error because this expression is usually not meant to handle multiple data types.

When a program is considered not to be type-safe, there is no single standard course of action that happens upon encountering a type error. Many Programming languages throw type errors which halts the run-time or compilation of the program, depending on the language type — static or dynamically typed.

## Statically typed languages

A language is statically-typed if the type of a variable is known at compile-time instead of at run-time. Common examples of statically-typed languages include Java, C, C++, FORTRAN, Pascal and Scala.  In Statically typed languages, once a variable has been declared with a type, it cannot ever be assigned to some other variable of different type and doing so will raise a type error at compile-time(some IDE’s generally shows a Red Cross mark denoting the error).

### Advantages od Statically Type Languages

- A large class of errors are caught in the early stage of development process.
- Static typing usually results in compiled code that executes more quickly because when the compiler knows the exact data types that are in use, it can produce optimized machine code (i.e. faster and/or using less memory).
- Better code completion.- 
- Better performance (type constraints offer more opportunities for compiler optimizations).
- You can get hints and documentation inside your IDE while you code. This reduces the likelihood of making incorrect assumptions about the behavior of specific functions/methods.
- It’s easier to find things. For any variable or function, you can easily jump to its class definition without leaving the IDE and without having to know anything about the directory structure of the project. Conversely, for any class or function definition, you can easily and unambiguously
- see where that class or function is used in your code and jump to it without leaving the IDE. (Statically typed languages make it easier for IDEs to do this).
- Static typing makes it easier to work with relational databases and other systems which also rely on static types — It helps you catch type mismatches sooner at compile-time.
- It can help reduce the likelihood of some kinds of errors. For example, in dynamically typed languages, if you’re not careful with sanitising user input, you can end up doing weird stuff like (for example) trying to add a number 10 with the string “8” and you would get the string “108” as a result instead of the number 18 that you were expecting.

## Dynamically typed languages

A language is dynamically-typed if the type of a variable is checked during run-time. Common examples of dynamically-typed languages includes JavaScript, Objective-C, PHP, Python, Ruby, Lisp, and Tcl.

In Dynamically typed languages, variables are bound to objects at run-time by means of assignment statements, and it is possible to bind the same variables to objects of different types during the execution of the program.

Dynamic type checking typically results in less optimized code than static type checking. It also includes the possibility of run time type errors and forces run time checks to occur for every execution of the program (instead of just at compile-time).

### Advantages of Dynamic Type Languages

- Implementations of dynamically type-checked languages generally associate each run time object with a type tag (i.e., a reference to a type) containing its type information. This run-time type information (RTTI) can also be used to implement dynamic dispatch, late binding, down-casting, reflection, and similar features.
- The absence of a separate compilation step means that you don’t have to wait for the compiler to finish before you can test your code changes. This makes the debug cycle much shorter and less cumbersome.
- More succinct/less verbose.
- The absence of a separate compilation step (which is much more common) means that you don’t have to wait for the compiler to finish before you can test changes that you’ve made to your code. This makes the debug cycle much shorter and less cumbersome. The delay introduced by the compile step can be distracting and break your train of thought. Even a 10-second compile step tends to add up over time. Pretty much every statically-typed language will claim to have “instant”, “partial” or “incremental” compilation, but in practice on any decent-sized project, it’s rare to see compilation take less than 10 seconds on an average machine.
- You spend less time debugging syntax and semantic errors — Instead, almost all of your debugging time is spent purely on logic errors (which are more interesting). A semantic error could be as simple as having a variable myVariable of type ClassA and trying to assign to it an instance of ClassB (type mismatch; even if they have the exact same interface)— These kinds of errors are often easy to resolve but cumulatively, they still take up a fair amount of developer time. Semantic errors are the obvious, silly kinds of errors that make you blame yourself for not adhering to the compiler’s stringent needs. For example in a dynamically-typed language something like if (1) { ... } is usually OK, but the compiler of some statically typed languages will throw an error because 1 is not a Boolean.
- More tolerant to change; code refactors tend to be more localized (they have a smaller area of effect). For example, with statically-typed languages, if you rename a class, you have to rename references in more different places in your code (though many IDEs can automate this to some extent)… A better example is if you have two or more different classes and you decide that they should share a single interface and refer to them by that interface, it takes more time to update them. Also with statically typed languages, because each object has more rigid relationships with other objects, the system can become a complex, inflexible puzzle; if a new piece doesn’t fit exactly into the existing structure, you may have to redesign the entire puzzle sooner rather than later.

## Strongly typed languages

A strongly-typed language is one in which variables are bound to specific data types, and will result in type errors if types do not match up as expected in the expression — regardless of when type checking occurs. Python is strong-typed, and so is Java.

## Weakly typed languages

A weakly-typed language on the other hand is a language in which variables are not bound to a specific data type; they still have a type, but type safety constraints are lower compared to strongly-typed languages.  PHP is weakly-typed, and so is C.

# Gang of Four 23 Design Patterns to help Fix Design Object-Oriented Problems

## GoF What is a Design Pattern?

"Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice"  - Christopher Alexander

## GoF Elements of a Pattern

In general, a pattern has four essential elements:

1. The **pattern name** is a handle we can use to describe a design problem, its solutions, and  consequences in a word or two. Naming a pattern immediately increases our design vocabulary. It lets us design at a higher level of abstraction. Having a vocabulary for patterns lets us talk about them with our colleagues, in our documentation, and even to ourselves. It makes it easier to think about designs and to communicate them and their trade-offs to others. Finding good names has been one of the hardest parts of developing our catalog.
 
1. The **problem** describes when to apply the pattern. It explains the problem and its context. It might describe specific design problems such as how to represent algorithms as objects. It might describe class or object structures that are symptomatic of an inflexible design. Sometimes the problem will include a list of conditions that must be met before it makes sense to apply the pattern.

1. The **solution** describes the elements that make up the design, their relationships, responsibilities, and collaborations. The solution doesn't describe a particular concrete design or implementation, because a pattern is like a template that can be applied in many different situations. Instead, the pattern provides an abstract description of a design problem and how a general arrangement of elements (classes and objects in our case) solves it.

1. The **consequences** are the results and trade-offs of applying the pattern. Though consequences are often unvoiced when we describe design decisions, they are critical for evaluating design alternatives and for understanding the costs and benefits of applying the pattern. The consequences for software often concern space and time trade-offs. They may address language and implementation issues as well. Since reuse is often a factor in object-oriented design, the consequences of a pattern include its impact on a system's flexibility, extensibility, or portability. Listing these consequences explicitly helps you understand and evaluate them.

## GoF Describing Design Patterns

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

## GoF Diagram of the Design Patterns Relationships

![design patterns relationships](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Fig1-1-Gof-DesignPatternsRelationships-23Patterns.jpg)

## GoF The Catalog of Gang of Four 23 Design Patterns

The catalog beginning on page 79 contains 23 design patterns. Their names and intents are listed next to give you an overview. The number in parentheses after each pattern name gives the page number for the pattern (a convention we follow throughout the book).

- **Abstract Factory (87)** - Provide an interface for creating families of related or dependent objects without specifying their concrete classes. Yield objects whose only responsibilities are creating other objects.

- **Adapter (139)** - Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

- **Bridge (151)** - Decouple an abstraction from its implementation so that the two can vary independently. Yield objects whose only responsibilities are creating other objects. This pattern use delegation less heavily. Bridges decouples an abstraction from its implementation. If the abstraction and a particular implementation are closely matched, then the abstraction may simply delegate operations to that implementation.

- **Builder (97)** - Separate the construction of a complex object from its representation so that the same construction process can create different representations.

- **Chain of Responsibility (223)** - Avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chain the receiving objects and pass the request along the chain until an object handles it. This pattern use delegation less heavily. This pattern handles requests by forwarding them from one object to another along a chain of objects. Sometimes this request carries with it a reference to the original object receiving the request, in which case the pattern is using delegation. Chain of Responsibility (223) also results in communication patterns that inheritance doesn't reveal.

- **Command (233)** - Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations.  Yield objects whose only responsibilities are to implement a request on another object or group of objects.

- **Composite (163)**- Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly. introduces an abstraction for treating objects uniformly that doesn't have a physical counterpart. Composite (163) is especially useful for
building complex run-time structures

- **Decorator (175)** - Attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. Decorator (175) is especially useful for building complex run-time structures.

- **Facade (185)** - Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use. It describes how to represent complete subsystems as objects.

- **Factory Method (107)** - Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

- **Flyweight (195)** - Use sharing to support large numbers of fine-grained objects efficiently. It describes how to support huge numbers of objects at the finest granularities.

- **Interpreter (243)** - Given a language, define a represention for its grammar along with an interpreter that uses the representation to interpret sentences in the language.

- **Iterator (257)** - Provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation.

- **Mediator (273)** - Define an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently. This pattern use delegation less heavily. It introduces an object to mediate communication between other objects. Sometimes the Mediator object implements operations simply by forwarding them to the other objects; other times it passes along a reference to itself and thus uses true delegation.

- **Memento (283)** - Without violating encapsulation, capture and externalize an object's internal state so that the object can be restored to this state later. It describes how to encapsulate and save the internal state of an object so that the object can be restored to that state later. The pattern stipulates that Memento objects must define two
interfaces: a restricted one that lets clients hold and copy mementos, and a privileged one that only the original object can use to store and retrieve state in the memento.

- **Observer (293)** - Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically. Observer (293) involves run-time structures that are often hard to understand unless you know the pattern.

- **Prototype (117)** - Specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.

- **Proxy (207)** - Provide a surrogate or placeholder for another object to control access to it.

- **Singleton (127)** - Ensure a class only has one instance, and provide a global point of access to it.

- **State (305)** - Allow an object to alter its behavior when its internal state changes. The object will appear to change its class. In the State pattern, an object delegates requests to a State object that represents its current state. In the State pattern, an object delegates requests to a State object that represents its current state. States uses delegation in its implementation.

- **Strategy (315)** - Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it. Describes how to implement interchangeable families of algorithms. In the Strategy pattern, an object delegates a specific request to an object that represents a strategy for carrying out the request. An object will only have one state, but it can have many strategies for different requests. The purpose of both patterns is to change the behavior of an object by changing the objects to which it delegates requests. Strategy uses delegation in its implementation.

- **Template Method (325)** - Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.

- **Visitor (331)** - Represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.  Yield objects whose only responsibilities are to implement a request on another object or group of objects. In Visitor, the operation that gets performed on each element of an object structure is always delegated to the Visitor object. Visitor uses delegation in its implementation.

## GoF Design Patterns Space

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

# GoF How Design Patterns Solve Design Problems

Design patterns solve many of the day-to-day problems object-oriented designers face, and in many different ways. Here are several of these problems and how design patterns solve them. 

# GoF P1 Finding Appropriate Objects

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

# GoF P2 Determining Object Granularity

-  Note: Granularity = the scale or level of detail present in a set of data or other phenomenon.

Objects can vary tremendously in size and number. They can represent everything down to the hardware or all the way up to entire applications. How do we decide what should be an object?

Design patterns address this issue as well. 

- The **Facade (185) pattern** describes how to represent complete subsystems as objects, and 
- the **Flyweight (195) pattern** describes how to support huge numbers of objects at the finest granularities.

Other design patterns describe specific ways of decomposing an object into smaller objects. 

- **Abstract Factory (87)** and **Builder (97)** yield objects whose only responsibilities are creating other objects.
- **Visitor (331)** and **Command (233)** yield objects whose only responsibilities are to implement a request on another object or group of objects.

# GoF P3 Specifying Object Interfaces

Every operation declared by an object specifies the operation's name, the objects it takes as parameters, and the operation's return value. This is known as the **operation's signature**. The set of all signatures defined by an object's operations is called the **interface to the object**. An object's interface characterizes the complete set of requests that can be sent to the object. Any request that matches a **signature** in the object's interface may be sent to the object.

A *type* is a name used to denote a particular interface. We speak of an object as having the type "Window" if it accepts all requests for the operations defined in the interface named "Window." An object may have many types, and widely different objects can share a type. Part of an object's interface may be characterized by one type, and other parts by other types. Two objects of the same type need only share parts of their interfaces. Interfaces can contain other interfaces as subsets. We say that a **type** is a *subtype* of another if its interface contains the interface of its supertype. Often we speak of a subtype inheriting the interface of its *supertype**.

**Interfaces** are fundamental in object-oriented systems. Objects are known only through their interfaces. There is no way to know anything about an object or to ask it to do anything without going through its interface. An object's interface says nothing about its implementation—different objects are free to implement requests differently. That means two objects having completely different implementations can have identical interfaces.

When a request is sent to an object, the particular operation that's performed depends on both the request and the receiving object. Different objects that support identical requests may have different implementations of the operations that fulfill these requests. The run-time association of a request to an object and one of its operations is known as **dynamic binding**.

Dynamic binding means that issuing a request doesn't commit you to a particular implementation until runtime. Consequently, you can write programs that expect an object with a particular interface, knowing that any object that has the correct interface will accept the request. Moreover, dynamic binding lets you substitute objects that have identical interfaces for each other at run-time. This substitutability is known as **polymorphism**, and it's a key concept in object-oriented systems. It lets a client object make fewassumptions about other objects beyond supporting a particular interface. Polymorphism simplifies the definitions of clients, decouples objects from each other, and lets them vary their relationships to each other at run-time.

- The **Memento (283) pattern** is a good example. It describes how to encapsulate and save the internal state of an object so that the object can be restored to that state later. The pattern stipulates that Memento objects must define two interfaces: a restricted one that lets clients hold and copy mementos, and a privileged one that only the original object can use to store and retrieve state in the memento.

Design patterns also specify **relationships between interfaces**. In particular, they often require some classes to have similar interfaces, or they place constraints on the interfaces of some classes. For example, both **Decorator (175)** and **Proxy (207)** require the interfaces of Decorator and Proxy objects to be identical to the decorated and proxied objects. In **Visitor (331)**, the Visitor interface must reflect all classes of objects that visitors can visit.

Design patterns help you define interfaces by identifying their key elements and the kinds of data that get sent across an interface. A design pattern might also tell you what not to put in the interface. 

# GoF P4 Specifying Object Implementations

So far we've said little about how we actually define an object. An object's implementation is defined by its **class**. The class specifies the object's internal data and representation and defines the operations the object can perform.

Objects are created by instantiating a class. The object is said to be an instance of the class. The process of instantiating a class allocates storage for the object's internal data (made up of **instance variables**) and associates the operations with these data. Many similar instances of an object can be created by instantiating a class.

New classes can be defined in terms of existing classes using **class inheritance**. When a **subclass** inherits from a **parent class**, it includes the definitions of all the data and operations that the parent class defines. Objects that are instances of the subclass will contain all data defined by the subclass and its parent classes, and they'll be able to perform all operations defined by this subclass and its parents.

An **abstract class** is one whose main purpose is to define a common interface for its subclasses. An abstract class will defer some or all of its implementation to operations defined in subclasses; hence an abstract class cannot be instantiated. The operations that an abstract class declares but doesn't implement are called **abstract operations**. Classes that aren't abstract are called **concrete classes**.

Subclasses can refine and redefine behaviors of their parent classes. More specifically, a class may **override** an operation defined by its parent class. Overriding gives subclasses a chance to handle requests instead of their parent classes. Class inheritance lets you define classes simply by extending other classes, making it easy to define families of objects having related functionality.

A **mixin class** is a class that's intended to provide an optional interface or functionality to other classes. It's similar to an abstract class in that it's not intended to be instantiated. Mixin classes require **multiple inheritance**.

# GoF P5 Class versus Interface Inheritance

It's important to understand the difference between an object's **class** and its **type**.

An object's class defines how the object is implemented. The class defines the object's internal state and the implementation of its operations. In contrast, an object's type only refers to its interface—the set of requests to which it can respond. An object can have many types, and objects of different classes can have the same type.

Of course, there's a close relationship between class and type. Because a class defines the operations an object can perform, it also defines the object's type. When we say that an object is an instance of a class, we imply that the object supports the interface defined by the class.

Languages like C++ and Eiffel use classes to specify both an object's type and its implementation. Smalltalk programs do not declare the types of variables; consequently, the compiler does not check that the types of objects assigned to a variable are subtypes of the variable's type. Sending a message requires checking that the class of the receiver implements the message, but it doesn't require checking that the receiver is an instance of a particular class.

It's also important to understand the difference between class inheritance and interface inheritance (or subtyping). Class inheritance defines an object's implementation in terms of another object's implementation. In short, it's a mechanism for code and representation sharing. In contrast, interface inheritance (or subtyping) describes when an object can be used in place of another. 

It's easy to confuse these two concepts, because many languages don't make the distinction explicit. In languages like C++ and Eiffel, inheritance means both interface and implementation inheritance. The standard way to inherit an interface in C++ is to inherit publicly from a class that has (pure) virtual member functions. Pure interface inheritance can be approximated in C++ by inheriting publicly from pure abstract classes. Pure implementation or class inheritance can be approximated with private inheritance. In Smalltalk, inheritance means just implementation inheritance. You can assign instances of any class to a variable as long as those instances support the operation performed on the value of the variable. 

Although most programming languages don't support the distinction between interface and implementation inheritance, people make the distinction in practice. Smalltalk programmers usually act as if subclasses were subtypes (though there are some well-known exceptions [Coo92]); C++ programmers manipulate objects through types defined by abstract classes.

  - [Cpp02] William R. Cook. Interfaces and specifications for the Smalltalk-80 collection classes. In Object-Oriented Programming Systems, Languages, and Applications Conference Proceedings, pages 1–15, Vancouver, British Columbia, Canada, October 1992. ACM Press.

Many of the design patterns depend on this distinction. For example, objects in a Chain of Responsibility (223) must have a common type, but usually they don't share a common implementation. In the Composite (163) pattern, Component defines a common interface, but Composite often defines a common implementation. **Command (233)**, **Observer (293)**, **State (305)**, and **Strategy (315)** are often implemented with abstract classes that are pure interfaces.

# GoF P6 Programming to an Interface not an Implementation

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

# GoF P7 Putting Reuse Mechanisms to Work

Most people can understand concepts like objects, interfaces, classes, and inheritance. The challenge lies in applying them to build flexible, reusable software, and design patterns can show you how.

## GoF Inheritance versus Composition

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

![composition_idea](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/composition_image.PNG)

![composition_has_a_relationship](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/composition%20_has-a%20relationship%20image.png)

# GoF Delegation

Delegation is a way of making composition as powerful for reuse as inheritance [Lie86, JZ91]. In
delegation, two objects are involved in handling a request: a receiving object delegates operations to its delegate. This is analogous to subclasses deferring requests to parent classes. But with inheritance, an inherited operation can always refer to the receiving object through the this member variable in C++ and self in Smalltalk. To achieve the same effect with delegation, the receiver passes itself to the delegate to let the delegated operation refer to the receiver.

For example, instead of making class Window a subclass of Rectangle (because windows happen to be
rectangular), the Window class might reuse the behavior of Rectangle by keeping a Rectangle instance variable and delegating Rectangle-specific behavior to it. In other words, instead of a Window being a Rectangle, it would have a Rectangle. Window must now forward requests to its Rectangle instance explicitly, whereas before it would have inherited those operations.

The following diagram depicts the Window class delegating its Area operation to a Rectangle instance.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Windows_Class_Delegation_001.jpg)

A plain arrowhead line indicates that a class keeps a reference to an instance of another class. The reference has an optional name, "rectangle" in this case.

The main advantage of delegation is that it makes it easy to compose behaviors at run-time and to change the way they're composed. Our window can become circular at run-time simply by replacing its Rectangle instance with a Circle instance, assuming Rectangle and Circle have the same type.

Delegation has a disadvantage it shares with other techniques that make software more flexible through object composition: Dynamic, highly parameterized software is harder to understand than more static software. There are also run-time inefficiencies, but the human inefficiencies are more important in the long run. Delegation is a good design choice only when it simplifies more than it complicates. It isn't easy to give rules that tell you exactly when to use delegation, because how effective it will be depends on the context and on how much experience you have with it. Delegation works best when it's used in highly stylized ways—that is, in standard patterns.

Several design patterns use delegation. The State (305), Strategy (315), and Visitor (331) patterns depend on it. In the State pattern, an object delegates requests to a State object that represents its current state. In the Strategy pattern, an object delegates a specific request to an object that represents a strategy for carrying out the request. An object will only have one state, but it can have many strategies for different requests. The purpose of both patterns is to change the behavior of an object by changing the objects to which it delegates requests. In Visitor, the operation that gets performed on each element of an object structure is always
delegated to the Visitor object.

Other patterns use delegation less heavily:

- **Mediator (273)** introduces an object to mediate communication between other objects. Sometimes the Mediator object implements operations simply by forwarding them to the other objects; other times it passes along a reference to itself and thus uses true delegation.
 - **Chain of Responsibility (223)** handles requests by forwarding them from one object to another along a chain of objects. Sometimes this request carries with it a reference to the original object receiving the request, in which case the pattern is using delegation. 
 - **Bridge (151)** decouples an abstraction from its implementation. If the abstraction and a particular implementation are closely matched, then the abstraction may simply delegate operations to that implementation.
 
 Delegation is an extreme example of object composition. It shows that you can always replace inheritance with object composition as a mechanism for code reuse.
 
# GoF P8 Inheritance versus Parameterized (or Generic) Types

Another (not strictly object-oriented) technique for reusing functionality is through parameterized types, also known as generics (Ada, Eiffel) and templates (C++). This technique lets you define a type without specifying all the other types it uses. The unspecified types are supplied as parameters at the point of use. For example, a List class can be parameterized by the type of elements it contains. To declare a list of integers, you supply the type "integer" as a parameter to the List parameterized type. To declare a list of String objects, you supply the "String" type as a parameter. The language implementation will create a customized version of the List class template for each type of element.

Parameterized types give us a third way (in addition to class inheritance and object composition) to compose behavior in object-oriented systems. Many designs can be implemented using any of these three techniques. To parameterize a sorting routine by the operation it uses to compare elements, we could make the comparison:

1. an operation implemented by subclasses (an application of **Template Method (325)**,

1. the responsibility of an object that's passed to the sorting routine (**Strategy (315)**, or

1. an argument of a C++ template, or Generic Class in Java, or Ada generic that specifies the name of the function to call to
compare the elements.

There are important differences between these techniques:

>1. **Object composition** lets you change the behavior being composed at run-time, but it also requires indirection and can be less efficient. 
>1. **Inheritance** lets you provide default implementations for operations and lets subclasses override them. 
>1. **Parameterized types** let you change the types that a class can use. But neither inheritance nor parameterized types can change at runtime. 

Which approach is best depends on your design and implementation constraints.

None of the patterns in this book concerns parameterized types, though we use them on occasion to customize a pattern's C++ implementation. Parameterized types aren't needed at all in a language like Smalltalk that doesn't have compile-time type checking.

Example: Use of Generic or Parameterized Classes in Java 8:

```java
public class Pair<K, V> {	
	private K key;
	private V value;
	
	public Pair(K key, V value) {
		this.key = key;
		this.value = value;
	}
	public void setKey(K key) { 
		this.key = key; 
	}
	public void setValue(V value) { 
		this.value = value; 
	}
	public K getKey() {
		return key; 
	}
	public V getValue() { 
		return value; 
	}
}
```

```java
public class Util {
	
	public static <K, V> boolean compare(Pair<K, V> p1, Pair<K, V> p2) {	 	
		    return p1.getKey().equals(p2.getKey()) &&
   			       p1.getValue().equals(p2.getValue());	
	}
}
```

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class UtilTest {
	@Test
	void test() {

		Pair<Integer, String> p1 = new Pair<>(1, "apple");
		Pair<Integer, String> p2 = new Pair<>(2, "pear");
		assertEquals (false, Util.<Integer, String>compare(p1, p2));
		
		Pair<Integer, String> p3 = new Pair<>(1, "orange");
		Pair<Integer, String> p4 = new Pair<>(2, "melon");
		assertEquals (false, Util.compare(p3, p4));	
	}
}
```

# GoF P9 Relating Run-Time and Compile-Time Structures

An object-oriented program's run-time structure often bears little resemblance to its code structure. The code structure is frozen at compile-time; it consists of classes in fixed inheritance relationships. A program's runtime structure consists of rapidly changing networks of communicating objects. In fact, the two structures are largely independent. Trying to understand one from the other is like trying to understand the dynamism of living ecosystems from the static taxonomy of plants and animals, and vice versa.

Consider the distinction between object **aggregation** and **acquaintance** and how differently they manifest themselves at compile- and run-times. Aggregation implies that one object owns or is responsible for another object. Generally we speak of an object having or being part of another object. Aggregation implies that an aggregate object and its owner have identical lifetimes.

**Acquaintance** implies that an object merely knows of another object. Sometimes acquaintance is called "association" or the "using" relationship. Acquainted objects may request operations of each other, but they aren't responsible for each other. Acquaintance is a weaker relationship than aggregation and suggests much looser coupling between objects.

In our diagrams, a plain arrowhead line denotes acquaintance. An arrowhead line with a diamond at its base denotes aggregation:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/Aggreggator_Aggregatee_001.jpg)

It's easy to confuse aggregation and acquaintance, because they are often implemented in the same way. In Smalltalk, all variables are references to other objects. There's no distinction in the programming language between aggregation and acquaintance. In C++, aggregation can be implemented by defining member variables that are real instances, but it's more common to define them as pointers or references to instances. Acquaintance is implemented with pointers and references as well.

Ultimately, acquaintance and aggregation are determined more by intent than by explicit language
mechanisms. The distinction may be hard to see in the compile-time structure, but it's significant. Aggregation relationships tend to be fewer and more permanent than acquaintance. Acquaintances, in contrast, are made and remade more frequently, sometimes existing only for the duration of an operation. Acquaintances are more dynamic as well, making them more difficult to discern in the source code.

With such disparity between a program's run-time and compile-time structures, it's clear that code won't reveal everything about how a system will work. The system's run-time structure must be imposed more by the designer than the language. The relationships between objects and their types must be designed with great care, because they determine how good or bad the run-time structure is.

Many design patterns (in particular those that have object scope) capture the distinction between compiletime and run-time structures explicitly. Composite (163) and Decorator (175) are especially useful for building complex run-time structures. Observer (293) involves run-time structures that are often hard to understand unless you know the pattern. Chain of Responsibility (223) also results in communication patterns that inheritance doesn't reveal. In general, the run-time structures aren't clear from the code until you understand the patterns.

# GoF P10 Designing for Change

The key to maximizing reuse lies in anticipating new requirements and changes to existing requirements, and in designing your systems so that they can evolve accordingly.

To design the system so that it's robust to such changes, you must consider how the system might need to change over its lifetime. A design that doesn't take change into account risks major redesign in the future. Those changes might involve class redefinition and reimplementation, client modification, and retesting. Redesign affects many parts of the software system, and unanticipated changes are invariably expensive.

Design patterns help you avoid this by ensuring that a system can change in specific ways. Each design pattern lets some aspect of system structure vary independently of other aspects, thereby making a system more robust to a particular kind of change.

Here are some common causes of redesign along with the design pattern(s) that address them:

1. **Creating an object by specifying a class explicitly**. 

>*Specifying a class name when you create an object commits you to a particular implementation instead of a particular interface. This commitment can complicate future changes. To avoid it, create objects indirectly.*
>
>* Design patterns: **Abstract Factory (87), Factory Method (107), Prototype (117).**

2. **Dependence on specific operations**. 

>*When you specify a particular operation, you commit to one way of satisfying a request. By avoiding hard-coded requests, you make it easier to change the way a request gets satisfied both at compile-time and at run-time.*
>
>* Design patterns: **Chain of Responsibility (223), Command (233).**

3. **Dependence on hardware and software platform**. 

>*External operating system interfaces and application programming interfaces (APIs) are different on different hardware and software platforms. Software that depends on a particular platform will be harder to port to other platforms. It may even be difficult to keep it up to date on its native platform. It's important therefore to design your system to limit its platform dependencies.*
>
>* Design patterns: **Abstract Factory (87), Bridge (151).**

4. **Dependence on object representations or implementations**. 

>*Clients that know how an object is  represented, stored, located, or implemented might need to be changed when the object changes. Hiding this information from clients keeps changes from cascading.*

>* Design patterns: **Abstract Factory (87), Bridge (151), Memento (283), Proxy (207).**

5. **Algorithmic dependencies**. 

>*Algorithms are often extended, optimized, and replaced during development and reuse. Objects that depend on an algorithm will have to change when the algorithm changes. Therefore algorithms that are likely to change should be isolated.*
>
>* Design patterns: **Builder (97), Iterator (257), Strategy (315), Template Method (325), Visitor (331).**

6. **Tight coupling**. 

>*Classes that are tightly coupled are hard to reuse in isolation, since they depend on each other. Tight coupling leads to monolithic systems, where you can't change or remove a class without understanding and changing many other classes. The system becomes a dense mass that's hard to learn, port, and maintain. Loose coupling increases the probability that a class can be reused by itself and that a system can be learned, ported, modified, and extended more easily. Design patterns use techniques such as abstract coupling and layering to promote loosely coupled systems.*
>
>* Design patterns: **Abstract Factory (87), Bridge (151), Chain of Responsibility (223), Command (233), Facade (185), Mediator (273), Observer (293).**

7. **Extending functionality by subclassing**. 

>*Customizing an object by subclassing often isn't easy. Every new class has a fixed implementation overhead (initialization, finalization, etc.). Defining a subclass also requires an in-depth understanding of the parent class. For example, overriding one operation might require overriding another. An overridden operation might be required to call an inherited operation. And subclassing can lead to an explosion of classes, because you might have to introduce many new subclasses for even a simple extension.*  
>
>*Object composition in general and delegation in particular provide flexible alternatives to inheritance for combining behavior. New functionality can be added to an application by composing existing objects in new ways rather than by defining new subclasses of existing classes. On the other hand, heavy use of object composition can make designs harder to understand. Many design patterns produce designs in which you can introduce customized functionality just by defining one subclass and composing its instances with existing ones.*
>
>*  Design patterns: **Bridge (151), Chain of Responsibility (223), Composite (163), Decorator (175), Observer (293), Strategy (315).**

8. **Inability to alter classes conveniently**. 

>*Sometimes you have to modify a class that can't be modified conveniently. Perhaps you need the source code and don't have it (as may be the case with a commercial class  library). Or maybe any change would require modifying lots of existing subclasses. Design patterns offer ways to modify classes in such circumstances.*
>
>* Design patterns: **Adapter (139), Decorator (175), Visitor (331)**.

These examples reflect the flexibility that design patterns can help you build into your software. How crucial such flexibility is depends on the kind of software you're building. Let's look at the role design patterns play in the development of three broad classes of software: application programs, toolkits, and frameworks.

# GoF P11 Application Programs

If you're building an application program such as a document editor or spreadsheet, then internal reuse, maintainability, and extension are high priorities. Internal reuse ensures that you don't design and implement any more than you have to. Design patterns that reduce dependencies can increase internal reuse. Looser coupling boosts the likelihood that one class of object can cooperate with several others. For example, when you eliminate dependencies on specific operations by isolating and encapsulating each operation, you make it easier to reuse an operation in different contexts. The same thing can happen when you remove algorithmic and representational dependencies too.

Design patterns also make an application more maintainable when they're used to limit platform dependencies and to layer a system. They enhance extensibility by showing you how to extend class hierarchies and how to exploit object composition. Reduced coupling also enhances extensibility. Extending a class in isolation is easier if the class doesn't depend on lots of other classes.

# GoF P12 Toolkits

Often an application will incorporate classes from one or more libraries of predefined classes called toolkits. A toolkit is a set of related and reusable classes designed to provide useful, general-purpose functionality. An example of a toolkit is a set of collection classes for lists, associative tables, stacks, and the like. The C++ I/O stream library is another example. Toolkits don't impose a particular design on your application; they just provide functionality that can help your application do its job. They let you as an implementer avoid recoding common functionality. Toolkits emphasize code reuse. They are the object-oriented equivalent of subroutine libraries.

Toolkit design is arguably harder than application design, because toolkits have to work in many applications to be useful. Moreover, the toolkit writer isn't in a position to know what those applications will be or their special needs. That makes it all the more important to avoid assumptions and dependencies that can limit the toolkit's flexibility and consequently its applicability and effectiveness.

# GoF P13 Frameworks

A framework is a set of cooperating classes that make up a reusable design for a specific class of software [Deu89, JF88]. For example, a framework can be geared toward building graphical editors for different domains like artistic drawing, music composition, and mechanical CAD [VL90, Joh92]. Another framework can help you build compilers for different programming languages and target machines [JML92]. Yet another might help you build financial modeling applications [BE93]. You customize a framework to a
particular application by creating application-specific subclasses of abstract classes from the framework.

The framework dictates the architecture of your application. It will define the overall structure, its partitioning into classes and objects, the key responsibilities thereof, how the classes and objects collaborate, and the thread of control. A framework predefines these design parameters so that you, the application designer/implementer, can concentrate on the specifics of your application. The framework captures the design decisions that are common to its application domain. Frameworks thus emphasize design reuse over code reuse, though a framework will usually include concrete subclasses you can put to work immediately.

Reuse on this level leads to an inversion of control between the application and the software on which it's based. When you use a toolkit (or a conventional subroutine library for that matter), you write the main body of the application and call the code you want to reuse. When you use a framework, you reuse the main body and write the code it calls. You'll have to write operations with particular names and calling conventions, but that reduces the design decisions you have to make.

Not only can you build applications faster as a result, but the applications have similar structures. They are easier to maintain, and they seem more consistent to their users. On the other hand, you lose some creative freedom, since many design decisions have been made for you.

If applications are hard to design, and toolkits are harder, then frameworks are hardest of all. A framework designer gambles that one architecture will work for all applications in the domain. Any substantive change to the framework's design would reduce its benefits considerably, since the framework's main contribution to an application is the architecture it defines. Therefore it's imperative to design the framework to be as flexible and extensible as possible.

Furthermore, because applications are so dependent on the framework for their design, they are particularly sensitive to changes in framework interfaces. As a framework evolves, applications have to evolve with it. That makes loose coupling all the more important; otherwise even a minor change to the framework will have major repercussions.

The design issues just discussed are most critical to framework design. A framework that addresses them using design patterns is far more likely to achieve high levels of design and code reuse than one that doesn't. Mature frameworks usually incorporate several design patterns. The patterns help make the framework's architecture suitable to many different applications without redesign.

An added benefit comes when the framework is documented with the design patterns it uses [BJ94]. People who know the patterns gain insight into the framework faster. Even people who don't know the patterns can benefit from the structure they lend to the framework's documentation. Enhancing documentation is important for all types of software, but it's particularly important for frameworks. Frameworks often pose a steep learning curve that must be overcome before they're useful. While design patterns might not flatten the learning curve entirely, they can make it less steep by making key elements of the framework's design more explicit.

Because patterns and frameworks have some similarities, people often wonder how or even if they differ. They are different in three major ways:

1. Design patterns are more abstract than frameworks. Frameworks can be embodied in code, but only examples of patterns can be embodied in code. A strength of frameworks is that they can be written down in programming languages and not only studied but executed and reused directly. In contrast, the design patterns in this book have to be implemented each time they're used. Design patterns also explain the intent, trade-offs, and consequences of a design.

2. Design patterns are smaller architectural elements than frameworks. A typical framework contains several design patterns, but the reverse is never true.

3. Design patterns are less specialized than frameworks. Frameworks always have a particular application domain. A graphical editor framework might be used in a factory simulation, but it won't be mistaken for a simulation framework. In contrast, the design patterns in this catalog can be used in nearly any kind of application. While more specialized design patterns than ours are certainly possible (say, design patterns for distributed systems or concurrent programming), even these wouldn't dictate an application architecture like a framework would.

Frameworks are becoming increasingly common and important. They are the way that object-oriented systems achieve the most reuse. Larger object-oriented applications will end up consisting of layers of frameworks that cooperate with each other. Most of the design and code in the application will come from or be influenced by the frameworks it uses.

# UML Relationships among Classes

- **Association** - "Using Relationship" or "is part of association" relationship
- **Composition (Dependency)** - one element is dependent on another element -“has-a” relationship 
- **Aggregation (Dependency) or "Has-a" Relationship** - what distinguishes it from **composition**, that **it doesn't involve owning**
- **Generalization (inheritance)** - “is-a” relationship
- **Realization** - one model element **implements** the responsibility specified by another model element

## Definitions Extracted from the "UML 2.0 Specifications"

>-  "**Association**: specifies a semantic relationship that can occur between typed instances. An instance of an association is called a link.”. What They Mean: An association between two classes indicates that objects (instances) of one class may be related (linked) to objects of the other class. You specify an association at the class level; you specify a link at the object level;
>
>- “**Aggregation**: A special form of association that specifies a whole-part relationship between the aggregate (whole) and a component part." What They Mean: Formally, in the UML, aggregation is considered to be a specific type of association, where the class on one end of the association represents a whole and the class at the other end represents 
a part. Aggregation may be used by the BA as an alternative to modeling an association with the name “is a part of”;
>
>- “**Composition**: is a strong form of aggregation that requires a part instance be included in at most one composite at a time. If a composite is deleted, all of its parts are normally deleted with it.” What They Mean: Formally, composition is a specific kind of aggregation. In aggregation, a part may belong to more than one whole at the same time; in composite aggregation, however, the object may belong to only one whole at a time. The parts are destroyed whenever the whole is destroyed—except for those parts that have been removed prior to the deletion of the whole.
>
>- “**Inheritance**: The mechanism by which more specific elements incorporate structure and behavior of more general elements.” What They Mean: Inheritance refers to the mechanism by which a specialized class adopts—that is, inherits—all the attributes, operations, and relationships5 of a generalized class.

## Aggregation versus Association

It´s easy to confuse **aggregation** and **association**, because they are often implemented in the same way - there´s no distinction in thew programming languages between **agreggation** and **association**. Ultimately, **association** and **aggregation** are determined more by intent than by explicit language mechanisms. The distinction may be hard to see in the compile-time structure, but it's significant. **Aggregation relationships** tend to be fewer and more permanent than **association**. **Association**, in contrast, are made and remade more frequently, sometimes existing only for the duration of an operation. **Associations** are more dynamic as well, making them more difficult to discern in the source code.

# UML Association or Using Relationship

![umlassociations Relationships](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/AssociationCompositionAggregationRelationshipsImage001.jpg)

* Association is relation between two separate classes which establishes through their Objects. 

* Association can be:

  - one-to-one, 
  - one-to-many, 
  - many-to-one, or 
  - many-to-many.
  
* In Object-Oriented programming, an Object communicates to other Object to use functionality and services provided by that object. 

* Composition and Aggregation are the two forms of association.

* **Association** - In UML diagrams, an association class is a class that is part of an association relationship between two other classes.  You can attach an association class to an association relationship to provide additional information about the relationship. Association is the semantic relationship between classes that shows how one instance is connected or merged with others in a system. The objects are combined either logically or physically.

Association is the weakest relationship between the three (Association, Generalization and Composition). It **isn't** a **“has-a” relationship**, *none of the objects are parts or members of another*.  Association is called a **"using relationship"**.

Association only means that "the objects “know” each other*. For example, a mother and her child.

In UML, If the **association is unidirectional** we mark it with an arrow:

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

# UML Composition

Composition is known as "Whole-part" Relationship. Composition or Composite aggregation is a "strong" form of aggregation with the following characteristics:

- it is binary association,
- it is a whole/part relationship,
- a part could be included in at most one composite (whole) at a time, and
- if a composite (whole) is deleted, all of its composite parts are "normally" deleted with it.

Note, that UML does not define how, when and specific order in which parts of the composite are created. Also, in some cases a part can be removed from a composite before the composite is deleted, and so is not necessarily deleted as part of the composite.

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

# UML Aggregation or Has a Relationship 

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

# UML Generalization or Inheritance

Generalization or Inheritance is name "a kind of" or  "is-a" relationship.

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

# Inheritance in Design Patterns

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

# UML Realization

In UML modeling, the realization is a relationship between two objects, where the client (one model element) implements the responsibility specified by the supplier (another model element). The realization relationship can be employed in class diagrams and components diagrams.  The realization relationship does not have names. It is mostly found in the interfaces. It is represented by a dashed line with a hollow arrowhead at one end that points from the client to the server.

# Interface Realization

Interface realization is a kind of specialized relation between the classifier and the interface. In interface realization relationship, realizing classifiers conforms to the contract defined by the interface.

A classifier implementing an interface identifies the objects that conform to the interface and any of its ancestors. A classifier can execute one or more interfaces. The set of interfaces that are implemented by the classifier are its given interfaces. The given interfaces are the set of services offered by the classifiers to its clients.

The interface realization relationship does not contain names, and if you name it, then the name will appear beside the connector in the diagram.

The interface realization relationship is represented by a dashed line with a hollow arrowhead, which points from the classifier to the given interface.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/uml-realization.png)

# UML Realization
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

# Creational Design Patterns

## Introduction to Creational Design Patterns

These patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code. The Creational Patterns are the following:

**A - Creational Object Design Pattern:**

* Factory Method (107)

**B - Creational Class Design Patterns:**

* Abstract Factory (87)
* Builder (97)
* Prototype (117)
* Singleton (127)

# Description of Creational Design Patterns

# DCP1 Factory Method

A factory method is a generalization of a simple factory:

* There is a superclass or interface which has the factory or method declared
* Subclasses or implementers specialize this factory to create the kinds of objects they need
* Advantage over simple factory above is no switch statement is needed when the factory decides what kind of object to make: the choice of subclass already made the decision.
-- recall switch is a smell, and we are removing a switch

The only thing that we can be sure in software development is that the change in the requirements of applications will occur inevitably. So, the business requirements change over time. New product launches, new regulations, effect of competitors, new markets needs, economic factors, adn  so on: there are lots of potential causes for business software to need updating. From those observations we can infer that the code they write is going to change, but not what those changes will be or when they will happen. Writing code in such a way that it can be easily adapted is a skill that takes years to master. How you code your application has a big impact on how easy it is to adapt to meet new requirements. As weprogress through our career, we learn techniques that make adapting code easier. Once we've grasped fundamentals of object-oriented programming we wonder how we ever did without it!

### What is Factory Design Pattern ?

A Factory Pattern or Factory Method Pattern says that just define an interface or abstract class for creating an object but let the subclasses decide which class to instantiate. In other words, subclasses are responsible to create the instance of the class.

The Factory Method Pattern is also known as Virtual Constructor.

The Factory Method pattern is useful when you need to abstract the creation of an object away from its actual implementation. Let’s say the factory will be building a “MobileDevice” product type. A mobile device could be made up of any number of components, some of which can and will change later, depending on advances in technology.

### What is the Factory Pattern used for?

The Factory Method pattern is a design pattern used to define a runtime interface for creating an object. It's called a factory because it creates various types of objects without necessarily knowing what kind of object it creates or how to create it.

Design patterns are not about designs such as linked lists and hash tables that can be encoded in classes and reused as is. Nor are they complex, domain-specific designs for an entire application or subsystem. The design patterns in this book are descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context.

A design pattern names, abstracts, and identifies the key aspects of a common design structure that make it useful for creating a reusable object-oriented design. The design pattern identifies the participating classes and instances, their roles and collaborations, and the distribution of responsibilities. Each design pattern focuses on a particular object-oriented design problem or issue. It describes :

- when it applies, 
- whether it can be applied in view of other design constraints, and 
- the consequences and trade-offs of its use. 

### Advantage of Factory Design Pattern

- Factory Method Pattern allows the sub-classes to choose the type of objects to create.
- It promotes the loose-coupling by eliminating the need to bind application-specific classes into the code. That means the code interacts solely with the resultant interface or abstract class, so that it will work with any classes that implement that interface or that extends that abstract class.

### Usage of Factory Design Pattern

- When a class doesn't know what sub-classes will be required to create
- When a class wants that its sub-classes specify the objects to be created.
- When the parent classes choose the creation of objects to its sub-classes.

### GOF Description of Factory Method (107) 

 - Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

### Generic diagram of Factory Method (107) Pattern

![UML Class Diagram Factory Method Pattern](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/UML_Class_Diagram_BeverageMachineApp001.jpg)

Beverage Machine Application Code Example:

```java
package designpatterns;
public interface IBeverageMachine {

    //Factory Method 
    
    public Beverage createBeverage(int TypeOfBeverage);
    
    // The Other Methods of the Application
    
    public void recordSale (Product p, int qty);
    public void purchaseItemToSale (Product p, int qty, float priceSale);
    public float getPriceTotalSold();
    public int getQtyTotalSold();
}
```
```java
package designpatterns;
public abstract class Beverage {

	Product _prod;	
	public abstract Product getFullProduct();
}
```
```java
package designpatterns;
public class Coffee extends Beverage {	

	private static Product _prod;	
	public Coffee ( float price, int qty ) {		 
		_prod = new Product ("Coffee",  price, qty);
	}
	@Override
	public Product getFullProduct() {
		return _prod;
	}
}
```
```java
package designpatterns;
public class Soda extends Beverage {

	private static Product _prod;	
	public Soda ( float price, int qty ) {		 
		_prod = new Product ("Soda",  price, qty);
	}
	@Override
	public Product getFullProduct() {
		return _prod;
	}
}
```
```java
package designpatterns;
public class Chocolate extends Beverage {

	private static Product _prod;	
	public Chocolate ( float price, int qty ) {		 
		_prod = new Product ("Chocolate",  price, qty);
	}
	@Override
	public Product getFullProduct() {		
		return _prod;
	}
}
```
```java 
package designpatterns;
public class Product {	

	String productName;
	float productPrice;
	int inventory;	
	
	public Product (String Name, float Price, int inventory) {
		this.productName = Name;
		this.productPrice = Price;
		this.inventory = inventory;
	}
	public String getName() {
		return productName;
	}
	public float getPrice() {
		return productPrice;
	}	
	public void setPrice(float price) {
		productPrice = price;
	}	
	public int getInventory( ) {
		return inventory;
	}
	public void addInventory (int quantity) {
		inventory += quantity;
	}
	public void subtractInventory (int quantity) {
		inventory -= quantity;
	}	
}
```
```java
package designpatterns;
public class SalesMachine implements IBeverageMachine {

	private static final int _soda      = 111;
	private static final int _coffee    = 222;
	private static final int _chocolate = 333;	
	private int _qtySold;
	private float _valueSold;

	public SalesMachine() {
		this._qtySold = 0;
		this._valueSold = 0f;	 
	}
	// Factory Method Pattern
        @Override
	public Beverage createBeverage(int TypeOfBeverage) {
		switch (TypeOfBeverage) {
		case _soda  :      return new Soda (10.5f, 0);
		case _coffee:      return new Coffee (4.5f, 0);
		case _chocolate:   return new Chocolate (6.5f, 0);		
		}
		return null;	
	}
	@Override
	public void recordSale (Product p, int qty ) {
		Product _p = p;
		_qtySold += qty;
		_p.subtractInventory(qty);
		_valueSold += (qty * _p.getPrice());
	}
	@Override
	public void purchaseItemToSale (Product p, int qty, float priceSale ) {
		Product _p = p;
		_p.addInventory(qty);
		_p.productPrice = priceSale;
	}
	@Override
	public float getPriceTotalSold () {
		return _valueSold;
	}
	@Override
	public int getQtyTotalSold () {
		return _qtySold;
	}
}
```
```java
package designpatterns;
import static org.junit.Assert.assertEquals;
import org.junit.jupiter.api.Test;

class BeverageMachineTest {
	@Test
	void test() {
	
		int _soda      = 111;
		int _coffee    = 222;
		int _chocolate = 333;
		
		Product _prodSoda;
		Product _prodChocolate;
		Product _prodCoffee;
		Beverage bg;
		IBeverageMachine _bm = new SalesMachine();

		bg = _bm.createBeverage(_soda);
		_prodSoda = bg.getFullProduct();
		_bm.purchaseItemToSale(_prodSoda, 121, 12.8f );
		assertEquals ( "Soda", _prodSoda.productName);

		bg = _bm.createBeverage(_coffee);
		_prodCoffee = bg.getFullProduct();
		_bm.purchaseItemToSale(_prodCoffee, 12, 8.5f );
		assertEquals ( "Coffee", _prodCoffee.productName);

		bg = _bm.createBeverage(_chocolate);
		_prodChocolate = bg.getFullProduct();
		_bm.purchaseItemToSale(_prodChocolate, 18, 6.2f);
		assertEquals ( "Chocolate", _prodChocolate.productName);	

		assertEquals (  18, _prodChocolate.getInventory());
		assertEquals (  12, _prodCoffee.getInventory());
		assertEquals ( 121, _prodSoda.getInventory());
		
		_bm.recordSale (_prodChocolate, 5);
		_bm.recordSale (_prodChocolate, 2);
		assertEquals (  11, _prodChocolate.getInventory());
		
		assertEquals (  7,_bm.getQtyTotalSold());
		Assert.assertEquals(43.40f, _bm.getPriceTotalSold(), 0.0002);
	}
}
```

## Use of the Dependency Inversion Principle in the Factory Design Pattern

"High level code should not depend directly on low level code; instead, both should depend on an abstractions". 

Put an interface in the middle! Separate those concerns! Factory Method is a really good iillustration for applying the depedency inversion principle. T

Arrows in the above (read as "dependent-on") show high-level code directly dependent on details of low-level code (it needs their names to create them via new) 

The UML Class Diagram above shows how the depenencies get inverted whan a factory method is used, meaning PizzaStore only deals with Pizza abstraction, not all the low-level details. The dependencies were inverted. 


# Model View Controller Pattern

Model–view–controller (usually known as MVC) is a software design pattern commonly used for developing user interfaces that divides the related program logic into three interconnected elements. This is done to separate internal representations of information from the ways information is presented to and accepted from the user.

Traditionally used for desktop graphical user interfaces (GUIs), this pattern has become popular for designing web applications. Popular programming languages like JavaScript, Python, Object Pascal/Delphi, Ruby, PHP, Java, C#, and Swift have MVC frameworks that are used for web or mobile application development straight out of the box.

## Components of MVC Pattern

### Model

The central component of the pattern. It is the application's dynamic data structure, independent of the user interface. It directly manages the data, logic and rules of the application.

### View

Any representation of information such as a chart, diagram or table. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.

### Controller

Accepts input and converts it to commands for the model or view.In addition to dividing the application into these components, the model–view–controller design defines the interactions between them.

### Interactions

- In addition to dividing the application into three kinds of components, the model–view–controller design defines the interactions between them.
- The model is responsible for managing the data of the application. It receives user input from the controller.
- The view means the presentation of the model in a particular format.
- The controller responds to the user input and performs interactions on the data model objects. The controller receives the input, optionally validates it and then passes the input to the model.

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/model-view-controller_pattern_iamge001.jpg)

## Reasons to Use MVC Pattern

- The following advantages of the MVC design pattern make it suitable to be used in software development:
- Simultaneous development — Multiple developers can work simultaneously on the model, controller and views.
- High cohesion — MVC enables logical grouping of related actions on a controller together. The views for a specific model are also grouped together.
- Low coupling — The very nature of the MVC framework is such that there is low coupling among models, views or controllers
- Ease of modification — Because of the separation of responsibilities, future development or modification is easier
- Multiple views for a model — Models can have multiple views

## Java Application Example Implementing MVC Pattern

The UML Class Diagram showing the architecture design using MVC Pattern:

![](https://github.com/aridiosilva/DesignPrinciplesAndPatterns/blob/main/MVC%20Model-View-Controller%20App%20Prof%20Jacques_iamge002.jpg)

```java
package enquete;

import enquete.view.*;
import enquete.controller.*;
import enquete.model.*;

@SuppressWarnings("deprecation")
public class Enquete {

	public static void main(String[] args) {
		Enquete _e = new Enquete();
		_e.start();
	}
	@SuppressWarnings("deprecation")
	public void start() {

		EnqueteSimplesModel _enquete= new EnqueteSimplesModel();

		TelaVotacaoController _ctrl = new TelaVotacaoController(_enquete);

		TelaVotacaoView _votacao = new TelaVotacaoView(_ctrl);
		_votacao.setLocation(5,5);

		TelaResultadoView _resultado = new TelaResultadoView(_votacao);
		_resultado.setLocation(120,5);

		TelaResultadoPercentualView _resultadoPerc = new TelaResultadoPercentualView(_votacao);
		_resultadoPerc.setLocation(250,5);

		_enquete.addEnqueteListener(_votacao);
		_enquete.addEnqueteListener(_resultado);
		_enquete.addEnqueteListener(_resultadoPerc);

		_enquete.addOpcao("Opcao 1");
		_enquete.addOpcao("Opcao 2");
		_enquete.addOpcao("Opcao 3");
		_enquete.addOpcao("Opcao 4");
		
		_votacao.show();
		_resultado.show();
		_resultadoPerc.show();
	}
}
```

```java
package enquete.model;

import java.util.HashMap;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;
import java.util.Set;

public class EnqueteSimplesModel {

	private Map <String, Integer> _opcoes;
	private List <EnqueteListenerModel> _enqueteListeners; 
 
	public EnqueteSimplesModel(){
		this._opcoes = new HashMap<String, Integer>();
		this._enqueteListeners = new LinkedList();
	}
	public void addOpcao(String opcao){
		_opcoes.put(opcao,new Integer(0));
		this.disparaNovaOpcao(opcao);
	}
	public Set <String> getOpcoes(){
		return _opcoes.keySet();
	}
	public void votar(String opcao){
		int _votoAtual = (_opcoes.get(opcao)).intValue();
		_opcoes.put(opcao,new Integer(++_votoAtual));
		this.disparaNovoVoto(opcao);
	}
	public int getTotalVotos(){
		int _total = 0;
		for(Integer _votos : _opcoes.values()){
			_total+= _votos.intValue();
		}
		return _total;
	}
	public int getVotos(String opcao){
		return (_opcoes.get(opcao)).intValue();
	}
	 public synchronized void addEnqueteListener(EnqueteListenerModel listener){
		if(_enqueteListeners.contains(listener)){ return; }
		this._enqueteListeners.add(listener);
	}
	 private synchronized void disparaNovoVoto(String opcao){		
		for(EnqueteListenerModel listeners : this._enqueteListeners){
			listeners.novoVoto(new EnqueteEventModel(this,opcao));
		}
	}
	 private synchronized void disparaNovaOpcao(String opcao){		
		for(EnqueteListenerModel listeners : this._enqueteListeners){
			listeners.novaOpcao(new EnqueteEventModel(this,opcao));
		}
	}
}
```
```java
package enquete.model;

public class EnqueteAdapterModel implements EnqueteListenerModel {

	public void novaOpcao(EnqueteEventModel event) {}
	public void novoVoto(EnqueteEventModel event) {}
}
```
```java
package enquete.model;
import java.util.EventObject;

public class EnqueteEventModel extends EventObject {

	private static final long serialVersionUID = 1L;
	private String _opcao = null;
	private int _votos = 0;

	public EnqueteEventModel(EnqueteSimplesModel source){
		super(source);
	}
	public EnqueteEventModel(EnqueteSimplesModel source,String opcao){
		this(source);
		this._opcao = opcao;
	}
	 public String getOpcao() {
		return _opcao;
	}
	 public int getVotos() {
		return ((EnqueteSimplesModel)this.source).getVotos(_opcao);
	}
	 public int getTotalVotos() {
		return ((EnqueteSimplesModel)this.source).getTotalVotos();
	}
}
```
```java
package enquete.model;
import java.util.EventListener;

public interface EnqueteListenerModel extends EventListener {

public void novoVoto(EnqueteEventModel event);
	public void novaOpcao(EnqueteEventModel event);
}
```
```java
package enquete.view;
import java.awt.*;
import java.awt.event.*;
import java.util.*;
import enquete.model.*;

public class TelaVotacaoView extends Frame implements EnqueteListenerModel{

	private static final long serialVersionUID = 1L;
	private Collection <String> _botoes = new ArrayList();
	private ActionListener _controller;

	public TelaVotacaoView(ActionListener controller){		

	        super("Tela de Votacao - Enquete");
		this.setSize(100,120);
		// Grid com qualquer numero de linhas e uma coluna
		this.setLayout(new GridLayout(0,1)); 	
		this._controller = controller;
	    this.addWindowListener(new WindowAdapter() {
	        public void windowClosing(WindowEvent e) {
	        	e.getWindow().hide();
	        	System.exit(0);
	        }
	    });
	}
	public void novaOpcao(EnqueteEventModel event) {
		
		String _opcao = event.getOpcao();
		Button _botao;
		if(!_botoes.contains(_opcao)){
			_botoes.add(_opcao);
			_botao = new Button(_opcao);
			_botao.setActionCommand(_opcao);
			_botao.addActionListener(_controller);
			this.add(_botao);
		}
	}
	public void novoVoto(EnqueteEventModel event) {
	}
}
```
```java
package enquete.view;
import java.awt.*;
import java.util.*;
import enquete.model.EnqueteEventModel;
import enquete.model.EnqueteListenerModel;

public class TelaResultadoView extends Window implements EnqueteListenerModel{

	private static final long serialVersionUID = 1L;
	private Map <String, Label> _labels = new HashMap();

	public TelaResultadoView(Frame parent){

		super(parent);
		this.setSize(110,120);
		this.setLayout(new GridLayout(0,2)); 
		this.add(new Label("Votos"));
		this.add(new Label());
	}
	public void novaOpcao(EnqueteEventModel event) {

		String _opcao = event.getOpcao();
		Label _label;
		Label _votos;
		if(!_labels.containsKey(_opcao)){
			_label = new Label(_opcao+" - ");
			_votos = new Label(""+event.getVotos());
			_labels.put(_opcao,_votos);
			this.add(_label);
			this.add(_votos);
		}
	}
	public void novoVoto(EnqueteEventModel event) {

		String _opcao = event.getOpcao();
		Label _votos;
		_votos = _labels.get(_opcao);
		_votos.setText(""+event.getVotos());
	}
}
```
```java
package enquete.view;
import java.awt.*;
import java.util.*;
import enquete.model.EnqueteEventModel;
import enquete.model.EnqueteListenerModel;

public class TelaResultadoPercentualView extends Window implements EnqueteListenerModel{

	private static final long serialVersionUID = 1L;
	private Map <String,Label> _labels = new HashMap();

	public TelaResultadoPercentualView(Frame parent){

		super(parent);
		this.setSize(180,120);
		this.setLayout(new GridLayout(0,2)); 
		this.add(new Label("Percentual"));
		this.add(new Label());
	}
	public void novaOpcao(EnqueteEventModel event) {

		String _opcao = event.getOpcao();
		Label _label;
		Label _votos;
		if(!_labels.containsKey(_opcao)){
			_label = new Label(_opcao+" - ");
			_votos = new Label(""+event.getVotos()+" %");
			_labels.put(_opcao,_votos);
			this.add(_label);
			this.add(_votos);
		}
	}
	public void novoVoto(EnqueteEventModel event) {

		String _opcao = event.getOpcao();
		Label _votos;
		_votos = _labels.get(_opcao);
		_votos.setText(""+(event.getVotos()*100/event.getTotalVotos())+" %");
	}
}
```
```java
package enquete.controller;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import enquete.model.EnqueteSimplesModel;

public class TelaVotacaoController implements ActionListener{

	private EnqueteSimplesModel _enquete;
	public TelaVotacaoController(EnqueteSimplesModel enquete){
		
		this._enquete = enquete;
	}
	public void actionPerformed(ActionEvent event) {
		
		_enquete.votar(event.getActionCommand());
	}
}
```

