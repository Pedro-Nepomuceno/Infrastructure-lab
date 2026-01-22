# Infrastructure-lab

# Infrastructure Homelab

This repository documents my hands-on home lab built to simulate a small enterprise environment. The goal is to practice real-world system administration tasks: provisioning servers, configuring networking, deploying Active Directory, and managing core Windows infrastructure services.

This lab is part of my transition into IT/System Administration and complements my cloud work on AWS.

---

## 🎯 Lab Goals

* Build a functional Windows-based network from scratch
* Deploy and manage Active Directory
* Configure core services (DNS, DHCP)
* Practice real sysadmin workflows: planning, troubleshooting, documenting
* Create recruiter-visible proof of hands-on infrastructure experience

---

## 🧱 Current Architecture

* **Host:** macOS
* **Hypervisor:** UTM
* **Primary Server:** Windows Server 2022 (Evaluation)

  * Hostname: `DC01`
  * Role: Domain Controller
  * Services:

    * Active Directory Domain Services (AD DS)
    * DNS
    * DHCP
* **Networking:**

  * Static IP assigned to DC01
  * Internal virtual network (NAT)

> This environment simulates a small business network with a single Domain Controller providing identity, name resolution, and IP address management.

---

## ✅ What Has Been Implemented

* [x] Windows Server 2022 installed in UTM
* [x] Static IP configured on the server
* [x] Server promoted to Domain Controller
* [x] New Active Directory domain created
* [x] DNS installed and integrated with AD
* [x] DHCP role installed
* [x] DHCP scope created and authorized

---

## 🛠 Build Log (High Level)

1. Created a new virtual machine in UTM
2. Installed Windows Server 2022 (Desktop Experience)
3. Renamed the server to `DC01`
4. Assigned a static IP address to ensure stability for infrastructure roles
5. Installed **Active Directory Domain Services**
6. Promoted the server to a Domain Controller
7. Created a new forest and domain
8. Verified DNS integration
9. Installed **DHCP Server** role
10. Created and authorized a DHCP scope

---

## 📂 Planned Documentation

Detailed step-by-step notes will live under `/docs`:

* `docs/01-windows-server-install.md`
* `docs/02-static-ip-configuration.md`
* `docs/03-active-directory-setup.md`
* `docs/04-dns-configuration.md`
* `docs/05-dhcp-scope.md`
* `docs/troubleshooting.md`

---

## 🧭 Next Steps

* [ ] Create a Windows 11 client VM
* [ ] Join the client to the domain
* [ ] Create Organizational Units (OUs)
* [ ] Create users and security groups
* [ ] Apply Group Policies (password policy, lock screen, etc.)
* [ ] Test DHCP lease assignment
* [ ] Add a Linux client and test interoperability
* [ ] Implement basic backup strategy

---

## Lessons Learned

This section will capture real issues and how I solved them, such as:

* Why a static IP is mandatory before installing AD DS
* Common DHCP installation errors on non-static servers
* DNS dependency pitfalls during domain promotion

These notes are intentionally written from a learner's perspective, mirroring real troubleshooting in production environments.

---

## 📸 Diagrams & Screenshots

Network diagrams and screenshots will be added under `/diagrams` to visually represent the environment.

---

##  Safety Note

This repository contains **sanitized** documentation only. It will never include:

* Passwords or secrets
* Real IP addresses
* Product keys
* Personal or client data

---

This homelab is an evolving project. Each change reflects a real operational decision, just like in a production environment.
