# COMP90024-CCC

## Week1 - How we got here
1. Computing and Communication Technologies (r)evolution
    - from centralised to decentralised
2. distributed system history
    - Once upon a time we had standards
    - Then we had more standards
    - mid-90s: focused on computer-computer interaction
    - internet: peer-to-peer
        - challenge: sharing data between different organizations
        - soln: grid computing
        - Grid: only need access to it no matter it is data or super computer the process to move things
            - problem: people have different ways to do it


## Week2 - Domain Drivers – tour of some big data projects
1. compute scaling
    - method:
        1. Vertical Computational Scaling
            - Have faster processors
            - disabv: processor speed is limited  
              Moore's law is no longer working, CPU stop goes faster as we expected
        2. Horizontal Computational Scaling
            - Have more processors
            - adv: 
                - 1) Easy to **add more** (more cores or cluster of nodes)
                - 2) cost increase not so much
            - disadv: 
                - 1) **add more** limition (see week3 - Amdahl's law)
                - 2) harder to design, develop, test
2. network scaling
    - volume of data on network grows each year
3. massive amount of data generated among a time requires compute infrasture
    - e.g. mapping the sky with data from tele-scope
5. Cloud Computing in Different Domains
    - **High energy physics**
    - Astrophysics
    - **Macro-micro simulations**
    - Electronics
    - Arts and humanities
    - Life sciences
    - Social sciences
        - Aurin
    - Clinical sciences
    - Data sharing and ethics
    - **e-Health**
        - **Security**
    - environmental
    - social
    - geographical
    - Genome

## interesting discussion
- [difference between grid, cluster and cloud computing](https://canvas.lms.unimelb.edu.au/courses/17514/discussion_topics/139892)

## Week3 - Overview of Distributed and Parallel Computing Systems
1. Amdahl's law
    - Goal: If n processors (cores) are thrown at a problem how much faster will it go?
    - Some terminology:
        - <img src="./docs/1.png" width="50%" height="50%" />
    - <img src="./docs/2.jpg" width="60%" height="50%" />
2. Gustafson-Barsis's Law
    - speedup is a linear formula dependent on the number of processes and the fraction of time to run sequential parts
    - <img src="./docs/3.jpg" width="60%" height="50%" />
    - Faster (more parallel) equipment available, larger problems can be solved in the same time.
3. Parallelisation Paradigms
    - Master-Worker 
        - Master decomposes the problem into small tasks
        - distributes to workers and gathers partial results to produce the result
        - <img src="./docs/4.jpg" width="20%" height="50%" />
    - Divide and Conquer
        - 1) A problem is divided into two or more sub problems
        - 2) each of these sub problems are solved independently
        - 3) their results are combined
        - 3 operations: split, compute, and join
        - Master-worker/task-farming is like divide and conquer with master doing both split and join operation
        - <img src="./docs/7.jpg" width="20%" height="50%" />
    - Single-Program Multiple-Data (SPMD)
        - Each process executes the same piece of code, but on different parts of the data
        - Data is typically split among the available processors
        - Commonly exploited model: MapReduce
        - <img src="./docs/5.jpg" width="20%" height="50%" />
    - Pipelining 
        - Suitable for applications involving multiple stages of execution
        - typically operate on large number of data sets.
        - <img src="./docs/6.jpg" width="20%" height="50%" />
    - Speculation
        - Used when it is quite difficult to achieve parallelism through the previous paradigms
        - use "look ahead" execution
        - prcedure: 
            - Consider a (long running) producer P and a consumer C such that C depends on P for the value of some variable V. If the value of V is *predictable*, we can execute C speculatively using a predicted value in parallel with P.
                - If the prediction turns out to be correct, we gain performance since C doesn’t wait for P anymore. 
                - If the prediction is incorrect (which we can find out when P completes), we have to take corrective action, cancel C and restart C with the right value of V again. 
    - Parametric Computation
        - not discussed?
4. Erroneous Assumptions of Distributed Systems
    - The network is reliable
    - Latency is zero
    - Bandwidth is infinite - I can send any amount of data I wish between any nodes
    - The network is secure
    - Topology doesn't change - Node x is always there
    - There is one administrator
        - e.g.: Firewall changes, server reconfigurations, services, access control (students/staff/others…)
    - Transport cost is zero - I can send as much data as I like for free
    - The network is homogeneous
    - Time is ubiquitous - Clock is same across all computers in network

## Week5 - Cloud Computing & ~~Getting to Grips with the University of Melbourne Research Cloud~~
Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) <u>that can be rapidly provisioned and released with minimal management effort or service provider interaction</u> 可以通过最少的管理工作或服务提供者交互从而可以快速地配置和发布
- <img src="./docs/8.jpg" width="70%" height="50%" />
1. Deployment Models

    || Private| Community| Public| Hybrid |
    |---|---|---|---|---|
    |pro|1. **Control**<br>2. **Consolidation of resources**<br>3. **Easier to secure** - easy to setup firewall<br>4. **More trust**||1. Utility computing<br>2. **Can focus on core business** - no need to care infrasture or be a devop<br>3. Cost-effective - use as much as you need<br>4. “Right-sizing”<br>5. Democratisation of computing<br>|1. **Cloud-bursting** - Use private cloud, but burst into (突然变成) public cloud when needed |
    |con|1. Relevance to core business?<br>e.g. Netflix to Amazon<br>2. Staff/management overheads - need devop<br>3. Hardware obsolescence - need to refesh hardware<br>4. Over/under utilisation challenges - recycle resources<br>| | 1. **Security** - people can see your sensitive data<br>2. Loss of control<br>3. **Possible lock-in** - difficult to switch Azure if using AWS<br>4. Dependency of Cloud provider continued existence<br>| 1. How do you move data/resources when needed?<br>2. How to decide (in real time?) what data can go to public cloud?<br>3. Is the public cloud compliant with PCI-DSS (Payment Card Industry – Data Security Standard)?<br>|
    |example| | | | Eucalyptus, VMWare vCloud Hybrid Service|

