---
layout: post
title:  "Software Factory"
date:   2021-02-21 18:06:00 +0800
categories: notes
---
## What is DevOps?
* **DevOps** is from **Development** and **Operations**.
* **Development** is the team delivering the software
   * This includes **planning**, **implementation**, **build** and **test**
* **Operations** is the team putting the delivered software into production, monitoring and making sure everything works fine
   * focusing on **deployment**, **operating** and **monitoring** 
* **DevOps** goal is to integrate these 2 process resulting to faster delivery which can end up to customer satisfaction
* **DevOps** is different for **Agile** but it blends each other
   * For your **Agile** to be successful you'll need **DevOps**, but to successfully achieve **DevOps** you might want to go for **Agile** methodolgy for your development

[!image](https://algorithmia.com/blog/wp-content/uploads/2019/09/CI_CD_pipeline.gif)

## Why DevOps?
Without DevOps, this will be common scenario:

[!image](https://www.metaltoad.com/sites/default/files/inline-images/22605665.jpg)

Operations blaming the developers not able to deliver quality software and developers blaming operations with misconfigurations.

In the current world where also software are the center for different businesses, a bug in production will not be able to wait and might result to great loss for the business.

The IT industry are in fast paced, most softwares are releasing every 2 weeks, hotfix within an hour, if your business cannot do this you will be out of the game before even releasing the next version or hotfix of your software :P

[!image](https://pbs.twimg.com/profile_images/1200389077243064322/ulM9c1t8.jpg)

Most companies are now investing a lot in their DevOps - and for them to be able to transform to DevOps, they need to create a **Software Factory**.

## What is software factory?
**Software** contains a set of logic coded into programs, procedures and routines - this is the product. Every product is manufactured, created or developed and this all happens in a **Factory**, in this you will need machines, a step by step process, quality controlled and packaging until you come up with a product that is ready to deliver. 

So, in short, **Software Factory** is defining how you want to deliver the software with the help of tooling and processes that makes the developers deliver faster without sacrificing the quality.

[!image](https://i.imgur.com/REPnV1u.gif)

**Software Factory** should include the following:
* *tools* - IDE, code repository, application builder
* *versioning and release management* - how will you version *(e.g. Semantic Versioning or SemVer)*, defining the process of releasing the major, minor, patch or hotfix
* *quality control* - testing (unit, integration, e2e etc..) of your application, static code analysis
* *packaging* - a product, to be able to be use, it needs to be package (you don't deliver a code, you need to deliver a software)
* *deployment* - somehow like logistics - you need to move it and bring it to your customer -- in this case, production.

Imagine a factory without any machines, a sewer without a sewing machine, a delivery guy without any vehicle - sounds slow right - to make it faster you need more people - and it will require more **$$$** which is opposite to the goal of **DevOps**. In Software Factory, these machines are equivalent to automations that are continouos, a cycle and this is where **Continouos Integration, Delivery and Deployment** will be needed.

## Continouos Integration
Building a software is not just done by 1 person, it can be a team of 2 or more, this people need to be aware of each other changes and make sure its not breaking each others codes.

[!image](https://thumbs.gfycat.com/IdioticInsignificantHapuku-max-1mb.gif)

**Continouos Integration** or simply **CI** is an automation that compiles, build, run test and package for every commit of your code. This happens with help of your *code repository* of automation tools like:

1. **Jenkins** - a very powerful automation tool - you'll almost can automate everything with this
2. **Gitlab CI** - a very good toold if you are using Gitlab as it is hight integrated with your repository
3. and there's a lot more in the  market, like **Travis**

**How will you achieved CI?**
1. Design how your pipeline will look like
   * Pipeline is a set of stages and each stages can have 1 or more jobs
   * The code you write will go through all the stages and execute the jobs sequentially based on how you define in your pipeline
   * Sample stages can be: `build`, `test`, `analysis` and etc.
2. Choose your tool 
   * check which and what fits you the best - most of it has the capability of basic stuff that you'll need
3. Implement your design
   * a machine can normally do one or more thing and you'll need to tell it what exactly you want it to do for you

## Continouos Delivery and Deployment
These are extension to your CI, if you want to take things further, then go for continouos delivery and deployment.

**Continouos Delivery** or i call it **CDel** involves the packaging and versioning of your software, and it should just be one click away to production.

[!image](https://miro.medium.com/max/1000/1*ifzvyLF6P-LhCmRE3zs8jQ@2x.gif)

While **Continouos Deployment** is one step further than **CDel** - this is removing the only manual step for your product to be in production - which is the `click`. Everything is automation - the only way you can stop your process if one your stage/job has failed.

[!image](https://clm-consulting.com/wp-content/uploads/2018/02/ci-1.png)

**If you achieve CI/CDel/CDep within your business, then you've got yourself a DevOps!**

## Conclusion
At the end of the day, all these things have benefits - i'll focus more on developer (as i am one of them), wouldn't it be nice that all I have to do is commit my changes and let the process tell me that I break something?

[!image](https://cdn.dribbble.com/users/1480650/screenshots/4739771/autodevops-dribbble-gif.gif)

**Even though, to maintain this process successfully, you need to do your part as a developer - number one is *to write unit test*, *fix code smells*, *give your feedback with process* and *try to find a way to improve it* :)**

## References
* https://www.youtube.com/watch?v=mBBgRdlC4sc 
* https://techbeacon.com/devops/devops-scale-how-build-your-software-factory 
* https://www.atlassian.com/continuous-delivery/continuous-integration 
* https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment 

*Pictures are not mine - see image addresses for original owners*





