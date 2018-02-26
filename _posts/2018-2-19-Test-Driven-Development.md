Being introduced to the world of Test Driven Develoment has been a big eye-opening experience for me. I decided to redesign and re-code my solution to the MYOB Challenge using the TDD approach to allow myself the chance to implement TDD and see how it works in a project.

**How I implemented TDD**

* I started out with sketching out the different domains and their interactions
* Then, I picked a small domain to work on at a time. This could be either an Entity or a class that contains a single purpose such as a SuperannuationCalculator.
	* For the chosen domain, I would start thinking about what it should do upon receiving a particular input, and wrote the JUnit test to test for that. 
	* I started with a failing test, and then created the required class/method to make the test pass. 
	* I then built upon the test to incorporate more complex input, which in turn required the corresponding class/method to be implemented properly
	* I repeated the above steps until I moved up to the bigger components and then the entire program 

**The main benefits I can see from using this approach are**

* Better domain design: 
	* TDD encourages a design in which classes are more de-coupled but at the same time cohesive. 
	* JUnit tests promote the design approach in which each class serves a single main purpose and does not contain too many other coupled behaviours
* You can be sure that each small independent units (class/methods) that you have built and tested using JUnits will work and hence you can confidently use them to build other bigger components
* It helps narrow down areas to debug, making the debugging more efficient and faster.

**Some other lessons learnt in relation to coding and design practice**

* Decide from the beginning the data structure to store data because any changes later on will make it very complicated to change the old data structure that has been used across multiple classes. This also makes the program more error prone and messy. 
* When dealing with money value, use BigDecimal or Decimal for better precisions. Any error in calculating money is a error we do not want. 