2. Delivery Models
- <img src="./docs/9.jpg" width="70%" height="50%" />
    
    | | Iaas| Paas|Saas|
    |---|---|---|---|
    | example| Amazon Web Services<br>Oracle Public Cloud<br>NeCTAR| Azure| Gmail|


## Week 6 – Web Services, ReST Services ~~and Twitter demo~~

### SOA

1. What's in an Architecture?
    - A (system) architecture is just the way different components are distributed on computers, 
    - and the way in which they interact with each other.
2. Why Service-oriented Architectures - SOA?
    - When an architecture is completely contained within the same machine, components can communicate directly
        - e.g. through function calls or object instantiations.
    - However, when components are distributed such a direct approach typically cannot be used  (e.g. Assignment 2!)
    - Therefore, components (more properly, systems) have to interact in more loosely-coupled ways. 
    - **Services** are often used for this. Typically combinations and commonality of services can be used to form a **Service-oriented Architecture (SoA)**.
3. SOA goal

    |||
    |---|---|
    |A set of externally facing services|that a business wants to provide to external collaborators|
    |An architectural pattern|based on service providers, one or more brokers, and service requestors based on agreed service descriptions|
    |A set of architectural principles, patterns and criteria|that support modularity, encapsulation, loose coupling, separation of concerns, reuse and composability|
    |A programming model|complete with standards, tools and technologies that supports development and support of services (note that there can be many flavours of services)|
    |A middleware solution|optimized for service assembly, orchestration, monitoring, and management (Can include tools and approaches that combine services together.)<br/>e.g. as workflows. - later on security lecture|

4. SOA design principle

    |||exmaple|
    |---|---|---|
    |Standardized service contract| Services adhere to a communications agreement, as defined collectively by one or more service-description documents.|Use defined twitter API|
    |Service loose coupling| Services maintain a relationship that minimizes dependencies and only requires that they maintain an awareness of each other.|
    |Service abstraction| Beyond descriptions in the service contract, services hide logic from the outside world.|Twitter decide the API for you to use i.e. the rule how you can see inside through the Twitter, hide things which you have no access to
    |Service reusability| Logic is divided into services with the intention of promoting reuse.|
    |Service autonomy| Services have control over the logic they encapsulate.|you can have tweets older than 2 weeks than you really can't
    |Service statelessness| Services minimize resource consumption by deferring the management of state information when necessary.|
    |Service discoverability| Services are supplemented with communicative meta data by which they can be effectively discovered and interpreted.|
    |Service composability| Services are effective composition participants, regardless of the size and complexity of the composition.|
    |Service granularity| a design consideration to provide optimal scope at the right granular level of the business functionality in a service operation.|
    |Service normalization| services are decomposed and/or consolidated to a level that minimizes redundancy, for performance optimization, access, and aggregation.|
    |Service optimization| high-quality services that serve specific functions are generally preferable to general purpose low-quality ones.|
    |Service relevance| functionality is presented at a level of granularity recognized by the user as a meaningful service.|
    |Service encapsulation| many services are consolidated for use under a SOA and their inner workings hidden.|
    |Service location transparency| the ability of a service consumer to invoke a service regardless of its actual location in the network.|client only use url to use the service on the web regardless of location of service

### Web Services
1. Web Services & SOA
    - Web Services = SOA for the Web
    - Both use HTTP, hence can run over the web (although SOAP/WS often run over other protocols as well)
    - Web services used to implement SOA
2. Web Services flavor
    - (main focus of the lecture) SOAP-based Web Services
    - (main focus of the lecture) ReST-based Web Services
        - Both flavours to call services over HTTP
    - Geospatial services (WFS, WMS, WPS…)
    - Health services (HL7)
    - SDMX (Statistical Data Markup eXchange)
        - approach the statistical data around the world
3. SOAP/WS v.s. ReST  
    SOAP(Simple Object Access Protocol)

    |ReST|SOAP/WS|
    |---|---|
    is centered around resources, and the way they can be manipulated (added, deleted, etc.) remotely|built upon the <u>Remote Procedure Call paradigm (a language independent function call that spans another system)</u>|
    |Actually ReST is more of a style to use HTTP than a separate protocol|while SOAP/WS is a stack of protocols that covers every aspect of using a remote service, from service discovery, to service description, to the actual request/response|

### ReST-based Web Services
1. What is ReST?  
Representational State Transfer (ReST) is intended to evoke an image of how a well-designed Web application behaves: a network of web pages (a virtual state-machine), where the user progresses through an application by selecting links (state transitions), resulting in the next page (representing the next state of the application) being transferred to the user and rendered for their use.
2. How it works?
    - <img src="./docs/10.png" width="50%" height="50%" />
    - Client wants to access a service (Amazon) a product and things come back
        ```
        1. Clients requests Resource through Identifier (URL)
        2. Server/proxy sends representation of Resource 
        3. This puts the client in a certain state. 
        4. Representation contains URLs allowing navigation.
        5. Client follows URL to fetch another resource.
        6. This transitions client into yet another state.
        7. Representational State Transfer!
        ```
4. Resource  
    is anything that’s important enough to be referenced as a thing in itself.
    - e.g.: 
        ```
        If your users might
        - want to create a hypertext link to it
        - make or refute assertions about it
        - retrieve or cache a representation of it
        - include all or part of it by reference into another representation
        - annotate it
        - or perform other operations on it
                    ...then you should make it a resource.
        ```
3. Resource-Oriented Architecture (ROA) v.s. ReST/WS  
    is a way of turning a problem into a RESTful web service:   
    an arrangement of URIs, HTTP, and XML that works like the rest of the Web
4. ROA procedure
    ```
    1. Figure out the data set 
    2. Split the data set into resources and for each kind of resource 
    3. Name the resources with URIs 
    4. Expose a subset of the uniform interface 
    5. Design the representation(s) accepted from the client 
    6. Design the representation(s) served to the client 
    7. Integrate this resource into existing resources, using hypermedia links and forms 
    8. Consider the typical course of events: what’s supposed to happen? - How would a user interact with it?
    9. Consider error conditions: what might go wrong?
    ```

