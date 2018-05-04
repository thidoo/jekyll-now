So yesterday, I got to attend a developer conference sponsored by MYOB called VoxxedDay. It was the first time it ran in Melbourne. I have to say I thoroughly enjoyed it and was left feeling very inspired and motivated to continue learning and bettering my craft. 

Below is a summary of what I learned from the talks I attended as well as from speaking to speakers whose talks I did not have a change to go to. 

### 1. Kubernetes - by Carter Morgan @_askcarter (Developer Evangelist at Google)

In this talk, Carter ran through how Kubernetes helped the process of scaling up or down the number of containers for your application very quickly and effectively, with many other additional features such as monitoring, security, etc. 

He emphasised the importance of having **both** the application and infrastructure to be great for the final production to be of great quality to customers. 

The high-level summary of the talk is as followed:

* **The app**:
	* Build a Docker container to run the app in its own isolated environment on a particular Virtual Machine in the container.
	* This ensures that the app will be able to run consistently across all machines
	* It's easy to spin up a container on your local machine to run the application. However, when you want multiple versions of the container, the process is not as simple. It becomes significantly more trouble when you have to scale up your project to many more versions than just a few. This is where Kubernetes comes in. 

* **The infrastructure**:
   * Kubernetes allows for the process of scaling up your application to be a lot easier and efficient. The additional stress of other factors to take care of such as security, monitoring, automation, etc. can be handled   
   * A few concepts to consider when running Kubernetes:
   		* Pod
   		* Label
   		* Service
   		* Deployment

* **The Wild**:
	* In production, things don't always work as we expect, so the takeaway message is to **Deploy with Care**
	* Build a pipeline:
		* Have the application working on your local environment first
		* Then stage it for testing on the pipeline
		* Then ship to production

### 2. Build a microservice in 30 minutes with JHipster and Docker - by Dennis Sharpe (CTO at Ippon)

Dennis went through how to build a microservice in 30 minutes with SpringBoot in the backend, and React in the front end using JHipster. In the past, JHipster only supported Angular, but now it's incorporated React as well and the final product should be released in a couple of weeks. 

Overall, the process he went through was:

1. Built the backend in SpringBoot using JHipster. This process pretty much just involved providing a few parameters in the command line prompts and JHipster just created a simple working backend with authentication and security included. 
2. Built a Docker image for the backend. 
3. Built the frontend in React using JHipster. The process was the same as for the backend. 
4. Built a Docker image for the frontend. 
5. My notes for this section are a bit fuzzy, but I believe at this stage, he ran a Docker container to get the full app working. I don't recall how he bridged the frontend to the backend, perhaps there was a way for JHipster to link them automatically for you. 

Overall, the takeaway I got for this talk was that JHipster could save you a lot of time setting up a basic end-to-end application. From there, you can customise the application however you like, but JHipster definitely can save you a couple of weeks of setting up a simple working end-to-end app. 

### 3. Bootiful Atomist - by Rod Johnson (creator of SpringBoot) and Josh Long (Spring advocate at Pivotal)

This was one of my favourite talks from the day, not merely because of the contents that were presented, but more because of the energy these two talented and passionate speakers brought to the room. I was very inspired after this talk to work harder to master my craft after seeing the way the two talked about code and life. 

Josh has a [blog]("http://joshlong.com/") that I'm now following. I would recommend you guys check it out to see what he's like as a person and a developer, and learn more about different computing topics. 

Josh started the presentation by quickly creating a SpringBoot application with very funny and interesting side comments along the way about code and stars and the universe.. and showed us some very cool ASCII arts he's created as well. 

Rod then jumped in when Josh started to get the app ready for deployment. He introduced a new tool called Atomist, which you could say is a new way of doing CI/CD. 

* Instead of using .yml files to define build rules, you can create "push rules" in JavaScript in Atomist. 

	* These push rules are expressed in terms of code, for example: 
	
	```
	whenPushSatisfies(condition)
	.itMeans("Ready for deployment")
	.setGoals(deploy)
	```
	* It's easy to define complex rules this way rather than write them in a .yml file (According to Rod, .yml is not the best medium to define complicated rules, and the whitespace errors or other syntax issues can be a real pain for developers)

* Atomist also provides ways of easily unit testing these rules. And as we know, unit tests are fundamental to code maintenance and code quality.

