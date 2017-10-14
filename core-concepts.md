## Core concepts

The AsyncAPI specification is based on the assumption of 2 core concepts:

### Messages

The way a consumer\(s\) can communicate with your API is based on messages. A message is a piece of information two or more programs exchange. Most of the times to notify the other end\(s\) that, either an event has occurred or you want them to perform an action.

Technically speaking the events and actions will always be sent in the same way. These are just messages and their content can be anything. So when we speak about the difference between events and actions, this is just a semantic differentiation of message's content. We do not enforce you to make any difference between them, although we encourage you to do it.

A message can contain headers and a payload, however both are optional. To remain as much protocol-agnostic as possible, the specification allows you to define any kind of header.

### Topics

Message-driven protocols usually contain something that can be found as topic \([MQTT](http://www.hivemq.com/blog/mqtt-essentials-part-5-mqtt-topics-best-practices)\), routing key \(AMQP\), destination \(STOMP\), etc. To some extent, they can compare to URLs in HTTP APIs. So when you send a message to your API it will be routed depending on the topic you published on. It allows you to create APIs that subscribe to certain topics and publish to other ones.

There's no standard way of naming topics so we recommend you to [**have a look at our proposal here**](https://github.com/asyncapi/topic-definition).

{% youtube %}STKCRSUsyP0{% endyoutube %}

