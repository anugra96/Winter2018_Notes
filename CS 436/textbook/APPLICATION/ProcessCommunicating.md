[TOC]

# Process Communicating

A **process **can be thought of as a program that is running within an end system.

- when processes are running on the same end system, they can communicate with each other with **interprocess communication** using rules that are governed by the operating system
- we are more concerned with how processes communicate when they are running on *different hosts*
- processes on different end systems communicate by exchanging messages across the computer network
  - **sending process** creates and sends message into the network
  - **receiving process** receives these messages and possibly responds by sending messages back



### Client and Server Processes

A **network application** consists of pairs of processes that send messages to each other over a network.

> Example:
>
> In the Web application a client browser process exchanges messages with a Web server process.
>
> - For each **pair of communicating process** we typically label one as the **client** and the other as the **server**
>
> In a P2P file-sharing system, a file is transferred from a process in one peer, to a process in another peer.
>
> - the peer that is downloading the file is labeled as the **client** and the uploading peer is labeled as the **server**



### The Interface Between the Process and the Computer Network

A process sends messages into and receives messages from the network through a software interface called a **socket**

#### Socket Analogy

- think of a process as a house, and its socket as the door
- when a process wants to send a message to another process (on another host), it shoves the message out of its door (socket)
  - there is an assumption by the sending process that there is a transportation infrastructure on the other side of the door that will transport the message to the door of its destination process
- once the message arrives at the destination host, the message passes through the receiving process's door (socket) and then the receiving process acts on the message

> ![1548966474383](C:\Users\ANUGRA~1\AppData\Local\Temp\1548966474383.png)
>
> The figure shows that the socket is the interface between the application layer and the transport layer within a host. 



The socket is also referred to as the **Application Programming Interface (API)** between the application and network.

- the socket is the programming interface with which network applications are built

The application developer has control of everything on the application layer side of the socket, but not much of the network layer side

- the only control they have on the network layer side is:
  1. choice of transport protocol
  2. ability to fix transport layer parameters such as max buffer and max segment sizes 



### Addressing Processes

left off: page 117 of textbook









