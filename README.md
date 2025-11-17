Enterprise Network Design with VLANs, EtherChannel, HSRP, and Centralized DHCP

This project involves designing and deploying a resilient enterprise LAN using Cisco routers and switches.
The goal was to build a segmented, scalable, and highly available network using VLANs, EtherChannel, redundant gateway protocols (HSRP), and centralized DHCP services with relay support.
All configurations were implemented in Cisco Packet Tracer.

Implementation Summary
1. VLAN Segmentation and Port Assignment

I created two VLANs to separate user groups and reduce broadcast traffic.

VLAN 10 assigned to devices (DOM, ASHLEY, PAUL, PETER PCs)

VLAN 20 assigned to devices (FATOU, SARAH, JEAN, ALAN PCs)

All switch ports were mapped to the appropriate VLAN. 
This segmentation reflects how real businesses separate departments for security and traffic optimization.

2. EtherChannel Deployment Between Switches

-To increase bandwidth and resiliency between the switches, I configured EtherChannel.

-Bundled FastEthernet 0/21–0/24 on both switches into a single logical link

-Improved throughput while providing redundancy against single link failure

-Reduced dependence on spanning tree by aggregating links

This created a stable and high-performance switching backbone.

3. Trunk Links to Routers

I configured trunk links between the access switches and both routers.

Allows multiple VLANs to travel across a single interface

Supports router-on-a-stick inter-VLAN routing design

This step ensured that VLAN-tagged traffic reached the routers correctly.

4. Inter-VLAN Routing (Router-on-a-Stick)

-I enabled inter-VLAN routing by creating sub-interfaces on both routers.

-One sub-interface per VLAN (for example, Gig0/0.10 for VLAN 10, Gig0/0.20 for VLAN 20)

-Each sub-interface was assigned an IP address from its corresponding subnet

-This allowed VLANs to communicate securely while maintaining logical separation.

5. Gateway Redundancy Using HSRP

To provide high availability for default gateways, I configured HSRP on both routers.

-Created virtual gateways for VLAN 10 and VLAN 20

-Router 1 acts as Active

-Router 2 acts as Standby

If Router 1 fails, Router 2 takes over instantly, ensuring no interruption for connected devices.

6. Centralized DHCP Server Configuration

Router 1 was configured as the DHCP server for both VLANs.
Each DHCP pool included:

Subnet and mask

HSRP virtual IP as default gateway

DNS server assignment

This created a centralized and automated addressing system for all network devices.

7. DHCP Relay on Router 2

Router 2 does not host DHCP services, so I configured it as a relay.

Forwards DHCP broadcasts to Router 1

Ensures devices behind Router 2 receive valid IP configurations

This models how enterprise networks use relay agents to centralize DHCP operations.

Skills Demonstrated

-VLAN design and segmentation
-Cisco switch configuration and trunking
-EtherChannel aggregation for redundancy and performance
-Inter-VLAN routing using router-on-a-stick
-High availability gateway setup using HSRP
-DHCP server and DHCP relay implementation
-Troubleshooting routing, switching, and VLAN communication

Understanding of enterprise LAN design principles
![NETWORK DESIGN](https://github.com/user-attachments/assets/73b5c549-4431-439c-b07a-1e1bca515381)
![Jean in Vlan 20 can communicate with Cyr in Vlan 10](https://github.com/user-attachments/assets/f37c2e0a-2e1a-40e7-b1bb-7f27ca56c649)
![Dom in Vlan 10 can communicate with Sarah in Vlan 20](https://github.com/user-attachments/assets/30ba169d-32a3-4838-a9ca-ec1792295534)
![Switch B VLAN](https://github.com/user-attachments/assets/a64fd463-1dd8-4722-aaea-cc2995b7034b)
![Switch B Trunk Interfaces](https://github.com/user-attachments/assets/89d60f07-c055-4387-bf38-c6d842a53b0c)
![Switch B Etherchannel Verification](https://github.com/user-attachments/assets/535fe49b-cb6a-4a8a-b09f-880571dc6a6b)
![Switch B Etherchannel](https://github.com/user-attachments/assets/5d2183bd-a70c-408f-8697-ae34837b3c70)
![Switch A VLAN](https://github.com/user-attachments/assets/b9fa99f8-92a3-4007-871f-4a71af3e3a03)
![Switch A Trunk interfaces](https://github.com/user-attachments/assets/7c1544d4-179e-4449-a9d0-bf96b929cf9c)
![Router B Inter-VLAN Routing](https://github.com/user-attachments/assets/668b6a14-b5cf-41b5-b738-3290a94ec804)
![Router B HSRP Config verification](https://github.com/user-attachments/assets/f3573a56-9775-4514-bd1d-76521209d27d)
![Router A Inter-VLAN Routing](https://github.com/user-attachments/assets/2ed14d36-22bb-4d02-95da-d623717fad05)
![Router A HSRP Verification](https://github.com/user-attachments/assets/138b3c8b-e9ff-48aa-8517-ffbb34d38bea)
![Router A as DHCP Server](https://github.com/user-attachments/assets/fd312ba5-cabd-4cdf-96ab-ce832bb07f0f)
![Router A Active ](https://github.com/user-attachments/assets/b70c0769-b313-4981-9ee9-a9b39fe5e6fe)
![Ping test connectivity](https://github.com/user-attachments/assets/a3dc00fd-6ad6-4149-8994-354abff72a5f)
