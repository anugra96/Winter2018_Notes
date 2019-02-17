# Lecture 10

## Week 5 Quiz/Exercise

**Why are sequence numbers not needed in UDP? Why did we need to introduce sequence numbers in TCP?**

The header of UDP, we have port number, destination number, checksum, length of UDP segment. There is no sequence number because there are no services that are provided by UDP doesn't need it.

Reliability and order of the delivered data are services provided by TCP. The sequence number is needed to know which data is acknowledged and which data need to be re-sent at the sending side, and on the receiving side, it needs to know if the data is in order. If the segment is out of order, cache or discard the data. If you cache, and receive a packet that fills the gap, then re-build data and send to application.

**Why did we need to introduce timers in TCP?**

The timer is running on the sender. We need only one timer. The sender should not be waiting indefinitely for a response. If the sender receives an acknowledgement before the time-out, then the sender will re-send the packet. The send-base, the packet that has been sent, but not acknowledged, is sent again after timeout.

**In TCP, the size of the transmission window is static. True or False?**

False. The transmission window is how much data can we send without receiving an acknowledgement. The size of the transmission window depends on the buffer space in the receiving socket, which is captured by the flow control mechanism. The size also depends on the congestion level of the network, congestion control mechanism.

**Suppose that TCP sequence number space is 0..N-1. What relation should there be between N and W, TCP maximum window size?**

When the sender is sending segments, they have to be different sequence numbers, because when you receive an acknowledgement, we wouldn't know which packet is being acknowledged, if some of them have the same sequence number. 

This is why, we need W to be less than N.

**Host A and Host B are directly connected with a 100 Mbps link. There is  one TCP connection between the two hosts, and Host A is sending to Host B a very large file over this connection. Host A can send its application data into its TCP socket at a rate as high as 120 Mbps but Host B can  read out of its TCP receive buffer at a maximum rate of 50 Mbps.  Describe the effect of TCP flow control.**  

As the buffer fills up, the receiver will send an acknowledge to the sender saying how much free space is remaining in its buffer. The sender will decrease the rate of the transmission, (decreasing W). The W will convert to 50 Mbps. The flow control will throttle the amount of data that is being sent according to the remaining buffer left in the receiver.

**Consider a TCP connection between Host A and Host B. Suppose that the  TCP segments traveling from Host A to Host B have source port number x  and destination port number y. What are the source and destination port  numbers for the segments traveling from Host B to Host A?**  

Destination - x

Source - y

**Consider congestion control in TCP. When the timer expires at the  sender, the value of the threshold (value of the window after which  congestion avoidance starts) is set to one half of its previous value.**  True or False?

TRUE. The value of the slow start threshold is half of its previous value.

**If TCP was working in stop-and-wait mode, what would a good enough sequence number space?**

0, N are the only sequence numbers we'll need.

**Consider an idealized case of two hosts, one located on the West Coast  of the United States and the other located on the East Coast. The  speed-of-light round-trip propagation delay between these two end  systems, RTT, is approximately 30 milliseconds. Suppose that they are  connected by a channel with a transmission rate, R, of 1 Gbps (109 bits per second). With a packet size, L, of 1,500 bytes, how big would  the TCP transmission window size have to be for the channel utilization  to be greater than 98 percent?** 

Utilization = ((Wp x L) / RTT)/R
$$
Utilization\ =\ \frac{\frac{Wp\ *\ L}{RTT}}{R}
$$
Wp = number of packets inthe window that are sent

Wp x L / RTT = rate at which TCP sender is sending

R = rate at which we can send

Wp = (0.98 * R * RTT) / L = how many segments we should be able to transmit over a utilization of 98%

***do the conversions***



## The Network Layer

The network layer will take the transport layer segment and add a header, in the header, we'll have addresses needed for demultiplexing (IP addresses). The sender needs to know what the IP address of the destination and insert it into the packet header before transporting the packet into the link. Using DNS, the www. address is converted to the IP address. 

Network layer on host will take the segment, will encapsulated into an IP datagram, append the IP address and then sent. 

In the router, there is a switch that takes the information in the header packet, to decide where to "route" the packet.

**Routers provide two services:**

- forwarding
  - 
- routing
  - deciding the best route a packet should take to a destination



**INTERNET (IP) IS:**

- packet switched
- datagram network
- connectionless
  - we don't establish the connection, the packets are just sent
- best effort network
  - its not reliable, IP will do its best to transmit the package

