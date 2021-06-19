<div align="center" font-size="32px">JMS - Concepts</div>

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
 