* Atomist also allows for collaboration between team members working on the same Github repo on Slack. 
	* One can create a specific channel for each Github repo
	* They can merge a pull request straight from Slack
	* Any changes to the pipeline will be displayed on the channel 

Overall, Atomist allows for a new way of doing CI/CD. You can still use your traditional tool such as BuildKite and use Atomist on top of it to allow for more customisations in ways that suit your application. 

### 4. Functional - Reactive (Core Java 8 - 11) - by Sven Ruppert @svenruppert from [vaadin](https://vaadin.com/)

Sven was another very interesting speaker whose talk I also enjoyed a lot. And it's not just because he sounds like Batman.. 

Sven presented the current state of where Java is at when it comes to being functional. Some of the things that Java have recently incorporated to make the language more functional were:

* Java 8 - Optional
* Java 8 - Stream

He introduced other concepts that a functional language should have and showed how long and tedious it could be when trying to use what Java currently offers to illustrate them. He then showed what Java could do to allow for these functional properties to be expressed in a readable way. Some of the concepts mentioned were:

* Functions
* Predicates
* Currying
* BiFunctional
* MatchCase
* CompletableFuture:
	* Used in a situation where you have to grab data from different places and perform computation on them. 
	* Instead of multithreading, this new class could allow for the collection of the data and computation to happen in one place. 

To fully understand what Sven is suggesting to fix some problems that Java currently has with being functional, please refer to his slides from the VoxxedDay website when they are up. 

### 5. Aggressive Web Apps - by Phil Nash @philnash from [twilio](www.twilio.com)

In this talk, Phil was very excited about the fact that all browsers have now supported **Service Worker** as of this week (except for Internet Explorer of course). A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction. He went through a demo to show us how to add a push notification and notification permission to a web app. 

The remainder of the talk was more about how it's detrimental to the web that most people are boycotting web push notifications. He argued that notifications can be useful, when they are timely, actionable and personal. People don't want all kinds of notifications, but the right notifcations can be of great use to people and businesses. 

Some of Phil's suggestions for creating a great user experience with web browser push notifications are: 

* Don't trigger permissions straight away, instead, wait for the user to perform an action that would triggers a potential push notification in the future to ask for permission. Otherwise, the user would just refuse permission straight away.
* Allow for users to opt out  
* And of course, make them timely, actionable and personal. 

### 6. Knit one, compute one - by Kris Howard @web_goddess

In the final talk of the conference, Kris delighted us all with her presentation on how knitting is very much like programming. The process one goes through is analogous to how a computer produces a program:

* Our brain is the CPU that takes in these knitting instructions
* The knitting instructions are the code 
* The knit stiches created by our hands are the binary code produced by a computer

She showed us a lot of super cool and nerdy knits that have been produced by customised knitting machines, ones where humans have built or programmed in certain features to automate some knitting tasks for them. Some of the knit patterns were of incredibly complicated patterns or have some very awesome visual effects. 

My summary does no justice to the actual talk that was given. 

### 7. After show talk with Daniel Chambers @danielchmbrs from [Readify](https://readify.net/) about Haskell and functional programming

After the talks finished, I had the chance to have a good chat to Daniel about Haskell and functional programming. I didn't get to go to his talk because I was also interested in another one that was running at the same time. 

I asked Daniel a few questions regarding functional programming languages such as Haskell. 

1. How it fits into cases where you have a very large enterprise application:

	* Haskell is probably not a suitable choice of language for a monolith, but would be perfectly fine for a microservcie. 
	* As with anything, choose the right tool for the job, and not just blindly go with one.
	
2. How well Haskell supports testing
	* Very well
	* Haskell is functional, therefore unit testing is very well supported
3. What IDE he uses 
	* Atoms with plug-ins for Haskell
	* There is a lack of well supported IDEs for Haskell at the moment
4. What the number one selling feature would be for functional programming 
	* Type safe - the compiler will not allow the code to compile if the type is not matching correctly
	* It allows for "fearless programming"

His slides provide a lot more useful information regarding functional programming and Haskell. I highly recommend that you check it out when it's available on the VoxxedDay website. 

-----

## CONCLUSION

In conclusion, I loved VoxxedDay. There was a wide range of topics ranging from machine learning, to web apps, to cloud infrastructre, to language specific talks. The venue was amazing and the food was exceptional. Most importantly, there was a diverse number of super knowledgable and passionate speakers who brought this contagious energy to the conference. I was left exhausted, but inspired and very motivated to continue my journey as an apprentice in this field.
