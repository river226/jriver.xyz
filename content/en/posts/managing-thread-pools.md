+++
date = '2025-05-30T09:58:00-05:00'
draft = true
title = 'Managing Thread Pools'
+++

## Managing Thread Pools in Java and Springboot

This post builds off of the previous posts:
- [Java Multi-threading basics]()

When speed is a factor taking things one by one can be quite painful. That's where Parallel processing and Multi-threading come in handy. The tooling for this is constantly getting better and improving, but one powerful tool is the Threadpool. This allows us to collect a series of Runners, and coordinate their efforts. This is ideal for situations where you need to manage the load on the system, and can work really well when you have a series of tasks that are not dependent on and can be run asyncronously from each other. Lets get more into the implementation though. 

### Advantage of Threads

If you are unfamiliar with Multi-Threading, let me cover a basic rundown of threads:
- Threads are descrete processes that can be run in series or in parallel
- Your program is it's own thread, but you can run additional threads that run along side it
- Threads will eat up resources. We are talking about threadpooling as a way to help manage that load on your system without losing the benefit
- ["Thread safety"](https://en.wikipedia.org/wiki/Thread_safety) is vital. We will not be coving that in this blog, but it's important to make sure any "Side effects" of a thread are handled in a secure and reliable way. There are many resources for this online
- In newer Java versions ["virtual threads"](https://www.baeldung.com/java-virtual-thread-vs-thread) which come with a lower *cost*, but we will not being looking into that

### Executors

In Java threads are built around the Runnable interface. An object you want to launch into it's own thread therefor needs to implement runnable, and then have a defined Run Method

### Building a 