# Internet Protocol

The Internet Protocol is the main protocol in the Internet protocol suite.

This protocol is responsible for addressing host interfaces, encapsulating data into datagrams, and routing those datagrams from source hosts to destination hosts.

## Addressing

IP addressing involves assigning an IP address and other parameters to host interfaces. The address space is further divided into subnetworks.

## Data Encapsulation

The protocol defines a packet structure that encapsulates data into datagrams. Datagrams have the following structure:

- _Header_: Contains the source host's IP address, destination host's IP address, and other metadata needed to route the packet. There are 14 different fields for IPv4 headers, some of which are optional.
- _Payload_: The actual data being transmitted.

Datagrams are a form of connectionless communication, thus their delivery, arrival time, and order are not gaurenteed.

## Routing

Routing is performed by all hosts, in addition to routers. Routers have additional protocols that are used in this process.

## Reliability

The Internet Protocol adheres to the end-to-end principle and is considered unreliable at any given network element in terms of availability (think of servers being turned off or cables being damaged).

Other fault conditions include data corruption, packet loss, and duplication. These faults must be detected and handled by the end nodes.

## Links

- [Wikipedia - Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol)
- [Cloudflare - What is the Internet Protocol?](https://www.cloudflare.com/learning/network-layer/internet-protocol/)
