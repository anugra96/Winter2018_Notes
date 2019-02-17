[TOC]



# Socket Programming

## Socket Programming with UDP

**Recall:** processes running on different machines communicate with each other by sending messages into sockets

#### Closer Look at Interaction Between Two Processes (Using UDP)

- a destination address must be attached to the packet that is being sent out the sending socket
- when the packet arrives at the receiving socket, the receiving process will get the packet from its socket and then interact with the packet

#### Examining the Destination Address

- the destination host's IP address

- an identifier, **port number** of the destination socket

  

> Example: demonstrate socket programming 
>
> 1. The client reads a line of characters from its keyboard and sends the data to the server
> 2. The server receives the data and converts the characters to uppercase
> 3. The server sends the modified data to the client
> 4. The client receives the modified data and displays the line on its screen



#### Implementation of Simple Client-Server Program (UDP)

- begin with UDP client, which sends a simple application level message to the server
- the server MUST be running, before it can receive and reply to the client's message



![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 436\screenshots\socketprogramming.png)



##### UDPClient.py

```python
from socket import *
serverName = 'hostname'
serverPort = 12000
clientSocket = socket(socket.AF_INET, socket.SOCK_DGRAM)
message = raw_input('Input lowercase sentence:')
clientSocket.sendto(message, (serverName, serverPort))
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print modifiedMessage
clientSocket.close()
```



##### Analyzing the Code

| **Line Number** | Meaning                                                      |
| --------------- | ------------------------------------------------------------ |
| line 1          | We need the socket module in Python. We can create sockets within our program with this. |
| line 2, 3       | Here, we set the hostname, which can be an IP address of the server, or the hostname of the server. Then we assign the port number of the server. |
| line 4          | We create the client's socket. First parameter indicates the address family; AF_INET, indicates the underlying network is using IPv4. Second parameter indicates the socket type, SOCK_DGRAM means it is a UDP socket. We are not specifying the port number for the client socket, and instead letting the OS do this for us. |
| line 5          | raw_input() is a python function that prompts the user to input data. The data is then stored in the message variable. |
| line 6          | method sendto() attaches the destination address (serverName, serverPort) to the message and sends the packet into the process's socket, clientSocket. Now the client waits to receive data from the server. |
| line 7          | When a packet arrives (the reply) at the client's socket, the packet's data is stored in modifiedMessage, and the source address is put into serverAddress. serverAddress contains the server's IP Address and its port number. The method recvfrom takes the buffer size 2048, which works for most purposes. |
| line 8          | prints the modifiedMessage to the user's display             |
| line 9          | this line closes the socket, and the process is then terminated. |



##### UDPServer.py

```python
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))
print "The server is ready to receive"
while 1:
    message, clientAddress = serverSocket.recvfrom(2048)
    modifiedMessage = message.upper()
    serverSocket.sendto(modifiedMEssage, clientAddress)
```



##### Analyzing the Code

| Line Number | Meaning                                                      |
| ----------- | ------------------------------------------------------------ |
| line 4,5,6  | this assigns (binds) the port number 12000 to the server's socket. Now when anyone sends a packet to port 12000 at the IP address of the server, the packet will be directed to this socket. UDPServer then enters a while loop, which allows UDPServer to receive and process packets from clients indefinitely. It now waits for a message to arrive. |
| line 7      | when a packet arrives, the data is put into the variable message and the packet's source is put into the address clientAddress (containing both client's IP Address and client's port number). UDPServer uses this as it needs a return address. |
| line 8      | here the message is modified (capitalized)                   |
| line 9      | this line sends the modified message to the server's socket. The assigning of the server address is also attached to the packet, but its done automatically, not in code. |



## Socket Programming with TCP

#### Closer Look At Interaction of Client and Server Programs (using TCP)

- client has to initiate contact with the server
- server has to be ready to react to the client's initial contact, implying two things:
  - TCP server must be running as a process before the client attempts initial contact
  - server program must have a special socket, that welcomes the initial contact from a client process running on a random host
- Once the server is running, the client process initiates a TCP connection to the server. Done by creating a TCP socket in the client program.
  - it specifies the address of the welcoming socket in the server
    - its IP address and port number
- client now creates a three-way handshake, taking place in the transport layer, completely invisible to the client and server programs
- during the **three-way handshake** the client process knocks on the server's welcoming socket. 
  - the server creates a new socket that is dedicated to that particular event

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 436\screenshots\three-way-handshake.png)

#### Implementation of Simple Client-Server Program (TCP)

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 436\screenshots\socketprogramming.png)

##### TCPClient.py

```python
from socket import *
serverName = 'servername'
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_STREAM)
clientSocket.connect((serverName, serverPort))
sentence = raw_input('Input lowercase sentence:')
clientSocket.send(sentence)
modifiedSentence = clientSocket.recv(1024)
print 'From Server:', modifiedSentence
clientSocket.close()
```



##### Analysis of code

| Line Number | Meaning                                                      |
| ----------- | ------------------------------------------------------------ |
| line 4      | We create the client's socket. First parameter we have seen before (IPv4). Second parameter SOCK_STREAM means it will be a TCP socket. Note that we are not specifying a port number of the client socket, when we create it, the OS will take care of that. |
| line 5      | Here, the client is making the first initial TCP connection to the server. The connect() method's parameter is the address of the server side connection. A three-way handshake is performed after this line of code, and a TCP connection is established |
| line 7      | This line sends the sentence through the client's socket, and into the TCP connection. Note that there is no creation of packet needed, as dropping the bytes of data into the TCP pipeline is enough. The client now waits for a response. |



##### TCPServer.py

```python
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', serverPort))
serverSocket.listen(1)
print 'The server is ready to receive'
while 1:
    connectionSocket, addr = serverSocket.accept()
    sentence = connectionSocket.recv(1024)
    capitalizedSentence = sentence.upper()
    connectionSocket.send(capitalizedSentence)
    connectionSocket.close()
```



##### Analysis of code

| Line Number | Meaning                                                      |
| ----------- | ------------------------------------------------------------ |
| line 5      | Because of TCP, serverSocket will be our welcoming socket. We will wait and listen for some client to knock on the door. The parameter (1) specifies the max number of queued connections. (Atleast 1) |
| line 8      | When a client knocks on this door, the program uses accept() method which creates a new socket in the server, called connectionSocket. There is now a TCP connection between clientSocket and the server's connectionSocket. Now client and server can send bytes to each other. |

