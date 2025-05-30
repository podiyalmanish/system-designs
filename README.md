# System-designs 
- **A collection of my recent system design work, showcasing scalable architecture, design patterns, and best practices.**

## Serverless Messaging Service Architecture

![Serverless Messaging Service Architecture Diagram](serverless-messaging-service-architecture-diagram.png)

This architecture diagram illustrates a serverless messaging service flow built on AWS components:

- **API Consumer**: Initiates requests to the system.
- **API Gateway**: Handles and routes inbound API requests.
- **Messaging Service (Lambda-based API)**: Validates requests and publishes messages to a queue.
- **MessageQ (SQS)**: Provides reliable message queuing.
- **Messaging Service (Consumer Lambda)**: Polls the queue, processes messages, and triggers downstream actions.
- **AWS Pinpoint**: Sends messages to end-users (such as SMS, email, or push notifications).
- **End-User**: Receives the final communication.

**Workflow Overview**:
1. The API Consumer sends a request via the API Gateway.
2. The Lambda-based messaging API validates and accepts the request, placing a message in the SQS queue.
3. The Consumer Lambda polls SQS, processes the message, and interacts with AWS Pinpoint.
4. AWS Pinpoint sends the message to the intended end-user.

This design leverages AWS managed services to achieve scalability, decoupling, and cost efficiency with minimal server management.
