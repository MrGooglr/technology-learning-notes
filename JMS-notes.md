<div align="center" font-size="32px"><h6><b>JMS - Concepts</b></h6></div>

## JMS Overview

1. **Messaging** is a method of communication between software components or applications.
1. Messaging enables distributed communication that is **loosely coupled**.
1. The sender and the receiver need to know only which message format(as per the application we are going to communicate) and which destination to use.
1. In this respect, messaging differs from **tightly coupled technologies**, such as **Remote Method Invocation (RMI)**, which require an application to know a remote application’s methods.

> ***NOTE*** 
> Messaging also differs from electronic mail (email), which is a method of communication between people or between software applications and people. Messaging is used for communication between software applications or software components.

The JMS API enables communication that is not only loosely coupled but also:
 * ***Asynchronous:*** A JMS provider can deliver messages to a client as they arrive; a client does not have to request messages in order to receive them.
 * ***Reliable:*** The JMS API can ensure that a message is delivered once and only once. Lower levels of reliability are available for applications that can afford to miss messages or to receive duplicate messages.

> We will see the diferrence between JMS and Apache Kafka shortly based on these two points.
> Reference : [Oracle Docs](https://docs.oracle.com/javaee/6/tutorial/doc/bncdr.html)

The JMS API enhances the Java EE platform by simplifying enterprise development, allowing loosely coupled, reliable, asynchronous interactions among Java EE components and legacy systems capable of messaging. 

## Messaging Domains

1. Point-to-Point Messaging Domain
   
A point-to-point (PTP) product or application is built on the concept of message queues, senders, and receivers. Each message is addressed to a specific queue, and receiving clients extract messages from the queues established to hold their messages. Queues retain all messages sent to them until the messages are consumed or expire.
   Use PTP messaging when every message you send must be processed successfully by one consumer.

1. Publish/Subscribe Messaging Domain

In a publish/subscribe (pub/sub) product or application, clients address messages to a topic, which functions somewhat like a bulletin board. Publishers and subscribers are generally anonymous and can dynamically publish or subscribe to the content hierarchy. The system takes care of distributing the messages arriving from a topic’s multiple publishers to its multiple subscribers. Topics retain messages only as long as it takes to distribute them to current subscribers. 

### Message Consumption

Messaging products are inherently asynchronous: There is no fundamental timing dependency between the production and the consumption of a message. However, the JMS specification uses this term in a more precise sense. Messages can be consumed in either of two ways:

1. Synchronously: A subscriber or a receiver explicitly fetches the message from the destination by calling the receive method. The receive method can block until a message arrives or can time out if a message does not arrive within a specified time limit.
1. Asynchronously: A client can register a message listener with a consumer. A message listener is similar to an event listener. Whenever a message arrives at the destination, the JMS provider delivers the message by calling the listener’s onMessage method, which acts on the contents of the message.

> ***NOTE:*** What MQs are doing here in JMS?
> JMS is an API and there are multiple implementations of it available.
> A Message Queue (MQ) is just one of these implementaions and is an application server.
> No Producee and Consumer directly call or interact with each other, intead they have MQ as a middleware (MOM: Message Orieneted Middleware).

Refer the image below:
<div align="center">
 <img src="/image_resources/to_JMSAppElements.gif">
</div>
The broker here is the MQ from vendor.
