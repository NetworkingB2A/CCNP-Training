Management port vs Service port vs RP
- Both are for management of the WLC. The SP is a out of band physical management port. The management port is a virtual port for management of the WLC. the main difference is the SP port is physical. The management port is a logical port. the RP port is a if you have HA set up between two WLC. The RP would plug into the second WLC

Virtual port
- The cases i have used the virtual port is where i am connected to the wireless but the splash screen will not show up. Cisco recommends to use 192.0.0.2 as the ip address.



setting up a interface
- create a interface name.
- select how you want to take the interface.
- assign to a port number
- set up ip address for the new interface.

Setting up a WLAN
- click new
- create profile name
- create SSID
- select an ID

Edit your new wireless profile
- enable
- assign to a interface or interface group
- if someone joins the new vault200 all of their traffic will be tagged with vlan 200 because i set up the interface as a tagged interface.

Security
- Layer 2
  - Here you are using EAP, PSK and other authentication protocols
  - When configuring EAP if you select 802.1x only, that will only allow for authentication and not encryption. 
- Layer 3
  - Here you will be using a splash screen or some for of website based authentication.
- AAA servers

## NOTES
In a large business environment using PSK is a VERY BAD IDEA. You should use 802.1x. 
You will want to use a Radius server ( or some kind of authentication server)

for now i set up a PSK with a password of cisco123

Mobility/RF group name allows clients to move from one AP to another AP.

Radius/802.1x is sometimes called wpa-ent