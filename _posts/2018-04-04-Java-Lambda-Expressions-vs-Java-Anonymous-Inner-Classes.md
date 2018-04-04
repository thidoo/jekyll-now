## JAVA LAMBDA EXPRESSIONS vs. JAVA ANONYMOUS INNER CLASS

Java 8 introduced a new functional feature which is the Lambda expression. Read on to learn more about what it is and how it works. 

### JAVA LAMBDA EXPRESSIONS (Java 8)

* Is a function which can be created without belonging to any class
* Can be passed around as if it was an object and executed on demand

**Matching Lambdas to Interfaces**

* A lambda expression can be used where the type they are matched against is a **single method interface** (also known as *functional interface*)
* Conditions for matching a Java lambda expression:
	* Single method interface
	* Parameter match
	* Return type match

**Lambda Type Inference** 

* The type of the lambda expressions can be inferred from the surrounding code.
	* E.g. From the method declaration right before the lambda expression
	* E.g. From the parameter types

* Sometimes, we'll need to specify the parameter types for a lambda expression if the compiler cannot infer the parameter types from the functional interface method.
	* E.g. (Car car) -> {};

**Lambdas as Objects**

* A Java lambda expression is essentially an object.
* It can be assigned to a variable and passed around, like with any other object.

----

Another similar feature that Java offers that can get confusing with the Java Lambda expressions is the Java anonymous inner class. Below is a quick recap of what it is.  

### JAVA ANONYMOUS INNER CLASS (Java 7)

* Anonymous inner class: is a class that has no name.
	* Used if you have to override method of class or interface.
	* Used if you need to use a local class only once

**Accessing local variables of the enclosing scope:**

* Anonymous classes have the same access to local variables of the enclosing scope:

	* They have access to members of its enclosing class
	* Cannot access local variables in its enclosing scope that are not declared as ```final``` or effectively final
	* Declaration of a type in an anonymous class shadows any other declarations in the enclosing scope

**Same restrictions as local classes:**

* Cannot declare static initializers or member interfaces in an anonymous class
* Can have static members, provided they are constant variables

**Can declare the following fields in an anonymous class:**

* Fields
* Extra methods
* Instance initilizers
* Local classes

**Cannot declare constructors in an anonymous classs**

-----

**GENERAL RULES:**

* Lambda functions can only be used in cases of single method interfaces. If you need to have classes/methods with more than one method, you need to use anonymous functions.
* The body of a lambda expression does not define a new scope -> its scope is the same as the enclosing scope
* If you find yourself using lambda functions in multiple places, consider creating a class