### Not included:
- ReST Uniform Interface 
- ReST Best Practice
- HTTP
    - errors commonly made
    - safe, ...

## Week 7 – Big Data and CouchDB
### "Big data" challenges and architectures
#### challenge
1. four "Vs"

    |||
    |---|---|
    |Volume| yes, volume (Giga, Tera, Peta, …) is a criteria, but not the only one
    |Velocity| **the frequency (that data arrive)** at which new data is being brought into the system and analytics performed
    |Variety| **the variability and complexity** of data schema. The more complex the data schema(s) you have, the higher the probability of them changing along the way, adding more complexity.
    |Veracity| **the level of trust** in the data accuracy (provenance); the more diverse sources you have, the more unstructured they are, the less veracity you have.

2. Big Data Calls for Ad hoc Solutions
    - While Relational DBMSs are extremely good at ensuring consistency, they rely on normalized data models that, in a world of big data (think about Veracity and Variety) can no longer be taken for granted.
    - Therefore, it makes sense to use DBMSs that are built upon data models that are not relational (relational model: tables and relationships amongst tables).
    - While there is nothing preventing SQL to be used in distributed environments, alternative query languages have been used for distributed databases, hence they are sometimes called NoSQL DBMSs

3. DBMSs for Distributed Environments

    |||
    |---|---|
    |key-value store|is a DBMS that allows the retrieval of a chunk of data given a key: **fast, but crude** (e.g. Redis, PostgreSQL Hstore, Berkeley DB)
    |BigTable DBMS store|data in columns grouped into column families, with rows potentially containing different columns of the same family (e.g. Apache Cassandra, Apache Accumulo) for **quick retrive**
    |Document-oriented DBMS store|data as structured documents, usually expressed as XML or JSON (e.g. Apache CouchDB, MongoDB)

    - Why Document-oriented DBMS for Big data?
    While Relational DBMSs are extremely good for ensuring consistency and availability, the normalization that lies at the heart of a relational database model implies fine-grained data, which are less conducive to partition-tolerance than coarse-grained data.
        - Example:
            -  A typical contact database in a relational data model may include: a person table, a telephone table, an email table and an address table, all relate to each other.
            -  The same database in a document-oriented database would entail one document type only, with telephones numbers, email addresses, etc., nested as arrays in the same document.

4. Brewer’s CAP Theorem
    - Consistency, Availability, Partition-Tolerance

        |||
        |---|---|
        |Consistency|every client receiving an answer receives **the same answer** from all nodes in the cluster
        |Availability|every client receives **an answer** from any node in the cluster 
        |Partition-Tolerance|the cluster **keeps on operating** when one or more nodes cannot communicate with the rest of the cluster
    - Brewer’s CAP Theorem: you can only pick any two of Consistency, Availability and Partition-Tolerance.
        - <img src="./docs/13.jpg" width="30%" height="50%" />
        - While the theorem shows all three qualities are symmetrical, Consistency and Availability are at odds when a Partition happens
        - “Hard” network partitions may be rare, but “soft” ones are not (a slow node may be considered dead even if it is not); ultimately, every partition is detected by a timeout
        - Can have consequences that impact the cluster as a whole, e.g. a distributed join is only complete when all sub-queries return
        - Traditional DBMS architectures were not concerned with network partitions, since all data were supposed to be in a small, co-located cluster of servers
        - The emphasis on numerous commodity servers, can result in an increased number of hardware failures
        - The CAP theorem forces us to consider trade-offs among different options

5. CAP Theorem and the Classification of Distributed Processing Algorithms
    - <img src="./docs/14.jpg" width="30%" height="50%" />

    1. Two phase commit: Consistency and Availability
        - This is the usual algorithm used in relational DBMS's (and MongoDB, to same extent)

            ||what does it entail?|by|
            |---|---|---|
            |enforces consistency|every database is in a consistent state, and all are left in the same state|1. locking data that are within the transaction scope <br/>2. performing transactions on write-ahead logs <br/>3. completing transactions (commit) only when all nodes in the cluster have performed the transaction <br/>4. aborts transactions (rollback) when a partition is detected
            |reduced availability|data lock, stop in case of partition
        - Therefore, two-phase commit is a good solution when the cluster is co-located, less good when it is distributed
    2. Paxos: Consistency and Partition-Tolerance
        - This family of algorithms is driven by consensus, and is both partition-tolerant and consistent
        - In Paxos, every node is either a proposer or an accepter:
            - a proposer proposes a value (with a timestamp)
            - an accepter can accept or refuse it (e.g. if the accepter receives a more recent value)
            - When a proposer has received a sufficient number of acceptances (a quorum is reached), and a confirmation message is sent to the accepters with the agreed value
        - Paxos clusters can recover from partitions and maintain consistency, but the smaller part of a partition (the part that is not in the quorum) will not send responses, hence the availability is compromised
    3. Multi-Version Concurrency Control (MVCC): Availability and Partition-tolerance
        - MVCC is **a method to ensure availability** (every node in a cluster always
accepts requests), and **some sort of recovery from a partition** by reconciling
the single databases with revisions (data are not replaced, they are just given
a new revision number)
        - In MVCC, **concurrent updates are possible without distributed locks** (in
optimistic locking only the local copy of the object is locked), since the
updates will have different revision numbers; the transaction that completes
last will get a higher revision number, hence will be considered as the current
value.
        - In case of cluster partition and concurrent requests with the same revision
number going to two partitioned nodes, both are accepted, but once the
partition is solved, there would be a conflict. Conflict that would have to be
solved somehow (CouchDB returns a list of all current conflicts, which are
then left to be solved by the application).


#### Architecture
1. Clustered database architecture
- Distributed databases are run over “clusters”, that is, sets of connected computers
- Clusters are needed to: 
    - Distribute the computing load over multiple computers, e.g. to improve availability
    - Storing multiple copies of data, e.g. to achieve redundancy 
