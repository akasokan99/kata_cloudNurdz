Something to look out with respect to fitness functions are availability and scalability if all the users try to access the system at the same time, since we have cloud deployment this shouldn’t be an issue and managing it with auto-scale using cloud providers will provide a lot of flexibility for the cost. We would also write load handling tests to flood our system with hundreds of parallel Trip Management sessions with varying levels of users. We would then check on response times to verify if our system scaled to the appropriate level.This would be a great indicator to determine what resources in our pipeline need to be scaled up or down to find an ideal allocation of resources to handle different traffic patterns. 

1. Availability - Modular approach provides high availability of a component aided with cloud infrastructure. 

2. Scalability - deployment with cloud infrastructure , microservice approach and event driven provides highly scalable solutions for volume growth.
