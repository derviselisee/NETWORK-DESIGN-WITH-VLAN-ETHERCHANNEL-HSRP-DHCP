# NETWORK-DESIGN-WITH-VLAN-ETHERCHANNEL-HSRP-DHCP
Enterprise Network with VLAN Segmentation, Redundant Gateways (HSRP), DHCP Server, Relay, and EtherChannel .

In this project, I designed and configured a small enterprise network infrastructure using Cisco routers and switches in Packet Tracer. The goal was to build a scalable and resilient LAN that includes VLAN segmentation, redundant default gateways with HSRP, centralized DHCP services, and a high availability switching backbone using EtherChannel. 

WHAT DID I DO IN THIS PROJECT? 

Step 1: VLAN Creation and Port Assignment 

 I began by creating two VLANs: 

-VLAN 10 for one group of devices (DOM , ASHLEY ,PAUL ,PETER PCs) 

-VLAN 20 for another group (FATOU , SARAH , JEAN , ALAN PCs) 

Then I assigned the appropriate switch ports to each VLAN, ensuring proper segmentation of broadcast domains. This approach mimics how businesses isolate departments for security and traffic control. 

Step 2: EtherChannel Between Switches To improve both bandwidth and fault tolerance 

 I configured the EtherChannel between the two access switches. This combined multiple physical links into one logical link, increasing performance and preventing loops without over-relying on Spanning Tree. I bundled (port f0/21 to f0/24 on Switch A and Switch B to form on single link ) 

Step 3: Trunk Links to Routers 

Each switch was connected to both routers using trunk links, enabling them to carry traffic from multiple VLANs. This was essential for the router-on-a-stick inter-VLAN routing design I applied later. 

Step 4: Inter-VLAN Routing (Router-on-a-Stick)  

I configured sub-interfaces on both routers for each VLAN: 

One sub-interface per VLAN (e.g., Gig0/0.10 for VLAN 10, Gig0/0.20 for VLAN 20) 

Each sub-interface was assigned a unique real IP address in its VLAN subnet 

This allowed routers to route traffic between VLANs, enabling communication between different segments while preserving VLAN separation. 

Step 5: HSRP (Hot Standby Router Protocol) Configuration 

To ensure default gateway redundancy, I implemented HSRP on both routers: I assigned a shared virtual IP address per VLAN (e.g., 192.168.10.1, 192.168.20.1)  

-Router 1 was configured as the active router  

-Router 2 was configured as the standby 

HSRP ensures that even if the primary router fails, the standby router immediately takes over without interrupting client traffic. This adds high availability to the network. 

Step 6: Centralized DHCP Server on Router 1  

Router 1 was configured as a DHCP server to dynamically assign IP addresses to end devices in both VLANs.  

For each pool: I defined the subnet Assigned the HSRP virtual IP as the default gateway Set the DNS server and lease time 

This provided automatic and centralized IP management, simulating what an enterprise DHCP server does in production. 

Step 7: DHCP Relay on Router 2  

Since only Router 1 runs DHCP, I configured Router 2 as a DHCP relay agent. This allows devices behind Router 2 to send DHCP requests to Router 1 and still receive valid IP configurations. 
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
