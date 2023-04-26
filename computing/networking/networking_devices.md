# Networking Devices

## What is a Network?

A **computer network** is a communications network which allows nodes to share resources.

### What is a Node?

Network nodes include:
- routers
- switches
- firewalls
- servers
- client machines

## Node Types

### Clients

A **client** is a device that accesses a service made available by a server. These are regular computers, smartphones, tablets, etc.

### Servers

**Servers** are devices that provide services for clients.

### Switches

A **switch** is a device that connects other devices on a LAN. Note that they do _not_ provide connectivity between LANs or over the Internet.

### Routers

**Routers** are devices that provide connectivity between LANs. Thus, they are used to send/receive data over the Internet.

### Firewalls

A **firewall** is a security device that monitors and controls network traffic. Must be configured with security rules to determine what should be allowed and what should be blocked.

## Ethernet

**Ethernet** is a collection of network protocols and standards.

Ethernet standards are defined in IEEE 802.3.

### Interfaces and Cables

There are two types of cables used in the Ethernet standard: UTP cables and fiber-optic cables.

#### UTP Cables

UTP cables are cables that use copper wires to transmit data. When communicating over a copper wire, a variation in the electrical signal is interpreted by devices as a 0 or a 1. RJ-45 connectors are used to plug in these types of cables.

The acronym "UTP" stands for "Unshielded Twisted Pair". This is because the wires inside the cable are grouped into four pairs which are twisted around each other. The twisting is to prevent electromagnetic interference (EMI).

Non-twisted cables are called "straight-through" cables. With these types of cables, each pin in the cable connects to the same pin on the port. Usually this doesn't work, because you end up with both sides trying to send and receive on the same pins. These days most cables come with a feature called "Auto MDI-X", which allows devices to detect which pins their partner is using, allowing them to adjust their pins based on that. Auto-MDI-X also eliminates the need for crossover cables.

UTP cables can have a length of up to 100 meters.

##### 10BASE-T and 100BASE-T

10BASE-T and 100BASE-T are Ethernet speed standards. The "T" stands for "Twisted Pair". These two types of cables only use two of the four pairs of pins.

Different connection pairs work differently from one another.

###### PC/Server-Switch

When connecting a PC or a server to a switch:

- The PC/Server transmits data on pins 1 and 2, and receives data on pins 3 and 6
- The switch receives data on pins 1 and 2, and transmits data on pins 3 and 6

There is something called **full duplex**, where both devices can send and receive data at the same time. There are no collisions in this setup because the devices use different pins for transmitting and receiving.

###### Switch-Router

Switches and routers also use pins 1,2,3, and 6:

- Switches use pins 1 and 2 to receive data, and 3 and 6 to transmit data
- Routers use pins 1 and 2 to transmit data, and 3 and 6 to receive data

Note that routers use the same pin setup as PCs/servers. Firewalls also share this configuration.

###### Two of the same device

When connecting two of the same type of device with a straight-through cable, you run into an issue where both devices are sending and receiving on the same pins. To solve this, use a **crossover cable**. In a crossover cable, the copper wire pairs are reversed on each end. This results in the following connections:

- pin 1 connects to pin 3
- pin 2 connects to pin 6
- pin 3 connects to pin 1
- pin 6 connects to pin 2

With this setup, the transmit pins on one side are connected to the receive pins on the other.

##### 1000BASE-T and 10GBASE-T

These types of cables use all four pairs of pins. Pins 4 and 5 connect to pins 7 and 8. The pins are also **bidirectional**, which is why they can operate at faster speeds.

#### Fiber-Optic Cables

Fiber-optic cables transmit data by sending light over glass fibers instead of electrical signals over copper wire.

The ports for these types of cables take an SFP Transceiver (Small Form-Factor Pluggable), which the actual cable plugs into. There are two connectors on each end, one for transmitting data and one for receiving data.

The structure of the cable end consists of a fiberglass core, a cladding that reflects light, a protective buffer, and the outer jacket of the cable.

There are two different types of fiber-optic cables:

##### Single-Mode Fiber-Optic Cables

In a **single-mode** cable, the fiberglass core is narrower and light enters at a single angle (mode). This allows for longer cables than UTP and multi-mode, but is more expensive due to the cost of laser-based SFP transceivers.

##### Multi-Mode Fiber-Optic Cables

In a **multi-mode** cable, the fiberglass core is wider than with single-mode. This allows light to enter at multiple angles (modes). This allows for longer cables than UTP, but shorter than single-mode. These cables are cheaper than single-mode cables due to the lower cost of LED-based SFP transceivers.

## Resources

- [Jeremy's IT Lab - Network Devices](https://www.youtube.com/watch?v=H8W9oMNSuwo&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=1)
- [Wikipedia - Twisted Pair](https://en.wikipedia.org/wiki/Twisted_pair)