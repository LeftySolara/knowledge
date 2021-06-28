# Network Sockets

On UNIX systems all I/O is done by writing to file descriptors, including networking. In this case, the descriptor is referred to as a _socket_. There are many types of sockets, but for now we'll focus on one: _Internet Sockets_.

## Internet Sockets

There are many types of internet sockets, but we'll focus on two for now: _stream sockets_ and _datagram sockets_. _Raw sockets_ are also important and we will look into those at a later date.

### Stream Sockets

Stream sockets are two-way connected communication streams. They use TCP to ensure that data arrives sequentially and error-free.

These are used by things like Telnet and HTTP.

### Datagram Sockets

Datagram sockets are considered "connectionless" and unreliable, as they use UDP for host-to-host transport. These sockets may or may not arrive at their destination, though the data will be error-free if they do arrive.

The "connectionless" part stems from the fact that an active, open connection need not be maintained like with stream sockets. To send on a datagram socket, you simply build a packet, add an IP header, send, and hope for the best.

Datagram sockets are normally used when there is no TCP stack available or when a few dropped packets isn't the end of the world.
