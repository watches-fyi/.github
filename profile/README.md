# Watches.fyi

Watches.fyi is a dedicated platform for watch enthusiasts, providing a one-stop-shop experience for finding and managing luxury watches from various marketplaces. This project leverages **microservices**, **gRPC** and **Kafka** to deliver a scalable, responsive, and modular architecture.

## Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
  - [Microservices](#microservices)
  - [gRPC](#grpc)
  - [Kafka](#kafka)
- [Technologies Used](#technologies-used)


## Project Overview

Watches.fyi aims to simplify the process of finding, tracking, and purchasing watches by aggregating listings from multiple watch marketplaces and providing tools to manage watch inventories, track prices, and set up notifications. This README describes how microservices, gRPC, and Kafka are used to achieve an efficient and scalable architecture for this platform.

## Key Features

- **Data Aggregator**: Collects listings from marketplaces like eBay, Chrono24, and others.
- **Real-Time Notifications**: Alerts users to new listings or price changes via Webhook, SMS, or email.
- **Marketplace**: Allows verified sellers to list watches for sale and supports buyer bids.
- **Inventory Management**: Helps users manage and track their watch collections.
- **User Forum**: A community space for discussing watches and sharing insights.


## Architecture

### Microservices

The Watches.fyi architecture is based on a microservices design to achieve modularity, scalability, and flexibility. 

- Modular Services: Separate the functionalities like data aggregation, notifications, marketplace management, inventory tracking, and user forums into distinct microservices. This modular design would allow each service to be developed, deployed, and scaled independently.

- Scalability: Since Watches.fyi aims to grow with features like watch tracking and marketplace listings, a microservices approach allows the project to scale as demand increases without impacting other services.

The main services include:

- **Data Aggregator Service**: Collects data from external marketplaces and updates the Watches.fyi platform.
- **Notification Service**: Handles user notifications (webhook, SMS, email) for price changes or new listings.
- **Marketplace Service**: Manages buy/sell listings, bid processing, and marketplace interactions.
- **Inventory Service**: Allows users to track their collections, manage inventory, and sync listings across platforms.
- **Forum Service**: Hosts user discussions and posts related to watches.
- **Pricing and Listing Tracking Service**: Track and logs prices, historical data, and trends across multiple marketplaces. It could connect to the data aggregator to pull in new pricing information as it becomes available.
- **Authentication Service**: Handles user login, registration, and integration with OAuth providers like Google, Apple, and Microsoft. Can expose gRPC endpoints for other services to verify user sessions and permissions securely and efficiently.
- **Authorization Service**: The Authorization Service determines which resources and actions each user is allowed to access, based on their roles or permissions. This service evaluates whether a user has the rights to perform specific actions, such as viewing sensitive data or performing administrative tasks.
- **User Service**: The User Service manages user-related data, including profiles, contact information, and preferences. It is responsible for CRUD (Create, Read, Update, Delete) operations for user accounts but doesn’t handle authentication or authorization directly.

Each microservice can be independently deployed and scaled based on the load and usage patterns, allowing Watches.fyi to grow without impacting other services.

### gRPC

gRPC is used for efficient communication between microservices, chosen for its high performance and low latency, which is essential for real-time data aggregation and notifications.

- **Efficient Communication**: Use gRPC for communication between microservices, especially for services with high data throughput needs, like aggregating listings from marketplaces or syncing inventory data. Its binary protocol ensures fast, low-latency data transmission, which is well-suited for real-time notifications. 

- **Language Interoperability**: gRPC supports multiple languages, which would be useful if Watches.fyi incorporates services developed in languages other than Go, as it allows seamless communication across different systems.

### Kafka

Kafka serves as the real-time event streaming platform for Watches.fyi, enabling robust data streaming and event processing.

- **Event-Driven Notifications**: Kafka is used to publish events for price changes, new listings, and user bids, which the Notification Service consumes to deliver real-time alerts to users.
- **Data Ingestion Pipeline**: External marketplace data flows into Kafka, where it is processed and distributed to the Data Aggregator Service.
- **Scalability and Reliability**: Kafka’s fault tolerance and horizontal scalability make it well-suited for handling the data and traffic volume anticipated as Watches.fyi grows.


## Technologies Used

- **Programming Languages**: Go, Python
- **Communication Protocol**: gRPC
- **Event Streaming Platform**: Apache Kafka
- **Data Storage**: PostgreSQL, MongoDB
- **Frontend**: React
- **Containerization**: Docker
- **Orchestration**: Kubernetes
