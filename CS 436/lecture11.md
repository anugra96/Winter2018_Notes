# Lecture 11

- review longest prefix matching

**The Internet Network Layer**

- the IP protocol
- routing protocols
  - used to maintain routing tables
  - routing algorithm chooses the destination, helping routers communicate with each other, to find the best path to a destination



**IP Datagram Format**

- review slide 4-10

```
TTL <- TTL - 1
if TTL = 0 {
    drop packet
    send ICMP to source
} else {
    forward packet
}
```



router only bases its routing decision on the destination IP address.

- source IP address is useful, when TTL = 0, so that it can tell the source that the packet was dropped



**IP Addressing: Introduction**

- 32-bit identifier for a host, router interface
- **interface: ** connection between host/router and physical link
  - if both wireless and ethernet are active, then your host will have two different IP addresses
- **subnet**
  - network of interfaces that connect to each other without having to go through a router
- IP address is composed of two parts
  - subnet part
    - all addresses in the same subnet start with the same first three bytes
  - host part
    - changes between the network interfaces



### Subnets

**Mark in CIDR**: /24 can translate to subnet mask:

255.255.255.0

/16:

255.255.0.0

8bits.8bits.8bits.8bits

/15:

255.254.0.0



**example in 4-15**

223.1.1.0	/24

223.1.9.0	/24

223.1.2.0	/24

223.1.8.0	/24

223.1.3.0	/24

223.7.1.0	/24

- when choosing the CIDR, you have to make sure there is no overlapping