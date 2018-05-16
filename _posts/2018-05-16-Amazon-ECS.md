* ECS: Elastic Container Service
	* Is a logical grouping of EC2 machines/instances
	* Is a mere configuration for an efficient use and management of your EC2 instances resources
	* Uses Docker to instantiate containers/instances/virtual machines on these (EC2) hosts
	* To add/register EC2 instances --> all you need is Amazon ECS Container Agent running on your EC2 instance/machine
	
	**Amazon ECS Container Agent**
	
	* The container agent running on each instance within an Amazon ECS cluster sends information about the instance's current running tasks and resource utilization to Amazon ECS
	* It can start and stop tasks whenever it receives a request from Amazon ECS

### What does ECS let you do?

* Launch & stop container-based applications with simple API calls
* Get state of your cluster from a centralized service
* Give access to many familiar Amazon EC2 features
* Schedule placement of containers across your cluster --> autoscaling group

### Containers and Images

* To deploy applications on Amazon ECS, your application components must be architectured to run in containers
* Container images are stored in a **registry** from which they can be downloaded and run on your cluster

### Task Definitions

* To prepare your application to run on Amazon ECS, you create a task definition:
	* Text file - in JSON format
	* Describes one or more containers (max 10) that form your application
	* Is a blueprint for your application
	* Some parameters:
		* Which launch type
		* Which ports 
		* What data volumes

### Tasks and Scheduling

* **Task**:
	* is the instantiation of a task definition within a cluster

* You can specify the number of tasks to run on your cluster after creating a task definition for your application

* **Scheduler**:
	* Place tasks in your cluster
	* There are different scheduling options available - for example, you can define a **service** that runs and maintains a specified number of tasks simultaneously

* **Clusters**:
	* When you run tasks using Amazon ECS, you place them on a cluster, which is a logical grouping of resources
	* Launch type:
		* **Fargate**: Amazon ECS manages your cluster resources
		* **EC2**: you manage your group of container instances
