[TOC]

# Transport Services Provided by the Internet

The internet makes two transport protocols available to applications, **UDP and TCP**. 



## TCP Services

TCP service model includes a connection-oriented service, with reliable data transfer. 

#### Connection - Oriented Service

- TCP has the client and server exchange transport layer control information with each other **BEFORE** the application-level messages begin to flow, this is called **handshaking**
  - this alerts both the client and server, and "prepares" them for the packets
- Now a **TCP Connection** is said to exist between the sockets of the two processes
- known as a **full-duplex connection**, now the two processes can send messages to each other over the connection at the same time
- the application must break the connection once it's done sending messages

#### Reliable Data Transfer Service

- communicating processes rely on TCP to deliver all data without error and in the right order
- TCP can be counted on to deliver the the stream of bytes (data) with no missing or duplicate bytes



## UDP Services

UDP is connectionless, hence there is no "handshaking" before the two processes start communicating.

#### Unreliable Data Transfer Service

- when a process sends a message into a UDP socket, UDP does not guarantee that the message will reach the receiving process
- messages that do arrive, may arrive out of order



## Summary of TCP vs. UDP

| **TCP Service**                                              | **UDP Service**                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Reliable transport** between sending and receiving process | **Unreliable data transfer** between sending and receiving process |
| **Flow control**: sender won't overwhelm the receiver        | **Does not provide:** reliability, flow control, congestion control, timing, throughput guarantee, security or connection setup |
| **Congestion control:** throttle sender when network is overloaded |                                                              |
| **Does not provide:** timing, minimum throughput guarantee, security |                                                              |
| **Connection-oriented:** setup required between client and server processes |                                                              |





