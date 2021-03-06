**Team Name :** **CloudNurdz**

**Members:** *Anandhakumar Asokan / Nagendar Peethambaram / Pradeep Sarangula*

 
**Introduction:**
  
  **Purpose:**
  
   Outline the architectural design and requirements for an online trip management dashboard for customers to view all of their existing reservations.
  

 [Requirements](Requirements/Requirement.md) for Trip Management System
  
 [Assumptions](Assumptions.md) for Trip Management System.

****Solution Approach:****

**Architecture Challenges :**
 
  1. System must support multiple sessions and multiple users at a given time 
 
  2. Real time updates to the customer dashboard should be seamless with existing travel systems as it's critical for the customer
     to see real time updates about their hotel, flight and car reservation.
 
  3. Security implementation is critical as the customer should not have the option to look at any trip information 
     using the reservation code. Customers shall look at the reservation pertaining to their travel / trips.

**Solution Architecture :**

The Road Warrior is a major travel agency that wants to build the next generation online trip management dashboard which will allow the users to see all of their existing reservations organized by trip either online or through their mobile devices.As long as users have access to a network capable device connected to the internet and access to the dashboard they can review the existing reservations from anywhere. The system is designed for high scalability using cloud deployment models and integrates with the agency's existing airline, hotel and car rental systems in order to automatically load reservations via frequent flier accounts, hotel point and car rental reward accounts for validating or updating the travel information to the dashboard. Architecture is based on real time(API), web sockets and event driven styles. 

**Architecture Style :**

We have chosen a microservices architecture. The trip management system requires real time refresh of the dashboard. Dashboard displays the existing reservations (made through Agency system) through a web portal or mobile device. This can be implemented by integrating the Agency system API components. Whenever a user logs into the trip management system, all the user???s latest reservations are pulled from the Agency system. For the realtime user updates on the web portal/mobile, we have chosen to design the system as a single page application.The proposed architecture for the Trip Management system is a modular and highly decoupled system which can be enhanced and integrated with third party systems seamlessly without altering the core Trip Management system framework. The Trip Management system is designed to integrate with the existing Agency system API for retrieving the reservation details.

![**Architecture Diagram:**](Architecture/Logical/Logical_Architecture.png)

**Process flow for Trip Management Real Time updates:**
![**Process flow Diagram:**](Architecture/ProcessFlow.JPG)

**Architecture Style and Benefits:**

Microservice - Provides modular approach using domain driven concepts keeping the functions loosely coupled with one another to give greater extensibility capabilities for building new features to the product.This will help ensure that the business will not need to replace their system for the foreseeable future.Allow for scalability of the system if the number of users / customers  increases.Frequent updates from other interfaces like car rental, airport and hotel.Frequent data refresh from the interfaces for getting airlines, car rental and hotel information. 

**Risks/mitigations:** 

Reservation accuracy integrating with all the system???s is another risk we are working to solve with the overall system. By having a system driven process it allows us to remove potential human error and modernize a manual process of logging in to multiple systems to check on each reservation.
Risk of displaying reservations made by someone else based on a frequent flier account or hotel point or car rental reward account. By having a notification or consent from the customer based on the phone number or email attached to the flier account we can validate if the dashboard user is the actual customer associated with the account.

**Other Architecture Options :**

We discussed having another menu / feature item in the existing agency reservation portal to view the trip management information by reusing the existing pipelines for getting data , existing web portal interfaces. But thinking in terms of offering this as a new product for the users to provide the users for managing the trips and also to offer the best offers with the favored vendors / partnership ,creating separate portal and reusing the agency reservation API provides the agency to think on API-first approach and to build headless application / portals for serving the users for reservation and trip management. 

**Deployment Architecture:**

Our deployment model is using cloud native features which provides scalable, highly resilient infrastructure for the solution. It also helps in reduced maintenance and allows us to focus on delivering more business value than managing the infrastructure. 

![**Deployment Diagram:**](https://github.com/akasokan99/kata_cloudNurdz/blob/main/Architecture/Deployment/Deployment_Architecture.png)


**Business Continuity Plans:**

When we thought about architecting the system we knew there were key factors we needed to consider in order to avoid unnecessary friction to the business process. The single page web application allows any user with a device that can connect to the internet the ability to view the Trip details on their dashboard.  Network connectivity is a crucial factor in the success of the online Trip Management, the Trip Management app would provide users the option to allow them to store data locally if they are in flight or can't connect to the internet so that they always have the details about their reservation. Once they connect to the internet the dashboard will be refreshed with the latest information.

**State Diagram:**

A critical factor of the system is handling the user volume and providing the information in real time.  When the trip management portal loads the trip information between a threshold (>1s and < 3s), the overall application would be in a warning state, when the portal loads the trip information above a threshold of >3s, it would be in an alarm state notifying the operations team. 
![**State Diagram:**](Architecture/StateDiagram.JPG)

**User Growth (Increase in the number of users):**

Based on the microservices based cloud deployment that we are proposing, we can autoscale the needs to support the data volume or number of users accessing the dashboard to view the trip management.

 [Fitness Functions](https://github.com/akasokan99/kata_cloudNurdz/blob/b64ea14cf4b910911e412605775205cdc68f54aa/Fitness%20Functions.md) for Trip Management System

