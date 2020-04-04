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
