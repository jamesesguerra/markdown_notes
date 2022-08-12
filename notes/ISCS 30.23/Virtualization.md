---
tags: [Notebooks/ISCS 30.23]
title: Virtualization
created: '2022-08-12T09:08:09.096Z'
modified: '2022-08-12T09:18:14.748Z'
---

# Virtualization

Virtualization is the process of creating a software-based version of something whether that be servers, storage, networking, or applications. What makes this feasible is something called the hypervisor.

### Hypervisor

A hypervisor is a piece of software that runs above the physical server/host. They pool the resources from the physical server and allocate them to your VMs.

Two types:

1. __Type 1 / bare metal__ 
- installed directly on top of the physical server
- most frequently used
- more secure and lower the latency
- ex: VMware ESXi, Microsoft Hyper-V, KVM


2. __Type 2 / hosted__
- difference is that there's a layer of host OS that sits between the physical server and the hypervisor
- less frequent
- mostly used for end-user virtualization
- ex: Oracle VM VirtualBox

### Building

Once you have a hypervisor installed, you can build VMs. A VM is simply a software-based application. Each VM is completely independent of one another. You can run multiple VMs on a hypervisor. 

Because they're independent, you can run different OSs on each VM. They're extremely portable as well -- you can move a VM from one hypervisor to a different hypervisor on a completely different machine almost instantaneously. 


### Benefits

1. __cost savings__ - when you can run multiple VMs on one piece of infrastructure, you can reduce your physical-infrastructure footprint. Less electricity, maintenance cost.
2. __agility & speed__ - spinning up a VM is easy and quick
3. __lowers down time__ - when the host goes out unexpectedly, you have a backup -- you can simply move VMs to different hypervisor on a machine that is working

![image](https://user-images.githubusercontent.com/68677613/184325388-5d3ca03f-a508-4c80-ba2d-138dc408af58.png)

