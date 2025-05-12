---
layout: post
title:  "Running RabbitMQ in Containers"
date:   2025-05-12 16:13:00 +0300
categories: development
---

RabbitMQ can be used for task queue management in applications that need some time to perform something. With containers, it's quite easy to start a group of RabbitMQ containers, some as workers, some as producers. Here, I will show how to create a setup with a single worker and a single producer. The worker will wait for messages from the queue and the producer will send messages to the worker through a queue.

Here 