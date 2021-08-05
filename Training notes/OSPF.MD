# OSPF


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


## Extra Notes
Hello Messages
- All OSPF routers - 224.0.0.5 or FF02::5
- All designated routers - 224.0.0.6 or FF02::6