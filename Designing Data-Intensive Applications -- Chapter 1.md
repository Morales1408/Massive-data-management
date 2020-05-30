# Chapter N.1

### 1. _Name three of the most important concerns in more software systems in general. Describe them._
+ Reliability: 
  The system should continue to work correctly even in the face of adversity (hardware or software faults, and even human errors)
+ Scalability:
  As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with that growth
+ Maintainability:
  Over time, many different people will work on the system (engineering and operations, both maintaining current behavior and adapting the system to new use cases), and they should all be able to work on it productively

### 2. _Imagine I developed a software and I claimed it to be real Reliable, what characteristics does it need to have so we can confirm that? What does it need to do?_
- It needs to be capable of perform that is expected for the user.
- It should be able to tolerate unexpected usage or user mistakes
- It should have a good enough performance for the required use case regardless the data volume 
- The system should prevent any unauthorized acces and abuse. It needs to be safe.

### 3. _If we are talking about a resilent system, is there a difference between a "fault" an a "failure"? if so, explain it._
Yes, there are not the same. A fault is usually defined as one component of the system deviating from its spec, whereas failure is when the system as a whole stops providing the required service to the user. 

### 4. _While designing our applications, to what kind of errors do we need to put more atention on?_
To the human ones, actually, studies have shown that configuration errors by operations were the leading cause of outages, whereas hardware faults played a rol in only 10-25% of outages.

### 5. _What is scalability and why is it important while designing a system?_
Scalability  is  the  term  we  use  to  describe  a  system’s  ability  to  cope  with  increased load. It is important because even thogh our system works correctly nowadas it doesn't mean it will always do in case that, let's say, it has grown from 10 concurrent users to 10,000. While designing a system we need to be aware that it might evolve and maybe it will need to hold thousands operations besides that the ones it holds today. We need to think in the future as well so it can still be reliable. 

### 6. _What kind of statistical metric should I follow if I am keen on knowing the "typical" response time and which one is not a good idea to follow for the same case?_  
The mean is not a very good metric because it doesn't tell you how many users actually experienced delay.
Usually it is better to use percentiles. If you take your list of responde times and sort it from fastes to slowest, then the median is the halfway point: for example, if your median responde time is 200 ms, that means half your requests return in less than 200 ms, and half your requests take longer than that. 

![](Fotos%20monfo/librojuan.png)

### 7. _What is the difference between Scalling up and Scalling out?_
Scalling up, or vertical scalling, could be explained as moving to a more powerful machine, while scalling out (or horizontal scalling) is distribuiting the loead across multiple smalled machines.

### 8. _Name one advantage of the elastic system and one of the scaled-manually one. Which one is better?_
Elastic systems can automatically add computing resource when they detec a load increase, whereas other scalled-manually ones are simpler and may have fewer operational advantages.
There is not a general answer for the second part of the questions, it really depends a lot on your type of program or service. 

### 9. _Mention some of the typical reponsibilities of a good operation team_
+ Monitoring the health of the system and quickly restoring service if goes into a bad state
+ Tracking down the cause of problems, such as system failures or degraded performance
+ Keeping software and platforms up to date, including security patches
+ Keeping tabs on how different systems affect each other, so that a problematic change can be avoided before it causes damage
+ Anticiping future problems and solving them before they occur
+ Establishing good practices and tools for deployment, configuration management, and more
+ Performing complext maintenance tasks, such as moving an application from one platform to another
+ Maintaining the security of the system as configuration changes are made
+ Defining processes that make operations predictable and help keep the production environment stable
+ Preserving the organization's knowledge about the system, even as individual people come and go



### 10. _What is abstraction good for? explain it_ 
Abstraction is one of the best tools we have for removing accidental complexity . A good abstraction can hide a great deal of implementation detail behind a clean, simple-to-understand- face.





