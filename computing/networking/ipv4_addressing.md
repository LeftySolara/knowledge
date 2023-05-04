# IPv4 Addressing

**IPv4** is the primary Layer 3 protocol in use today.

An IPv4 address is 4 bytes (32 bits) in length and is usually written in dotted decimal notation. At the end of the address there is often a slash and another number; this number specifies which portion of the address represents the network and which represents the host.

## Classes

IPv4 addresses are split into seven classes. Each class is determined by the first octet of the address.

### Class A

Class A addresses have a first octet in the range of 0-127.

Usually the maximum is considered to be 126, since 127 is reserved for loopback addresses.

These addresses have a /8 at the end, which is equivalent to the subnet mask 255.0.0.0.

### Class B

Class B addresses have a first octet in the range of 128-191. They have a /16 at the end, which is equivalent to the subnet mask 255.255.0.0.

### Class C

Class C addresses have a first octet in the range of 192-223. They have a /24 at the end, which is equivalent to the subnet mask 255.255.255.0

### Class D

Class D addresses have a first octet in the range of 224-239. This class is reserved for multicast addresses.

### Class E

Class E addresses have a first octet in the range of 240-255. This class is reserved for experiments uses.

## Special Addresses

The first address in a network is the address of the network itself, so it can't be assigned to a host. Likewise, the last address in a network is the broadcast address, so it can't be assigned to a host, either. A broadcast address is used when you want to send data to all hosts on a local network.

## Subnet Masks

The **subnet mask** is another way to write the number at the end of an address (the one after the slash). It is written in dotted decimal notation (just like an IP address), and is also 32 bits long.

If the host portion of the mask is all 1's, then it is the network address. If the host portion is all 0's, then it is the broadcast address.

To find the maximum number of usable addresses in a network, take the number of bits in the host portion, raise 2 to it, and the subtract 2 (to account for the network and broadcast addresses). In brief:

```
max = 2^n - 2
```

where *n* is the number of bits in the host portion of the address.

## Configuring IP Addresses on Cisco Switches

To configure IP addresses on a Cisco router:

- Use the `enable` command to enter privileged exec mode
- Use `show ip interface brief` to list network interfaces and their IP addresses
    - The `status` column represents the Layer 1 status
    - The `protocol` column represents the Layer 2 status
- Use `configure terminal` to enter global config mode
- Use `interface <interface name>` to enter interface config mode
- To set the IP address of an interface, use the command `ip address <address> <mask>`
- To enable the interface, use `no shutdown`

## Resources

[Jeremy's IT Lab](https://www.youtube.com/watch?v=3ROdsfEUuhs&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=13)