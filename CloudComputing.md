# Cloud Computing

at University of Bristol, 4th year MEng unit.

Author: Sunny Miglani

**I wrote this from the slides, didn't watch the lectures unless it was needed! So this may not have _all_ the information**

**NOTE:** This **will** be missing some information, and is NOT a substitute for studying the lectures!

# Table of Contents

- [Cloud Computing](#cloud-computing)
- [Lecture 1:](#lecture-1)
  - [\*AAS abreviations:](#aas-abreviations)
- [Lecture 3 : Economics of Cloud](#lecture-3--economics-of-cloud)
  - [Technical side of scaling a warehouse of computers](#technical-side-of-scaling-a-warehouse-of-computers)
- [Lecture 5: Public Clouds, Infrastructure and Platform (IaaS, PaaS)](#lecture-5-public-clouds-infrastructure-and-platform-iaas-paas)
  - [How is the Cloud (aws) structured?](#how-is-the-cloud-aws-structured)
    - [Availability Zones:](#availability-zones)
    - [Regions:](#regions)
    - [Why regions though?](#why-regions-though)
    - [High availability & fault tolerance:](#high-availability--fault-tolerance)
    - [Examples of IaaS Services on AWS:](#examples-of-iaas-services-on-aws)
      - [VPC: Virtual Private cloud (IaaS example)](#vpc-virtual-private-cloud-iaas-example)
      - [EC2: Virtual Machines (IaaS example)](#ec2-virtual-machines-iaas-example)
      - [S3 Storage](#s3-storage)
      - [Examples of PaaS:](#examples-of-paas)
        - [RDS](#rds)
        - [Elastic Beanstalk:](#elastic-beanstalk)
      - [IaaS vs PaaS](#iaas-vs-paas)
- [Lecture 07: Virtualisation, Containers and Container Orchestration](#lecture-07-virtualisation-containers-and-container-orchestration)
  - [Virtualization:](#virtualization)
  - [Containers](#containers)
  - [Virtualisation and Containerisation:](#virtualisation-and-containerisation)
    - [Docker in Detail (WHY THO??!?)](#docker-in-detail-why-tho)
  - [Container Orchestration (Kubernetes)](#container-orchestration-kubernetes)
    - [Kubernetes in detail ( what is this degree legit?)](#kubernetes-in-detail--what-is-this-degree-legit)
      - [Master:](#master)
      - [Nodes:](#nodes)
      - [Deployments:](#deployments)
- [Lecture 09 Serverless](#lecture-09-serverless)
  - [Case Study: AWS Lambda](#case-study-aws-lambda)
    - [Performance Limitations:](#performance-limitations)
    - [Vendor Lock-in](#vendor-lock-in)
    - [Monitoring and Debugging](#monitoring-and-debugging)
    - [Serverless Security:](#serverless-security)
- [Lecture 11 : Developing Scalable Cloud Applications](#lecture-11--developing-scalable-cloud-applications)
  - [How to scale out these architectures? (Example, blackboard)](#how-to-scale-out-these-architectures-example-blackboard)
    - [X Axis Scaling:](#x-axis-scaling)
    - [Y Axis Scaling:](#y-axis-scaling)
    - [Z Axis Scaling:](#z-axis-scaling)
  - [Software Architectures in Cloud](#software-architectures-in-cloud)
  - [Architectural Components & Patterns for Scalable Systems (Basically keywords and buzzwords)](#architectural-components--patterns-for-scalable-systems-basically-keywords-and-buzzwords)
    - [Decoupled Components](#decoupled-components)
      - [Load Balancing:](#load-balancing)
      - [Message Topics](#message-topics)
      - [Message Queues](#message-queues)
      - [Service Registries](#service-registries)
- [Lecture 13 : MapReduce and Distributed File Systems](#lecture-13--mapreduce-and-distributed-file-systems)
  - [MapReduce fault tolerance](#mapreduce-fault-tolerance)
  - [Google File System (GFS)](#google-file-system-gfs)
    - [GFS explained](#gfs-explained)
    - [Leases and Mutation in GFS](#leases-and-mutation-in-gfs)
  - [HDFS - Hadoop File System](#hdfs---hadoop-file-system)
  - [Next Step for HDFS (3.0) is using ERASURE CODING](#next-step-for-hdfs-30-is-using-erasure-coding)
- [Lecture 13: Theory of Distributed Systems (CAP, Byzantine Generals)](#lecture-13-theory-of-distributed-systems-cap-byzantine-generals)
  - [Paxos Algorithm](#paxos-algorithm)
  - [So, how does this damn Paxos actually work???](#so-how-does-this-damn-paxos-actually-work)
    - [-- FLOW: --](#---flow---)
      - [Proposer:](#proposer)
      - [Acceptor:](#acceptor)
      - [Interaction once Acceptors prepare:](#interaction-once-acceptors-prepare)
      - [How does an acceptor choose a value?](#how-does-an-acceptor-choose-a-value)
  - [Byzantine Generals or Byzantine Fault Tolerance (BFT)](#byzantine-generals-or-byzantine-fault-tolerance-bft)
    - [Results of the Byzantine Generals:](#results-of-the-byzantine-generals)
    - [Solution to a simplied version of the problem](#solution-to-a-simplied-version-of-the-problem)
      - [If there are 3 armies, 1 traitor](#if-there-are-3-armies-1-traitor)
      - [Now if there are 9 armies and only 1 traitor](#now-if-there-are-9-armies-and-only-1-traitor)
    - [Actual Algorithm "Oral Message Algorithm": OM(m)](#actual-algorithm-oral-message-algorithm-omm)
    - [Solving the BG problem with traitors](#solving-the-bg-problem-with-traitors)
- [Lecture 15: Hadoop and Related Technologies (Hadoop ecosystem)](#lecture-15-hadoop-and-related-technologies-hadoop-ecosystem)
- [Lecture 17: NoSQL Databases](#lecture-17-nosql-databases)
  - [Key-Value DBs:](#key-value-dbs)
    - [Examples of DBs](#examples-of-dbs)
      - [Amazon SimpleDB:](#amazon-simpledb)
      - [GAE's Datastore (Google's version)](#gaes-datastore-googles-version)
      - [Document DB (AWS DynamoDB)](#document-db-aws-dynamodb)
    - [Columnar DBs](#columnar-dbs)
- [Lecture 18 (Graph Processing and Graph DBs)](#lecture-18-graph-processing-and-graph-dbs) - [Case Study - Web Pages](#case-study---web-pages)
  - [Graph Processing](#graph-processing)
    - [Execution of a "Pregel" program:](#execution-of-a-pregel-program)
  - [Examples of other graph based applications](#examples-of-other-graph-based-applications)
- [Lecture 19: NewSQL and Stream Processing](#lecture-19-newsql-and-stream-processing) - [Challenges with NoSQL](#challenges-with-nosql)
  - [NewSQL:](#newsql)
  - [Case Study : Google AdWords / Ads](#case-study--google-adwords--ads)
  - [Google Spanner (in MORE DETAIL BECAUSE WHY NOT YOU KNOW!!?!?)](#google-spanner-in-more-detail-because-why-not-you-know)
    - [SpanServers:](#spanservers)
    - [Google TrueTime:](#google-truetime)
    - [Google F1 (F-one) Deployment Structure:](#google-f1-f-one-deployment-structure)
      - [How does G-F1 deal with high latency?](#how-does-g-f1-deal-with-high-latency)
  - [Real Time Event Streaming](#real-time-event-streaming)
    - [Case Study: Apache Storm](#case-study-apache-storm)
      - [Structure of Apache Storm:](#structure-of-apache-storm)
- [Lecture 20: Cloud Security & Cloud Research](#lecture-20-cloud-security--cloud-research)
  - [Academic Side of Cloud Security / Cloud Research](#academic-side-of-cloud-security--cloud-research)
- [Lecture 21 Public Clouds for Software Dev - DevOps](#lecture-21-public-clouds-for-software-dev---devops)
  - [DevOps](#devops)
- [End of Lectures](#end-of-lectures)

# Lecture 1:

Normal Failure:
Essentially the idea that the chance of failure scales up drastically when you have a LOT of servers, for example 50 servers surviving 3 years -> 0.99^(50) = 61%, but 50,000 servers is 0.99^(50k) = 1%.

Which means if you're dealing with a lot of servers, you're just going to have failure in it.

That's why **Scalability** is very important!

These are some characteristics of Cloud Computing (**NIST DEFINITION**):

1.  On-Demand Self Service: Consumer can unilaterally obtain computing capabilities automatically without needing human interaction with each service provider.
2.  Broad Network Access: Capabilities are accessed through standard mechanisims and networks to promote heterogenous client
    platforms.
3.  Resource Pooling: Providers's computing resources are pooled to serve multiple consumers with resources reassigned according to demand.
4.  Rapid Elasticity: Resources can be elastically provided and released, hopefully automatically.
5.  Measured service: Automatically control and optimize resource by leveraging a meter capability.

## \*AAS abreviations:

1. SaaS : Software as a Service
   - Application software functionality served remotely. Imagine a program from a CD.
2. PaaS: Platform as a Service
   - Middlewear functionality, remotely accessible.
     Provices a combination of OS, Server, Data-base etc.
     **Example:** LAMP : Linux, Apache, MySQL, PHP/Python-- GOOGLE APP ENGINE, RDS, DYNAMODB
3. IaaS: Infrastructure as a Service
   - IT Infrastructure, almost virtualised and remotely accessible. Basically bare metal given to you. -- AMAZON EC2, S3, etc.

# Lecture 3 : Economics of Cloud

Economies of Scale are why cloud works!
["Required Reading"](https://cacm.acm.org/magazines/2013/2/160173-the-tail-at-scale/abstract)

Definitions:

1. Capital Expenditure: One time cost, to get the infrastructure built for your system (servers, building, etc)
2. Operating Expenditure: Electricity, man power, cooling, marketing etc.

Some Amazon Propogranda:
EC2 is a virtual server, it uses Amazon Machine Image, and you can build your own AMIs. Amazon has some prebuilt AMIs and now third party AMIs as well.

Cooling is very important for data centres

1. Open the window: small scale
2. Two-loop cooling: Bigger scale, but not BIG
3. Three loop cooling: Basically need to go to a different centre just to get rid of heat.

PUE: **Power Usage Effectiveness** -- PUE reflects the quality of the datacentre.
PUE = Facility Power / IT Power.

## Technical side of scaling a warehouse of computers

Architecture of a Warehouse-scale computer (WSC) is largely defined by the choice of it's building blocks.

In WSCs, the main building blocks are server hardware, network and storage components.

WSCs are now built from low-end servers, there used to be something called SMPs (symmetric multi-processing ) systems, but they were too expensive on scaling.

**Communication efficiency is very important for scaling**. That's why there is a focus in loading time efficiency.

Fault-Tolerant computing is well developed:
Having an N-Plex Redundancy deals with "normal failure", however Latency-tolerant is a new field.

## Key Insights from "Tail at Scale":

- Localised performance "hiccups" can radiate out to affect a significant fraction of all requests.
- Some sources of variablity are:
  - Woken Daemons
  - Maintanence activities
  - Normal failure
  - queuing.
- Having even probability of a system being slow at 0.01% can have a huge impact when you're running thousands of computers.
- Latency **Tail-tolerant** software techniques, have been developed to smooth out unpredictability.

# Lecture 5: Public Clouds, Infrastructure and Platform (IaaS, PaaS)

[Good resource for quick explanation](https://apprenda.com/library/paas/iaas-paas-saas-explained-compared/)

\*aaS's allow for Undifferentiated heavy lifting, they're usually done with a dedicated service provider.

**Undifferentiated Heavy Lifting**: Doing things that doesn't really differentiate us from the other companies, and it doesn't help the company stand out. Things like running and building boilerplate code that could be just built by someone else.

1. IaaS: Infrastructure as a Service (IaaS): Provides automted and scalable environments. (eg EC2)
2. Platform as a Service (PaaS): Provides a framework for quickly developing and deploying applications ex: AWS Beanstalk, Google App engine
3. Software as a Service (Software as a Service): Makes applications available through the internet, Gmail, Office365 etc.

With an IaaS - You only get the physical hardware from the cloud, you install and manage the OS, it's often just the bare metal!
With a PaaS - You get the OS, physical hardware, and runtime management all from the cloud. You need to handle the data and Applications.
With a SaaS - You get everything from the cloud, and only have to run the actual service you need from the cloud itself.

## How is the Cloud (aws) structured?

#### Availability Zones:

1. Clustures of independent data centres
2. Interconnected via low latency
3. Good to handle broken down data centres, and you can have high availability and fault isolation

**Fault Isolation**: Practice of designing systems such that when "something bad" happens, the negative consequences are limited in scope.

#### Regions:

1. Regions are independent 'clouds'
2. Often different geographical locations
3. Consist of different AZs
4. Often connnected on a backbone, but independent of each other.

#### Why regions though?

1. Data Sovereignty and Complaince: Data is stored where it's supposed to be and it's not sent across
2. Proximity of users to data: To provide low latency such as for streaming videos etc.
3. Service and Feature availability: Slowly allows you to scale your features to region, managing costs in setup and infrastructure.
4. Cost Effectiveness: Cheaper and easier depending on locations, so prices vary.

#### High availability & fault tolerance:

High Availablity:

- Ability to minimise service downtime by using redundant components.
- Requires service components in **atleast 2 AZs**

Fault Tolerance:

- High Availablity is included.
- Ability to ensure no service disruption by using active-active architectures.
- Requires service components in 3 AZs.

**IaaS**: Maybe have HA, but FT is not possible / unlikely

**PaaS**: Usually have HA, and some services offer FT

### Examples of IaaS Services on AWS:

##### VPC: Virtual Private cloud (IaaS example)

It's software-defined networking.
Ususally done via AWS CLI / UI
VPC Must have:

1. Defined private or public IP Address range
2. Atleast one subnet (partition) using a subset of the IP addresses
3. Firewalls, with or without security groups.

Optionally (additional):

1. Creating routing paths between VPCs
2. Create private connections using software/hardware VPNs
3. Connected via AZs and Regions
4. Have IPv4 or IPv6 addresses

##### EC2: Virtual Machines (IaaS example)

1. Uses Amazon Machine images (AMI)
2. You can create your own AMIs for faster booting and scaling
3. Default Elastic Block Store with network attached SSDs
4. Easy automated deployment for scaling and delivery

EC2s are not HA by default
EC2 for HA configuration:

- Duplicate VMs in differnet AZs with a custom AMI for easier deployement
- Configuration can be applied manually, or automatically via templates scripts or PaaS services.

EC2 Storage options:

1. Elastic Block Store:

- Net Attached Storage
- SSD, Magnetic system

2. Instance Storage:

- On-host storage
- Very fast / transient
- Available on certain instance types
- useful for caching

##### S3 Storage

1. Internet Based Storage, it's highly durable and cheap
2. Used by a LOT of apps
3. Accessible via AWS UI, CLI etc.
4. Files are **IMMUTABLE** objects.
5. Max for 1 file is 5TB
6. Stored in Buckets.
7. Each object has a unique key
8. Objects can be put into long term storage S3.

#### Examples of PaaS:

##### RDS

1. Manages DBs, has SQL/MySQL etc.
2. Scales and backups well
3. Saved time and money for admin
4. Cannot get to DB instances, doens't work well for highly customised services
5. RDS has multi AZs and uses Master/Slave DBs

##### Elastic Beanstalk:
It's a software built by AWS for you to be able to upload your project, and not have to worry about how the infrastructure of those applications is going to run. It will use scalable services from the AWS Free Tier

1. Deploy scalable applications
2. Custom docker containers
3. Load balances, scales etc automatically for you
4. Can define various environments yourself.
5. Manages DNS so it's seamless to roll between deployements.
6. Can upload thru git

#### IaaS vs PaaS

IaaS:

1. Used by Sys Admins
2. Provides infrastructures, and storage services
3. Offers flexibility in config and lowers risk of lock-in.
4. Lowers cloud resources needed, and lower costs needed.

PaaS:

1. Used by Devs
2. Provides application development platform, like hosted DBs, App Deployment and management
3. Locked into the application.
4. Offers low cost solutions for race to markets.

# Lecture 07: Virtualisation, Containers and Container Orchestration

Focus is on an application called Xen, it's used in AWS.
Docker is great for containers
Kubernetes is great for Container Orchestration

### Virtualization:

1. Provision of emulations of specific computer programs
2. Specifics of the hardware and host server should be hidden from user. They should only sese waht they added (VM)
3. AWS offers AMIs, and these are managed and run by a **Virtual Machine Monitor** (VMM), AKA the _hypervisor_
4. This allowes the VM to be paused, moved and copied, therefore making it easily scalable.

Different look into virtualisation is the use of a HOST OS or not.
The two types are defined as

1. Bare Metal -> <Hardware, Hypervisor, {VMs}> as the structure
2. Hosted -> <Hardware, **HOST OS**, Hypervisor {VMs}>

Full virtualization is a complete or almost complete simulation of the guest machine hardware, and the virtualized guest OS (VM) runs as if it was on the bare machine.

Paravirtualisation : Guest OS is edited to make system calls to the hypervisor API, and executes safe rewrites of the sensitive instructions. hypervisor doesn't simulate the hardware.

**Xen is an example of a hypervisor**:

1. Developed in Cambridge
2. Paravirtualisation
3. Open Source
4. Hardware-Assisted Virtualisation (Intel x86, ARM)

The flow of Xen is as follows (top to bottom):

> Application->Domain U Guest ->TCP/IP Stack->Split Device Driver-> Xen -> Shared Meemory segment -> Split Device Driver of Domain 0 guest, -> tcp then -> REAL device driver, THEN to the PHYSICAL device.

The domain 0 guest is the domain management and control.
Domain U guest, is the virtualised OS.

### Containers

Containers are a solution to the problem created due to the difference in requirements from Apps, DBs, Websites, Queues and the related VMs, Servers, Cloud structures, OSs etc, and how they all might interact with each other.

Containers allowed a simple solution, where the developer builds in an environment, and the environment easily maps the instructions and data between the hardware to the software.

Docker allows for :

1. Packaging and running applications in light and isolated environments.
2. Managed by docker engine, that uses a REST api.
3. Small footprint for running on Linux based servers.
4. Runs user processes in an isolated mode.
5. **Operating system level virtualisation with a shared kernel**

Advantage of Docker: No need to boot an operating system (faster to boot up in clouds)

Disadvantage: Isolation not as complete as with virtualisation, potentially not as secure for critical apps

Docker Definitions

1. Images: Read only templates, with instructions for creating docker containers, they're layered and kept track with a docker file
2. Container: It's a runnable instance of an image, and is created, stopped, started, moved or deleted. It's defined by it's image and also any environment variables you use when you start or create it

Network isolation in Docker makes it quite bad, DiskIO is native however, and the aggregate performance is much better than VMs

## Virtualisation and Containerisation:

1. Similarities: Both emulate compute infrastructure, and encapsulate the tenant
2. Differences:
   - VMs provide HARDWARE level virtualisation, containers provide OS level virtualisation
   - VMs need more time than containers for provisioning
   - Virtualisation is slower than VMS in comparison to containers except for networking
   - VM tenants are usually isolated, but containers provide process level isolation to tenants.

### Docker in Detail (WHY THO??!?)

Docker works similar to virtualisation, where we take the approach of

> Server -> HOST OS -> Docker Engine -> <CONTAINER>

The container contains the applications that are interacting with the middle-ware used by docker.
Focusing on the distinction between Containers and Images:

1. Containers running images
2. Images are publically displayed / deployed on docker hub
3. you can pull various images into a repository/dev machine
4. cloud operators have container servecies for your images.

Images in docker are basically composed of layers, similar to git, where they only keep track of changes to ensure that the data used is light and it's easily scalable.

## Container Orchestration (Kubernetes)

Why?

Well, running containers at scale requires tools. Fault tolerance is an important factor along with auto-scaling on demand of users.

Kubernetes uses docker containers to package applications then added tons of frameworks around it. It's got a LOT of support and it's quite powerfull. However, it's got a steeep learning curve.

It's great for scheduling work and replacing and scheduling in broken / failed containers.

It's service discovery and load balancing is good

It's good for horizontal scaling: which means basically adding in more parallel roads to handle more traffic, but not increasing the length or width of a single road.

This means the hardware per instance isn't scaled up, but the number of instances being run are.

### Kubernetes in more detail

Some components are:

1. Master
2. Etcd - Distributed key-value store. (Primary datastore of kubernetes)
3. Nodes
   - Pods
   - Kubelet
   - Kube Proxy
4. Kubectl
   - Local cli manager to manage clusters
   - configured to know cluster target for commands

##### Master:

1. Manages the cluster state
2. Subcomponents include
   - API server, - Gateway to the outside
   - controller, - Regulates state from current to desired state
   - scheduler - Schedules pods to worker nodes, with constraints
3. Possibly redundant
4. Writes to etcd - etcd: key-value store.

##### Nodes:

1. Run work in pods
2. Pods are the scheduling unit
   - Contain **one or more containers**
   - scheduled together on the same host
   - mount the same external storage
3. Container at runtime
4. Kubelet - Agent that communicates with the big boi master
5. kube-proxy: Network agent, overlays network routes.

Kubernetes has some Runtime Objects, such as

1. Pods
2. Deployments
3. Services

These are all stored in `yaml` files.

#### Deployments:

1. ReplicaSets: Balances the number of scheduled and running pods, it kills and creates them as needed
2. Deployments provides declarative updates for pods and ReplicaSets.
3. They're managed via
   - Specs : These describe the state
   - Status: The actual status

The steps to run kubernetes:

- Create a deployment to rollout a ReplicaSet
- Declare the new state with Pods
- Rollback with the deployement revision
- Scale it up with the Deployment to handle more load.

[Quickly read this as it's a really good summary of each service](https://www.digitalocean.com/community/tutorials/an-introduction-to-kubernetes)

Master: Primary control, it is the main contact point of the Admins and deals with any issues in the cluster. It's good for determining how to schedule workload, authenticate nodes and manage scaling + health checks.

etcd: Since Kubernetes depends so much on the containers and how they work, the etcd provides the _configurations_ in the cluster. This is used for service discovery and helps components configure or reconfigure themselves with the new information.

Nodes are the platform that run the containers in the system.

Deployments in Kubernetes:

- ReplicaSets: Balances the number of scheduled and running pods.
- Deployments provide declerative updates for pods and ReplicaSets.

# Lecture 09 Serverless

Serverless still has servers, it's just the idea that the developer doesn't need to care about them.

The servers themselves work on more generic generalised structure, rather than application specific.

Examples of some serverless layers.

1. Computing focused - Google Cloud Functions, AWS Lambda etc (FaaS)
2. Data Focused - Storage and Management, AWS S3, DynamoDB, Firebase etc
3. Messaging Focused - AWS SNS/ SQS etc
4. User Management and Identiy - AWS Cognito, Auth0 etc
5. Montiring and Dev - AWS CloudWatch, DataDog
6. Edge / APIs - AWS API Gateway, Cloudfront etc.

The **Main pillers of serverless** are:

1. No server management
2. Flexible scaling
3. High availability
4. Never pay for idle servers.

### Case Study: AWS Lambda

- Quick and easy to use
- Supports NodeJS, Python, C#, JS, Java etc
- Triggered via "events"
- Permissions and access to other AWS services

How does it work?

    - Is invoked via an event or schedule
    - It's run on a minimum Amazon Linux container, which contains the required runtime and function along with dependencies
    - JSON focused inputs and outputs
    - Timelimit allows for timeouts to save costs
    - Logs are created IF given permissions

**Cool Feature:** The container that runs this lambda, is actually retained for sometime to reduce the time needed to start it up each time.

The **Four Stumbling Blocks of Serverless**:

1. Performance limitations
2. Vendor Lock-in
3. Montioring and Debugging
4. Security and Privacy

#### Performance Limitations:

Specifically we're going to focus on the "cold start" issue
Essentially having auto deployment and auto-scaling require provisioning. This means that code that hasn't been used in a while and therefore cached takes longer to start

#### Vendor Lock-in

This essentially means that because we use a vendor like AWS Lambda, the associated programs that can run well with it are other lambda structures. Such as cloudwatch for logging or API gateway for https reqs.

However the lock-in has the advantage of easy integration with other processess if we'd like to use them.

#### Monitoring and Debugging

It's harder to test the lambdas in production unless you test locally, it's harder to enusre that the worktimes will be the same etc.
It's a new field to learn how to monitor and debug serverless applications / functions

#### Serverless Security:

Strengths is that the OS running the lambda is likely to be updated and managed by the vendor, so requires no extra effort on your side.

The time that hackers have to interact with your device can be limited due to timeouts ensureed by the vendor. The permissions are quite specific as well ensuring that the data isn't messed wiht on a large scale.

Weaknesses:
App code is still dependent to the library dependencies
The normal vulnerabilities that apply to code would still be valid.

# Lecture 11 : Developing Scalable Cloud Applications

Definitions:

1. Horizontal Scaling: add more machines to the process, this would require scaling the architecture to handle more machines
2. Vertical Scaling: Add better and bigger machines to the network. This requires no change in architecture

X Axis
- Split Horizontal Duplication with unbiased cloning of services and data:
- Each clone can do the work of all the other clones, and the work is distributed among clons without bias
- Inefficient compared to alternatives
- But EASY to do

Y Axis
- Split refers to isolating and making scalable individual responsibility of components
- Needs to be split on the code base
- More costly than x-Axis

Z Axis
- Partitioning the domain of incoming requests
- Data partitioning, split relative to client
- Improves fault tolerance and cache performances
- Most costly system

Simpler explanation of the above
If you split on X axis, imagine adding more clones of the system

If you split on Y axis, imagine splitting responsibility of the computers, so scaling by them doing different things

Splitting on Z axis means each server runs the same version of the code, but are responsible for different subsets of the data. Like imagine routing paying customers to a faster computer, and free customers to a slower computer.

[A good explanation is here](https://microservices.io/articles/scalecube.html)

### How to scale out these architectures? (Example, blackboard)

If the basic structure is

> Presentation -> Logic -> DataBase

#### X Axis Scaling:

You would expand the application logic and presentation layers, keeping the DB constant

> LoadBalancer -> {Presentation}\* + {Logic}\* -> DB

#### Y Axis Scaling:

Would decompose the logic into functional versions:

> Presentation -> {Login, Accounting, Booking} -> DB

#### Z Axis Scaling:

You would have a load balancer application, that would route them through various layers

Where the Presentation / Logic layers would be different depending on who has paid.

## Software Architectures in Cloud

It's a set of structures needed to reason about a system. This includes the software components, the relations between them and the properties of both.

Architecture is implicit even if it's a big scaled project. Maybe you haven't documented or communicated it explicitly, but it exists.

Good differentiation to think of is the Napster / Torrents system

Napster depends on a single login node, and then multiple client nodes (the logic / downloads etc)

Whereas torrent is a peer-to-peer network, which while badly scalable, is very fault tolerant unlike napster

## Architectural Components & Patterns for Scalable Systems (Basically keywords and buzzwords)

### Decoupled Components

- Independent scalibility of components (basically they don't depend on each other to scale)
- Preliminary fault tolerance and high availability (one breaks won't bring down the others unless heavy dependency)
- Uses APIs, RPCs or Typed Messages, and will HEAVILY rely on communication

Four important aspects of decoupled components is :

1. Load Balancers
2. Message Queues
3. Message Topics
4. Service Registers

#### Load Balancing:

Distribute Requests, manage availability, perform health checks and session affinity. Have lists of various servers and mappins and have a concrete load balancing polciy.

Sticky LBs means that the router is always routing client's requests to the same sever instances.

Cookies are managed by the load balancer, there is session replications and session-aware clusters.

The algorithms used can be Even Task Distribution and Round Robin. - Sequential distribution of work amongst the servers - Ignored the difference in weight required
Can also be weighted round robin

or least connections.

**Load balancers also check the health of other load balancers to ensure no clients are being missed**

#### Message Topics

1. Messages are immidiately pushed to subscribers
2. Decouple producers from subscribers
3. concurrent processing of the data
4. push the data, one to many

Essentially use a Pub/Sub system, and handle that not like an idiot.

#### Message Queues

1. Asynchronous, queue it and leave it
2. Decoupling, as it seperates application logic
3. Guarantees that things will run atleast once
4. Scalable, many workers can observe add and remove from the queue
5. Introduces latency however

#### Service Registries

1. Resolve addresses for names
2. Internal and ensure the HA system
3. Some workflows might need more scaling than others, and this can identify and handle that

Also handles things like Databasing and logging, as it _should_ have a sight of all the services being run

### Automation of Scaling:
Scaling cannot be manual, you need to use some form of **auto scalers!**


# Lecture 13 : MapReduce and Distributed File Systems

How do you store, process and analyse such large quantities of data on the cloud? (From the perspective of a cloud provider)

Google made MapReduce and GoogleFileSystem for their own in-house developement of Google. These are proprietary technologies.

MapReduce has now been taken over by Hadoop, and GoogleFileSystem is now also Hadoop File System

MapReduce is a "style of programming and of implementation". It's essentially simply described as splitting a large task amongst multiple workers, then taking the final output and combining it to give you a final output. [Simple Explanation here](https://www.ibm.com/analytics/hadoop/mapreduce)

MapReduce is great because it's **FAULT TOLERANT**, in the presence of normal failure.

MapReduce operates independent of storage systems and doens't require the data to be in a database before it's processed.

### MapReduce fault tolerance

MapReduce is usually done over hundreds or thousands of worker machines, so normal failure is a significant issue.

To handle normal failure, there exists a "master" worker, which would ping the worker threads periodically and if the worker does not reply in time, the master assumes that it's failed and marks it as such.

Since the master cannot retrieve the data from the "failed" worker, it just resets the data the worker was allocated as unallocated, and the next available worker will take over.

All workers that depended on the failed worker are notified and therefore will switch to reading from the local disks of the new worker that takes the workload.

When a map is finished, notifications are sent to the master and these include the names of the local files of the outputs. If the the Master receives the notification of the file that's already been completed, it ignores it otherwise it records the completiton data.

## Google File System (GFS)

Google started out wanting to use cheap current technology, for a huge scalable distributed storage.
This meant storing MASSIVE files, and overall HUGE datasets.

If you have cheap computers, they're unreliable, so how do you hande "normal failure" in this case?

1. Constant monitoring
2. Error detection
3. Fault-Tolerance
4. Automatic Recovery

### GFS explained

Files in GFS are divided into 64Mb blocks called `chunks`, each chunk has a `chunk handle` which is a unique ID.These chunks are stored on `chunkservers`.

**Fault-Tolerance** is provided by replicating each chink accross multiple servers. Usually there are 3 replicas, but this can be user-configured.

Meta-data records _where_ a chunk is stored, so GFS knwos where they are.

GFS consists of these three core processess

1. GFS Master Server (single) - Maintains all file system metadata
2. GFS Chunkserver (multiple)
3. GFS Clinet (multiple)

The application being run with GFS would talk to the GFS client, which would then deal with GFS as a whole, specifically going in contact with the GFS master

The role of the GFS Chunkserver, is to contact and map the storage to the linux file system.

To find the fastest access time by name in the name filespace of GFS.
The Master basically finds which chunkserver the data is stored in, and handles the retrieving and mutation of the data.

**Mutation of the data is a key factor**. Mutation basically means changing the data. Here to handle and maintain fault-tolerance, the chunks are replicated `n` times over the multiple servers. Each mutation is performed on all replicas, and is synchronised via [leases](http://vandanat.blogspot.com/2011/01/how-google-file-system-manages.html)

### Leases and Mutation in GFS

1. Client asks the master which chunkserver holds the lease on the chunk to be mutated, and where the replicas are stored
2. If no chunk**server** lease is given out, then master assignes a lease to a replica and marks this replica as the `Primary replica`. Now the master replies with the location of the primary and all secondary replicas
3. Client will push data to _all_ the replicas, each replica (chunkserver) holds the data in a cache. Upon receiving this, the chunkserver/replica replies back with an acknowledgement
4. Client instructs the primary chunkserver to do the writing
5. The `primary chunk` instructs the secondaries to do the same write
6. Secondaries reply back to the primary confirming the write has been executed
7. Primary replies back to the client with confirmation that the mutation is replicated.
8. Any point of failure will mean that the process is restarted by the Client pushing the data to all the replicas.

## HDFS - Hadoop File System

In hadoop the following changes are made to the naming convention

1. GFS Client -> HDFS Client
2. Master Server -> NameNode
3. GFS ChunkServer -> DataNode
4. Chunks -> Blocks

HDFS has new features, specifically high availability for the NameNodes, Snapshots / backups for any horrible event that might bring things down

and something called a **Federation**

**Federation:** Horizontal scaling of namenodes, with multiple independent namenodes instead of one + backup. The namenodes talk to a generic block-pool layer that further seperates namespace from storage. Basically handles data flow and manages workload.

The `blockpool` layers help communicate with various `datanodes` and maps better data.

## Next Step for HDFS (3.0) is using ERASURE CODING

Erasure coding is a "forward error correction" code. It's basically used to see whether data is corrupted and finds a way to recover the data by recovering chunks of it from other storages / sets.

EC can kinda be understood with this line

When written, data bits are encoded along with additional bits
When read back, data missing from erasures can be reconstructed from the extra bits
It can reduce / eliminate need to maintain `n` identical replicas.

# Lecture 13: Theory of Distributed Systems (CAP, Byzantine Generals)

A good cloud system should aim to achieve these three things

1. Consitency (C): All nodes should see the same data at the same time
2. Availability (A): Node failures shouldn't prevent survivors from working
3. Partition-tolerance (P): System continues to operate despite network partitions, i.e. partitions temporarily speperate systems from communicating with each other.

However, there's no chance a service can provide all three of the above simultaneously, and there will be some trade-off betweeen them. It's upto the service to pick which tradeoff they prefer.

Imagine a scenario with A, B servers and they suffer a partition:

A must decide

- Wait to hear back from B sacrificing Availability of A
- Proceed without hearing back from B, meaning the consistency would be gone b/w them
- Never actually be paritioned from B in the first place, meaning losing the tolerance to partitions

**However, this isn't a scenario of pick 2 out of 3, as parititions will ALWAYS happen and is NEEDED in a cloud structure**
You infact just choose how much of Availability and Consistency you're willing to sacrifice.

Sometimes in a cloud it might make more sense to focus on Consistency(C) (finance as an example).

## Paxos Algorithm

Paxos is an approach to ensuring agreement on a series of asynchronous operations taking place accross a distributed system.

It's a family of protocols for solving consensus in a network of unreliable processors.

Paxos guarantees saftey (consistency) and the conditions that could prevent it from making progress are difficult to provoke. Paxos is good for places where durability is required, for example replicating a file or a database where the amount of data could be large.

The Paxos algorithms is for systems that must

Achieve consensus on an order in which to carry out actions
Ensure that actions that are agreed upon cannot be forgotten
Despite system messages being duplicated, delayed or lost

Here **Paxos makes an assumption that the messages are not deliberately malicious, which is different form the Byzantine Generals Problem**

A set of replicas handle a series of Async requests that relate to the same resource

- Replicas have identical behaviour
- they suffer "fail/stop/restart" failures
- and have sufficient storage available

So what happens if replicas fail or become paritioned?

All surviving replicas must remain identical despite replica failure and message loss.

Paxos treats `value` to be any of {reading, writing, roll-backs, commits} that the system might choose to make.

For each attempt to agree on a `value`, Paxos must ensure that

- Only a value that has been actually proposed may be chosen
- Only a single value is chosen
- No one thinks a value has been chosen UNLESS IT ACTUALLY HAS

**Paxos doesn't guarantee a pick on the oldest, or best, it just says a valid value**

## So, how does this damn Paxos actually work???

There are a set of `replicas` that handle a series of synchronus requests that deal with **the same resource**. We remember that a `value` can be {reading, writing, roll-backs or commits}.

There are three main roles a `replica` or `process` can play:

- `Proposers`: Learn values that are already accepted; propose those values
- `Acceptors`: Let proposers knows already-accepted-values; accept or reject values they propose, and reach a consensus on choosing a particular proposal or value.
- `Learners`: Become aware of the chosen proposal/value and _act on it_.

Replicas can play **more than one** of these roles at different times. Often a replica is _elected_ to be a priviliged learner and or proposer. This means that they're the ONLY one allowed to play the role.

[This is a really good video on Paxos](https://youtu.be/s8JqcZtvnsM), it gets a bit confusing at points, but with the explanation and the idea of "integrity is important" in mind, it makes a lot more sense.

### -- FLOW: --

#### Proposer:

P asks some majority of acceptors to prepare for a proposal N. A "majority" is asked to get ready for the proposal and not all the players as if a majority of replicas agree on `V`, then a different majority CANNOT agree on another proposal `V'`. We also say majority **because not all acceptors could be in easy contact**

(Note, that P hasn't offered a value yet, and the acceptors can sign up whether or not they want to listen to the proposal)

#### Acceptor:

An acceptor A, gets a `prepare please` message from P with an ID `N`.
Acceptor has these possible options

1. A promises to ignore future proposals with ID lesser than `N`
2. A has already accepted a proposal P, and then sends the value to P with the ID of the last proposal that was accepted.
3. If N is too low, (N is behind the last ID she accepted), then acceptor can reject the `prepare please` message.

#### Interaction once Acceptors prepare:

- If P gets majority of acceptors, P can set a `value v`.
- If the acceptors sent a value `v'` as their accepted values, she an shoose `v` associated with the highest proposal ID number, if not, P can set the value herself.
- She requests that the acceptors accept `N.v` with N propsal number v value.
- They HAVE to accept unless P was too slow and they accepted a higher proposal number. (ID_of_new > N)
- If they accept, they can register a proposal with **learners** who take action on the value **if the majority of accepters accept the same proposal**

#### How does an acceptor choose a value?

1. Acceptor will accept the first proposal it sees
2. Acceptor will accept the proposal with the highest ID number it sees
3. A majority of acceptors must accept the same value.
4. Once a value is chosen, all proposals with a higher ID coose to recommend the same chosen value.

## Byzantine Generals or Byzantine Fault Tolerance (BFT)

BFT is the dependability of a fault tolerant computer system, where components may fail and there is imperfect information whether it has failed.

In a Byzantine failure, a component can inconsistently appear both failed and functioning to failure-detection systems, presenting different symptoms to different observers.

It's difficult for other components to declare it failed and shut it out of the network, as they first need to reach a consensus regarding which component has failed. This is derived from the Byzantine Generals' problem where the "actors" need to agree on a stategy to avoid a system failure, but some of the "actors" are malicious.

It's **focused on consistency in a distributed system**.

Byzantine General's problem:

- N allied generals must decide on a plan of attack
- They must all follow the SAME consensus plan
- But `m` of the generals are **traitors** (DUN, DUN, DUNNN) trying to prevent this.
- --- What is the largest value of `m` that the loyal generals can cope with and why?

(`m` here refers to broken / failing components)

If we look at simple majority vote of the generals, if there's any traitors, they basically vote the opposite. But the loyal generals will always reach a consensus.

However, the problem arrises when the traitors send different messages to different generals, not allowing them to reach a consensus.

### Results of the Byzantine Generals:

Byzantine generals can achieve consensuss when n > 3\*m + 1
To do so, they must engage in m+1 rounds of message passing

### Solution to a simplied version of the problem

##### If there are 3 armies, 1 traitor

1. If the commander is the traitor: Then the lieutenants cannot tell the difference and will not reach a consensus
2. If one of the lieutenants is the traitor, they still cannot reach consensus because they cannot tell which is true.

##### Now if there are 9 armies and only 1 traitor

Problem becomes relatively straightfoward.

1. The commander being a traitor: No matter how he splits it, there will always be a consensus in the system, and they will always reach the same consensus. They might even be able to identify that the commander is a traitor
2. If **one** of the lieutenants is a traitor, then everyone else will be able to spot it out or ignore him as there would be only 1 person going against the general "gossip"
3. If there are **two traitors** amongst 10 lieutenants, then one level of gossip wouldn't be enough to solve the problem, so you need something like "L1 told me that C said that .. ".

### Actual Algorithm "Oral Message Algorithm": OM(m)

If OM(M) & M>0:

1. The commander sends a vote `v_i` to n-1 lieutenants
2. Each lieutenant, `i` acts as a Commander for a new call OM(m-1), sending `v_i` to the other n-2 lieutenants.
3. If `V_i` is the set of the values that Lieutenant `i` receives during the above step, then Lieutenant `i` uses the value majority (`V_i`)

If OM(0):

1.  The commander sends a vote `v_i` to each lieutenant, i. 2. Each Lieutenant `i` uses the vote received from the Commander.

m being the number of adversaries.

### Solving the BG problem with traitors

So we need to spot traitors as the main focus in this kind of problem, as once traitors have been removed we can proceed easily (here traitors can be broken / faulty servers remember that).

To solve this, the BG problem uses the ideas of _"gossip chains"_, which simply is

> L2 and L3 speaking, L2 says "L1 said attack!", L3 says "L1 said retreat!"

This helps spot traitors, however traitors may not always gossip truthfully, and it may take `m+1` rounds to spot `m` traitors. (Need a cycle to spot fake news?)

The easier way to solve this might be to use longer chains, like L3 telling L4 that "L2 told me that L1 told her to Attack!"

This could include all `m+1` conversatiosn in one chain, and if chains are shared between honest parties then the solution can be to reach mini consensus about who the traitors are.

**However**, that could get out of hand quite quickly, as the chains will get big quite fast.

Which means that finding a consensus could take longer as gossip chains get longer. If we have too many traitors `3m+1 > n`, then it breaks

This is because we'd never reach consensus as the number of votes required would never reach majority

# Lecture 15: Hadoop and Related Technologies (Hadoop ecosystem)

[Vimeo link!](https://vimeo.com/303507914)

Hadoop's history

- Hadoop was built to do open source MapReduce
- But now they needed a file system to handle it, like Google File System, so they built HDFS
- Now they needed a DB system to handle this, so built Apache HBase like Google BigTable

The above three {Hadoop, HDFS, HBase} became Hadoop Core

Apache Pig Latin was developed to create functions that can be MapReduced by Hadoop.

`Hive` was created to build a SQL-like query language for Hadoop core // HBase

`YARN` was built as a method to deal with interacting HDFS2 layer, when MapReduce/Hadoop became too big

Literally the best understanding you'll get from this lecture is to read the "one slide summary" that Dave's put up.

Here's a summary of that summary

1. Pig : Platform for understanding and writing MapReduce/Sparkable code, uses `Pig Latin` as the main language
2. Hive: Another language / data warehousing software, makes it easy to write code that can handle large data sets in an SQL Like language
3. YARN: API that handles the job scheduling, in the HDFS of Hadoop infrastrucutre
4. Mahout: Basically a scalable ML platform, it provides tools for Hadoop to work on large data sets
5. Hoya/HBase: The actual No-sql relational DB that is used in hadoop
6. Storm: Great for stream processing, will go into detail later. It was made by twitter and is now used by most people. It's based on async graph stuff
7. Giraph: Graph database, and runs mapReduce jobs to process graphs. Used for more social media / connection focused jobs
8. Spark: High performance analytics engine, think of this as a way to replace MapReduce (MP), it's a lot faster and has more features than MP.

# Lecture 17: NoSQL Databases

There are 4 main classes of a NoSQL DB:

1. Key-Value DBs: DynamoDB
2. Document DB: MongoDB
3. Column Family DB: HBase
4. Graph DBs : Giraph

Relational Databases was great when you wanted to keep _relations_ (suprise suprise) between the data and easily access them based on these relations.

Relational databases are great for **ACID**: **Atomicity, Consistency, Isolation and Durability**

But, this isn't what we always want,
sometimes we want **CRUD: Create/Read/Update/Delete**

Also RDBMS (Relational) are not scalable. They become more and more expensive as they get bigger and bigger.
They're hard to scale down if the need dies out, therefore they end up having a long term permanently rising cost

## Key-Value DBs:

Think of them as an associative array (or a dictionary). Where each `key` has an associated `value`.

Keys are unique in a particular K-V namespace

Values can be almost any digital object, and usually the DB will put it's own constraints on the data.

KV DB's restricitons very much depend on the system being used, they may or may not provide auto indexing or generate keys.
Most of them **will use hashing** for quick access

### Examples of DBs

##### Amazon SimpleDB:

- Reliable storage
- language that allows you to Store, Modify, Query and Retrieve data sets
- Automatic indexing of all your data

SimpleDB has 3 main resources

1. `Domains`: High level **containers** for related data `items`. The searches only search through one `domain`.
2. `Items`: Named collection of `attributes` that represent a data object. Items have a unique name in the `domains`. They can be created/modified/deleted and manipulated.
3. `Attributes`: Individual category of information in the items, and have unique names for that item. It has one ore more text string's associated with the name.

The data is stored **in a "tree like" structure** not a table.
SimpleDB **only stores text**

##### GAE's Datastore (Google's version)

GAE's approach is a cloud style scale _out_ not up system. Basically this means as it's easier to scale _out_, it makes more sense for it to be automated.

- GAE Datasores holds data as `entities`
- Each entity has one ore more `properties`
- Each property has a `name`, with one or more `values`
- `Entities` belong to a `kind`, a unique `key` within the kind.

GQL is the language used to interact with GAE, and it's used in a similar fashion to SQL queries.

It allows for filtering based on property values, returning in a sorted order and can sort/filter keys too.

GAE like services

1. Memcache - Short term key/value storage serivce, that uses RAM and not disk and is therefore faster. It's not persistent though.
2. Blobstore - Store large items like videos and images
3. URL fetch - HTTP reqs to other servers on the internet.

##### Document DB (AWS DynamoDB)

Document DBs manage more complex data structures than KeyValue datastores.

They don't rrquire you to define a common structure for all records in the data store

They **DONT** store electronic documents like MS Word files. A `document` is a structured object, it contains information not only about what is being stored, but how it is being stored.

A Document example is a JSON file.

Exampls of DocumentDBs:

1. MongoDB
2. Couch (Apache open source based)

### Columnar DBs

- These are also known as Wide-Column DBs
- Great for "Big Data", technical term is VeryLargeDBs (VLDBs)
- RDBMSs can scale up to VLDBs, but the costs increase a lot and it gets insane
- KeyValue DBs scale nicely, but aren't the best for organising data like needed for Big Data
- While DocDBs can scale like this if not better, they're again not great for querying.

ColumnDbs come from the fact that groups of _related_ columns, which are frequently used together can be arranged in groups called `families`. The columns of a `family` are kept together on a disk to reduce access times.

Data modelers using Column DBs can implement their own `families` when defining the structure, but devs can add onto it as needed.

Examples:

1. Cassandra- V famous, used in apple, netflix, reddit uber etc.
2. HBase - Part of hadoop, used by airbnb, netflix, pintrest, spotify etc.

# Lecture 18 (Graph Processing and Graph DBs)

Networks are represented using Graphs in CS.

1. Fully Connected - Each node is connected to all other nodes directly
2. Clique is a **sub-graph** that is complete
3. Path is a sequence of edges connecting nodes
4. Cycle is a closed path.

Number of ways to arrive or leave a node is a node's \*_degree_.

This is equivalent to counting a node's neighbours.

1. An "in-degree" is **ways to arrive AT it**
2. An "out-degree" is **ways to leave it**
3. Undirected Graph implied in-degree=out-degree.
4. Regular Path : All nodes in the network have the same degree.

**Definition: Adjacency Matrix**

    - Basically a matrix representation that shows how a graph is connected
    - Colums and rows label's are both matrix nodes
    - A_ij represents teh number of edges from node i to node j.
    - Sum of **rows** = Out-degree of i
    - sum of **columns** = In-degree of j

If you square an adjacency matrix, the values in the graph show you how many connections of **LENGTH = 2** does it take to get from A to B.
Connections that used to be true for length = 1 will now show 0

_NB: I recommend looking at the slides for this, since that makes more sense_

#### Case Study - Web Pages

How do you see how important a web page is?

- If there's `a` link from `b` to `a`, then `a` must be important
- If `b` is important and links to `a` then `a` must be VERY important
- if `b` only links to `a` few pages, one of them being `a` then `a` is super important

That's the main logic behind page rank!

(Look at page rank example on slides):
Essentially the matrices give us a good way to look at the ranking and connections between web pages,

however there exists the problem when you have a "dangling node". These dangling nodes have incoming connection but no outgoing ones.

This can cause problems as they will accumulate a high score but never distribute it.

A **fix** for this is to teleport the surfers to random pages. Damping the pages imposes transitions between all nodes.

## Graph Processing

Google developed **Pregel**, a framework for running network analysis using graph processing.

It provides

1. High Scalability
2. Fault-Tolerance
3. Flexibility in arbitrary graph algorithms

Facebook developed **Giraph** (now Apache Giraph) to solve a similar problem.

Both the algorithms above have the same model

- Concurrent Computation: Computation is local to each node.
- Communication: There is messaging between nodes
- Barrier Synchronisation: Checkpoints that globally block nodes before processing.

Essentially this means run everything in parallel for processing, where each node does the computation for the related nodes nearby, but make sure to synchronise at some point before running the next iteration of the processing.

Pregel operates over a directed graph

- Each vertex is associated with a modifiable user-defined value
- Each edge has a value, and links a source vertex to a destination vertex

It runs a sequence of "supersteps" that's similar to MapReduce rounds

- Each vertex runs a user defined function
- It takes input from the last function run and gives output for the next function to run
- It can also change the surrounding topology by modifying it's outgoing edges.

The algorithm terminates based on the nodes voting to halt

- Initially every node is active
- All active nodes participate in the computation of a "superstep"
- Node deactivates itself by voting to halt
- Node can return to the active state if it gets the appropriate message

### Execution of a "Pregel" program:

- There is a master worker across all the workers
- The master worker is in charge of partitioning the graph and assigning the workers some respective partitions
- The master coordinates the running and communication and then couns the inactive vertices after each step and singals workers if there is an incoming message.

Master is also incharge of

- Keeping track of failed workers (via pings)
- Keeping track of superstep and sync steps
- Failed workers' work is reassinged to other workers, and the step is restarted

## Examples of other graph based applications

1. Neo4j Graph DB -

- GraphDB in Java
- Associative Data Sets (nodes with edges)
- Clustred
- Uses a query language
- Works fast on connected data

2. Cypher Query Language

- Declerative
- Matches a pattern

**NOTE: Understand page rank algorithm better, because there's an 8 mark example question**

# Lecture 19: NewSQL and Stream Processing

NewSQL is a class of modern RDBMSs that want to provide the same scalability of the NoSQL systems but still maintaining the ACID guarantees of a traditional RDBMs system.

reCAPping CAP:

- Consistency
- Availability
- Parition Tolerance

NoSQL offerings grew in comparison to the other two because the requirement of Partial Tolerance grew as the internet did. Partial tolerance being a core factor in web dev.

#### Challenges with NoSQL

Lack of strong ACID consistency, this adds complication for developers (imagine multiple transactions?)

Theres limitations with what SQL support is available, and there's very few systems that have robust management tools.

### NewSQL:

It's a DBS that delivers the **scalability** and **flexibility** of NoSQL while retaining the support for SQL queries / ACID.

- SQL is the primary interface
- ACID support exists
- Non-Locking concurrency control (no mutex)
- High per node performance
- Parallel architecture

## Case Study : Google AdWords / Ads

The workflow of the application used to be

- Do a content based list of ads to display
- take £££ related to it by the advertisers
- Set rules for the ads (time, location)
- Incorporate any rules and quota limitations
- If there's an ad click, then record the transaction for billing purposes.

The limitations it faced tho

- Availablity : There was downtime for updating the schema and replicating the data
- Scaling : Since it used a shared MySQL Db, rebalancing was difficult as you added nodes
- Functionality: Couldn't do sharing accross apps for the data

New version that happened in 2011:

- Architecure: It uses shared servers, it has a stateless server to deal with data. Worker pools are used for distributed SQL execution
- It has a relational schema, with consistent indexes and extensions for rich data types
- It uses MULTIPLE INTERFACES, like MapReduce, Key-Value, SQL etc.
- Can change the values in this.

It's used in GCP, Google Photos, Adwords!

## Google Spanner (in MORE DETAIL BECAUSE WHY NOT YOU KNOW!!?!?)

The google spanner universe has

1. `Zonemaster`: Assigns data to span servers
2. `Spanserver:` serves data to clients
3. `Location Proxies`: Used to locate spanservers with accurate data
4. `Universe master`: Only one exists, owns everything
5. `Placement Driver`: handles data movement for replication and load balancing

### SpanServers:

Each Spanserver contains

1. Colossus: Distributed FileSystem
2. Tablet: a bag of key/value timestamps. the State of this is tracked
3. Paxos state machine: it maintains consistency amongst replicas
4. Participant leader: Coordinates Paxos, maintains a transaction manager for distributed transactions

Application Data Model:

- Data is stored on atleast 3 replicas
- Schematised, and is semi-relational
- Supports UNILIMITED tables and DBs
- Supports SQL and transactions
- Not actually relational, i.e. all tables ahve primary keys etc.

### Google TrueTime:

It's an API that tells you what the time is
Specifically, that it can GUARANTEE that if time T has been given out, then the next call will only give T' > T, which is IMPORTANT AS HECK for transactions.

Each google data centre has an atomic clock, accurate to < 10ms

Clients can poll the TimeMaster, and they use "Marzullo's algorithm" which can detect liars and reach consensus in noisy conditions.

### Google F1 (F-one) Deployment Structure:

- Five replicas needed for High Availability
- Geography-> it's spread accross the world to survive regional natural distasters, approx 100ms apart
- Performance: High commit latency, have high throughput (bandwidth kinda)

#### How does G-F1 deal with high latency?

- Preferred Transaction structure
  - One read phase
  - Read in async
  - Buffer writes in client, uses RPC
- Use coarse schema
- Use bulk operations, but do small transactions in parallel for high throughput

## Real Time Event Streaming

Where would you need this?

- Large Haldron Collider
- Network monitoring
- Fraud detection
- Marketing

What do i need?

- Data arrives in real time (as close)
- High throughput
- Low latency
- Fault tolerance
- Straggler tolerant

### Case Study: Apache Storm

It's great to process unboudned streams of data

Good for realtime processing.

Good for low latency passing

#### Structure of Apache Storm:

- Define nodes and their roles
- Create a graph of computation

The structure work with `Streams` which is a sequence of tuples.

There are also `Spouts` and `Bolts`.

Spout may be connected to APIs to stream values, such as tweets.

Bolts use 1 or more input streams to process, and emit new streams if need be. Imagine a way of collating info.

For each node in the topology, several instances can exist that run in parallel.

Apache storm provides an **atleast once** processing guarantee, such that each data point has been touched on atleast once.

It cannot guarantee a **Only once** system, because they may be done in parallel and no way of telling.

It cannot provide consistency in the nodes, as they're hard to reason about. This is because the nodes process messages as they come.

# Lecture 20: Cloud Security & Cloud Research

There's a thing called the "Treacherous Twelve", which is basically a list of threats that exist in cloud security.

1. Data Breaches: When organisation's sensitive data falls into someone else's hands
2. Identity/Credential/Access Management: Data breaches occur due to faulty / not scalable Identiy Access Management sysems, things that use weak passwords, don't have multi factor authentication or fail to do other security measures
3. Insecure Interfaces & APIs: If you build a large structure with small microservices, it raises risk that one or more APIs would be weak / comprimised. This spreads and ruins the security of the whole infrastructure
4. System Vulnerabilities: Exploitable bugs in programs that attackers can use. These could be in the software, the kernel or just other application tools.
5. Account Hijacking: Phishing, Fraud man-in-the-middle etc.
6. Malicious Insiders: Malicious insider is someone who worked for the company / has access to the system in suc ha way that they might negatively affect the (C-I-A) of the system.
7. Advanced Persistent Threats: Parasitical form of attack where the "parasite" stays in the infrastructure stealithily and aims to smuggle as much data as possible.
8. Data Loss: Because of Confidientiality in the cloud, it's hard to see users // your own data. This could mean data loss for things via accidental deletion, forgetting keys etc.
9. Insufficient Due Diligence: Moving things to the cloud could cause vulnerabilities for the organisations if they're not well trained into what they're using.
10. Abuse & Nefarious Use of Cloud Services: Basically use the cloud to do bad things like DDoS or try and crack an encryption key.
11. Denial of Service: Inject malicious code into cloud systems which could result in DoS or a malicious party could rack up charges for a system via pings.
12. Shared Technology Issues: Shared resources that may have problems but also get someone to monitor the actual system to ensure there are no problems.

### Academic Side of Cloud Security / Cloud Research

There are 5 pitfalls and 5 opportunities of Cloud Research

**Pitfalls:**

1. Infrastructure at Scale: No one can get AWS level resources
2. Abstractions: Important details are often hidden (VMs)
3. Non-Reproducible Results: Often research is done using un-validated simulators
4. Rebradning: People mess up vocabulary (?)
5. Industry Relations: Industries aren't super happy giving access to academics sometimes

**Opportunities:**

1. User-Driven Research: Budget limited comptuation from reearch group forces the research to be user oriented
2. Programming Models: Can write scalable elastic ode without worrying about IaaS issues (?? are they saying that it's good to use cloud basically ??)
3. Debugging Large-Scale Applications: (?? Same as above ??)
4. PaaS Environments: ??????
5. Elasticity: ?????

# Lecture 21 Public Clouds for Software Dev - DevOps

Waterfall is bad, agile is good.

Agile people sprint

Aim of a sprint is to **deliver a working minimum viable product**.

New system is DevOps, merge Dev and Ops (wow)

## DevOps

**Goal:** Release updates as quickly as possible, without losing quality.

The problem in classical method is that Developers like having agility, wheras Operations love stability.

DevOps is an extension of Agile methodolgy.

- People: Break down the silos and walls between the teams, merge them together
- Process: Automate the manual processes that can be automated, make it more streamlined
- Tools: Create a pipeline that aims for speed and consistency and shows a clear path to the destinations.

Dev/Ops teams should focus on Collaboration with other teams (such as QA and IT). Responsibilities are shared amongst the team, focusing from the end to end quality of the product. The Devs will learn what the operations do, and the operations will learn what the developers need. Communication between the teams is integral, people usually use Slack & JIRA (issue tracker) to improve this.

**Continous Integration** is very important.

- Shared Code repo
- Automated testing on commits
- Frequent integrations

**Integrate early and intergrate often**!

Continous Delivery is another very key feature, this is because it would include more testing, and ensures that the production stage is more release ready each time.

**Robust Product Releases**:

Fail-Fast Philosophy: Having Continous integration and continous deliver helps spot any code problems early, and can alert the dev teams almost instantly.

This also means that the developers can have integrated mointoring, which allows the developers to have more detailed information about bugs which can lead to easier fixes.

**Consistent Deployment Environments**

Having identical environments across the workers ensures that you don't have problems of systems only working on a particular machine

It means that it's easier to scale up engineers as you can use VM images, have backups of productions and make changes accross all developers.

This also means you can use IaaS systems as an advantage, focusing on cloud systems to scale engineers.

---

# End of Lectures
