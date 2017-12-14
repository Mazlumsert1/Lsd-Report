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
These are also the userstories we have implemented, still missing some of them. More is to come.

+ Users can publish a story
+ Users can comment a story
+ Users can reply a comment
+ Users can up-vote/down-vote a story
+ Users can read a story
+ Users can login
+ Guests can read stories
+ Guests can register
+ Rest-API Service

#### Tasks 
Since we are using **Laravel PHP framework**, it was pretty obvious for us using **Laravel Forge** for **Continuous Deployment** since it is build for laravel, and **Travis** for **Continuous Integration**. The steps on how we have accomplished this is shown in the picture below:   

![Visualisation of CD flow](https://raw.githubusercontent.com/bigstepdenmark/HackerNews/master/systemmodels/CDflow.png)

The CD chain steps:

+ Push to master branch on Github.
+ Travis CI trigs the push and runs the tests.
+ Then Forge is trigged by Travis CI and deploy the changes to the remote server.

You can think of Laravel Forge as, administration UI on top of Digital Ocean. Where we not required to learn server administration skills, laravel forge automates deployment! in that way we can spend more time on our code instead of devops.   

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


