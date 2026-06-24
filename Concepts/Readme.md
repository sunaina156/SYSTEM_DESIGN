Latency
~~~~~~~~~~~~~~
In Monolithic, 
latency = computational delay

In Microservice, 
latency = computational delay + network delay



Reducing Latency:
1. Caching
2. Content Delivery Network
3. Upgrading hardware etc


Throughput
~~~~~~~~~~~~~~~~
The volume of work or information flowing through a system
It is the amount of data transmitted per unit of time.
It is the process flow rate.
Throughput is measured in bites per second i.e. bps

In monolithic, throughput less
In distributes, it is more, no limit on reosurces, we can use load balancer


Causes of Low Throughput:
1. latency high
2. Protocol overhead
3. Congestion

Improving Throughput:
1. CDN
2. Caching
3. Use distributes system
4. load balancer
5. Improve resources

Availability
~~~~~~~~~~~~~~~~~~~
In monolithic, it is less
In distributed, it is high

Fault Tolerance proportional to Availability


To Increase Availability:
1. Replication
2. Distributed system
3. Redundancy


Consistency
~~~~~~~~~~~~~~~

When more than one client requests the system, for all such requests, it will be called
consistent when each client gets the same data. The data should always be consistent, regardless of who is 
accessing it.

When more than one client requests the system, for all such requests, when different clients get different responses due to some recent updat
that has not been committed to all systems yet, this reading operation will be called dirty read.

Monolithic is natively consistent

To Improve Consistency:
1. Improving network bandwidth
2. stop the read
3. Replication based on Distance aware strategies


Types of Consistency:
1. Strong Consistency
    when the system doesn't allow read operation until all the nodes with replicated data are updated
2. Eventual Consistency
    User Read requests ae not halted till all the replicas are updated rather the update process is eventual.
    Some users might receive old data but eventually all the data is updated to the latest data.
3. Weak Consistency


CAP Theorem
~~~~~~~~~~~~~~~~~
C - Consistency
A - Availability
P - Partition Tolerance


For a distributed system, the CAP Theorem states that it is possible to attain only two properties and the third
would be always compromised.
The system requirements should define which two properties should be chosen over the rest.

CA  - monolithic
CP - Distributed system
AP - distributed

Mainly in application, partition tolerance must be there, choice comes to Availability and consistency

Blogs website - A
Multiplayer online games - A
Stock trading platforms - C
Video streaming sites - A
Ticket booking system - C
Video chat applications - A
Bank - C


Lamport Logical Clock
~~~~~~~~~~~~~~~~~~~~~~


*******************************************************************************************************************************************************************
Scalability
~~~~~~~~~~~~~~~~

1. Vertical Scaling
pros:
easy implementation
less power supply
management is easy

cons:
single point of failure
limit
price

2. Horizontal Scaling
pros:
it overcomes cons of vertical scalability

cons:
pros of horizontal 



Replication vs Redundancy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Redundancy 
It is simply the duplication of nodes or components so that when a node or component fails,
the duplication node is available to service customers.

Active Redundancy is considered when each unit is operating/active and responding to the action. 
Multiple nodes are connected to a load balancer, and each unit receives an equal load.

Passive Redundancy is considered when one node is active or operational and the other is not operating. 
During the breakdown of the active node, the passive node maintains availability by becoming the active node.


Replication:
redundancy + synchronization
1. active
2. passive

every read - write -> mastr
if master goes down one slave becomes master

Master-slave replication can be either synchronous or asynchronous. 
The difference is simply the timing of propagation of changes. If the changes are made to the master
and slave at the same time, it is synchronous.
If changes are queued up and written later, it is asynchronous.


Load Balancer
~~~~~~~~~~~~~~~~~~
































