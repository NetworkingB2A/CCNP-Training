# BGP
Notes
- BGP = Border Gateway Protocol
- EGP ( exterior gateway protocol) is the predecessor to BGP
- Forms Neighborships
- Neighbor's IP address is explicitly configured 
- working between Autonomous systems
- A TCP session is established between neighbors
- Advertises address prefix and length ( called network layer reachability information - NLRI )
  - NLRI is a routing update that consists of the network prefix, prefix length, and any BGP PAs for a specific route.
- Path vector routing protocol  


Loop prevention
If a BGP router receives a prefix advertisement with its AS listed in the AS_Path attribute, it discards the prefix because the router thinks the advertisement forms a loop.

Address families
- Every address family maintains a separate database ans configuration for each protocol in BGP.
## BGP Attributes
There are 4 catagories of BGP Attributes
- Well-known mandatory
- Well-known discretionary
- Optional transitive
- Optional non-transitive



BGP Attributes|Description
-|-
Weight| A locally significant Cisco-specific parameters. Higher weight is preferred. Info does not get sent to our neighbors. Commonly used to influence outbound routing decisions.
local preference| A parameter communicated throughout a single AS. A higher local preference is preferred. Commonly used to influence outbound routing decisions.
Originate| Path sourced locally are preferred. the next hop ip address will appear as all 0.0.0.0
AS path| The number of autonomous systems in the AS_PATH path attribute. Lower AS Path lengths are preferred.
Origin type|Indicate how the route was injected into BGP: i ( network command), e (egp), or ? (redistributed). i is preferred to e, and e is preferred to ?.
Multi-Exit Discriminator (MED)|A parameter set and advertised by routers in one AS to influence the BGP path selection decisions of routers in another AS. Lower med is preferred.
Paths| Prefer eBGP path over iBGP path
Router ID| A tie breaker, where the route received from the router with the lowest router ID is preferred.



BGP messages
Type|Name|Functional Overview
-|-|-
1|OPEN|Sets up and establishes BGP adjacency
2|UPDATE|Advertises,updates, or withdraws routes
3|NOTIFICATION|Indicates an error condition to a BGP neighbor
4|KEEPALIVE|Ensures that BGP neighbors are still alive

NOTES
Hold time - When establishing a BGP session, the routers use the smaller hold time value contained in the two routers' OPEN messages. Default hold time for Cisco is 180 seconds.

BGP Neighbor states 
Idle
Connect
Active
OpenSent
OpenConfirm
Established





Basic eBGP configuration

Router10
router bgp 65010
neighbor 10.11.10.11 remote-as 65011  
network 10.10.10.10 mask 255.255.255.255

Router11
router bgp 65011
neighbor 10.11.10.10 remote-as 65010
network 10.11.11.11 mask 255.255.255.255
