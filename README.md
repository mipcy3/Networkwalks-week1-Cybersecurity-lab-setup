# Networkwalks-B084-week1-Cybersecurity-lab-setup
## Project Information
**Submitted By:** David Ayomipo Gege
* **Milestone Objective:** Deploy an isolated virtual network environment using Oracle VM VirtualBox and configure a Kali Linux virtual machine with a permanent manual static IP address architecture.

## Lab Infrastructure Configurations
* **Hypervisor Platform:** Oracle VM VirtualBox
* **Guest Operating System:** Kali Linux 2025.4 (AMD64)
* **Network Adapter Profile:** Custom NAT Network (`NatNetwork`)
* **Network Subnet Architecture (CIDR):** 10.0.0.0/24
* **Static Interface Assignment:** 10.0.0.2/24
* **Default Network Gateway Router:** 10.0.0.1
* **Upstream DNS Resolver Routing:** 8.8.8.8 (Google Public DNS)

## Completed Tasks
1. Designed and deployed a custom global NAT Network configuration mapped to the required 10.0.0.0/24 IP address space.
2. Hardened hypervisor interoperability capabilities by enabling bidirectional shared clipboards and mounting persistent host-to-guest shared directories (`/downloads`).
3. Switched network interfaces inside Kali Linux from dynamic DHCP lease architectures to manual internal routing configurations.
4. Created a system snapshot restoration profile checkpoint (`My Fresh Kali`) to ensure deployment backup redundancy.

## Verification Artifacts
* Verified Static IP Configuration via `ip address show` and external internet traversal via `ping -c 4 google.com` successfully deployed below.

* <img width="1440" height="900" alt="Screenshot_2026-11-04_22_44_03" src="https://github.com/user-attachments/assets/0644ae66-74ca-4ecf-9b82-de1e09bb75bc" />
