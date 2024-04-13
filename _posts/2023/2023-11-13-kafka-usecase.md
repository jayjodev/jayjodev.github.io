---
title: Kafka Use Cases
author: Jay Jo
date: 2023-11-13 00:00:00 +09:00
categories: [Kafka]
tags: [Kafka, Software Architecture]
---

Kafka, developed at LinkedIn, is widely used for various data processing and handling tasks. Below are its key use cases:

## 1. **Activity Tracking**
- **Primary Use**: Originally used for tracking **user activities on websites**.
- **Data Types**: Captures both **passive interactions** (e.g., page views) and **active user actions** (e.g., profile updates).
- **Back-End Processing**: Messages are published to topics and then consumed by backend applications for diverse purposes like **report generation, machine learning, and updating search results**.

## 2. **Messaging**
- **Notifications**: Ideal for sending **notifications** like emails.
- **Simplified Message Production**: Allows applications to focus on message content without worrying about formatting or delivery.
- **Centralized Processing**: A single application can handle all messages, ensuring **consistent formatting** and application of user preferences, which **avoids duplicative efforts**.

## 3. **Metrics and Logging**
- **Versatile Data Collection**: Suitable for collecting **application/system metrics and logs**.
- **Efficient Data Utilization**: Data can be used for **monitoring, alerting, and long-term analysis** (like in Hadoop).
- **Flexibility in System Changes**: Simplifies transitions to new systems without needing to alter frontend applications.

## 4. **Commit Log**
- **Database Change Broadcasting**: Kafka's commit log structure is great for **publishing database changes**.
- **Real-Time Updates and Replication**: Useful for **live tracking of updates**, replicating changes to remote systems, or consolidating data from multiple sources.
- **Data Reliability**: Features like **durable retention** and **log-compacted topics** enhance data reliability.

## 5. **Stream Processing**
- **Real-Time Data Processing**: Contrasts with batch processing in Hadoop by offering **real-time processing**.
- **Flexible Application Use**: Enables small applications to perform tasks like **metrics counting, message partitioning, and data transformation**.