- Consider two document-oriented DBMSs (CouchDB and MongoDB) and their typical cluster architectures

2. CouchDB Cluster Architecture
- <img src="./docs/11.jpg" width="30%" height="50%" />
- All nodes answer requests (read or write) at the same time
    - no master
- Sharding (splitting of data across nodes) is done on every node
    - if a read request to shard A to node 1, then node 1 answer it
    - if a read request to shard A to node 2, then redirect it to node 1 or node 3 answer it
- When a node does not contain a document (say, a document of Shard A is requested to Node 2), the node requests it from another node (say, Node 1) and returns it to the client
- Nodes can be added/removed easily, and their shards are re-balanced automatically upon addition/deletion of nodes
- In this example there are 3 nodes, 4 shards and a replica number of 2
    - replica: copy of data

3. MongoDB Cluster Architecture
- <img src="./docs/12.jpg" width="30%" height="50%" />
- Sharding (splitting of data) is done at the replica set level, hence it involves more
than one cluster (a shard is on top of a replica set)
- Only the primary node in a replica set answers write requests, but read requests
can -depending on the specifics of the configuration- be answered by every node
(including secondary nodes) in the set 
- Updates flow only from the primary to the secondary
    - If a primary node fails, or discovers it is connected to a minority of nodes, a
secondary of the same replica set is elected as the primary
- Arbiters (MongoDB instances without data) can assist in breaking a tie in elections.
- Data are balanced across replica sets - Since a quorum has to be reached, it is better to have an odd number of voting members (the arbiter in this diagram is only illustrative)

4. MongoDB vs CouchDB Clusters

    ||CouchDB|MongoDB|
    |---|---|---|
    |clusters are (difference in API)|less complex|more complex
    |clusters are|more available|less available, as - by default - only primary nodes can talk to clients for read operations, (and exclusively so for write operations)
    |software routers|while any HTTP client can connect to CouchDB|(MongoS) must be embedded in application servers
    |Losing two nodes|out of three in the CouchDB architecture shown, means **losing access to one quarter of data**|in the MongoDB example implies **losing write access** to half the data (although there are ten nodes in the cluster instead of three), and possibly read access too, depending on the cluster configuration parameters and the nature (primary or secondary) of the lost nodes|
    |Some features (such as unique indexes)||not supported in MongoDB sharded environmen
    |Classification of Distributed Processing Algorithms|uses MVCC|uses a mix of two-phase commit (for replicating data from primary to secondary nodes) and Paxos-like (to elect a primary node in a replica-set)|
    |emphasis on and all have partition-tolerance|Availability|consistency|

- These differences are rooted in different approaches to an unsolvable problem, a problem defined by Brewer’s CAP Theorem
    - first 5
- The different choices of strategies explains the different cluster architectures of these two DBMSs
    - last 2

5. Sharding
    - What is it?  
        Sharding is the partitioning of a database “horizontally”, i.e. the database
    rows (or documents) are partitioned into subsets that are stored on different
    servers. Every subset of rows is called a shard.
    - Usually the number of shards is larger than the number of replicas, and the
    number of nodes is larger than the number of replicas (usually set to 3)
    - The number of shards that split a database dictates the (meaningful) number
    of nodes: the maximum number of nodes is equal to the number of shards
    (lest a node contains the same shard file twice)
    - The main advantage of a sharded database lies in the
        - improvement of performance through the distribution of computing load across nodes. 
            - i.e.: better distribution of data
        - In addition, it makes it easier to move data files around, 
            - e.g. when adding new nodes to the cluster
    - There are different sharding strategies, most notably:
        |||
        |---|---|
        |Hash sharding|to distribute rows evenly across the cluster|
        |Range sharding|similar rows (say, tweets coming for the same area) that are stored on the same node|

6. Replication and Sharding
    - What is replication?   
        Replication is the action of storing the same row (or document) on different nodes to make the database fault-tolerant.
    - Replication and sharding can be combined with the objective of maximizing availability while maintaining a minimum level of data safety.
    - A bit of nomenclature:
        - n is the number of replicas (how many times the same data item is repeated across the cluster)
        - q is the number of shards (how many files a database is split)
        - n * q is the total number of shard files distributed in the different nodes of the cluster

7. Partitions
    - What is it?  
        A partition is a grouping of logically related rows in the same shard
(for instance, all the tweets of the same user)
    - Advantage:  
    Partitioning improves performance by restricting queries to a single     shard
        - To be effective, partitions have to be relatively small (certainly
    smaller than a shard)
    - A database has to be declared “partitioned” during its creation
    - Partitions are a new feature of CouchDB 3.x

