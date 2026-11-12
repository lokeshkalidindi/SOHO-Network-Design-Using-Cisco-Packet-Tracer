# IP Addressing and Subnetting

## 1. Overview

The SOHO network uses the IPv4 addressing scheme with a `/26` subnet mask.

The network is divided into three subnets, with each subnet assigned to a separate department.

## 2. IP Addressing Table

| Department | VLAN ID | Network Address | Subnet Mask | Default Gateway | Broadcast Address |
|---|---:|---|---|---|---|
| ADMIN/IT | 10 | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 | 192.168.1.63 |
| FINANCE/HR | 20 | 192.168.1.64/26 | 255.255.255.192 | 192.168.1.65 | 192.168.1.127 |
| CS/RECEPTION | 30 | 192.168.1.128/26 | 255.255.255.192 | 192.168.1.129 | 192.168.1.191 |

## 3. Usable Host Address Ranges

| Department | First Usable IP | Last Usable IP | Total Usable Hosts |
|---|---|---|---:|
| ADMIN/IT | 192.168.1.1 | 192.168.1.62 | 62 |
| FINANCE/HR | 192.168.1.65 | 192.168.1.126 | 62 |
| CS/RECEPTION | 192.168.1.129 | 192.168.1.190 | 62 |

## 4. DHCP Address Allocation

The Cisco 2911 router is configured with three DHCP pools.

| DHCP Pool | Department | DHCP Address Range |
|---|---|---|
| Admin-pool | ADMIN/IT | 192.168.1.1 – 192.168.1.62 |
| Finance-pool | FINANCE/HR | 192.168.1.65 – 192.168.1.126 |
| Cs-pool | CS/RECEPTION | 192.168.1.129 – 192.168.1.190 |

## 5. Subnetting Details

The subnet mask used in this project is:

**255.255.255.192 (/26)**

Subnetting details:

- Total IP addresses per subnet: 64
- Network address: 1
- Broadcast address: 1
- Usable host addresses: 62

Each department receives a separate subnet to maintain logical network separation.

## 6. Conclusion

The `/26` subnetting scheme provides 62 usable host addresses for each department.

Separate IP networks are assigned to ADMIN/IT, FINANCE/HR, and CS/RECEPTION, with the Cisco 2911 router providing the default gateway for each VLAN.
