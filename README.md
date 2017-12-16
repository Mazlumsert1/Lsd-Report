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
To see our **Deployment Chain and Strategy** visit the link:

[CD chain](https://github.com/bigstepdenmark/HackerNews/blob/master/cd-documentation.md)

### 1.3. Software architecture 
We have implemented a **three-layered architecture**, the reason for this decission was simple it was an arcitecture we in team was familiare with. 
The three layers are **Presentation layer**, **Business Logic layer** and **Data Access layer**. 

![Architecture](https://github.com/Mazlumsert1/Lsd-Report/blob/master/images/Architecture.jpg)

The design is separated into different areas of concern, which minimizes the complexity. The user interface, business processing and data access all represent different areas of concern. Within each area, the components focus on that specific area, and does not incorporate code from other areas of concern. For example, the front-end UI processing component does not include code that directly accesses the database, but instead makes use of data access component or business components to retrieve data.

But these three layers, are handled by a **third party tier**, meaning a **remote server** which in our case is **Digital Ocean**. 

#### Laravel MVC
Laravel makes use of the **MVC architecture pattern**, which divides our application into 3 parts:

+ **Model**, This part of the application handles the user requests and retrives data. It is also here we have the database calls.    
+ **View**, Render pages, this where we output API data.  
+ **Controller**, Handles user request, and controlls the cooperation between Model and view. 

There are lot of advantages to MVC pattern **low coupling** between the three main components, **easier to unit test**, more **organized code** etc.  

![MVC](https://github.com/Mazlumsert1/Lsd-Report/blob/master/images/MVC_Model.jpg)

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
![Database](https://github.com/Mazlumsert1/Lsd-Report/blob/master/images/database.png)


### 1.5 Software implementation 
As most systems, our system consists of a hardware and software platform. 
We have created a small environment in Docker, first installing docker toolbox and we have created a container which consists of MariaDB database.   
![Docker Example](https://github.com/Mazlumsert1/Lsd-Report/blob/master/images/DockerCommand.JPG)

The software platform also consists, of Laravel which is a PHP framework, which interacts with the database. We also have front-end that interacts with the API. The front-end is build using Vue a Javascript framework. 

The hardware aspect in our system, consists of a remote server which is handled by third party company, in our case that company is DigitalOcean.    

## 2. Maintenance And SLA status 

### 2.1. Hand-over
The focus is on technical documentation. The purpose of a technical document is to show the development process. It includes information about the initial software requirements, system overview, technical requirements, system configuration, setup and dependencies. 

The technical documentation should allow other developers to operate our systems, report issues and provide feedback. Our technical document provides an overview of the Hacker news clone system requirements and a lead-in to the system architecture, components, dataflow and workflow. In addition, we have a section about Issue submission and system access.

It was our responsibility to operate Group J’s system. Their technical document was missing information about system architecture, proper description of data flow process and a detailed issue submission. Generally, their technical document was not very detailed and we didn’t feel well equipped to maintain their system. For example, we got a HTTP Status 404 – Not Found Error whenever we tried to access Group J’s backend through the browser. 

### 2.2. Service-level agreement

### 2.3. Maintenance and reliability


## 3. Discussion

### 3.1 Technical discussion

### 3.2 Group work reflection & Lessons learned


## Conclusion


