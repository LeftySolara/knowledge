# OSI Model & TCP/IP

## Networking Models

A **networking model** categorizes and provides structure for networking protocols and standards.

Network **protocols** are sets of logical rules defining how network devices and software should work.

## OSI Model

The **OSI Model** was an attempt to standardize network communications. It is not commonly in use today, but many people still refer to it.

OSI stands for "Open Systems Interconnection".

This is a conceptual model that categorizes and standardizes the different functions in a network. It was created by the International Organization for Standardization (ISO).

In this model, functions are divided into 7 layers. These layers work together to make the network work. The layers are:

- Application
- Presentation
- Session
- Transport
- Network
- Data Link
- Physical

The top three layers pass data to the bottom four, which handle actually sending the data across the network

### Layer 7 - Application Layer

The **application layer** is the layer closest to the end user. It interacts with software applications like web browsers. It's primary functions are to identify communication partners and to synchronize communication.

HTTP and HTTPS are examples of Layer 7 protocols.

### Layer 6 - Presentation Layer

Data in applications is stored in what's called **application format**. Before it can be sent over a network, it must be translated into a **network format**. This is the job of the **presentation layer**. Note that this layer can also translate between different application formats.

Encryption is one example of translating into a network format.

### Layer 5 - Session Layer

The **session layer** controls sessions between hosts. It establishes, manages, and terminates connections between the local application and the remote application.

### Layer 4 - Transport Layer

The **transport layer** segments and reassembles data for communications between end hosts. It breaks large pieces of data into smaller segments which can be more easily sent over a network and are less likely to cause transmission issues if errors occur (losing a few small pieces of data will have a different effect from losing a huge chunk of it).

This layer adds a Layer 4 **header** to the data before passing it to Layer 3. The object consisting of the data and the L4 header is called a **segment**.

### Layer 3 - Network Layer

Layer 3 is called the **network layer**. It provides connectivity between end hosts on different networks. It also provides logical addressing (IP addresses) and path selection between the data's source and destination.

Routers are an example of Layer 3 hardware.

This layer adds an additional header to the received segment. This header contains information like the IP address the data is coming from. The object object consisting of a segment and an L3 header is called a **packet**.

### Layer 2 - Data Link Layer

The **data link layer** provides node-to-node connectivity and data transfer (PC to switch, switch to router, router to router, etc.). It defines how data is formatted for transmissions over a physical medium. A switch is an example of Layer 2 hardware.

This layer detects and (sometimes) corrects errors from the physical layer. Also, note that Layer 2 uses its own, separate addressing.

An L2 header and trailer are added to the packet, creating a **frame**.

### Layer 1 - Physical Layer

The **physical layer** defines the physical characteristics of the medium used to transfer data between devices. These are things such as voltage levels, physical connectors, cable specifications, etc.

This layer does not do any further encapsulation.

In the physical layer, digital bits are converted into electrical signals (for wired connections) or radio signals (for wireless connections).

### Sending and Receiving Data

When a node sends data over a network, it first **encapsulates** the data before sending. This is the process of adding headers and trailers as the data moves down the layers. 

When a node receives data over a network, it performs **de-encapsulation** as that data moves up the layers. Basically, it does encapsulation in reverse. The process is as follows:

1. The raw physical data is transformed back into a frame
2. The L2 header and trailer are stripped
3. The L3 header is stripped
4. The L4 header is stripped

After these four steps (which all happen in their corresponding layers), we are left with only the original data.

Node: data, segments, packets, and frames are referred to as **Protocol Data Units (PDUs)**.

## TCP/IP Suite

The **TCP/IP Suite** is a conceptual model and set of communications used in the Internet and other networks. It was developed by DARPA. Unlike the OSI model, the TCP/IP Suite is actually in use today.

The suite has a similar structure to the OSI model, but with fewer layers. The layers are:

- Application
- Transport
- Network
- Link

The suite's Application layer is actually just a combination of OSI's layers 5, 6, and 7. The Transport and Network layers are the same as in OSI, and the Link layer is a combination of OSI's layers 1 and 2.

Note that when people refer to layers, they usually mean the OSI layers.