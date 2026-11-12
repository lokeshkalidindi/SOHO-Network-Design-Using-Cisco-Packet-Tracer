# Network Architecture

## 1. Project Overview

This project demonstrates the design and implementation of a Small Office Home Office (SOHO) network using Cisco Packet Tracer.

The network is designed for three departments: Admin/IT, Finance/HR, and Customer Service/Reception.

Each department is assigned a separate VLAN to organize the network and provide logical network segmentation.

## 2. Network Devices Used

The following devices are used in this project:

| Device | Model / Type | Purpose |
|---|---|---|
| Router | Cisco 2911 | Inter-VLAN routing and DHCP |
| Switch | Cisco 2960 | Connecting network devices and managing VLANs |
| Wireless Access Points | Access Point-PT | Providing wireless connectivity |
| End Devices | PCs, Printers, Tablets and Smartphones | Connecting users to the network |

## 3. Network Departments

The network is divided into three departments.

| Department | VLAN ID | Network Address | Subnet Mask |
|---|---:|---|---|
| ADMIN/IT | 10 | 192.168.1.0/26 | 255.255.255.192 |
| FINANCE/HR | 20 | 192.168.1.64/26 | 255.255.255.192 |
| CS/RECEPTION | 30 | 192.168.1.128/26 | 255.255.255.192 |

Each department uses a separate VLAN and IP subnet.

## 4. Network Architecture

The Cisco 2911 router is connected to the Cisco 2960 switch.

The switch connects the wired devices and wireless access points used by the three departments.

The router uses subinterfaces to handle communication between the different VLANs.

The connection between the router and switch uses IEEE 802.1Q trunking.

## 5. VLAN Configuration

The following VLANs are configured on the Cisco 2960 switch:

- VLAN 10 – ADMIN_IT
- VLAN 20 – FINANCE_HR
- VLAN 30 – CS_RECEPTION

Each VLAN has assigned switch ports for connecting departmental devices.

## 6. Inter-VLAN Routing

Inter-VLAN routing is configured using the Router-on-a-Stick method.

The router uses three subinterfaces:

| Router Subinterface | VLAN ID | Default Gateway |
|---|---:|---|
| GigabitEthernet0/0.10 | 10 | 192.168.1.1 |
| GigabitEthernet0/0.20 | 20 | 192.168.1.65 |
| GigabitEthernet0/0.30 | 30 | 192.168.1.129 |

IEEE 802.1Q encapsulation is configured on each subinterface.

## 7. DHCP Configuration

Three DHCP pools are configured on the router to provide automatic IP address assignment to network devices.

- Admin-pool – ADMIN/IT
- Finance-pool – FINANCE/HR
- Cs-pool – CS/RECEPTION

Each DHCP pool provides IP addresses, subnet masks, and default gateway information for its respective network.

## 8. Network Connectivity

The network includes both wired and wireless devices.

- Wired PCs and printers connect through the Cisco 2960 switch.
- Wireless devices connect through wireless access points.
- The router provides gateway services for the three departmental networks.

Network connectivity is evaluated using ICMP ping tests.

## 9. Project Implementation

The network was implemented using the following steps:

1. Designed the network topology.
2. Added and connected the router, switch, and end devices.
3. Created three departmental VLANs.
4. Assigned switch ports to their respective VLANs.
5. Configured trunking between the router and switch.
6. Configured router subinterfaces for inter-VLAN routing.
7. Created DHCP pools for automatic IP assignment.
8. Configured wireless access points.
9. Performed network connectivity testing.

## 10. Conclusion

This project provided practical experience in designing and configuring a small office network using Cisco Packet Tracer.

It demonstrates the use of VLANs, IPv4 subnetting, trunking, Router-on-a-Stick inter-VLAN routing, DHCP, and wired and wireless networking.
