---
title: Kafka Manual Commit and Implementation in Java Spring
author: Jay Jo
date: 2023-11-15 00:00:00 +09:00
categories: [Kafka]
tags: [Kafka, Software Architecture]
---

# Kafka Manual Commit and Implementation in Java Spring

Understanding Kafka's manual commit feature is essential, especially when integrating with Java Spring. This document covers the basics of manual commit in Kafka and how to apply it in a Java Spring application.

## Kafka Manual Commit Explained

Kafka offers two modes for consumer group offset management: automatic and manual.

### 1. Automatic Offset Commit
- **Default Mode**: Commits offsets automatically and periodically.
- **Potential Issue**: Can lead to duplicate processing if the application crashes between message processing and the next automatic commit.

### 2. Manual Offset Commit
- **Control Over Commits**: Allows the application to decide when to commit offsets.
- **Reduced Duplication**: Less chance of message duplication as commit happens post message processing.
- **Reliability**: More reliable for critical data processing tasks.

#### Methods in Manual Commit
- **CommitSync**: Synchronous and blocks until confirmation. More reliable but can impact performance.
- **CommitAsync**: Non-blocking, higher throughput but without immediate commit guarantee.

## Implementing Manual Commit in Java Spring

Spring Kafka facilitates Kafka integration with a Java Spring application. Below is a guide on implementing manual commit:

### 1. Add Dependencies
Ensure the Spring Kafka dependency is included in your project's `pom.xml` or `build.gradle`.

### 2. Configure Consumer Properties
```java
props.put(ConsumerConfig.ENABLE_AUTO_COMMIT_CONFIG, false);
```
Set `ENABLE_AUTO_COMMIT_CONFIG` to `false` to disable automatic offset commits.

### 3. Consume Messages
Use `@KafkaListener` to consume messages and process them within the listener method.

### 4. Manual Offset Commit
After message processing, commit the offset manually using one of the following methods:
- **Synchronous Commit**: `Acknowledgment.acknowledge()`
- **Asynchronous Commit**: `Consumer.commitAsync()`

```java
@KafkaListener(topics = "yourTopic", groupId = "yourGroup")
public void listen(String message, Acknowledgment acknowledgment) {
    // Process the message
    // ...

    // Manually commit the offset
    acknowledgment.acknowledge();
}
```

### 5. Error Handling
Implement robust error handling in your consumer method to decide on offset committing based on processing success.

### 6. Testing and Tuning
Perform thorough testing and adjust for performance and reliability as required.

## Conclusion
Manual committing in Kafka within a Spring application provides detailed control over message processing and offset management, ensuring reliable message consumption.
