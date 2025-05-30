+++
date = '2025-05-30T10:37:33-05:00'
draft = true
title = 'Java Multi Threading Basics'
+++

## Multi-threading in Java

In the history of programming one of the most valuable things is: Speed. In traditional computing this is often achived through optimization, careful design, better hardware, and tooling. In modern programming though those are becoming less critial. Our tools are better then ever, often optimizing better then a human can. Though careful optimal design is still necessary. Our hardware isn't getting faster as quickly as it used to, but to make up for that it is enabling Parallel computing more and more. Being able to multi-thread is critical to leverage this. 

### What are Threads

Threads for those unfamilar with them are essentially a process. There is more nuance there, as specically a thread is part of a process. We won't worry about the specifics of a process vs a thread, and the semantics that come with that. 



- ["Thread safety"](https://en.wikipedia.org/wiki/Thread_safety) is vital. We will not be coving that in this blog, but it's important to make sure any "Side effects" of a thread are handled in a secure and reliable way. There are many resources for this online
- In newer Java versions ["virtual threads"](https://www.baeldung.com/java-virtual-thread-vs-thread) which come with a lower *cost*, but we will not being looking into that