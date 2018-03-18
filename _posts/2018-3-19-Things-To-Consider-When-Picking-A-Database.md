If you are trying to decide what kind of database to pick for your project, the following principles and theorems would be beneficial to help you make that decision.

## ACID

* Is a set of properties of **database transactions** intended to guarantee validity even in the event of errors

* **Atomicity**
	* Each transaction be "all or nothing"
	* To the outside world: a committed transaction appears to be indivisible, and an aborted transaction does not happen
* **Consistency**
	* Any transaction must change affected data only in allowed ways
	* All data written to db must be valid according to all defined rules
* **Isolation**
	* Defines how/when changes made by one operation become visible to other
* **Durability**
	* Once a transaction has been committed, it will remain so, even in the event of power loss, crashes or errors

## CAP Theorem (also named Brewer's Theorem)

* It's impossible for a **distributed data store** to simultaneously provide more than two out of the following three guarantees:
	* **Consistency** - every read receives the most recent write or an error
	* **Availability** - every request receives a (non-error) response - without gurantee that it contains the most recent write
	* **Partition tolerance** - System continues to operate despite an arbitrary number of messages being dropped or delayed by the network **between nodes** 

* **OR** - stated simply:
	* In a network partition, one has to choose between consistency and availability
	* Because:
		* No distributed system is safe from network failures -> network partitioning generally has to be tolerated
		* Hence, left with: consistency or availability

**DB systems designed with traditional ACID such as RDBMS choose consistency over availability**

## PACELC theorem

* Is an extension to CAP theorem
* Both theorems describe how distributed databases have limitations and tradeoffs regarding consistency, availability, and partition tolerance.
* PACELC goes further: A trade-off also exists, between **latency and consistency** (even in the absence of partitions)

