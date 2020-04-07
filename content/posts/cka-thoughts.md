---
title: "Thoughts On The CNCF CKA Exam After Passing With 93%"
date: 2020-04-05T15:45:25+07:00
draft: false
tags: 
  - cka
  - kubernetes
  - cncf
  - cv
---
Last month I passed the CNCF CKA exam. I've been postponing the exam date for the better part of the year, assuming that it would be a very difficult exam. From what I've read, it used to be a difficult exam up until they broke the exam into two parts: CKA and CKAD. This happened around two years ago. 

The CKA is supposed to be the more difficult one of the two exams. [I've written a guide on how to study for the CKA]({{< ref "/posts/yet-another-cka-study-guide.md" >}}). Yet that's not what I experienced, and I'd like to tell you why. 

## What Is Going To Be On The Test

First of all, there's the skill of test taking. I remember during university studying law that some of my peers would be able to score high grades easily by only reading the summaries, while I was stuck in the library 24/7 for weeks before the exams. Little did I know, they aren't so much excellent lawyers as they are excellent test takers. 

[There's a good introductory book on test taking by Cal Newport](https://www.goodreads.com/book/show/253203.How_to_Become_a_Straight_A_Student). It's introductory because I think this only discusses the idea of how to learn. But the most important part is more about intuition of what's going to be on the test. Ideally, at one point you have a lightbulb flashing like the moment you master a new programming concept, to understand that only 5% of the course content is going to be on a final test. Perhaps one of the reasons is that creating a comprehensive test for a test (at least in university) is an administrative burden.

When you see this pattern, that all tests are created in equal fashion, you're Neo in the Matrix. Now you know what's going to be on the test, expect to have a score of at least 70% dedicated to knowing what to study. If you have a low aptitude for test taking and inherent lazyness like me, it's enough to coast school and end up with the 60.000$ paper bill that says I passed some tests. The remaining 30% is moulding your answers to the teacher's preference. 

The tests in beta sciences are also predictable. But the tests are more difficult, since you need more room to build up concepts in your mind. An example would be C pointers: you can't understand pointers without understanding functions; you can't understand function without understanding variables, etc. So you can imagine concepts stacked on top of each other, where each new layer requires understanding of the previous layer.

Let's view this in the light of the CKA exam. In the study guide I outlined the syllabus, where each concept you have to know for the test had some resources to understand that topic. But that's not going to be on the test: there's too much information. KodeKloud comes to the rescue, because it will help you study for the test and not for Kubernetes in particular. I consider this a 40$ well-spent; then again, I don't necessarily think it proves anything about one's understanding of Kubernetes. Maybe I'm too hard on the CKA; it's the only way to measure aptitude for kubectl at scale, which will definitely weed out some people that feign understanding.

## So Why Don't I Have 100%? 

Yes, in all my arrogance, I should have at least a score of 100%. Unfortunately, I spent about 1.5h of the exam on one question about DNS which I eventually didn't pass. So even if you get the tip to "read the questions well", the questions might be phrased in such a way that it doesn't make a lot of sense.

I had to perform a successful nslookup, but they didn't specify which host that's supposed to be. So it could be either localhost, one of the nodes, or one of the pods. I could do it successfully from the pod, but that didn't make a lot of sense, since it was my understanding that something was broken. So I spent all my time trying to make DNS work from the localhost; trying to copy over the /etc/hosts from the kube-proxy or whatever. Obviously, the questions aren't that deep and you might find yourself in a situation where you break the cluster more easily than follow the question.

## What now? 

I think these two points cover what I found lacking in other resources. For other tips, I think there are enough in the previous article. So how about this: you passed the Kubernetes exam. What's next?

I recently found myself in a discussion on Facebook about Kubernetes and what to study after understanding the basics of Kubernetes. Someone asked me what they should do to get into more advanced Kubernetes. 

Well that's kind of interesting, because why would anyone learn Kubernetes if it isn't for the benefits that come after the hard time of understanding this technology? Should you learn Kubernetes just for the sake of Kubernetes, or do you now have a very nice and universal hammer at your disposal? I think it's the latter, and I noticed learning Kubernetes is that all the IT concepts have their own place in the Kubernetes ecosystem. For example, the NGINX webserver is one of the most popular pods to deploy in the cluster as it serves the same purpose as with previous machines. 

So what you could do to get into more advanced Kubernetes, is pick a topic that you find interesting, like security, networking, operating systems, AI, web development, etc. Anything that could be run on a distributed framework. Then explore that topic in the context of Kubernetes. I replied that I'd like to explore web development, as a gateway to be able to launch MVP's when I feel ready for entrepreneurship. So for me it's logical to run my web stacks on Kubernetes, and learn about Kubernetes in that context in the process.