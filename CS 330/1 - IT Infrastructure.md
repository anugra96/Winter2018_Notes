[TOC]



# IT INFRASTUCTURE

**IT Infrastructure** refers to the shared technology resources that provide the platform for the firm's information system applications

- including investment in hardware, software, and services (consulting, education, training)



## Components of IT Infrastructure

![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 330\screenshots\IT_infrastructure_ecosystem.png)

### Component 1: Computer Hardware Platforms

#### Client Machines

- machines that are used by users to access the system
- referring to desktops, laptops, and portable computing devices

#### Server Machines

- high end PC/tower server
- **Blade servers**
  - thin modular devices, for single dedicated server application
  - stripped down server to minimize use of physical space and energy

#### Additional Hardware

- UPS, printers, scanners etc



### Component 2: Operating System Platforms

- the OS manages a computer's hardware
- Windows dominates the market for client machine software
  - 88% of PCs run on Windows (as of May 2018)
- UNIX/LINUX is widely used as server software
  - 66% of servers use Unix or Linux
  - mostly open source software



### Component 3: Enterprise Applications

- set of computer programs used by organizations that integrate business applications and services
- largest suppliers include:
  - SAP, Oracle, IBM, Microsoft, HP
- Cloud-based applications:
  - force.com, google docs, hotmail etc



### Component 4: Data Management and Storage 

#### Database Management System (DBMS)

- leading DBMS providers are IBM, Oracle, Microsoft and Sybase
- MySQL is open source and available free of charge
- **Database server:** may need a server machine to run DBMS
  - especially if it needs to be accessed by several machines at the same time
  - or even if it needs to be accessible by anyone on the internet
- **Document management system**
  - allows file sharing amongst users
  - example: Sharepoint

#### Data Storage

- **Hard drive, tape drive**
- Cloud based storage (discussed later)
- Holographic storage (RAID Storage)
  - **RAID:** Redundant Array of Independent Disk



#### RAID Technology

- **RAID Storage Architecture**

  - different levels: most common are Level 1 (RAID 1) - Level 5 (RAID 5)
  - measures to evaluate performance:
    - storage efficiency
    - fault tolerance
    - read/write speed

- RAID Technologies

  - **Mirroring**
    - Used in RAID 1
  - **Striping**
    - used in all RAIDs except RAID 1
  - **Parity**
    - odd or even
    - used in RAID 5 and others

- **How RAID Improves Performance**

  - **Data striping** is used, where parallelism is utilized to improve disk performance

    - distributes data transparently over multiple disks to make them appear as a single large, fast disk

  - **Parity**

    - a parity bit is added to a string of binary code that indicates whether the number 1-bits in the string is even or odd

    - example:

      - ![](C:\Users\Anugra Shah\OneDrive\University of Waterloo\Winter 2019\notes\CS 330\screenshots\parity.png)

        

| RAID # | How it works                                              | Problems                                                     |
| ------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| RAID 0 | Only data striping is used. This is good for performance. | There is a chance of data loss due to hard drive failure. Annual failure rate for a hard drive is **1.84%** |
| RAID 1 | Only use mirroring. This is good for performance.         |                                                              |
| RAID 5 | Striping and parity are used. Good for performance.       |                                                              |



#### Data Backup

- **Online Backup**
  - instant real-time back up of data
  - example: RAID 1 and RAID 5
  - protects against one hard drive failure
- **Offline Backup**
  - done at the end of the day, copied and shipped to a different location
  - protects against complete failure, but can only recover data from one day ago
  - full vs. incremental backup



#### Law of Mass Digital Storage

- the amount of digital information is roughly doubling every year
- the cost of storage is falling at 100% per year



### Component 5: Network and Telecom Platforms

- **Network**: group of computers linked together to share resources
- 



