---
title: Implements or Extends. What are the differences? 
date: "2022-05-17T22:40:32.169Z"
description: "What are the differences between the Java keywords extends and implements"
---
<div style="text-align: justify">

###### IMPLEMENTS vs EXTENDS

Implements is used to `implement a interface` on a class. Extends is used when you want to `extend a class` from a base class and inherit its properties and methods implementations. 

###### INTERFACES

To better understand the the implements and extends keywords, we need to understand about classes and interfaces.

A interface can be described as an abstraction of particular data type behaviors. They can be used to specify the actions that certain types of objects must do, it's a contract of business functionality represented by methods definitions. `An interface is nothing but an abstract class which contains no method implementations but only definitions.` 

Both a car, a motorbike and a bus must have start and stop methods, but, when they implement a vehicle interface that contains the definition of those methods, they will each have their own implementations. Only the class implementing the interface can implement the methods. 

```java
public interface VeihicleInterface {
  public void start();
  public void stop();
  public void changeGear(int a); 
  public void speedUp(int a);
  public void applyBrakes(int a);
}
```
###### ABSTRACT CLASSES
Abstract classes are meant to implement hierarchy. They can contain attributes, abstract and non-abstract methods while interfaces are fully abstract. Abstract classes provide default behaviors that your implementation can reuse.

> A class can only extend one other class, but can implement several interfaces. 

It's important to note that you can't create a object out of an abstract class. You don't simply drive a vehicle, you drive a vehicle of a certain brand and model. 

So, in summary, we use the implements keyword when we're implementing an interface on a class. We use the extends keyword when we want to extend a class from a base class.

<div style="text-align: right">

###### []'s 
