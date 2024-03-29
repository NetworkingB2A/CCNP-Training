Topic 3.2.b

# OSPF v2

## How does OSPF work?
### What is a LSA?
### What is the LSDB?
### What is an Area?
### What is the the Hello and Dead interval?
### What is OSPF authentication? 
### What is in a Hello Packet?



## Metric
Link Speed | Cost
---|---
10 Mbps|
100 Mbps|
1 Gbps|

## Neighborship vs Adjacencies

### Neighbors
Neighbors are routers that 
- Reside on the same network link
- Exchange hello messages  

Neighorship Requirements ** Need to know **
- Matching area
- Matching authentication
- Matching subnet
- Matching timers
- Matching stub flags
- Matching MTU (exstart/exchange state)


### Adjacencies 
Adjacencies are routers that
- Are neighbors
- Have exchanged link state updates (LSUs) and database description packets

Number of Adjacencies = [n*(n-1)]/2 ** n is the number of routers

Adjacencies only need to be formed with the DR and the BDR
DR = Designated Router
BDR = Backup Designated Router

### DR and BDR election
Highest router priority wins
- default is 1
- carried in hello packet
- configured in interface configuration mode
    - <code>router(config-if)# ip ospf priority number </code>
    - A priority of 0 prevents a router from participating in the election  

Highest router id wins
- configured in router configuration mode
- if there is no configured router id, the highest ip address on a loopback interface wins
- if there is no loopback configured, the highest ip address on an interface that is up wins

## Network Types
Broadcast Network Type
- Broadcast i send default OSPF network type for any ethernet interface
- dr and bdr routes are elected
- default hello interval: 10 seconds  

Point-to-Point Network Type
- point-to-point is the default ospf network type for a non-frame relay serial interface
- dr and bdr routers are not elected
- default hello interval: 10 seconds  

Non-Broadcast (NBMA) Network Type
- NBMA is the default ospf network type on a physical frame relay serial interface
- dr and bdr routers are elected
- uses the neighbor command to specify a neighbor's ip address
- default hello interval: 30 seconds

Point-to-Multipoint Network Type
- Replicates packets to send to neighbors
- Treats each PVC as a point-to-point link
- dr and bdr routers are not elected
- default hello interval: 30 seconds

Valid OSPF Network types for Peer
- broadcast to broadcast
- non-broadcast to non-broadcast
- point-to-point to point-to-point
- broadcast to non-broadcast (requires timer adjustment)
- point-to-point to point-to-multipoint (requires timer adjustment)

## LSA Types
- Type 1 LSA: A router LSA is created by each router and contains information about the router's directly attached network.
- Type 2 LSA: A network LSA is created for each transit network within an area on which a DR is elected
- Type 3 LSA: A summary LSA is send from on area to another area and is used to advertise a network in the source area
- Type 4 LSA: A summary ASBR is created by an ABR to tell members of an area how to reach and ASBR
- Type 5 LSA: An AS external LSA is created by an ASBR to advertise networks in a different AS.
- Type 7 LSA: An NSSA is sent from an ASBR into an NSSA to advertise network from a different AS.

## Area Types
- Normal
- Stub area
  - This is will you send an area only two types of Type 3 LSAs. (Side note - you can not send type 4/5 LSAs into this area type)
    - 1 Type 3 LSA will be a normal one. This will be a summary LSA for a listing LSA for a different area
    - The other LSA will be a Type 3 default LSA. This one will suppress the Type 4 LSA and and the Type 5 LSA into a single type 3 LSA
- Totally Stubby Area
  - This will happen when you only send a Type 3 Default LSA into an area. You will NO LONGER be sending a normal Type 3 LSA. (Side note - you can not send type 4/5 LSAs into this area type)
- Not-So-Stubby Area(NSSA)
  - This happen when you enter an ASBR in an Stub/Totally Stubby Area, The ASBR will send out Type 7 LSAs
- Totally Not-So-Stubby Area
  - this will act the same as a Totally Stubby area and a Not-So-Stubby area. this area will only receive the Type 7 LSA and the a Default Type 3 LSA.

## Extra Notes
Hello Messages
- All OSPF routers - 224.0.0.5 or FF02::5
- All designated routers - 224.0.0.6 or FF02::6


## Terminology
Term|Definition
---|---
OSPF
LSA|Link State Advertisement
LSDB
SFP
ABR
ASBR
passive-interface
Route table abbreviations | definition  
O | 
IA | 
N1 |
N2 |
E1 |
E2 | Default Metric Type, unless specified