# Core Infrastructure – Windows Domain Lab

This document describes the foundational architecture of my home lab.  
It represents the *baseline enterprise environment* on which all future work (GPOs, users, security, hybrid cloud, etc.) is built.

The goal of this phase was to design, deploy, and validate a functioning Windows domain from scratch.

---

## 1. Environment Overview

**Host Platform**
- macOS host using **UTM** for ARM virtualization

**Virtual Machines**
| Name  | OS                         | Role                          |
|-------|----------------------------|-------------------------------|
| DC01  | Windows Server             | Domain Controller (AD, DNS, DHCP) |
| WS01  | Windows 11 Pro             | Domain-joined client          |

**Domain**
- `corp.local`

**Objective**
Simulate a small enterprise network with centralized identity, name resolution, and IP management.

---

## 2. Network Architecture

UTM provides the virtual router and NAT.

- Subnet: `192.168.64.0/24`
- Gateway (UTM): `192.168.64.1`

**DC01**
- Static IP: `192.168.64.10`
- Roles:
  - Active Directory Domain Services
  - DNS Server
  - DHCP Server

**WS01**
- DHCP client
- DNS manually pointed to `192.168.64.10`


