---
title: "DevOps From Scratch"
date: 2020-04-07T12:10:20+07:00
draft: false
---
When hiring for DevOps Engineers, it's generally suggested that hiring one or more DevOps Engineers will not change the organizational blueprint. Meaning, hiring DevOps Engineers will not get all the alleged benefits described by high performing organizations like Netflix or in the DevOps Handbook.

I think that's partially true, however, we can make the first step in the right direction. Specifically, we can start with Flow. 

> Flow accelerates the delivery of work from Development to Operations to our customers. (DevOps Handbook, part I introduction)

What I want to do in this article series is reason about the theory and principles of Flow, then find out how that would look like in a concrete implementation. I'm trying to bridge the gap between all the marketing lingo on the one hand, and the groundworks of excellent engineers on the other, to make the underpinnings accessible to all. 

I think one good way to do that would be to use general-purpose tools so we can think about the design instead of pulling solutions off-the-shelve. Then we can discover on our own what the best implementation would be for an organization.

Furthermore, it's supposed to be the stepping stone to the principle of Feedback, after which we can make the step to Continual Learning and Experimentation, coming full circle with the Three Ways of Flow, Feedback, and Continual Learning and Experimentation.

# Continuous integration

We start with continuous integration ("CI"). "Doing CI" can be explained as applying Agile principles to infrastructure as opposed to application code. We can also define CI by its underpinning, the Lean Manufacturing principles, as a technology value stream. 

> In DevOps, we typically define our technology value stream as the process required to convert a business hypothesis into a technology-enabled service that delivers value to the customer. (DevOps Handbook, part I)

We recognize this concept by its Development variant: Scrum, user stories, Kanban, feature specifications, etc., implemented as the application or service being built. More importantly, the application will only be producing value once it's running in production.

> Because value is created only when our services are running in production, we must ensure that we are not only delivering fast flow, but that our deployments can also be performed without causing chaos and disruptions such as service outages, service impairments, or security or compliance failures. (DevOps Handbook, part I)

This subset of the technology value stream is known as the "deployment lead time" which can be described as the focus of DevOps.

> This value stream begins when any engineer in our value stream (which includes Development, QA, IT Operations, and Infosec) checks a change into version control and ends when that change is successfully running in production, providing value to the customer and generating useful feedback and telemetry. (DevOps Handbook, part I)

> In contrast, the second phase of work, which includes Testing and Operations, is akin to Lean Manufacturing. It requires creativity and expertise, and strives to be predictable and mechanistic, with the goal of achieving work outputs with minimized variability (e.g., short and predictable lead times, near zero defects). (DevOps Handbook, part I)

There is not one correct way to shorten the deployment lead time. As long as it shortens from whatever timeframe it is now -- allegedly months or quarters for some organizations -- to under 30 minutes.

Concretely, I think that the best option right now is to use and collaborate on open-source tools to create the most optimal solution for the organization at hand. I have my own set of tools that I prefer and I'd like to demonstrate why, of course with respect to other solutions that are also possible. 

We're going to limit the scope to Kubernetes and AWS. So why would we use Kubernetes and AWS, specifically in that combination? First of all, they are de facto industry standard platforms. Kubernetes is like an operating system on steroids. As a standard, it provides a common interface for networking, security, storage, etc. 

Kubernetes needs an environment to run in, and that's where we use AWS. AWS has provided the community with interfaces to their platform through an API and development SDKs. Consequently, in addition to AWS having market leader status, there are loads of useful tools to communicate with the platform. Combine the extensibility of these two tools, and you have an environment that's reliable, consistent, scalable, cost-effective, well-maintained, secure and performant, among other things.

Now, we only need two more tools to glue Kubernetes and AWS together. The first one is Terraform, which we can use to provision the environment Kubernetes needs to run in by using AWS resources. Secondly, we use Ansible to provide configuration management for the provisioned machines so Kubernetes has all the resources it needs. 

All the additional tools we need have an interface to Ansible, either through the front through Ansible Modules or through the back by tools that call Ansible for build, deploy and test steps, such as Make and Travis CI.

In the next article, we'll build a deployment pipeline with CI/CD using Ansible. We'll use that pipeline to deploy into Kubernetes. Additionally, we'll describe our environment as code in Terraform. When we're done with that, we can start building on top of Kubernetes and discover topics like Ingress, logging, monitoring, application lifecycle management, networking, storage, security, among other things. 

All the code will be open-source on Github, so you can replicate the code if you have a small organization and would like to start cost-effectively with Kubernetes and AWS. In this article series, we'll be going through the implementation step-by-step, so you'll have the understanding to build something on your own.