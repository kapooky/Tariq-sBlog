---
layout: post
title: First impressions with Jenkins
date: 2020-11-26 20:55 +0700
---

If you know anything about me, you know that I prefer staying inside the confines of AWS. Sometimes, I may venture out of my comfort zone, like how I dived into Terraform. But for the most part, my strongest skillset would be working inside AWS. But for the sake of broadening my skillset, I figured I would try out Jenkins. 

Upon firing up Jenkins from inside a docker container, being greeted with the iconic jenkins dashboard, I commenced my dive into Jenkins. Here are my findings: 

- he Jenkins doesn't come out of the box with basic plugins like Git, Docker integration. Things I previously took for granted now had to be manually installed. Annoying. 

- The user Interface is outdated and clunky. It's not beginner friendly either. 

- When I discovered I had to write in Groovy to write Jenkins scripts, I immediately barfed(figuratively). Java was my favorite progamming language at one point, but I realized it's verbosity, and to be perfectly honest, I'm not interested in learning it's derivative just to write ci script.  Rather than using Groovy, they should have met developers where they were at, which is in Typescript/Python land. 

I decided to ditch Jenkins halfway into the tutorial that I was following.Perhaps I didn't dive deep enough to find Jenkin's charm, but it's not neccesary in 2020. In today's day and age, modern ci tools like Gitlab-CI , CircleCI to name a few are the future of CI. They are easier, more stable, and integrate much better with modern microservice and cloud native tech stacks. It makes no sense to learn Jenkins when these tools exist.  
 



