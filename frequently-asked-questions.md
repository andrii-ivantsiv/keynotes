# frequently-asked-questions

### Messaging:
1. Acknowledge types? (JMS Kafka)
   - 0 - Fire and Forget
   - 1 - Leader Ack
   - 2 - Ack of all the brokers
   
2. How Kafka replicates?
   - Leader-Follower via Controller (use ZooKeeper)
   - Master-Slave in ActiveMQ, quorum
   
3. Durability?
   - A common pattern is to have the producer send the message to the topic and then have the queues subscribe to the topic. 
   This allows each queue to receive its own copy of the message. But what happens to the message if it is sent to the topic, 
   but no queues are online (remember our queues subscribe to the topic)? This is where durability comes into play. 
   When a durable subscription is set up between a queue and a topic, the queue can be offline when the message hits the topic. 
   Once the queue comes back online, the message can be received. If the subscription is non-durable, then any messages received 
   to the topic while the topic subscriber is offline will not be received by the subscriber (in this case the queue).

### VCS
1. Git flows?
   - Git flow
   - GitHub flow
   - GitLab flow
   - One flow
   
2. What is the difference between git merge and git rebase?
   - Merge:
     - Creates an extra merge commit every time you need to incorporate changes
     - Pollutes your feature branch history
   - Rebase:
     - Incorporates all the new commits in the master branch
     - Rewrites the project history by creating  brand new commits for each commit in the original branch
     
3. Branching Strategies?
   - Trunk (one branch)
   - Master and feature branches

### Deployment
1. Deployment strategies?
   - Recreate: Version A is terminated then version B is rolled out.
   - Ramped: (also known as rolling-update or incremental): Version B is slowly rolled out and replacing version A.
   - Blue/Green: Version B is released alongside version A, then the traffic is switched to version B.
   - Canary: Version B is released to a subset of users, then proceed to a full rollout.
   - A/B testing: Version B is released to a subset of users under specific condition.
   - Shadow: Version B receives real-world traffic alongside version A and doesn’t impact the response.

2. Orchestration vs choreography?
   - The choreography describes the interactions between multiple services, where as orchestration represents control 
   from one party's perspective. This means that a choreography differs from an orchestration with respect to where 
   the logic that controls the interactions between the services involved should reside.

### Architecture
1. Types of architecture design patterns?
   - Layered (n-tier) architecture
   - Component-based architecture
   - Database-centric architecture
   - Event-driven architecture
   - Service-oriented architecture
   
2. Temporal coupling?
   - Another form of coupling you may have heard of is temporal coupling. From a code-centric view of coupling, 
   temporal coupling refers to a situation in which concepts are bundled together purely because they happen at the same time. 
   Temporal coupling has a subtly different meaning in the context of a distributed system, where it refers to a situation 
   in which one microservice needs another microservice to do something at the same time for the operation to complete.