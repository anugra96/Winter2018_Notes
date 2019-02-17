[TOC]



## TCP Sender

### TCP: Retransmission Scenarios

**Scenario 1** - lost ACK scenario

If the package is out of order, it will either buffer or discard and will re-transmit the acknowledgement of the last package

If the acknowledgement is lost from host B, then host A will re-transmit the same package again, until host b will send another acknowledgment

**Scenario 2** - premature timeout

host A sends package seq92 and seq100 and receives acknowledgments for both, and when host A times out, then it will send the package associated with the timer again. Resend seq92 (because sendbase = 92)

Host B receives a duplicate package seq92 (and it knows that its a duplicate) hence it will send the latest acknowledgment (Seq100) so it will send back ACK = 120

- sendbase = 92 means all package before were acknowledged



### TCP Fast Retransmit

- if a packet is lost, we have to wait for the timer to reset until we send the package again
  - we dont have to wait for the timer to time out, **IF we receive 3 acknowledgements of previous packages**, then we will just retransmit, and not wait for the timer to timeout
- if a packet is out of order, then the host b will cache it, (or disregard) and then send the previous ACK



sequence numbers, acknowledements and timers are all artifacts that can be used to create a reliable transport layer protocol.

## TCP - Flow Control

**Goal of TCP Flow Control** - match sender and receiver rates 

transmission rate = W bits / RTT

- W is the number of bytes sent per RTT

Every socket is assigned a buffer (memory) where data is stored, waiting for the application to read it.

If the transmission rate is too fast, and too much data is being transmitted, then the socket will overflow.

**How to mitigate:**

- receiver keeps track of the free buffer space of the socket, rwnd , and this value will be inserted of the header of the acknowledgment, indicating that the sender can only send rwnd bytes of data.
- the sender then will set W = rwnd



**What happens if there is no more buffer space?**

- rwnd = 0
- sender will receive 0 from the ACK, so it will not be sending anything. But eventually there will be some buffer space available, but the sender will not know, because it is still not sending anything
- **solution: ** even if the sender received rwnd = 0, it will continue to send very small packets, to keep checking



## Connection Management



### TCP: closing a connection

client and server both close their side of connection

- they send a TCP segment with FIN bit = 1

there is a response to the received FIN with ACK, which can be combined with its own FIN



## Congestion Control

Additive increase, multiplicative decrease.

**approach:** sender increases transmission rate, probing for usable bandwidth, until loss occurs

**How does the sender know if the network is being congested?**

- if the buffer thing is 0
- routers can send messages to each other saying that they're overwhelmed (THIS IS NOT THE TCP WAY)
- **how does tcp sense the level of congestion in the network?**
  - higher delays (timeouts) and duplicate ACKs are signs of congestion
- when the sender senses congestion, it will drop the size of W 
  - W is controlled by two things:
    - value: rwnd
      - receiver socket buffer size
    - value: cwnd
      - congestion window

What is MSS?



### TCP Slow Start

- initial rate is slow, but it ramps up exponentially fast
- slow start is a very short phase where the connection sets the window size (1 MSS)
- when sender receives ACK, it doubles the size of the window
- **increase the size of the window every time an ACK is received**



### TCP: detecting and reacting to loss

- when there is a loss indicated by a timeout:

  - cwnd set to 1 MISS (go back to slow start)
  - window then grows exponentially (as in slow start) to threshold, then grows linearly
  - **slow start threshold:** where the timeout occurred / 2
  - then it increases at a linear rate, in a phase called the **congestion avoidance**
  - 

  



