---
tags: [Notebooks/ISCS 30.23]
title: 08/11/2022 Overview of Containers
created: '2022-08-12T08:40:42.428Z'
modified: '2022-08-12T09:19:24.268Z'
---

# 08/11/2022 Overview of Containers

## Virtual machines

A virtual machine allows you to virtualize things like hardware, RAM, CPU, OS, etc. 

Scenario: you have a dedicated server and getting it up and running takes a very long time. You have to go through procurement, buy a giant server, and you might have to buy more hardware. With VMs, you have a giant server, and that server can be split up into different VMs. So instead of having a hardware-based data center, you have a software-based data center. You can run multiple virtual servers on the same physical computer.

In most data centers today, you have giant servers, and then on those servers you have VMS. It becomes difficult to manage 50 applications on one computer without VMs. You can create a VM and manage an application only for that particular VM. Adopting this means it takes less time to deploy new solutions. You waste less resources and you have improved portability. However, the application, and all its dependencies and OS are stil bundled together. 

Hypervisors create and manage VMs. It is the software layer that breaks the dependencies of an OS on the underlying hardware and allows several VMs to share that hardware.

One VM is supposed to handle one particular application. What if you want to run multiple apps in the same VM? Then you'll run into the same problem you did if you didn't use VMs. You'll also have scaling issues -- the more servers you have, the more traffic you can handle. However, this is going to consume a lot of resources. Moreover, applications running on Django, Java, React, in one VM becomes very messy. 

> _"How can we get multiple applications on the same VM?"_

## Containers




