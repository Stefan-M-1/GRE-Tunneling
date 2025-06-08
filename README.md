Cisco GRE Tunneling with OSPF over EIGRP Backbone
This repository contains configuration files for establishing a Generic Routing Encapsulation (GRE) tunnel between two Cisco routers (R1 and R2) over a simulated public network backbone (SPR1 and SPR2) using EIGRP. OSPF is then used to route internal networks over the established GRE tunnel, allowing private network segments to communicate securely and efficiently.

Table of Contents
Overview
Network Topology
Configuration Files
Key Configuration Details
Router R1
Router R2
Service Provider Router SPR1
Service Provider Router SPR2
How to Implement
Verification
Assumptions and Prerequisites

Overview
This setup demonstrates a common use case for GRE tunneling: extending a private network across a public or untrusted network. The GRE tunnel encapsulates IP packets, allowing routing protocols like OSPF to operate seamlessly between the private networks of R1 and R2, even though their direct path traverses an EIGRP-controlled "internet" or service provider network.

Network Topology
The logical network topology is as follows:

R1 (Branch 1 Router):
Internal LAN: 10.0.1.0/24 (via GigabitEthernet0/0)
Public-facing interface: GigabitEthernet0/0/0 (100.0.0.2/30)
GRE Tunnel0: 192.168.1.1/30
R2 (Branch 2 Router):
Internal LAN: 10.0.2.0/24 (via GigabitEthernet0/0)
Public-facing interface: GigabitEthernet0/0/0 (200.0.0.2/30)
GRE Tunnel0: 192.168.1.2/30
SPR1 (Service Provider Router 1):
Connects to R1's public interface via 100.0.0.1/30 (GigabitEthernet0/0/0)
Participates in EIGRP for routing public IPs.
SPR2 (Service Provider Router 2):
Connects to R2's public interface via 200.0.0.1/30 (GigabitEthernet0/0/0)
Participates in EIGRP for routing public IPs.
SW1 & SW2 (Switches): Basic Layer 2 switches, assumed to provide connectivity to the internal LANs, but their configurations are generic and not directly involved in the GRE tunnel setup.

Configuration Files
R1.txt: Configuration for Router 1, including its internal network, public interface, GRE tunnel interface, and OSPF routing.
R2.txt: Configuration for Router 2, including its internal network, public interface, GRE tunnel interface, and OSPF routing.
SPR1.txt: Configuration for Service Provider Router 1, handling public network routing with EIGRP.
SPR2.txt: Configuration for Service Provider Router 2, handling public network routing with EIGRP.
SW1.txt: Generic configuration for Switch 1 (not directly involved in GRE).
SW2.txt: Generic configuration for Switch 2 (not directly involved in GRE).
