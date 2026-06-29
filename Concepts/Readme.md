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

Roles of Load Balancer
~~~~~~~~~~~~~~~~~~~~~~~~
1. Load distribution is equal over every node.
2. Health check (if node is not operational, request is passed to another)
3. Ensures high scalability, high throughput, high availability

In monolithic or in case of vertically scaled system, load balancer not needed
In microservice architecture, we need it


Challenges of Load Balancing
1. Single Poiint of Failure


Advantages of Load Balancers:
1. Optimisation
2. Better User Experience
3. Prevents Downtime
4. Flexibility
5. Scalability
6. Redundancy


Load Balancing Algorithms:
1. Round Robin (Static)
    rotation fashion
2. Weighted Round RObin (Static)
    It is similar to ROund RObin when the servers are of different capacities. some node can have better resources, others might not have
3. IP Hash Algorithm (Static)
    The servers have almost equal capacity, and the hash function (input is source IP) is used for random or unbiased distribution of requests to the nodes.
4. Source IP Hash (Static)
    It combines the server and client's source and destination IP address to produce a hash key.
    The key can be used to determine the request distribution
5. Least Connection Algorithm (Dynamic)
    Client requests are distributed to the application server with the least number of active connections at the time the 
    client request is received.
6. Least Response Time (Dynamic)
    The request id distributed based on the server which has the least response time


Caching
~~~~~~~~~~~~~~~~~~~
Two cache:
1. In memory/local cache
ex: memcache
2. Distributed or extended cache
ex: redis

When to use:
1. read - intensive
2. static content


Cache Eviction Techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. LRU
Least Recently Used
2. MRU
Most Recently Used
3. LFU
4. FIFO
5. LIFO
6. RR
Random Replacement


*******************************************************************************************************************************************************************
File-Based storage System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
File Based Database Managment System
DBMS

Here data is stored in form of files

Challenges:
1. Data Redundancy
2. Poor Security
3. Slow


RDBMS
~~~~~~~~~~~~~~~
A software that performs data operations on relational database
Operations include store, manage, query and retrieve data.
Data is represented in form of tables.
The relationship bw two tables is represented by foreign keys.

Advantages:
1. No data redundancy and inconsistency
2. Data concurrency
3. Data searching
4. Data Integrity


Problems:
1. Rigid schema
2. high cost
3. Scalability issues
(horizontal scaling or sharding is very difficult)


Types of NoSQL Databases
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
NoSQL Databases
~~~~~~~~~~~~~~~~~~~~~~
non-sql database
it is a non-relational database


NoSQL is the umbrella term comprising of four different types of databases
1. key value db 
 key value database generally used for caching
  eg: redis
2. Document db 
 Brings best of both RDBMS and NoSQL
 It combines relationship concept from RDBMS and dynamic schema and horizontal scalinf from NoSQL databases.
 eg: MongoDB
3. Columnar db
  The colums are stored together instead of rows.
  Because of that, the aggregation in such databases is rapid. It is widely used for Data analysis.
  eg: cassandra
4. Graph db
  it represents and stores entities and relationships in form of graph data structure.
  It is majorly used for social networks.


Cart - redis
Score card - redis
Machine Learning - columnar  , cassandra
Payment - we want high consistency, we us relational db like oracle


Polyglot Persistence
~~~~~~~~~~~~~~~~~~~~~
using multiple databases


Denormalization in RDBMS
~~~~~~~~~~~~~~~~~~~~~~~~~~
Normalization:
Putting data in multiple tables to avoid redundancy

Denormalization:
It combines the data and organizes it in a single table. 
Denormalization is process of adding redundant data to the normalized relational database o optimize its performance.

Benefits of denormalization:
1. faster data read operations
2. Management convenience
3. High data availability
4. Reduces the no. of network calls to fetch data from multiple places

Challenges of denormalization:
1. Redundant data -> wastage of memory
2. It increases complexity
3. Data inconsistency
4. It will cause slow write operations since we will need to write places due to redundancy


How does Indexing work in Databases
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`
Indexing creates a lookup table with the column and the pointer to the memory location of the row, containing this column.

B-trees data structure is used to store the indexing as it is a multilevel format of tree-based indexing, which has balanced binary search trees.


Synchronization
~~~~~~~~~~~~~~~~~~~~
blocking call

Industrial use cases:
1. Stock market
2. Bank payments
3. Ticket Booking
4. Real time decision making

Asynchronous Comunication
~~~~~~~~~~~~~~~~~~~~~~~~~~
Non-blocking call


*******************************************************************************************************************************************************************
Message Based Communication
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Client sends request in form of message
receives response in form of message
It is async, so client is not required to halt the process and wait for the process.


P2P Model
Publish Subscribe Model


eg: kafka, RabbitMQ


Web Server
~~~~~~~~~~~~~~~
 Tools or programs that help keep the web application always up and running.































