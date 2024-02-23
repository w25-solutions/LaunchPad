# Launch Pad - SaaS Base Kit

# Summary

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

- User Registration: <br />
A new user can register for an account by providing their email address, and a password, and verifying their email.

- User Login: <br />
A registered user can log in to their account using their email and password.

- Password Reset: <br />
Users can reset their password if they forget it, through a secure process that verifies their identity via email.

- Update User Information: <br />
Users can update their information (name). <br />
Users can`t change their registered e-mail

- Get Subscription Information: <br /> 
Users can retrieve their subscription information (plan name, expiration date).

- Cancel Subscription:  <br />
Users can cancel their subscription, with the option to provide feedback on their reason for cancellation.

- Subscribe: <br />
Users can subscribe to a plan, entering payment information through a secure Stripe integration.<br />
Extensible to any other payment provider as needed 

- View Subscription History: <br />
Users can view their current and past subscriptions, including start dates, end dates, and payment history.

### Actor: System itself

- Notify the user regarding successful subscription: <br />
The system should notify the user by email about successful subscriptions.

- Notify the user regarding subscription expiration: <br />
The system should notify the user by email about the subscription expiration.

### Actor: External Systems

- Payment Processing: <br />
External payment gateways should be able to communicate successful and failed payment attempts to the system.

- Subscription Renewal Notifications: <br />
External payment gateways should be able to communicate subscription status changes to the system.

# Proposed System Design 

![image](https://github.com/wilsonneto-dev/LaunchPad/assets/20674439/545f2b98-8eb1-4b33-884a-1d3ce7612f1c)

## Services Summary

### Auth API

Provides authentication services, allowing users to sign up, log in, and manage their profiles securely using JWT for sessions.

### Notifier

Manages sending transactional emails through SendGrid, including account verification, subscription notifications, and password resets.

### Subscriptions API

Handles subscription management, allowing users to subscribe, upgrade, downgrade, and cancel their subscriptions seamlessly.

### Payments Webhooks API

Integrates with Stripe to process subscription payments, handle invoices, and manage payment failures and retries.

## Dependencies

- External Payment services 
- Transactional email provider

# 4. Implementation Strategy

TBD

# 5. Testing and Validation

- Comprehensive unit and integration tests will be developed to cover all aspects of the system.
- Load testing to ensure scalability.


# 6. Risks and Mitigations

TBD

# 7. Future Considerations

TBD
