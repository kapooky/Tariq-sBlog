---
title: Projects 
permalink: /projects/
layout: page
excerpt: Hello world
comments: false
---
Here is a short list of some projects I've done. Please note that I didn't bother to add my university assignments, they are all scattered in my [github repo](https://github.com/kapooky?tab=repositories)

I have done some advanced solution architect kind of [demos](https://github.com/acantril/learn-cantrill-io-labs) . I love working on these demos but they probably won't get me a job. Employers who are looking for these kind of skills always assume that you need 7+ on the job experience. Annoying. 

Here are my own projects: 

### [League and Tournement Manager Application](https://github.com/kapooky/MultiPlayer-ELO-GUI-Ranking-System)
 My first project! I've come long a long way since then. 
 
Please note that this project is old, and it's not relevant to check out if you're looking for my cloud skills. 


I recall showcasing this project at an interview. The interview didn't seem interested and spat that, "nobody cares about software projects you've done in your basement". Needless to say, It took every bit of mental fortitude to not get up and leave. 

Looking back, the wording of his comment could have been better, but it did have merit: I wasn't doing any unit/integration testing, the code was bad, no documentation. These were some of the hallmarks of a professional software, and I here I was, not even practicing good documentation in my code. 

His comment did partly influence my perspective on projects. 



### Azma.io version 1 
 ***I got my feet wet in AWS with this project!***
 
 Tech used: Javascript, Nodejs, Webpack, Dealing with Binary readers/writers, Heavy emphasis on websocket technology, client-server architecture, Typescript. NGINX reverse proxies, Let's encrpt, Docker
 AWS services: Cloud front, S3, EC2, Code pipeline, 
 
*code is based upon the work of others, namely this and this. I did however modify parts of the code to augment/enhance it.* 

Azma.io was supposed to be a clone of Agar.io, a smash hit browser based game, but I lost interest in the project. I decided to revive this project by migrating it to a cloud enviorment. Afterall, I had the option to migrate some sample generic static wordpress site to the cloud or my dead project. I chose my dead project. 

There are 2 parts of this game: The static content and the stateful central gameserver. The static content is hosted in an s3 bucket, and uses cloudfrpmt as it's CDN network. The Central game server runs inside docker container within an EC2 instance(yeah, yeah I know it's inefficient, I should have used Fargate). 

Because the websocket library that the gameserver uses does not support SSL encryption, I had to place the gameserver behind an internet facing NGINX reverse proxy WITH SSL termination. This way, the connection between the client and the NGINX reverse proxy is in HTTPS, while the backend connection is in regular HTTP. 

 
Oh and I configured a pipeline for the static content.  Whenever I would commit to the github repository, github sends a trigger to AWS codepipeline to kickstart the build. Once finished, the artifacts are deployed to S3. 

I wanted to configure a pipeline for the central game server, but it would prove to be challenging as it's a stateful server. And any interruption to the server would impact players leading to a terrible experience. And no, a gameserver can't be made stateless. With a traditional webserver, you can push stateful session state of each client to some database, making the web-tier completely stateless. The same cannot be done with a gameserver as it's constantly needs to be running. 






 








 

  
  
  
  
  
  
  
 
 
 




