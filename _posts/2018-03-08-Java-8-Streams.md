## WHY `Stream`

**Some issues with processing collections in Java:**

1. Typical processing patterns such as "finding" or "grouping":
	* Don't need to implement 'how' to do the processing
	* Only express 'what' we expect
	* In Java: reimplementing these operations over and over again using loops
2. How can we process large collections effectively?

**New feature in Java SE 8: `Stream`**

* Let you process data in a **declarative** way - focuses on *what* is expected, instead of *how* to do it.
* A stream:
	* can be seen as an abstraction for expressing efficient, SQL-like operations on a collection of data
	* is a sequence of elements from a *source* that supports *aggregrate operations* (e.g. chaining) 
		* *source*: a data-providing source such as collections, arrays or I/O resources
		* *aggregrate operations*: SQL-like operations and common operations from functional programming languages, such as `filter`, `map`, `reduce`, `find`, `match`, `sorted`, etc.

* `stream()` 
* `parallel stream()` -- the Streams API will internally decompose your query to leverage the multiple scores on your computer

**Stream operations vs collection operations**

Two fundamental characteristics of stream operations:

* Pipelining:
	* Many stream operations return a stream themselves
	* This allows operations to be chained to form a larger pipeline
		* --> Optimizations: *laziness*, *short-circuiting*
* Internal iteration:
	* Iteration is done behind the scenes

**Main difference from collection operations**: *when* things are computed

* Collection - in memory data structure, every element has to be computed before it can be added to the collection
* Stream - 'conceptually' fixed data structure, elements are computed on demand

## Stream Creation

* USE `stream()` or `of()` methods:

**From Arrays:**

```
String[] days = {"Monday", "Tuesday", "Wednesday"};
```
Two ways to create a stream from an array:

```
Stream<String> stream = Arrays.stream(arr);
```
```
Stream<String> stream = Stream.of(arr);
```

**From Collections**

```
List<String> list = new ArrayList<String>();
list.add("Monday");
list.add("Tuesday");
list.add("Wednesday");
Stream<String> stream = list.stream();
```

**Use Stream.generate()**

```
Stream<String> stream = Stream.generate(() -> "Hello World!").limit(10);
```
There are other ways of generate a stream in Java 8, but those are the common ways. 

## Some Stream Operations: 

**Two main categories:**

1. **intermediate operations**
	* e.g. `filter`, `sorted`, `map` --> can be connected together to form a pipeline 
	* Do not perform any processing until a terminal operation is invoked on the stream pipeline --> are "lazy"
	* "short-circuiting" - process only part of the stream, not all of it, to return a result
2. **terminal operations**
	* e.g. `collect` --> closes the pipeline and returns a result

---

**Filtering**

Some operations that can be used to **filter** elements from a stream:

* `filter(Predicate)` - takes a predicate and returns a stream that includes all elements that match the given predicate
* `distinct` - returns a stream with unique elements
* `limit(n)` - returns a stream that is no longer than a given size n
* `skip(n)` - returns a stream with the first n number of elements discarded

```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
Stream<Integer> stream = numbers.stream().filter(x -> x % 2 == 0);

```

**Finding and matching**

* To determine whether some elements match a given property:
	* `anyMatch`
	* `allMatch`
	* `noneMatch`
* All take a predicate as an argument, and returns a `boolean` as a result --> terminal operations

```
boolean isEven = numbers.stream().allMatch(n -> n % 2 == 0);
```

**Mapping**

* Use `map` method to convert elements of a `Stream` 
	* by applying a function to them 
	* and collect the resulting new elements into a `Stream`

``` java
List<Integer> numbers = Arrays.asList(1, 2, 3);
Stream<Integer> stream = numbers.stream().map(n -> n*2);
``` 

**Reducing**

* Use `reduce()` method - to reduce a sequence of elements to some value according to a specified function (similar to `fold` operations in Haskell)
	* First parameter: an identity element (e.g. 0 for addition, 1 for multiplication)
	* Second parameter: an accumulator function

```java
List<Integer> numbers = Arrays.asList(1, 2, 3);
Integer sum = numbers.stream().reduce(0, (a,b) -> a+b)
```

**Collecting**

* Use `collect()` method to convert a stream to a `Collection` or a `Map`
* Utility class `Collectors` - provide a solution for almost all typical collecting operations.

```java
List<String> result = list.stream().map(word -> word.toLowerCase()).collect(Collectors.toList());
```

---
###REFERENCES

1. [Processing Data with Java SE 8 Streams, Part 1] (http://www.oracle.com/technetwork/articles/java/ma14-java-se-8-streams-2177646.html)
2. [Introduction to Java 8] (http://www.baeldung.com/java-8-streams-introduction)
3. [Java 8 Streams: An Intro to Filter, Map and Reduce Operations] (https://www.sitepoint.com/java-8-streams-filter-map-reduce/)




