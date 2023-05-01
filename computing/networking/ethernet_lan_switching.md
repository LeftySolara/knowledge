# Ethernet LAN Switching

Here we will discuss how data is moved between switches, end hosts, and routers over an Ethernet connection. Most of this information is in regards to Layer 2.

## Local Area Networks

There are many ways to define a Local Area Network (LAN). Essentially, it is a network contained within a relatively small area. Many switches and end hosts can be part of a LAN. Separate LANs are connected together using routers.

## Ethernet Frames

An **Ethernet frame** a type of PDU for Layer 2. It consists of a header, a trailer, and the encapsulated packet.

The header contains five fields: the Preamble, the Start Frame Delimiter, the Destination, the Source, and the Type. The trailer consists of just one field: the Frame Check Sequence.

The size of the header and trailer combined is 26 bytes.

The minimum size of an Ethernet frame (including the payload) is 64 bytes. This means that the payload must be at least 46 bytes. If it is less than 46 bytes, then it is padded with 0's.

### Header

The Ethernet frame **header** is a block of data containing five fields. Below is a description of each.

#### Preamble and Start Frame Delimiter (SFD)

These two fields are used for synchronization and allow the device to be prepared to receive the rest of the data in the frame.

The **Preamble** is a 7-byte sequence of alternating 1's and 0's. It allows devices to synchronize their receiver clocks, to make sure they are ready to receive the rest of the frame. It is sometimes not considered to be part of the header, though it is sent with every Ethernet frame.

The **Start Frame Delimiter (SFD)** is the one-byte sequence 10101011. It marks the end of the preamble and the beginning of the rest of the frame.

#### Destination MAC Address

This is the Layer 2 address (MAC Address) to which the data is being sent.

#### Source MAC Address

This is the Layer 2 address of the device that sent the frame.

#### Type / Length

This field indicates the Layer 3 protocol used in the encapsulated packet. Usually this is IPv4 or IPv6.

Sometimes this field represents the length of the encapsulated data instead of the protocol. This depends on the version of Ethernet being used.

This field is two bytes long. If its value is 1500 or less, then it is indicating the type of the encapsulated packet (length determined by other means). A value of `0x0800` means it is an IPv4 packet, a value if `0x86DD` means it is an IPv6 packet, and a value of `0x0806` means it is an ARP packet.

If the value is 1536 or greater, then it is representing the length of the packet in bytes.

### Trailer

There is only one field in the Layer 2 trailer: the FCS.

The **Frame Check Sequence** (FCS) is used by the receiving device to detect any errors that might have occurred in transmission. It is four bytes long and detects corrupted data by running a **Cyclic Redundancy Check (CRC)** algorithm over it.

## MAC Addresses

A **Media Access Control (MAC)** address is the six-byte address of a physical device. It is also referred to as a **Burned-In Address (BIA)**.

The first three bytes of the address is the **Organizationally Unique Identifier (OUI)**, which is unique to the company making the device. The last three bytes are unique to the device itself. This address is globally unique; no two devices in the world share the same MAC address.

The address is written as 12 hexadecimal characters.

On switches, MAC addresses are kept in a table. This table contains the MAC addresses of devices along with the interfaces that the devices are connected to. The table is filled dynamically by the switch looking at the source MAC address of frames it receives.

If a switch does not know the MAC address of a frame's destination, it sends the frame to every connected device except the one that it received the frame from. This is called **flooding** the frame. The devices that do not match the destination address will simply drop the frame, while the correct device will process the frame normally.

A frame destined for a single target is called a **unicast frame**. An **unknown unicast frame** is a frame with a destination that isn't in the MAC address table. This is what gets sent in a flood. A **known unicast frame** is a frame whose destination is already in the MAC address table.

On Cisco switches, entries in the MAC address table are removed after 5 minutes of inactivity.

## ARP

The **Address Resolution Protocol (ARP)** is used to discover the Layer 2 address (MAC address) of a known Layer 3 address (IP address). 

The ARP process consists of two messages: the ARP Request and the ARP Reply. The **ARP Request** is sent by a device that wants to know the address of another device. The **ARP Reply** is sent to inform the requesting device of the MAC address.

The ARP Request is sent as a broadcast (sent to all hosts on the local network). The sending device then awaits a response from another device. This response is in the form of a unicast frame. The frame is sent to the switch and follows the same send-receive process as an Ethernet frame.

The ARP Reply frame contains the source IP, destination IP, source IP, and destination IP. In this case, the destination MAC address is called the **broadcast MAC Address**.

After receiving an ARP Reply, a device will add an entry into its ARP table.

## Resources

- [Jeremy's IT Lab](https://www.youtube.com/watch?v=u2n762WG0Vo&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=10)