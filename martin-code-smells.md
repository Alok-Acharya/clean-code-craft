
### Primitive Obsession
---
> Primitive Obsession is using primitive data types to represent domain ideas
> For example, we use a String to represent a message, an Integer to represent an amount of money, or a Struct/Dictionary/Hash to represent a specific object.
> **The Fix**: Typically, we introduce a **ValueObject** in place of the primitive data
> For example, instead of scattering all the parsing/formatting behavior for dates stored as text, introduce a DateFormat class which attracts that behavior as methods called parse() and format(), almost like magic
> **ValueObject** is a measure or description of something. Their identity is based on their state rather than on their object identity. This way, you can have multiple copies of the same conceptual value object. _Every $5 note has its own identity (thanks to its serial number), but the cash economy relies on every $5 note having the same value as every other $5 note_
### Data Clumps
---
>Whenever two or three values are gathered together – turn them into a $%#%^ object.” - Martin
>Data clumps are when more than one piece of data is oftentimes found together
>A data clump is a collection of two or more bits of information that are consistently used together. You’ll find that your data loses its meaning when you remove items from the clump
>A good way to identify a **data clump is that when one of the pieces does not make sense in isolation but only makes sense together**.
>Martin Fowler suggests replacing these clumps with a single object. Iexample  the startXXXX and endXXXX could be replaced by a "Range" class

### **Object Oriented Abusers** 
---
Object Oriented Abusers are a particular genre of Code Smells which refers to incorrect or incomplete implementation of Object Oriented Concepts.

#### Switch Case
---
- Violation of **Open Closed Principle**
- Replace Conditional With **Polymorphism**, typically done using the **Strategy Pattern**
- _Polymorphism gives you many advantages. The biggest gain occurs when the same set of conditions appears in many places in the program. If you want to add a new type, you have to find and update all of the conditionals. But with subclasses, you just create a new subclass and provide the appropriate methods. Clients of the class don't need to know about the subclasses, which reduces the dependencies in your system and makes it easier to update._
- When you get the SwitchStatementsSmell, it's an indication that your code isn't ObjectOriented

#### Temporary Fields
----
>There are times the developer decides to introduce Fields in the Class which are used only by one Method, instead of passing it as method parameter to avoid **Long Parameter List**. These fields sit idle in the class at all time, except when the particular method is used.

#### Alternative Classes with Different Interfaces
>This smell occurs when two methods in different classes do the same thing but have a different method signature
>**categories of different tunes with equal performance** .

>When many people develop the system together, different people may write similar code to deal with the same problem, but due to poor communication, each other did not notice this phenomenon. Therefore, these functions are similar or the same code, with different interfaces (different names or parameters) exist in the system at the same time
>**For example**, in the program, a string needs to be split into different substrings based on certain tokens. Some developers may directly use string objects plus formal notation for processing, some people write their own split() public function, and some people write a function with the same function but named subString(). For the same function, if there is a unified approach, it will be easier for future maintenance, system expansion, and debugging
>The reason why Alternative Classes with Different Interfaces is a bad smell (force)   because of  **understandability,  modifiability, and testability (increase test workload).**

### **Couplers**
---
 #### Inappropriate Intimacy
> InappropriateIntimacy is a CodeSmell that describes a method that has too much intimate knowledge of another class or method's inner workings, inner data, etc.
> If a class is more interested in the internals of another class, this can indicate that related data and behavior is not put in one place. Therefore, intimate classes should be refactored by moving the methods and fields in such a way that related data and behavior is put together and there is no need for a class to look at another class' internals.
> _sometimes classes become far too intimate and spend too much time delving in each other's private parts. we may not be prudes when it comes to people, but we think our classes should follow strict, puritan rules. over intimate classes should be broken up as lovers were in ancient days.... Inheritance often can lead to over intimacy. sub classes are always going to know more about the their parents ( base class) then their parents would like them to know._
> -peterluzc
intimacy is bad, which is the direct anti-pattern of Encapsulation. when you have this smell in the code, you will find it is difficult to change code, change in one class may lead to changes in many other classes. change in one user control may lead to change in many hosts( form or user controls) and hosts of the hosts and even more,,,, if you run code metrics, you will see high in class coupling, this is another direct anti-pattern of "high cohesion and low coupling".
ex:- Me.Address.DomesticAddUserControl.County.HideToCustomization()
  
"inside AddressUserControl control, there is an instance of another control  LayoutControlItem control , there is a method call HideToCustomization ()"

Take form as level zero, you can tell the intimacy level is 3, anything happen to the API of all these user controls involved will affect the code in the form. this is a typical case of Inappropriate Intimacy.

Refactoring
- Try to keep the public facing members to minimum. follow the rule called "Secure by default".
- move methods and fields so that they stay together ( in the same class)  
- change bidirectional association to unidirectional association between classes  
-  if there are 2 classes sharing common interest, extract the commonality into a separate class  
-  replace inheritance with Delegation  



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTUyNzQ2MSw2OTAzNDc1MTMsLTE4Nz
A0OTczNDQsLTEwNjY5NTYzNzgsMTEyOTU1Nzk1NCwtNTEwMjU4
MTUsNTkzODQ2ODA4LDgzNjMxNDc4Niw1ODY2NjQzOTYsLTE4MD
MzMjIzMSwtMjk3Njg0NDg0LDEwMDgwODM0OTZdfQ==
-->