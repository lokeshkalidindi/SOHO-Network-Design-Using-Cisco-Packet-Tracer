# Cisco Network Configuration Commands

## 1. Introduction

This document contains the Cisco IOS commands used to configure the SOHO network using Cisco Packet Tracer.

The configurations include VLAN creation, switch port assignment, trunk configuration, Router-on-a-Stick, and DHCP.

## 2. Switch Configuration (Cisco 2960)

### 2.1 Enter Global Configuration Mode

```bash
enable
configure terminal
```

### 2.2 Create VLANs

```bash
vlan 10
name ADMIN_IT
exit

vlan 20
name FINANCE_HR
exit

vlan 30
name CS_RECEPTION
exit
```

### 2.3 Assign Switch Ports to VLANs

**ADMIN/IT – VLAN 10**

```bash
interface range fa0/2-4
switchport mode access
switchport access vlan 10
exit
```

**FINANCE/HR – VLAN 20**

```bash
interface range fa0/5-7
switchport mode access
switchport access vlan 20
exit
```

**CS/RECEPTION – VLAN 30**

```bash
interface range fa0/8-10
switchport mode access
switchport access vlan 30
exit
```

### 2.4 Configure Trunk Port

The connection between the router and switch uses FastEthernet0/1.

```bash
interface fa0/1
switchport mode trunk
exit
```

### 2.5 Verify VLAN Configuration

```bash
show vlan brief
```

### 2.6 Verify Trunk Configuration

```bash
show interfaces trunk
```

## 3. Router Configuration (Cisco 2911)

### 3.1 Enter Global Configuration Mode

```bash
enable
configure terminal
```

### 3.2 Configure Router Subinterfaces

**VLAN 10 – ADMIN/IT**

```bash
interface gigabitEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.1.1 255.255.255.192
exit
```

**VLAN 20 – FINANCE/HR**

```bash
interface gigabitEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.1.65 255.255.255.192
exit
```

**VLAN 30 – CS/RECEPTION**

```bash
interface gigabitEthernet 0/0.30
encapsulation dot1Q 30
ip address 192.168.1.129 255.255.255.192
exit
```

### 3.3 Verify Router Interfaces

```bash
show ip interface brief
```

## 4. DHCP Configuration

DHCP pools are configured on the router to automatically assign IP addresses to network devices.

### 4.1 ADMIN/IT DHCP Pool

```bash
ip dhcp pool Admin-pool
network 192.168.1.0 255.255.255.192
default-router 192.168.1.1
dns-server 192.168.1.1
domain-name Admin.com
exit
```

### 4.2 FINANCE/HR DHCP Pool

```bash
ip dhcp pool Finance-pool
network 192.168.1.64 255.255.255.192
default-router 192.168.1.65
dns-server 192.168.1.65
domain-name Finance.com
exit
```

### 4.3 CS/RECEPTION DHCP Pool

```bash
ip dhcp pool Cs-pool
network 192.168.1.128 255.255.255.192
default-router 192.168.1.129
dns-server 192.168.1.129
domain-name Cs.com
exit
```

## 5. DHCP Excluded Addresses

The following gateway addresses are excluded from dynamic DHCP allocation.

```bash
ip dhcp excluded-address 192.168.1.1
ip dhcp excluded-address 192.168.1.65
ip dhcp excluded-address 192.168.1.129
```

This prevents DHCP from assigning the gateway addresses to client devices.

## 6. DHCP Verification Commands

### Display DHCP Pools

```bash
show ip dhcp pool
```

### Display Assigned IP Addresses

```bash
show ip dhcp binding
```

## 7. Configuration Verification

The following commands are used to inspect the network configuration.

| Command | Purpose |
|---|---|
| show vlan brief | Displays configured VLANs |
| show interfaces trunk | Displays trunk port information |
| show ip interface brief | Displays router interface status |
| show running-config | Displays the current device configuration |
| show ip dhcp pool | Displays DHCP pool information |
| show ip dhcp binding | Displays dynamically assigned IP addresses |

## 8. Save Configuration

To save the router configuration:

```bash
copy running-config startup-config
```

To save the switch configuration:

```bash
copy running-config startup-config
```

## 9. Conclusion

These commands demonstrate the configuration of VLANs, trunking, Router-on-a-Stick inter-VLAN routing, and DHCP services in a small office network using Cisco Packet Tracer.
