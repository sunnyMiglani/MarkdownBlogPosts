# Cloud Computing 
at University of Bristol, 4th year MEng unit.




# Lecture 1:

Normal Failure:
Essentially the idea that the chance of failure scales up drastically when you have a LOT of servers, for example 50 servers surviving 3 years -> 0.99^(50) = 61%, but 50,000 servers is 0.99^(50k) = 1%.

Which means if you're dealing with a lot of servers, you're just going to have failure in it.

That's why **Scalability** is very important!

These are some characteristics of Cloud Computing:
    
    1. On-Demand Self Service: Consumer can unilaterally obtain computing capabilities automatically without needing human interaction with each service provider.
    2. Broad Network Access: Capabilities are accessed through standard mechanisims and networks to promote heterogenous client platforms.
    3. Resource Pooling: Providers's computing resources are pooled to serve multiple consumers with resources reassigned according to demand.
    4. Rapid Elasticity: Resources can be elastically provided and released, hopefully automatically.
    5. Measured service: Automatically control and optimize resource by leveraging a meter capability.
    
## *AAS abreviations:
    1. SaaS : Software as a Service
        - Application software functionality served remotely. Imagine a program from a CD
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

Cooling is v v v important for data centres
    1. Open the window -small scale
    2. Two-loop cooling: Bigger scale, but not BIG
    3. Three loop cooling: Basically need to go to a different centre just to get rid of heat.
 
 PUE: Power Usage Effectiveness -- PUE reflects the quality of the datacentre.
 PUE = Facility Power / IT Power.
 
 
## Technical side of scaling a warehouse of computers
Architecture of a Warehouse-scale computer(WSC) is largely defined by the choice of it's building blocks. 

In WSCs, the main building blocks are server hardware, network and storage components.

WSCs are now built from low-end servers, there used to be something called SMPs (symmetric multi-processing ) systems, but they were too expensive on scaling.

**Communication efficinecy is very important for scaling**. That's why there is a focus in loading time efficiency.


# Lecture 5: Public Clouds, Infrastructure and Platform (IaaS, PaaS)

Undifferentiated Heavy Lifting: Doesn't really differntiate us from the other companies, and it doesn't help the people stand out.

    1. IaaS: Infrastructure as a Service
        EC2, GCS
    2. Platform as a Service (PaaS):
        AWS Beanstalk, Google App engine
    3. Software as a Service (Software as a Service):
        Makes applications available through the internet, Gmail, Office365 etc.

## How is the Cloud (aws) structured?

#### Availability Zones:

Clustures of independent data centres
Interconnected via low latency
Good to handle broken down data centres, and you can have high availability and fault isolation

#### Regions:

Regions are independent 'clouds'
Often different geographical locations
Consist of different AZs
Often connnected on a backbone, but independent of each other.

#### Why regions though?

    1. Data Sovereignty and Complaince: Data is stored where it's supposed to be and it's not sent accross
    2. Proximity of users to data: To provide low latency, and therefore you wanna move the regions around to allow things
    3. Service and Feature availability: Slowly allows you to scale your features to region, managing costs in setup and infrastructure. 
    4. Cost Effectiveness: Cheaper and easier depending on locations, so prices vary

#### High availability & fault tolerance:
Basically good ways to keep uptime and reduce problems if things breakdown. Amazon suggests 2 AZs at minimum

Fault tolerance means that no users notice anything broken, which is why they suggest 3 AZs

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
3. Default Elastic Band Storage with network attached SSDs
4. Easy automated deployment for scaling and delivery


##### S3 Storage
1. Internet Based Storage, it's highly durable and cheap
2. Used by a LOT of apps
3. Accessible via AWS UI, CLI etc.
4. Files are **IMMUTABLE** objects.
5. max for 1 file is 5TB


#### Examples of PaaS:
##### RDS
1. Manages DBs, has SQL/MySQL etc.
2. Scales and backups well
3. Saved time and money for admin
4. Cannot get to DB instances, doens't work well for highly customised services
5.RDS has multi AZs and uses Master/Slave DBs

##### Elastic Beanstalk:
1. Scalable applications
2. Custom docker containers
3. Load balances, scales etc automatically for you
4. Can define various environments yourself.
5. Manages DNS so it's seamless to roll between deployements.
6. Can upload thru git

#### IaaS vs PaaS
IaaS:
1. Used by Sys Admins
2. Provides infrastructures, and sotrage services
3. Offers flexibility in config
4. Lowers cloud resources

PaaS:
1. Used by Devs,
2. Locked into the application
3. offers low cost solutions for race to markets.

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

Paravirtualisation : Guest OS is edited to make system calls to the hypervisor API, and executes safe rewrites of the sensitive instructions. hypervisor wont emulate the hardware.

**Xen is an example of a hypervisor**:

    1. Developed in cambridge
    2. Paravirtualisation
    3. Open Source
    4. Hardware-Assisted Virtualisation (Intel x86, ARM)

The flow of Xen is as follows:

> Application->Domain Guest ->TCP/IP Stack->Split Device Driver-> Xen -> Shared Meemory segment -> Split Device Driver of Domain 0 guest, -> tcp then -> REAL device driver, THEN to the PHYSICAL device.

### Containers
Containers are a solution to the problem created due to the difference in requirements from Apps, DBs, Websites, Queues and the related VMs, Servers, Cloud structures, OSs etc, and how they all might interact with each other.

Containers allowed a simple solution, where the developer builds in an environment, and the environment easily maps the instructions and data between the hardware to the software.

Docker allows for :

    1. Packaging and running applications in light and isolated environments
    2. Managed by docker engine, that uses a REST api.
    3. Small footprint for running on Linux based servers.
    4. Runs user processes in an isolated mode.
    
