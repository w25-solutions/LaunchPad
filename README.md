<p><a target="_blank" href="https://app.eraser.io/workspace/Lv6Lpgi3FtX9H2FEBAuL" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

`Solution - Tech Design Doc` 

# Launch Pad - SaaS Base Kit
# Introduction
## Purpose
The purpose of this document is to outline the design and architecture of Launch Pad, a SaaS starter kit designed to help developers turn ideas into running projects quickly and efficiently. The kit simplifies user authentication, subscription management, and integration with payment and email services.

In the fast-paced world of software development, the ability to quickly launch and scale SaaS applications is crucial. Launch Pad addresses this need by providing a robust and scalable foundation.

## Business Context
Launch Pad will enable startups and developers to focus on their core product features instead of building common SaaS functionalities from scratch.

## Objectives
- To reduce development time for SaaS projects
- To offer scalable and secure user management and subscription services
- To streamline integration with payment and email services
- To be a modular and extensible solution
## Scope
- User signup and authentication
- Subscription control
- Stripe integration for handling subscriptions
- SendGrid integration for transactional emails
- JWT authentication, incorporating subscription data
- Modularity and Extensibility, easy to change external providers or extend capabilities
# Requirements
## Functional Requirements
- Secure user signup and login
- Efficient and simple subscription management
- Seamless Stripe and SendGrid integration
## Non-Functional Requirements
- Scalability to handle growth in the user base
- High availability for critical services
- Security measures to protect user data
- Extensibility through well bounded Microservices Architecture
- Extensibility through Event-Driven Architecture
## Use Cases
### Actor: User
- 1.1 User Registration: 

A new user can register for an account by providing their email address, and a password, and verifying their email.
- 1.2 User Login: 

A registered user can log in to their account using their email and password.
- 1.3 Password Reset: 

Users can reset their password if they forget it, through a secure process that verifies their identity via email.
- 1.4 Update User Information: 

Users can update their information (name). 

Users can`t change their registered e-mail
- 2.1 Subscribe: 

Users can subscribe to a plan, entering payment information through a secure Stripe integration.

Extensible to any other payment provider as needed 
- 2.2 Get Subscription Information: 

Users can retrieve their subscription information (plan name, expiration date).
- 2.3 Cancel Subscription: 

Users can cancel their subscription, with the option to provide feedback on their reason for cancellation.
- 2.4 View Subscription History: 

Users can view their current and past subscriptions, including start dates, end dates, and payment history.
### Actor: The system itself
- 3.1 Notify the user regarding successful subscription: 

The system should notify the user by email about successful subscriptions.
- 3.2 Notify the user regarding subscription expiration: 

The system should notify the user by email about the subscription expiration.
### Actor: External Systems
- 4.1 Payment Processing: 

External payment gateways should be able to communicate successful and failed payment attempts to the system.
- 4.2 Subscription Renewal Notifications: 

External payment gateways should be able to communicate subscription status changes to the system.
# Proposed System Design
![image](https://github.com/wilsonneto-dev/LaunchPad/assets/20674439/545f2b98-8eb1-4b33-884a-1d3ce7612f1c "")

## Services Summary
- Auth API
Provides authentication services, allowing users to sign up, log in, and manage their profiles securely using JWT for sessions.

- Notifier
Manages sending transactional emails through SendGrid, including account verification, subscription notifications, and password resets.

- Subscriptions API
Handles subscription management, allowing users to subscribe, upgrade, downgrade, and cancel their subscriptions seamlessly.

- Payments Webhooks API
Integrates with Stripe to process subscription payments, handle invoices, and manage payment failures and retries.

## Infrastructure / Deployment
- The solution can be deployed on any of the main public cloud providers
- The system will use extensive Containerization and Horizontal Scalability
- Rabbit MQ for Asynchronous communication between services
- Preferable managed API gateway as the System Entry-Point
- The System will use extensive Logging/Tracing/Events
- Env vars for environment segmentation
## Dependencies
- External Payment services 
- Transactional email provider
# Implementation Strategy
The implementation will happen in 5 stages, 4 microservices implementations and the acceptance criteria validation stage. 

## Auth API
Auth API - Design: [﻿Solution Design to be created](#) 

- Use Cases covered by this capability/service:
    - 1.1 User Registration
    - 1.2 User Login
    - 1.3 Password Reset
    - 1.4 Update User Information
## Notifier
- TBD in Stage 2
## Subscriptions API
- TBD in Stage 3
## Payments Webhooks API
- TBD in Stage 4
# Testing and Validation
- Comprehensive unit and integration tests will be developed to cover all aspects of the system.
- API Load testing to ensure scalability (JMeter / Blaze Meter).
- Automated Acceptance E2E Tests based on the Use Cases
- Use Cases working properly and as described will be the Acceptance Criteria
# Risks and Mitigations
- Dependency on External Services: Relying on third-party services like Stripe for payments and SendGrid for emails introduces risks related to service outages or API changes.Mitigation: The system will work with abstraction layers for these services to make swapping out or updating services more manageable. Regularly review and test the integration points for these services to ensure they're up to date with the latest API changes and best practices.
- Scalability Concerns: As user bases grow, the system must scale appropriately to handle increased loads, particularly for the Auth API and Subscriptions API.Mitigation: Design services with scalability in mind, using EDA Architecture and cloud-based infrastructure that can automatically scale to meet demand. Regularly conduct load testing to identify bottlenecks and address them proactively.
- Security Vulnerabilities: Handling user authentication and payment information requires rigorous security measures to protect against breaches and data theft.Mitigation: Adhere to best security practices, including regular audits, using encryption for data storage and transmission, and implementing robust access controls. Consider obtaining security certifications to build trust with users.
# Future Considerations
- Feature Expansion: 
 Based on community feedback and market demand, it will be considered expanding the features of Launch Pad. This could include more integrations with other payment providers, advanced analytics for subscription management, or enhanced security features.
- Technology Upgrades: 
 Keep the technology stack up to date with the latest advancements to maintain performance, security, and developer productivity. Plan for periodic technology refreshes and refactoring efforts.



<!--- Eraser file: https://app.eraser.io/workspace/Lv6Lpgi3FtX9H2FEBAuL --->