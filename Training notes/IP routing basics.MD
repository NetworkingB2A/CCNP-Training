## Three different types of routes
1. Directly connected routes
2. Static routes
3. Dynamic routes

## How is a route picked for the Routing table
longest mask  
Lower AD  
Lower cost  
Finally if both are the exact same then both routes will be added to the routing table



Type of Route|AD
---|---
Connected|0
Static|1
eBGP|20
Internal EIGRP|90
OSPF|110
IS-IS|115
RIP|120
External EIGRP|170
iBGP|200


## Different Routing protocols
Distance vector
- RIPv2
    - Doesn't care about Link speeds or bandwidth
    - Only cares about hop count
    - Not used very often
    - AD 120

Link-state
- OSPF
    - AD 110
- IS-IS 

Hybrid
- EIGRP (Enhanced Interior Gateway Routing Protocol)
    - Mostly open sourced, has an RFC. some advanced features are still proprietary 
    - The one big advantage to use EIGRP is when using DMVPN. Otherwise not used as often.
    - VERY FAST
    - AD 90

Path Vector
- BGP (Boarder gateway protocol)
  - peer to an IP address
  - TCP 179
  - iBGP and eBGP




