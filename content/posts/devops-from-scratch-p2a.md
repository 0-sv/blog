---
title: "DevOps From Scratch Part 2a"
date: 2020-04-08T18:35:27+07:00
draft: true
toc: false
images:
tags: 
  - ansible
  - devops
---
Today I'm going to take a small tangent into software. Let's recap what we came to do here. We're going to take the abstract concept of "Flow" and find out a way to "make it happen" in the implementation. Like mentioned in the previous article, the main value of Flow is shortening the development lead time. We shorten the development lead time by following the DevOps ideal. Don't listen to me, hear it from the experts:

> In the DevOps ideal, developers receive fast, constant feedback on their work, which enables them to quickly and independently implement, integrate, and validate their code, and have the code deployed into the production environment (either by deploying the code themselves or by others). 
> 
> (DevOps Handbook, part I)

> We achieve this by continually checking small code changes into our version control repository, performing automated and exploratory testing against it, and deploying it into production. This enables us to have a high degree of confidence that our changes will operate as designed in production and that any problems can be quickly detected and corrected. 
> 
> (DevOps Handbook, part I)

> This is most easily achieved when we have architecture that is modular, well encapsulated, and loosely-coupled so that small teams are able to work with high degrees of autonomy, with failures being small and contained, and without causing global disruptions. 
> 
> (DevOps Handbook, part I)

I think the last quote speaks volumes. I recently watched the GOTO 2019 - Modern Continuous Delivery talk by Ken Mugrage. He talks about his company (or the company he works for, whichever one it is) called Thoughtworks. Customers would come up to them, asking to build their CI/CD pipeline. Of course, he says, "I'm not gonna do it. It's not gonna matter much if your software is garbage in the first place." You can form your own opinion by watching the talk and we'll discuss it after you come back.

[![IMAGE ken-mugrage](http://img.youtube.com/vi/wjF4X9t3FMk/0.jpg)](http://www.youtube.com/watch?v=wjF4X9t3FMk?t=750 "GOTO 2019 - Modern Continuous Delivery")

You're back already? I agree, there are better things to do on a free day than watching Yet Another boring talk about software (these are your thoughts, not mine).

It makes me wonder... Weren't we supposed to do the whole DevOps-thingy do create better software? I think this is a common misconception when we talk about Flow. We're just gonna have to leave the garbage-in-garbage-out to the side while we shorten development lead time? Yes, it looks like the we're gonna start there. 

Like we already said, hiring a bunch of DevOps engineers is not gonna magically solve your organizational problems. Now we know -- a little bit, of course -- more about why (there are other factors involved, we will come back to this topic in a bit).

The whole point of this dialogue is to realize... it's not that easy. You can't buy DevOps in a store, or buy AWS DevOps, or whatever. 

It's not impossible either; but it's gonna take some effort. In other words:

> In software, when something is painful, the way to reduce the pain is to do it more frequently, not less. So instead of integrating infrequently, we should integrate frequently; in fact, we should integrate as a result of every single change to the system. 
> 
> (Modern Continuous Delivery, p. 24)

If you've paid attention, you'll notice that this is actually the first time we're taking the verb: "to integrate" into a dialogue. Obviously, when we talk about "integration" here, we're specifically referring to another way of saying: "continually checking small code changes into our version control repository, performing automated and exploratory testing against it."



> Deploying software ultimately involves three things: 
> - Provisioning and managing the environment in which your application will run (hardware configuration, software, infrastructure, and external services).
> - Installing the correct version of your application into it. 
> - Configuring your application, including any data or state it requires. 
> 
> (Modern Continuous Delivery, p. 25)



