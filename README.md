<h1 align="center"> Hackernews Exam Report </h1>

## Introduction
This report will contain an examination of the hackernews clone system, and a analysis where we dive into the thought process behind the development of system, how the group worked as a team and also get more technical. 
We will dive into crucial functinality the hackernews system consists of, the different requirements, the architecture, and how the maintenance process has been, and much more. 

Generely the report consists of:
+ **Requirements** 
+ **Architecture** 
+ **Design** 
+ **Development process**
+ **SLA(Service-level agreement) and Maintenance**  
+ **Discussion; technical and Group work**
+ **Conclusion** 

We have provided illustrations along the way, to make it more effortless for the reader.  

## 1. Requirements, architecture, design and process
This part of the report will consists of on the different requirements, the architecture we have choosen, the design behind the different components and the process it took to construct, the components and the architecture of the system.

### 1.1. System Requirements 
The system requirements has been assembled by analysing and diving into 2 different kind of resources, [Hackernews](https://news.ycombinator.com), and reading the description of hacker news by Helge, [Hackernews description](https://github.com/datsoftlyngby/soft2017fall-lsd-teaching-material/blob/master/assignments/01-HN%20Clone%20Task%20Description.ipynb ). 

#### Scope 
The scope of the system is making sure that we have all the requirements done and implemented, and also to make sure that it mimics some of the important functionalities of hackernews. To get an better idea of the scope of the system see our requirements below. To the mentioned functionallities, we will also provide a front-end.   

**Functional requirements:**
+ Users can publish a story
+ Users can comment a story
+ Users can reply a comment
+ Users can up-vote/down-vote a story
+ Users can read a story
+ Users can login
+ Guests can read stories
+ Guests can register
+ User has profile page
+ User can edit profile page
+ Rest-API service

**Non-Functional requirements:**
##### Usability: 
The system will be clone of hackernews, it will have a straightforward front-end, easy to use. 

Primarily when the user interacts with the website, the user should be able to see Stories, that has been posted that specific day where the newest post is at the top.    

The user should also be able to see comments to the selected story, if the comments are nested it should be in a understandable maner, and read through them effortlessly.   

##### Reliability:
According to our **Service Level Agreement**, [SLA](https://github.com/HakimiX/SLA) we are expecting 95% uptime for the overall system, that means that our system should be 95% operational. 

##### Performance:
The system is able to handle incomming stories even if the amount of stories it increases rapidly. 
We did have some problems with the server we got an **429 error code** therefor lots of data was lost, due to bad **team and time management**. The data we did receive, is working fine in our system and is responsiv.   

##### Supportability:
Everything will be documented as it now in this documentation, and also some of the documents mentioned above.  

### 1.2. Development process
##### Deploymemt

MVP Application: [http://165.227.136.184](http://165.227.136.184)

---

Because we are going to use the language PHP with the Laravel 5 framework, it was obvious to use  **Laravel Forge** tool for Continuous Deployment, and **Travis CI** for Continuous Integration.

**Travis CI:** With the help of Travis, we do continuous test for our application and trig our deployment service.   

**Laravel Forge:** The reason why we are using forge, is because forge is especially build for Laravel continuous deployment. 
You can think of Laravel Forge as, administration UI on top of in our case Digital Ocean. Where we not required to learn server administration skills, laravel forge automates deployment! It's important to note that laravel forge does not provide the servers, it's a UI that simplyfies the tasks. 

**Here are the steps on how laravel forge was set, and how it automates everything:**

+ Register and fill the form in [Laravel Forge form](https://forge.laravel.com/auth/register)
+ Connect to github
+ Reference your **service provider**, in our case Digitalocean, provide your **client id** and **API key** you can get them from Digitalocean. 
+ Choose **name**, **serversize** etc. In Laravel Forge.
+ Fill your github repo. 
+ Now the project your want deploy using Laravel Forge **git clone** that project so you have it locally. The same project from the previous step. 
+ Enable quick deploy.
+ Now change something in your project, to see the magic happen. 
+ Now, **git add**, **git commit**, & **git push**. 
+ You can now witness it has been deployed! Easy!

You could also deploy your changes manually. By doing an SSH to your server and run a git pull. Or just click **deploy now** button.       
 
**Envoyer:** Envoyer is a **zero-down-time deployer** for Laravel, generely for PHP. Envoyer gives os additional control over our deployments such as, **zero downtime during deployments**, provides **monitoring**, **health checks** and very **easy rollbacks** if your changes to your application goes wrong, or if you found some bug. 

In our hackernews system, we have combined **Laravel Forge** and **Envoyer**. We use **Laravel Forge** to manage our server, and using **Envoyer** to achieve **zero-downtime deployments**.     

**The CD chain steps:**

 - Push to master branch on Github.
 - Travis CI trigs the push and runs the tests.
 - Then Forge is trigged by Travis CI and deploy the changes to the remote server.

 ---



![CD](https://github.com/bigstepdenmark/HackerNews/blob/master/systemmodels/CDflow.png)



### 1.3. Software architecture 
We have implemented a **three-layered architecture**, the reason for this decission was simple it was an arcitecture we in team was familiare with. 
The three layers are **Presentation layer**, **Business Logic layer** and **Data Access layer**. 

![Architecture](https://github.com/HakimiX/Documentation/blob/master/Models/Subsystem.jpg)

The design is separated into different areas of concern, which minimizes the complexity. The user interface, business processing and data access all represent different areas of concern. Within each area, the components focus on that specific area, and does not incorporate code from other areas of concern. For example, the front-end UI processing component does not include code that directly accesses the database, but instead makes use of data access component or business components to retrieve data.

But these three layers, are handled by a **third party tier**, meaning a **remote server** which in our case is **Digital Ocean**. 

#### Laravel MVC
Laravel makes use of the **MVC architecture pattern**, which divides our application into 3 parts:

+ **Model**, This part of the application handles the user requests and retrives data. It is also here we have the database calls.    
+ **View**, Render pages, this where we output API data.  
+ **Controller**, Handles user request, and controlls the cooperation between Model and view. 

There are lot of advantages to MVC pattern **low coupling** between the three main components, **easier to unit test**, more **organized code** etc.  

![MVC](https://github.com/HakimiX/Documentation/blob/master/Models/MVCModel.jpg)

1. A request is made, when a user enters a URL associated with the application
2. A Route associated with that URL maps that URL to a Controller action
3. That Controller action leverages the necessary Models to retrieve information from the database, and the passes that data off to a View
4. And that View renders the final page

### 1.4. Software Design 

#### Front-end
The **front-end** is creatd using **Vue**, this was not planned from the start its something we planned later in the process. Using **Vue** to make api calls to our Rest-Api to get the different kind of data. We have tried keep it as simple as possible, so the code is easy to understand.    

#### Back-end
The **back-end** is created using **Laravel 5.5** where we have kept the classes and methods small and simple as possible. We have tried follow the concept **low coupling** and **high cohesion** to get better quality code, also make it better for changes to come, and also to unit test.      

#### Database
This is how we designed the database to start with, and also this is the way it is designed, so our plans have worked. The database is also normalized folowing the three normal forms **1NF, 2NF and 3NF**.  

**The Entity diagram**:  
![Database](https://camo.githubusercontent.com/ce02a2e2d3b1cd08ea1ef23020c5b27d1cb57116/68747470733a2f2f7777772e64726f70626f782e636f6d2f732f346c7767796b646f3534736d6f70752f45522e706e673f7261773d31)


### 1.5 Software implementation 
As most systems, our system consists of a hardware and software platform. 
We have created a small environment in Docker, first installing docker toolbox and we have created a container which consists of MariaDB database.   
![Docker Example](https://github.com/Mazlumsert1/Lsd-Report/blob/master/images/DockerCommand.JPG)

The software platform also consists, of Laravel which is a PHP framework, which interacts with the database. We also have front-end that interacts with the API. The front-end is build using Vue a Javascript framework. 

The hardware aspect in our system, consists of a remote server which is handled by third party company, in our case that company is DigitalOcean.    

## 2. Maintenance And SLA status 

### 2.1. Hand-over
The focus is on technical documentation. The purpose of a technical document is to show the development process. It includes information about the initial software requirements, system overview, technical requirements, system configuration, setup and dependencies. 

The technical documentation should allow other developers to operate our systems, report issues and provide feedback. Our technical document provides an overview of the Hacker news clone system requirements and a lead-in to the system architecture, components, dataflow and workflow. In addition, we have a section about Issue submission and system access. [Technical Documentation](https://github.com/HakimiX/Documentation)

It was our responsibility to operate Group J’s system. Their technical document was missing information about system architecture, proper description of data flow process and a detailed issue submission. Generally, their technical document was not very detailed and we didn’t feel well equipped to maintain their system. For example, we got a HTTP Status 404 – Not Found Error whenever we tried to access Group J’s backend through the browser. [Group J's backend](http://46.101.111.112:8080/lsd-backend/)

![Text](https://github.com/HakimiX/part2/blob/master/Models/GroupJBackend.jpg)

### 2.2. Service-level agreement
he service-level agreement is a contract that defines the agreement between a customer and service provider. It specifies what the customer will receive and clarifies what performance standards the service provider is obligated to meet. Our service-level agreement contains a description of what the contract includes and service agreements. The following service parameters were the responsibility of the service provider:

* __Uptime__ – applies to servers, cloud services or other parts of the system that are vital. Guaranteed at least 95% uptime. 

* __CPU Usage__ – applies to amount of actively used CPU, as percentage of total available CPU. Amount of used CPU time (CPU used, CPU wait etc.). Alert if CPU is above 70% for 5 min. 

* __Group A support response time__ – applies to how long it takes Group A to respond when we raise a request for support. Respond to critical problems within 24 hours. 

We did not have any disagreements about the service-level agreement. Our service-level agreement was written in a spirit of partnership. We were sure that Group A would do everything possible to rectify every issue. 

The service-level agreement was supposed to contain information about system monitoring using Grafana/Prometheus. Unfortunately, we were not able to setup Grafana/Prometheus properly. Group A could not comply with our service-level agreement, because we were not able to configure monitoring. Our monitoring problems will be explained in the following section.

## Monitoring

Monitoring is crucial for DevOps (Development Operations). It makes it possible to see what is happening in your system at any given time. It gives you an overview of system resources currently used such as CPU, Memory, storage etc. The main purpose of monitoring is detecting problems, notifying possible issues and preventing them. 

As mentioned earlier, we were not able to setup monitoring for our system. We made use of Docker and were able to install Grafana and Prometheus. They were both exposed on their ports 3000 and 9090. 

![Text](https://github.com/HakimiX/part2/blob/master/Models/docker.jpg)

Then we configured the Prometheus.yml file to point at 165.227.136.184 which is our Hacker News application. We also configured the scrape target to be Prometheus at localhost:9090. 

![Text](https://github.com/HakimiX/part2/blob/master/Models/ymlfile.jpg)

We installed the latest node exporter from [Prometheus](https://prometheus.io/download/#node_exporter), and exposed it on port 9100. Everything looked correct and we could see that everything was running on their respective ports. 

![Text](https://github.com/HakimiX/part2/blob/master/Models/netstat.jpg)

However, when we navigated to Prometheus at `165.227.136.184:9090/targets` we encountered node exporter errors such as `GET http://165.227.136.184:9100/metrics: dial tcp` and `165.227.136.184:9100: i/o timeout`. The Prometheus endpoint worked as intended besides the node exporter errors. 

![Text](https://github.com/HakimiX/part2/blob/master/Models/prometheus.jpg)

Grafana also worked fine, and we were able to get basic HTTP metrics by connecting Grafana to Prometheus. Since we were not able to expose node exporter metrics, we could not configure Grafana to show metrics such as, uptime, storage, CPU, memory etc. 

![Text](https://github.com/HakimiX/part2/blob/master/Models/grafana.jpg)

We could not understand what the problem was, because we created new droplets on digital ocean to test Grafana/Prometheus and it worked fine. Node exporter metrics were exposed on port 9100 and we were able to show CPU, memory and storage metrics on Grafana. We applied the same steps to our Hacker News application, but it didn’t work because of the earlier mentioned node exporter errors. We tried everything possible to fix this, but we were not successful. Below is the metrics we needed: 

![Text](https://github.com/HakimiX/part2/blob/master/Models/curl.jpg)

We have been very frustrated by this problem and are disappointed that we could not set up monitoring. Monitoring has been crucial for the service-level agreement, maintenance and generally development operations. 

### 2.3. Maintenance and reliability


## 3. Discussion

### 3.1 Technical discussion

### 3.2 Group work reflection & Lessons learned


## Conclusion