Docker Definitions
1. Images: Read only templates, with instructions for creating docker containers, they're layered and kept track with a docker file
2. Container: It's a runnable instance of an image, and is created, stopped, started, moved or deleted. It's defined by it's image and also any environment variables you use when you start or create it 


## Virtualisation and Containerisation:
1. Similarities: Both emulate compute infrastructure, and encapsulate the tenant
2. Differences:
    - VMs provide HARDWARE level virtualisation, containers provide OS level virtualisation
    - VMs need more time than containers for provisioning
    - Virtualisation is slower in VMS in comparison to  containers except for networking
    - VM tenants are usually isolated, but containers provide process level isolation to tenants.

### Docker in Detail (WHY THO??!?)
Docker works similar to virtualisation, where we take the approach of 
>   Server -> HOST OS -> Docker Engine -> <CONTAINER> 

The container contains the applications that are interacting with the middle-ware used by docker.
Focusing on the distinction between Containers and Images:
1. containers run images
2. images are publically displayed  / deployed on docker hub
3. you can pull various images int oa repository/dev machine
4. cloud operators have container servecies for your images.

Images in docker are basically composed of layers, similar to git, where they only keep track of changes to ensure that the data used is light and it's easily scalable.

## Container Orchestration (Kubernetes)
Why?

Well, running containers at scale requires tools. Fault tolerance is an important factor along with auto-scaling on demand of users. 

Kubernetes uses docker containers to package applications then added tons of frameworks around it. It's got a  LOT of support and it's quite powerfull. However, it's got a steeep learning curve.

It's great for scheduling work and replacing and scheduling in broken / failed containers.

It's service discovery and load balancing is good

It's good for horizontal scaling: Basically adding in more parallel roads to handle more traffic, but not increasing the length or width of a single road. Basically don't mess with the hardware, but feel free to add more versions 

### Kubernetes in detail ( what is this degree legit?)
Some components are:
1. Master
2. Etcd
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
    - API server,
    - controller,
    - scheduler
3. Possibly redundant
4. Writes to etcd

##### Nodes:
1. Run work in pods
2. Pods are the scheduling unit
    - Contain one or more containers
    - scheduled together on the same host
    - mount the same external storage
3. Container at runtime
4. Kubelete - Agent that communicates with the big boi master
5. kube-proxy: Network agent, overlays network routes.



Kubernetes has some Runetime Objects, such as 
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

--- You know what, I'm just not going to write down the kubernetes details because this is shit ----

# Lecture 09 Serverless


Serverless still has servers, it's just the idea that the developer doesn't need to care about them.

The servers themselves work on more generic generalised structure, rather than application specific.


Examples of some serverless layers.
1. Computing focused - Google Cloud Functions, AWS Lambda etc (FaaS)
2. Data Focused -  Storage and Management, AWS S3, DynamoDB, Firebase etc
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

It's harder to test the lambdas in production unless you test locally, it's harder to enusre that the tworktimes will be the same etc.
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

X Axis Split Horizontal Duplication with unbiased cloning of services and data:
    - Each clone can do the work of all the other clones, and the work is distributed among clons without bias
    - Inefficient compared to alternatives
    - But EASY to do
    
Y Axis Split refers to isolating and making scalable individual responsibility of components
    - Needs to be split on the code base
    - More costly than x-Axis

Z Axis - Partitioning the domain of incoming requests
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

>  Presentation -> Logic -> DataBase

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

The algorithms used can be Even Task Distribution and Round Robin.
    - Sequential distribution of work amongst the servers
    - Ignored the difference in weight required
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


# Lecture 13 : MapReduce and Distributed File Systems

How do you store, process and analyse such large quantities of data on the cloud? (From the perspective of a cloud provider)

Google made MapReduce and GoogleFileSystem for their own in-house developement of Google. These are proprietary technologies.

MapReduce has now been taken over by Hadoop, and GoogleFileSystem is now also Hadoop File System


MapReduce is a "style of programming and of implementation". It's essentially simply described as splitting a large task amongst multiple workers, then taking the final output and combining it to give you a final output. [Simple Explanation here](https://www.ibm.com/analytics/hadoop/mapreduce)

MapReduce is great because it's **FAULT TOLERANT**, in the presence of normal failure.

MapReduce operates independent of storage systems and doens't require the data to be in a database before it's processed.

### MapReduce fault tolerance
Tbh, MapReduce is usually done over hundreds or thousands of worker machines, so normal failure is a significant issue. 

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


To find the fastest access time by name in the name filespace of GFS, it uses a Trie kinda structure to deal with the dat.

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

**Federation:** Horizontal scaling of namenodes, with multiple independent namenodes instead of one + backuo. The namenodes talk to a generic block-pool layer that further seperates namespace from storage. Basically handles data flow and manages workload.

The `blockpool` layers help communicate with various `datanodes` and maps better data.

## Next Step for HDFS (3.0) is using ERASURE CODING

Erasure coding is a "forward error correction" code. It's basically used to see whether data is corrupted and finds a way to recover the data by recovering chunks of it from other storages / sets.

EC can kinda be understood with this line

    When written, data bits are encoded along with additional bits
    When read back, data missing from erasures can be reconstructed from the extra bits
    It can reduce / eliminate need to maintain `n` identical replicas.
    
# Lecture 13: Theory of Distributed Systems (CAP, Byzantine Generals)

A goood cloud system should aim to achieve these three things
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
    
Here **Paxos makes an assumption that the messages are not deliberately malicious, which is different form the Byzantine Generals Problemo**

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



