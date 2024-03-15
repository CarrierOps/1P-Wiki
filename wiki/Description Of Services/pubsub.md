# Pub/Sub Explained

## What is it?

It's a messaging service on GCP. It's a fully managed service that facilitates communication between systems/application/scripts. But what exactly is a messaging service in the context of software?

### Messaging Service

* A messaging service acts as a platform for sending and receiving messages.
* These messages can be anything: text, data, or even binary content.
* The key idea is that communication happens asynchronously, allowing components to interact without being tightly coupled.
*Think of it as a postal service for software—messages are delivered from sender to receiver.

### Components of a Messaging Service

A messaging service has 4 main components (it has others but we won't discuss them here):

* Topics
* Publishers
* Subscribers
* Messages

**Topics**: Intermediary holder of messages. It's essentially the broker that holds all messages before they get sent out to the final destination.

**Publisher**: Creater of the message. The publisher is the one that pushes data/messages that will be consumed downstream. It will push messages to a topic. 

**Subscriber**: Consumer of the message. Subscribes to a topic and grabs any and all messages published to the topic by publisher(s).

**Messages**: This is the data being sent and passed from publisher, to the topic, then to the subscriber.

Pub/Sub is just one example of a messageing service. There are others such as, Apache Kafka, RabbitMQ, AWS SQS, etc.

## Why and how do we use it

Messaging services like Pub/Sub have many many use cases such as streaming data, communication between distributed systems/micro-serivces, creating event-driven processes, etc. For our use cases, we use Pub/Sub to create an event-driven architecture on GCP. 

![alt text]('https://github.com/CarrierOps/1P-Wiki/tree/main/imgs/PubSub_event_example.png')