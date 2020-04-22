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
Representational State Transfer (ReST) is intended to evoke an image of how a well-designed Web application behaves: a network of web pages (a virtual state-machine), where the user progresses through an application by selecting links (state transitions), resulting in the next page (representing the next state of the application) being transferred to the user and rendered for their use.
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