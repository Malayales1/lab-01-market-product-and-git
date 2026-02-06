## Product Choice
Product name: Telegram
Website: https://telegram.org

Description: Telegram is a cloud-based instant messaging platform focused on speed, scalability, and security, supporting personal chats, groups, channels, and bots for a large global user base.

## Main components

//link//

The following components were selected from the component diagram and described based on publicly available information and reasonable assumptions.

Client Applications – Mobile, desktop, and web clients that provide the user interface, handle message composition, client-side encryption, and communicate with backend APIs.

API Gateway – A single entry point for all client requests, responsible for authentication checks, request routing, rate limiting, and forwarding requests to backend services.

Authentication Service – Manages user identity, phone number verification, session handling, and access control for all Telegram services.

Messaging Service – Core backend service that stores messages, ensures ordering and delivery, synchronizes chats across devices, and performs message fan-out for groups and channels.

Media Storage Service – Handles uploading, storing, and retrieving media files such as images, videos, and documents, optimized for large-scale storage and global delivery.

Notification Service – Sends push notifications to users via external providers when new messages or updates are available.


## Data flow

The selected flow describes the process of sending a message. A client application sends a message request with authentication data to the API Gateway. The gateway validates the request and forwards it to the Messaging Service. The Messaging Service persists the message, determines the recipients, and links media references stored in the Media Storage Service if the message contains attachments. After the message is stored, the Notification Service is triggered to notify recipients. Recipient clients then synchronize and fetch the new message from the Messaging Service.

During this flow, Client Applications exchange message payloads and authentication tokens with the API Gateway. The API Gateway communicates validated requests to the Messaging Service. The Messaging Service exchanges media identifiers with the Media Storage Service and notification metadata with the Notification Service.

## Deployment

Client applications are deployed on user devices across different platforms. Backend services such as the API Gateway, Authentication Service, Messaging Service, and Notification Service are deployed in geographically distributed data centers. Media Storage is deployed on dedicated storage clusters integrated with content delivery networks. Load balancers distribute traffic across service replicas to ensure scalability and fault tolerance.

## Assumptions

The Messaging Service is horizontally scaled using sharding based on user or chat identifiers.
Media Storage uses deduplication to reduce storage costs for identical files.
Secret chats use a different encryption and storage flow compared to regular cloud chats.

## Open questions

How does the infrastructure-level data flow differ between regular chats and secret chats?
What consistency and delivery guarantees are provided by the Messaging Service under failures?
How is cross–data-center replication implemented to minimize global latency?


