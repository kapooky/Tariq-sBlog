---
title: Projects 
permalink: /projects/
layout: page
excerpt: Hello world
comments: false
---
Here is a short list of some projects I have done. Please note that I ommited some projects and university assignments for brevity. Check my [github](https://github.com/kapooky?tab=repositories) for the full scoop. 

### Websocket Game App Migration to the Cloud 
 ***I got my feet wet in AWS with this project!***
 
 Tech used: Javascript, Nodejs, Webpack, Dealing with Binary readers/writers, Heavy emphasis on websocket technology, client-server architecture, Typescript. NGINX reverse proxies, Let's encrypt, Docker.
 
 AWS services: Cloud front, S3, EC2, Code pipeline, Route 53 
 
*Original Code is based upon the work of others, namely [this](https://github.com/Luka967/Cigar) and [this](https://github.com/Luka967/Cigar). I did however modify parts of the code to augment/enhance it migrated it to a cloud enviorment. .* 
##### Background context

Azma.io was supposed to be a clone of Agar.io, a smash hit browser based game, but I lost interest in the project. I decided to revive this project by migrating it into a cloud enviorment for learning purposes.  

There are 2 parts to this project: The static content and the stateful central gameserver. The static content is hosted in an S3 bucket, and uses Cloudfront as it's CDN network. The central game server runs inside a Docker container within an EC2 instance. 

Because the websocket library the gameserver uses does not support SSL encryption, I had to place the gameserver behind an internet facing NGINX reverse proxy WITH SSL termination. This way, the connection between the client and the NGINX reverse proxy is in HTTPS, while the backend connection is in regular HTTP. 
 
 
<figure>
<img src="diagram1.png" alt="installing nginx in ubuntu">
<figcaption>Diagram of the backend architecture </figcaption>
</figure>


 I also configured a CI/CD pipeline for the static content.  When I commit to the Production branch in the Github repository, Github sends a trigger to AWS Codepipeline to kickstart the build. Once finished, the artifacts are deployed to S3, and then served to clients by Cloudfront. [S3 Object Versioning](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/UpdatingExistingObjects.html) is used for better Cloudfront caching. 

I wanted to configure a pipeline for the central game server, but it would prove to be challenging as it's a stateful server. And any interruption to the server would impact players leading to a terrible experience. And no, a gameserver can't be made stateless. With a traditional webserver, because each client session is indpendent from other client sessions, you can therefore push out each session to some database, making the web-tier completely stateless. The same cannot be done with a gameserver as each client session(location,player attributes) needs to interact with other client sessions in order for the game to run. 


###### Conclusion  

Because this was my first project inside AWS, I wasn't too focused about doing things perfectly. It would have taken too long. Similar to an agile enterprise, I was interesting in rolling out a product to market quickly, and then iterating on it later. 














 








 

  
  
  
  
  
  
  
 
 
 




