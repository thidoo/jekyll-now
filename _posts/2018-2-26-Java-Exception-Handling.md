#EXCEPTIONS IN JAVA

## 3 TYPES OF EXCEPTIONS

1. **Checked exceptions** - exceptions that occur at compile time
2. **Unchecked exceptions (Runtime exceptions)** - occurs at time of execution
	* Include bugs, program logic, etc.
	* Are ignored at compile time
3. **Errors** - are not exceptions at all, but problems that occur beyond the control of the user or programmer. 
	* Are typically ignored in your code

## EXCEPTION HIERARCHY

* All exception classes are subtypes of the Java.Lang.Exception class
* The exception class is a subclass of the Throwable class
	* The Exception class has two main subclasses:
		* RuntimeException class
		* IOException class

## CATCHING EXCEPTIONS

* Use try/catch block
* Code within try/catch block is referred to as protected code

## The finally block

* The finally block follows a try or a catch block
* The finally block of code always executes
* Allows you to run any cleanup-type statements that you want to execute, no matter what happens in the protected code

## USER-DEFINED EXCEPTIONS

* Rules:
	* All exceptions must be a child of Throwable
	* If you want to write a checked exception that is automatically enforced by the Handle or Declare Rule, you need to extend the **Exception** class.
	* If you want to write a runtime exception, you need to extend the **RuntimeException** class.

	
##References

[Java - Exceptions (from tutorialspoint)] (https://www.tutorialspoint.com/java/java_exceptions.htm)

