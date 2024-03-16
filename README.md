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


[﻿View on Eraser](https://app.eraser.io/workspace/Lv6Lpgi3FtX9H2FEBAuL?elements=q5YNY-_D8jXJ3jjfGR4-Rw) 



```
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 396 92" width="396" height="92">
<!-- svg-source:excalidraw -->

<rect x="0" y="0" width="396" height="92" fill="#171717"></rect><g transform="translate(10 10) rotate(0 69 36)"><path d="M10.799999999999999 0 M10.799999999999999 0 C42.572235812433064 0.46292272150963554, 74.85256351791323 0.2174789243981243, 127.2 0 C134.9182034112513 -0.2031354881823063, 137.2468499518931 3.494027831405401, 138 10.799999999999999 M138 10.799999999999999 C137.5948051698059 24.23832950986922, 137.5693923480362 38.705943415761, 138 61.2 C137.2696668885648 68.89037791267037, 135.03222251161932 71.612858376652, 127.2 72 M127.2 72 C87.72289179783314 72.00072359915525, 48.55434123940765 73.12583720560819, 10.799999999999999 72 C3.096189961582422 72.58563554510474, 0.41339775100350384 68.3228386901319, 0 61.2 M0 61.2 C-0.1719824952572584 44.97322618834674, 0.4277275162249804 28.732798897922038, 0 10.799999999999999 C-0.499419591575861 3.3168950416147704, 3.440553786605596 -0.6281667612493038, 10.799999999999999 0" stroke="#e9e9e9" stroke-width="1.575" fill="none"></path></g><g transform="translate(248 10) rotate(0 69 36)"><path d="M10.799999999999999 0 M10.799999999999999 0 C53.26815622378141 -1.179252656956017, 95.7794491776079 -1.2448494997218251, 127.2 0 C135.15229691043496 0.524163606017828, 137.50142608657478 4.138625051826239, 138 10.799999999999999 M138 10.799999999999999 C138.65535906299053 25.90072722114623, 138.07803050025402 41.40389860451222, 138 61.2 C138.77774372324347 68.46726468577981, 134.93364727720618 71.68771801963449, 127.2 72 M127.2 72 C100.68098369460553 72.55742909503728, 74.3711300200969 71.92579297614843, 10.799999999999999 72 C4.1069352246820925 71.87023062929511, -0.09729329571127893 67.95532272085548, 0 61.2 M0 61.2 C0.5782755359202624 42.18187123410404, 0.3449418767482042 24.139541327655312, 0 10.799999999999999 C0.6798448346555234 4.390013656765222, 3.9492257140576834 -0.1255567215383053, 10.799999999999999 0" stroke="#e9e9e9" stroke-width="1.575" fill="none"></path></g><g><g transform="translate(150 46) rotate(0 48 0.22074364713951944)"><path d="M0 0 M0 0 C22.94132447168231 0.6012482998669149, 46.53574494943023 0.5760511515438558, 96 0" stroke="#ffffff" stroke-width="1.575" fill="none"></path></g><g transform="translate(150 46) rotate(0 48 0.22074364713951944)"><path d="M85.74872627220142 -6.287831461400294 C87.59884230867763 -5.446348568690737, 96.3659440319364 -2.535280947483901, 96.41984679172933 -0.4235164334625006 C96.47374955152226 1.6882480805588995, 87.90933853190148 5.247075416573582, 86.07214283095901 6.382755622728107" stroke="#ffffff" stroke-width="1.575" fill="none"></path></g></g></svg>
```
![image.png](/.eraser/Lv6Lpgi3FtX9H2FEBAuL___zLdt6iSpnoO2ZqZ5UiwDt81DP042___ipORD__rzqdYHYsNyluRj.png "image.png")






<!--- Eraser file: https://app.eraser.io/workspace/Lv6Lpgi3FtX9H2FEBAuL --->