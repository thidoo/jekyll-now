Below is a summary of the main concepts to consider when using exceptions in Java as discussed in Chapter 10 of the Effective Java book (Third Edition) by Joshua Bloch.

You can find a short dot point list of these points at the end of the post.

**A well-designed API must not force its clients to use exceptions for ordinary control flow.**

* Instead, do:
    * Use a separate state-testing method
    * Have a state-dependent method return an empty optional or a distinguished value such as null if it cannot perform the desired computation

* Guidelines to choose between the above two options:
    * Use optional or distinguished return value:
        * If state might be changed between invocations
        * Performance reasons
    * A state-testing method is mildly preferable to a distinguished return value:
        * Incorrect use throws an exception
        * But forgetting to check for a distinguished return value might result in a hard to detect bug
        * Not an issue for optional return values

**Checked exceptions, runtime exceptions, errors:**

* Use checked exceptions for conditions from which the caller can reasonably be expected to recover
    * By confronting the user with a checked exception, the API designer presents a mandate to recover from the condition
    * Provide methods that allow for further info on the exception to aid in recovery
* Use runtime exceptions to indicate programming errors
    * If it’s unclear whether recovery is possible, use an unchecked exception
* Convention: errors are reserved for use by the JVM to indicate it’s impossible to continue (for various reasons)

**Avoid unnecessary use of checked exceptions**

* It places a burden on the user of the API (this burden increased in Java 8 - methods throwing checked exceptions can’t be used directly in streams)
* Burden can be justified if BOTH conditions (below) are met:
    * The exceptional condition cannot be prevented by proper use of the API
    * And, the programmer can take some useful action once confronted with the exception
* Easiest way to eliminate checked exception —> return an optional
    * Disadvantage: can’t return additional info detailing its inability to perform desired computation
    * If more detailed info needed —> use checked exception

**Favour the use of standard exceptions**

* IllegalArgumentException
* IllegalStateException
* NullPointerException
* IndexOutOfBoundsException
* ConcurrentModificationException
* UnsupportedOperationException
* ArithmeticException
* NumberFormatException

*Reuse must be based on documented semantics, not just on name
*Subclass a standard exception if you want to add more details
*Exceptions are serializable (Chapter 12)

**Throw Exceptions appropriate to the abstraction**

* Exception translation:
    * Higher layers should catch lower-level exceptions
    * In their place, throw exceptions that can be explained in terms of higher-level abstraction
* Exception Chaining:
    * Higher-level exception’s constructor passes the **cause** to a **chaining-aware superclass constructor**
    * This is ultimately passed to one of *Throwable*’s chaining-aware constructors such as *Throwable(Throwable)* —> which provides *getCause* method to retrieve the cause
* Exception translation should not be overused:
    * Best way to deal with exceptions from lower layers is to avoid them -> by ensuring lower-level methods succeed
    * If it’s impossible to prevent exceptions from lower layers -> have the higher layer silently work around these exceptions (e.g. log the exception -> allows programmer to investigate the problem, while insulating client code and the users from it)

**Document all exceptions thrown by each method**

* ```**@throws**``` tags in doc comments

**Include failure-capture information in detail messages**

* *toString* method should return as much information as possible concerning the cause of the failure
* Should contain:
    * Values of all parameters & fields contributed to the exception
* Do not include passwords, encryption keys, and the like in detail messages
* Put information in constructor

**Strive for failure atomicity**
* A failed method invocation should leave the object in the state that it was in, prior to the invocation -> aka. ‘Failure-atomic’
* Several ways to achieve this effect:
    * Design immutable objects -> failure atomicity is free
    * For methods that operate on mutable objects:
        * Check parameters for validity before performing the operation -> causes most exceptions to be thrown before object modification commences
        * Order computation so that any part that may fail takes place before any part that modifies the object
        * Perform operation on a temporary copy, replace contents of object in temporary copy once operation is complete

**Don’t ignore exceptions**

------

**SUMMARY:**

* Do not use Exceptions for Control Flow (instead use state-testing method or optionals)
* Use checked exceptions if recoverable 
    * Put information in constructor
    * Throw exceptions appropriate to level of abstractions (exception translation or chaining)
    * Strive for failure atomicity
* Don’t overuse checked exceptions:
    * Use optionals if less detailed info is required
* Use standard exceptions where possible
* Don’t ignore exceptions

**REFERENCES:**

Joshua Bloch: Effective Java, Third Edition.

