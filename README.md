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
    e.g. mapping the sky with data from tele-scope

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