8. MapReduce Algorithms
    - What is it?  
        This family of algorithms, pioneered by Google, is particularly suited to parallel computing of the Single-Instruction, Multiple-Data type (see Flynn's taxonomy in a previous lecture).
    - Advantage:  
        Apart from parallelism, its advantage lies in moving the process to where data are, greatly reducing network traffic.
    - Procedure:  
        1. (Map), distributes data across machines, while 
        2. (Reduce) hierarchically summarizes them until the result is obtained.

                function map(name, document):
                    for each word w in document:
                        emit (w, 1)
                function reduce(word, partialCounts):
                    sum = 0
                    for each pc in partialCounts:
                        sum += pc
                    emit (word, sum)
    

### Introduction to CouchDB


### Note: not summarized
- Addendum: The Peculiar Case of the Blockchain
- Part 2: Introduction to CouchDB, recording 07:: 01:15:16


## Week 8.1 – Virtualisation
Terminology
- <img src="./docs/15.png" width="30%" height="30%" />
- 
    |||
    |---|---|
    |Virtual Machine Monitor/Hypervisor|The virtualisation layer between the underlying hardware the virtual machines and guest operating systems it supports.
    |Virtual Machine|A representation of a real machine using hardware/software that can host a guest operating system
    |Guest Operating System|An operating system that runs in a virtual machine environment that would otherwise run directly on a separate physical system.
1. What happens in a VM?
- <img src="./docs/16.jpg" width="70%" height="30%" />
2. Motivation ~~& History~~
    |||
    |---|---|
    |Server Consolidation|1. Increased utilisation<br/>2. Reduced energy consumption
    |Personal virtual machines can be created on demand|1. No hardware purchase needed<br/>2. Public cloud computing - won't lockin Amazon
    |Security/Isolation|Share a single machine with multiple users - won't want everyone see what you are doing
    |Hardware independence|Relocate to different hardware
3. Classification of Instructions
    ||||
    |---|---|---|
    |Privileged Instructions|instructions that trap if the processor is in user mode and do not trap in kernel mode
    |Sensitive Instructions|instructions whose behaviour depends on the mode or configuration of the hardware|Different behaviours depending on whether in user or kernel mode<br/>e.g. POPF interrupt (for interrupt flag handling)
    |Innocuous Instructions|instructions that are neither privileged nor sensitive|Read data, add numbers etc

    - Popek and Goldberg Theorem  
        For any conventional third generation computer, a virtual machine monitor may be constructed if the set of **sensitive instructions** for that computer is a subset of the set of **privileged instructions** i.e. have to be trappable
    - x86 architecture was historically not virtualisable, due to sensitive instructions that could not be trapped
    - Intel and AMD introduced extensions to make x86 virtualisable
3. What are the requirements for virtualisation?
    - <img src="./docs/17.jpg" width="40%" height="30%" />
    |||Achieved by|problem|
    |---|---|---|---|
    |De-privileging|trap-and-emulate: VMM emulates the effect on system/hardware resources of privileged instructions whose execution traps into the VMM|running GuestOS at a lower hardware priority level than the VMM|Problematic on some architectures where privileged instructions do not trap when executed at de-privileged level
    |Primary/shadow structures|1. VMM maintains “shadow” copies of critical structures whose “primary” versions are manipulated by the GuestOS, e.g. memory page tables<br/>2. Primary copies needed to insure correct versions are visible to GuestOS
    |Memory traces|Controlling access to memory so that the shadow and primary structure remain coherent|write-protect primary copies so that update operations cause page faults which can be caught, interpreted, and addressed - Someones app/code doesn’t crash the server you are using!!!
4. Virtualisation approaches
    |||e.g.|Advantages|Disadvantages|
    |---|---|---|---|---|
    |Full virtualisation|allow an unmodified guest OS to run in isolation by simulating full hardware - Guest OS has no idea it is not on physical machine|VMWare|1. Guest is unaware it is executing within a VM<br/>2. Guest OS need not be modified<br/>3. No hardware or OS assistance required<br/>4. Can run legacy OS|1. can be less efficient|
    |Para-virtualisation|VMM/Hypervisor exposes special interface to guest OS for better performance. Requires a modified/hypervisor-aware Guest OS - Can optimise systems to use this interface since not all instructions need to be trapped/dealt with|Xen|1. Lower virtualisation overheads, so better performance|1. Need to modify guest OS - Can’t run arbitrary OS!<br/>2. Less portable<br/>3. Less compatibility<br/>
    |Hardware-assisted virtualisation|Hardware provides architectural support for running a Hypervisor<br/>- New processors typically have this<br/>- Requires that all sensitive instructions trappable|KVM|1. Good performance<br/>2. Easier to implement<br/>3. Advanced implementation supports hardware assisted DMA, memory virtualisation|1. Needs hardware support
    |Binary Translation|– Trap and execute occurs by scanning guest instruction stream and replacing sensitive instructions with emulated code - Don’t need hardware support, but can be much harder to achieve|VMWare|1. Guest OS need not be modified<br/>2. No hardware or OS assistance required<br/>3. Can run legacy OS|1. Overheads<br/> 2. Complicated<br/> 3. Need to replace instructions “on-the-fly”<br/> 4. Library support to help this, e.g. vCUDA
    |Bare Metal Hypervisor|VMM runs directly on actual hardware<br/>- Boots up and runs on actual physical machine<br/>- VMM has to support device drivers, all HW mgt |VMWare ESX Server
    |Hosted Virtualisation|VMM runs on top of another operating system|VMWare Workstation
    |Operating System Level Virtualisation|1. Lightweight VMs<br/>2. Instead of whole-system virtualisation, the OS creates mini-containers|Docker|1. Lightweight<br/>2. Many more VMs on same hardware<br/>3. Can be used to package applications and all OS dependencies into container|1. Can only run apps designed for the same OS<br/>2. Cannot host a different guest OS<br/>3. Can only use native file systems<br/>4. Uses same resources as other containers
    - <img src="./docs/18.jpg" width="60%" height="30%" />  for Full virtualisation, Hardware-assisted virtualisation, Binary Translation
    - <img src="./docs/19.jpg" width="40%" height="30%" /> for Para-virtualisation
5. Memory management
    - <img src="./docs/20.jpg" width="40%" height="30%" />
        
        - In conventional case, page tables store the logical page number and physical page number mappings
    - <img src="./docs/21.jpg" width="40%" height="30%" />
        
        - In VMM case, VMM maintains shadow page tables in lock-step with the page tables. Additional management overhead is added.
    - Shadow Page Tables
        - <img src="./docs/22.jpg" width="40%" height="30%" />
        - VMM maintains shadow page tables in lock-step with the page tables
        - Adds additional management overhead
        - Hardware performs guest -> physical and physical -> machine translation
6. Live migration

    having continuity of service during data moving

## Week 8.2 – OpenStack & Comparing and Contrasting AWS with NeCTAR Cloud

TODO: Lecture 08: 00:44:19

## Week 8.3 - Serverless (Function as a Service (FaaS))
1. Why Functions?
    - A function in computer science is typically a piece of code that takes in parameters and returns a value
    - Functions are the founding concept of functional programming - one of the oldest programming paradigms
    - Why they are used in Faas?
    - Functions are free of 
        - side-effects, 
            - What is it?
                - A function that does not modify the state of the system
                    - e.g.: a function that takes an image and returns a thumbnail of that image
                - A function that changes the system somehow is not side-effect free
                    - e.g.: a function that writes to the file system the thumbnail of an image
            - How Side-effect free benefits parallel execition?
                - Side-effect free functions can be run in parallel, and are guaranteed to return the same output given the same input
            - How it benefits FaaS?
                - Side-effects are almost inevitable (不可避免的) in a relatively complex system. 
                Therefore consideration must be given on how to make functions with side effects run in parallel, as typically required in FaaS environments.
        - ephemeral (短暂的;瞬息的),
            - Synchronous/Asynchronous Functions
            - Relationship to FaaS
                - By default functions in FaaS are synchronous, hence they return their result immediately
                - However, there may be functions that take longer to return a result, hence they incur timeouts and lock connections with clients in the process, hence it is better to transform them into asynchronous functions
                    - a publish/subscribe pattern involving a queuing system can be used to deal with asynchronous functions
            - How them work?
                |Function|How|
                |---|---|
                |Synchronous functions|return their result immediately
                |Asynchronous functions|return a code that informs the client that the execution has started, and then trigger an event when the execution completes
        - stateless, 
            - What is it?
                - A subset of functions with side-effects is composed of stateful functions 
                    |||e.g.|
                    |---|---|---|
                    |stateful function|is one whose output changes in relation to internally stored information (hence its input cannot entirely predict its output)| a function that adds items to a "shopping cart" and retains that information internally
                    |stateless function|is one that does not store information internally|adding an item to a "shopping cart" stored in a DBMS service and not internally would make the function above stateless, but not side-effect free.
            - Why it is important for FaaS?
                - Because there are multiple instances of the same function, and there is no guarantee the same user would call the same function instance twice.
        - which make them ideal for 
            - parallel execution and 
            - rapid scaling-up and -down
2. Function & FaaS
    - Side effects
    - stateful & stateless
    - Synchronous/Asynchronous Functions

3. What is Function as a Service (FaaS)?
    - FaaS is also know as Serverless computing
    - FaaS is an extreme form of microservice architecture
    - The idea behind Serverless/FaaS is to develop software applications without bothering with the infrastructure (especially scaling-up and down as load increases or decreases). Therefore, it is more Server-unseen than Server-less
    - What does it do?
        - A FaaS service allows functions to be added, removed, updated, executed, and auto-scaled
4. Why we need Faas?
    |Reason|How|
    |---|---|
    |Simpler deployment|the service provider takes care of the infrastructure
    |Reduced computing costs|only the time during which functions are executed is billed
    |Reduced application complexity|due to loosely-coupled architecture
5. FaaS application
    - Functions are triggered by events
    - Functions can call each other
    - Functions and events can be combined to build software applications
    - Combining event-driven scenarios and functions resembles how User Interface software is built: user actions trigger the execution of pieces of code
    - E.g.: 
        - Amazon’s AWS Lambda
        - Google Cloud Functions
        - Azure Functions by Microsoft
6. proprietary FaaS services v.s. open-source FaaS frameworks
    - open-source FaaS frameworks can be deployed on your cluster, peered into, disassembled, and improved by you.

## Week 9 - Big Data Analytics
1. Why we need it?
    - There would not be much point in amassing vast amount of data without being able to analyse it, hence the blossoming of large-scale business intelligence and more complex machine learning algorithms. 
2. What is it?
    - There is a good deal of overlap and confusion among terms such as business intelligence, machine learning, statistics, and data mining. For the sake of clarity, we just use the more general term (big) data analytics
3. Examples of Analytics
    ||
    |---|
    |Full-text searching
    |Aggregation of data
    |Clustering
    |Sentiment analysis
    |Recommendations
4. Challenges of Big Data Analytics
    - A framework for analysing big data has to distribute both data and processing over many nodes, which implies:
        |imply||
        |---|---|
        |Reading and writing distributed datasets
        |Preserving data in the presence of failing data nodes
        |Supporting the execution of MapReduce tasks
        |Being fault-tolerant|a few failing compute nodes may slow down the processing, but not stop it
        |Coordinating the execution of tasks across a cluster
5. Tools for Analytics:
    - Apache Hadoop
    - Apache Spark
### Apache Hadoop
1. How it works?
    - Apache Hadoop started as a way to distribute files over a cluster and execute MapReduce tasks, but many tools have now been built on that foundation to add further functionality
2. Hadoop Distributed File System (HDFS)
    - What is it?
        - The core of Hadoop is a fault tolerant file system that has been explicitly designed to span many nodes
    - HDFS blocks v.s. blocks
        - HDFS blocks are much larger than blocks used by an ordinary file system (say, 4 KB versus 128MB)
        - Why?
            ||How achieve it?|
            |---|---|
            |Reduced need for memory to store information about where the blocks are|metadata
            |More efficient use of the network|with a large block, a reduced number network connections needs to be kept open
            |Reduced need for seek operations on big files
            |Efficient when most data of a block have to be processed
    - HDFS Architecture
        - A HDFS file is a collection of blocks stored in datanodes, with metadata (such as the position of those blocks) that is stored in namenodes
        - <img src="./docs/23.png" width="60%" height="50%" />
3. The Hadoop Resource Manager (YARN)
    - Lecture 09:: 00:22:10
4. The HDFS Shell
5. Programming on Hadoop
### Apache Spark
1. Why Spark not Hadoop?
    - While Hadoop MapReduce works well, it is geared towards performing relatively simple jobs on large datasets.
    - However, when complex jobs are performed (say, machine learning or graph-based algorithms), there is a strong incentive for caching data in memory and in having finer-grained control on the execution of jobs.
    - Apache Spark was designed to reduce the latency inherent in the Hadoop approach for the execution of MapReduce jobs.
    - Spark can operate within the Hadoop architecture, using YARN and Zookeeper to manage computing resources, and storing data on HDFS.
2. Spark Architecture
    - One of the strong points of Spark is the tightly-coupled nature of its main components
        - <img src="./docs/24.jpg" width="60%" height="50%" />
    - Spark ships with a cluster manager of its own, but it can work with other cluster managers, such as YARN or MESOS.
3. The Spark Shell
    - Lecture 09:: 00:39:50
4. Programming on Spark
    - Lecture 09:: 00:34:24
5. Spark Runtime Architecture
    - Lecture 09:: 00:48:44
6. Resilient Distributed Dataset (RDDs) (Central to Spark)
    - What is it?
        - the way data are stored in Spark during computation, and understanding them is crucial to writing programs in Spark:
            ||What?|
            |---|---|
            |Resilient|data are stored redundantly, hence a failing node would not affect their integrity
            |Distributed|data are split into chunks, and these chunks are sent to different nodes
            |Dataset|a dataset is just a collection of objects, hence very generic
    - Properties of RDDs
        - RDDs are
            |Property||benefit
            |---|---|---|
            |immutable|once defined, they cannot be changed|simplifies parallel computations on them, and <br/>is consistent with the functional programming paradigm
            |transient|they are meant to be used only once, then discarded (but they can be cached, if it improves performance)|
            |lazily-evaluated|the evaluation process happens only when data cannot be kept in an RDD, as when the number of objects in an RDD has to be computed, or an RDD has to be written to a file (these are called actions), but not when an RDD are transformed into another RDD (these are called transformations)
7. Spark Jobs, Tasks, and Stages
    - Lecture 09:: 01:24:05

## Week 10.1 – Security and Clouds
1. Why is security so important?
    - If systems (Grids/Clouds/outsourced infrastructure!) are not secure 
        - Large communities will not engage
            - medical community, industry, financial community, etc they will only use their own internal resources, e.g.: private clouds!
        - Expensive to repeat some experiments
            - Huge machines running large simulations for several years
        - Legal and ethical issues possible to be violated with all sorts of consequences
            - e.g. data protection act violations and fines incurred
                - Amazon Web Services, Sydney
        - Trust is easily lost and hard to re-establish
2. The Challenge of Security
    - Grids and Clouds (IaaS) allow users to compile codes that do stuff on physical/virtual machines
        - In the Grid world a rich blend of facilities co-existed (were accessible/integrated!) which had "issues" - prevent people do bad staff
            - Highly secure supercomputing facilities compromised by single user PCs/laptops
            - Need security technologies that scales to meet wide variety of applications 
        - Using services for processing of patient data through to “needle in haystack” searching of physics experiments
    - Should try to develop generic security solutions
        - Avoid all application areas re-inventing their own (incompatible/inoperable) solutions
    - Clouds allow scenarios that stretch inter-organisational security
        - Policies that restrict access to and usage of resources based on pre-identified users, resources
            - Groups/tenancy…
        - But what if new resources added, new users added, old users go…?
            - Over-subscription issues
            - User management (per user, per team, per organisation, per country…)
        - What if organisations decide to change policies governing access to and usage of resources, or bring their data back inside of their firewall?
            - Really not replicated somewhere else?
        - What if you share a tenancy with a noisy neighbour!
            - I/O demanding applications
                - You hopefully never experienced this, but early NeCTAR RC had performance issues!
        - The multi-faceted challenges of ”life beyond the organisational firewall”?

- What do we mean by security anyway?
    - Secure from whom?
        - From sys-admin?
        - From rogue employee?

- Secure against what?
    - Security is never black and white but is a grey landscape where the context determines the accuracy of how secure a system is
        - e.g. secure as given by a set of security requirements
- Note that security technology ≠ secure system
    - Ultra secure system using 2048+ bit encryption technology, packet filtering firewalls, …
        - on laptop in unlocked room
        - on PC with password on “post-it” on screen/desk
        - the challenge of peta/exa-scale computers and possibility for brute force cracking

- Technical Challenges of Security
    - All are important but some applications/domains have more emphasis on concepts than others
    - Key is to make all of this simple/transparent to users!
    - <img src="./docs/25.jpg" width="60%" height="50%" />
    - Single sign-on
        - **The Grid model (and Shib model!) needed**
        - **Currently not solved for Cloud-based IaaS**
        - Onus (责任) is on non-Cloud developers to define/support this
    - Auditing 
        - logging, intrusion detection, auditing of security in external computer facilities 
            - **well established in theory and practice and for local systems**
                - Less mature in Cloud environments (beyond the firewall!)
            - Tools to support generation of diagnostic trails 
                - Across federations of Clouds?
                - Log/keep all information?
                - For how long?
    - Deletion (and encryption!!!)
        - **Data deletion with no direct hard disk** (might cost a lot of money to delete it)
            - Many tools and utilities don’t work!
        - Scale of data
            - Securely deleting a few Mb easy enough
            - Try to delete a few Tb+?
    - Liability
        - notice risk when put data here
    - Licensing
        - Challenges with the Cloud delivery model (Where can jobs realistically run)
        - Many license models
            - Per user
            - Per server
            - Per organisation
            - Floating licenses
            - Fixed to machines
    - Workflows
        - Many workflow tools for combing SoA services/data flows
            - Taverna, Pegasus, Galaxy, Kepler, Nimrod, OMS, …
        - **Many workflows models**
            - Orchestration (**centralised** definition/enactment),
            - Choreography (**decentralised**)
        - Serious challenges of 
            - defining, 
            - enforcing, 
            - sharing, 
            - enacting 
        - security-oriented workflows
    - The Ever Changing Technical/Legal Landscape 
        - requirements and guarantee on cloud using

- Authentication
    - prove who you are
    - What is it?
        - Authentication is <u>**the establishment and propagation of a user’s identity in the system**</u>
        - e.g. so site X can check that user Y is attempting to gain access to it’s resources
            - Note <u>**does not check what user is allowed to do, only that we know (and can check!) who they are**</u>
                - <u>**Masquerading always a danger**</u> (and realistic possibility)
                - Security guidance/balances
                    - Password selection
                        - 16 characters, upper/lower case and must include nonalphanumeric characters and be changed quarterly…!?!?!?!
                    - Treatment of certificates
        - Local username/password?
            - 100,000+ users that come and go
        - Centralised vs decentralised systems?
            - More scalable solution needed
        - Decentralised Authentication (Proof of Identity) thru Shibboleth
            - <img src="./docs/28.jpg" width="70%" height="50%" />
            - Supports Single-Sign On (in case you were unaware)
        - Public Key Infrastructures (PKI) underpins MANY systems
            - What is it?
                - an arrangement that binds public key with respective identities of entities(like people and organization). 
                - The binding is established through a process of registration and issurance of certificates at and by a certificate authority 
                - The PKI role that assures valid and correct registration is called a registration authority(RA). RA is responsible for accepting requests for digital certificates and authenticating the entity making the reques
            - Based on public key cryptography
            - Public Key Cryptography
                - Also called Asymmetric Cryptography
                    - Two distinct keys
                        - One that must be kept private
                            - Private Key
                        - One that can be made public
                            - Public Key
                    - Two keys complementary, but essential that cannot find out value of private key from public key
                        - With private keys can digitally sign messages, documents and validate them with associated public keys
                            - Check whether changed, useful for non-repudiation
                - Public Key Cryptography simplifies key management
                    - Don’t need to have many keys for long time
                        - The longer keys are left in storage, more likelihood of their being compromised
                            - Instead use Public Keys for short time and then discard
                            - Public Keys can be freely distributed
                        - Only Private Key needs to be kept long term and kept securely
            - PKI and Cloud
                - So what has this got to do with Cloud…?
                    - IaaS – key pair!
                - Cloud inter-operability begins with security!
                    - There is no single, ubiquitous CA, there are many
                - There are many ways to prove your identity
                    - OpenId, FacebookId, Visa credit card for Amazon, …
                        - Degrees of trust 
                    - But remember need for single sign-on
                    - Prove identity once and access distributed, autonomous resources!
            - Public Key Certificates
                - (PKC & PKI) Mechanism connecting public key to user with corresponding private key is Public Key Certificate 
                    - Public key certificate contains public key and identifies the user with the corresponding private key
                        - Distinguished Name (DN): CN=Richard Sinnott; OU=Dept CIS; O=UniMelb; C=AU
                    - Not a new idea
                        - Business card
                            - My name, my association, contact details, …
                                - Can be distributed to people I want to exchange info with
                            - If include public key on it, then have basic certificate, but
                                - has to be delivered in person (or no trust!), who says I work at Melbourne?, could be a forgery, I might be an impostor, what if I move to Monash or my phone number changes, who would have 1024-bit key on business card, …
                - Public Key Certificates & Certification Authority
                    - Public Key Certificates issued by trusted "Certification Authority"
            - Certification Authority
                - What it it?
                    - <u>**Central component of PKI is Certification Authority (CA)**</u>
                - CA has numerous responsibilities 
                    - <u>**Policy and procedures**</u>
                        - How to’s, do’s and don’ts of using certificates 
                        - Processes that should be followed by users, organisations, service providers …(and consequence for violating them!)
                - Issuing certificates
                    - Often need to delegate to local Registration Authority
                    - Prove who you are, e.g. with passport, student card
                - Revoking certificates
                    - Certificate Revocation List (CRL) for expired/compromised certificates
                - Storing, archiving 
                    - Keeping track of existing certificates, various other information, …
                - models
                    - <img src="./docs/26.jpg" width="60%" height="50%" />
                - Typical Simple CA
                    - Based on statically defined centralised CA with direct single hierarchy to users
                    - Typical scenario for getting a certificate
                    - steps:
                    - <img src="./docs/27.jpg" width="60%" height="50%" />
- Authorisation
    - What is it?
        - Authorisation is concerned with controlling access to resources based on policy 
            - Can this user invoke this service, make use of this data?
            - Complementary to authenticationL Know it is this user, now can we restrict/enforce what they can/cannot do
    - Many different approaches for authorisation
        |approach|e.g.|
        |---|---|
        |Group Based Access Control|your project VMs
        |Role Based Access Control|RBAC
        |Identity Based Access Control|IBAC
        |Attribute Based Access Control|ABAC
    - Authorisation and Clouds
        - Authorisation typically applies to services/data deployed on Clouds, i.e. when they are running 
        - But not only… 
            - Who can install this patch, when can they do it, how many VMs will be affected if this happens…?
            - Is this virtual image free of trojans, malware etc?
            - Lots of tools to support this: Pakiti, Cfengine, Puppet, …
            - Real challenge of software dependency management for complex systems
                - Amazingly (?) most users/organisations do not patch!!! 
                - Side-effects, complexities, stopping jobs, restarting jobs etc
    - What does it do?
        - Defining what they can do and define and enforce rules
            - Each site will have different rules/regulations
    - How it is achieved?
        - Often realised through Virtual Organisations (VO)
            - Collection of distributed resources shared by collection of users from one or more organizations typically to work on common research goal
                - Provides conceptual framework for rules and regulations for resources to be offered/shared between VO institutions/members 
                - Different domains place greater/lesser emphasis on expression and enforcement of rules and regulations (policies)
    - Many Technologies
        - XACML, PERMIS, CAS, VOMS, AKENTI, VOMS, SAML, WS-*
    - typical model: RBAC
        - Basic idea is to define:
            - **roles** applicable to specific collaboration
                - roles often hierarchical
                    - Role X ≥ Role Y ≥ Role Z
                    - X can do everything and more than Y who can do everything and more than Z
            - **actions** allowed/not allowed for VO members
            - **resources** comprising VO infrastructure (computers, data etc)
            - A policy then consists of sets of these rules
                - { Role x Action x Target }
                    - Can user with VO role X invoke service Y on resource Z?
                - Policy itself can be represented in many ways, 
                    - e.g. XML document, SAML, XACML, …
            - Standards on when/where these used (PEP) and enforced (PDP)
            - Policy engines consume this information to make access decisions
    - Should all be transparent to end users!
    - Reflect needs and understanding of organisations involved!







Consider the Passport vs Frequent Customer Shopping experience



## recap
recording 10 01:29:00






