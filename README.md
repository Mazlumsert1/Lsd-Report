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

##### Implementation:
As any system, our system consists of a hardware and software platform. The software platform,       

#### Deploymemt
To see our **Deployment Chain and Strategy** visit the link:

[CD chain](https://github.com/bigstepdenmark/HackerNews/blob/master/cd-documentation.md)



### 1.2. Development process

### 1.3. Software architecture 

### 1.4. Software Design 

### 1.5 Software implementation 


## 2. Maintenance And SLA status 

### 2.1. Hand-over

### 2.2. Service-level agreement

### 2.3. Maintenance and reliability


## 3. Discussion

### 3.1 Technical discussion

### 3.2 Group work reflection & Lessons learned


## Conclusion


