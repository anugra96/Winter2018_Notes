[TOC]

# Transport Services and Protocols

### Intro to Transport-Layer Services and Protocols

A transport-layer protocol provides for **logical communication** between application processes running on different hosts.

- application processes use this logical communication to send messages to each other, without worrying about the physical infrastructure details used to carry the messages

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 436\screenshots\transport_layer.png)

As we can see in Figure 3.1, transport layer protocols are implemented on the end systems, but not in network routers.

- on sending side: transport layer converts the application-layer messages into transport-layer packets, (known as **segments**)
  - done by breaking the messages into smaller chunks, and adding a transport layer header to each chunk
- transport layer then passes the segment into the network layer at the sending end system, where the segment is encapsulated into a network-layer packet (known as a **datagram**) and sent to the destination
- on the receiving side, the network layer extracts the transport layer segment and passes the segment to the transport layer, which then processes data and makes it available to the receiving application process



### Relationship Between Transport and Network Layers

**Recall:** the transport layer lies just above the network layer in the protocol stack

A transport-layer protocol provides logical communication between ***processes*** running on different hosts, meanwhile a network-layer protocol provides logical communication between ***hosts***.

> **Analogy** 
>
> - consider two houses, one on the East Coast and the other on the West Coast, each house has 12 kids
> - the kids love to write to each other, and they write to their cousins every week. 
> - each household sends 144 letters to the other every week
> - Ann from East Coast, and Bill from West Coast, collect all the letters and take them to the postal service to be sent, and they also distribute received letters
>
> **Analysis**
>
> - application messages = letters in enveloppes
> - processes = cousins
> - hosts (end systems) = houses
> - transport-layer protocol = Ann and Bill
> - network-layer protocol = postal service



### Multiplexing and Demultiplexing

**Demultiplexing** - The job of delivering the data in a transport-layer segment to the correct socket

**Multiplexing** - The job of gathering data chunks at the source host from different sockets, encapsulating each chunk with headers, to create segments and passing segments to the network layer.





