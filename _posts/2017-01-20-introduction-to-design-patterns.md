---
layout: post
title: Introduction to design patterns
date: 2017-01-20
categories: programming patterns
---

## Design Patterns

This is my first post in a series about design patterns.  Later, I will make individual posts focusing on one pattern per post.  I will also have code examples from Drupal 8 and other open source projects.

### What is a design pattern?
According to Wikipedia, a design pattern is a "general reusable solution to a commonly occurring problem within a given context."  So, what does it mean?  Design patterns aren't specific code, but templates for code organization.  They cross language and community borders.  Although some languages do lend themselves to some patterns more than others.

There are multiple types of patterns: Creational Patterns, Structural Patterns, and Behavioral Patterns.  Here are a few patterns that fall under these categories.

#### Creational Patterns
These are patterns that template object creation, doing so in a manner suitable to a specific situation.

**Factory Method**  
Have an object whose job is to create other objects.  This is a way to implement polymorphism.

**Abstract Factory**  
Encapsulate a group of individual factories that have a common theme without specifying their concrete classes.

**Prototype**  
Create a new object by cloning an object that already exists.

**Builder**  
Build an object step by step.

**Singleton**  
Only one instance of an object exists.

**Lazy Initialization**  
Wait until an object is needed to initialize it

#### Structural Patterns
They provide ways to simplify the realization between entities

**Adapter Pattern**  
Allows the interface of an existing class to be used as another interface

**Facade Pattern**  
Simplify a complex subsystem into an interface

**Bridge Pattern**  
Decouple an abstraction from its implementation so the two can vary independently

**Decorator**  
Allows behavior to be added to added to an object

**Front Controller**  
Single Entry Point for all requests

**Module**  
Use software modules to logically break up an application

#### Behavorial Patterns
Communication patterns between objects

**Iterator**  
Provides a way to traverse a container and its elements

**Mediator**  
An object that encapsulates how a set of objects interact.

**Null Object**  
Avoid null references by setting default value

**Observer**  
An object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

**Repository**  
Create an abstraction layer between the data access layer and the business logic layer. 
