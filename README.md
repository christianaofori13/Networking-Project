# 👋 Hi, I'm Christiana Ofori Ansong

## 🌐 Introduction to Networking: NetCore Systems Ltd. Network Design and Security

Welcome to my GitHub project! This repository showcases my **Introduction to Networking assignment** for the September 2026 GRC cohort. The project focuses on designing and configuring a structured Local Area Network (LAN) for **NetCore Systems Ltd.** using Cisco Packet Tracer.

As I continue developing my skills in networking and cybersecurity, this project has given me practical experience with network topology design, IP addressing, DHCP, connectivity testing, network troubleshooting, Access Control Lists (ACLs), and HTTP services.

---

## 📌 Project Overview

**Project Name:** NetCore Systems Ltd. – LAN Design and Security  
**Course:** GRC – Introduction to Networking  
**Tools Used:** Cisco Packet Tracer  
**Network Device:** Cisco 2911 Router  
**Project Type:** Network Infrastructure Design and Configuration  
**Author:** Christiana Ofori Ansong  
**Date:** October 8, 2026

### 🎯 Project Objective

The primary objective of this project was to design and configure a structured LAN that connects the IT, Sales, and Human Resources (HR) departments of NetCore Systems Ltd.

The company lacked a properly organized network infrastructure, resulting in communication challenges, inefficient operations, limited network management, and potential security vulnerabilities.

The proposed solution uses separate departmental networks connected through a central router, with DHCP for automatic IP configuration, connectivity testing, HTTP services, and ACL-based access controls.

The goal is to improve communication, simplify administration, strengthen network security, and establish a foundation that can support the company's future growth.

---

## 🚨 Business Problem

NetCore Systems Ltd. faced several networking challenges:

- **Poor departmental connectivity:** The absence of a structured LAN limited efficient communication between departments.
- **Limited network management:** The lack of centralized network services made IP address management and troubleshooting more difficult.
- **Manual configuration challenges:** Without effective DHCP services, configuring network settings on individual devices could become inefficient.
- **Security risks:** Insufficient access controls could expose sensitive departmental resources to unauthorized access.
- **Limited service accessibility:** Network services such as HTTP and FTP needed to be considered as part of the company's network infrastructure.

### 💡 Proposed Solution

I designed a Cisco Packet Tracer network that connects the three departments through a central Cisco 2911 router. Each department operates on a separate IP network, allowing traffic to be routed between networks and providing a foundation for departmental security policies.

The design also incorporates automatic IP addressing, network connectivity tests, HTTP server access, and an Extended ACL to restrict traffic from Sales to IT.

---

## 🏗️ Network Architecture

The network consists of three departmental networks connected through a central router named `Netcore-Router`.

### Network Topology

```text
                      Netcore-Router
                       Cisco 2911
                           |
            +--------------+--------------+
            |              |              |
         IT Network    Sales Network    HR Network
       192.168.10.0   192.168.20.0    192.168.30.0
            |              |              |
          Switch         Switch         Switch
            |              |              |
       +----+----+      Sales PCs       HR PCs
       |         |
     PC1        PC2
       |
    IT Server
   HTTP Service
```

*Note: This is a simplified logical representation of the topology described in the assignment. The exact physical connections and device count in the Sales and HR departments may differ.*

### 🖥️ Departmental Network Design

| Department | Network Address | Purpose |
|---|---|---|
| IT | `192.168.10.0/24` | IT workstations and server resources |
| Sales | `192.168.20.0/24` | Sales department devices |
| Human Resources | `192.168.30.0/24` | HR department devices |

The `/24` subnet mask is explicitly used in the documented ACL configuration for the IT and Sales networks. The table applies the same subnet size to the HR network as a working representation of the design.

### Key Network Components

- **Cisco 2911 Router:** Serves as the central gateway and routes traffic between departmental networks.
- **Switches:** Connect end devices within the departmental LANs.
- **PCs:** Represent employee workstations used to test network connectivity.
- **Server:** Provides HTTP access and supports the network's server-based services.
- **DHCP:** Enables PCs to obtain their network settings automatically.
- **Extended ACL:** Controls traffic based on source and destination IP addresses.

---

## ⚙️ Technologies and Concepts Implemented

### 1. IP Addressing and Subnetting

The network uses separate IP address ranges for IT, Sales, and HR. This logical separation helps organize devices by department and provides a foundation for routing and security policies.

- IT network: `192.168.10.0/24`
- Sales network: `192.168.20.0/24`
- HR network: `192.168.30.0/24`

Using separate networks makes it easier to manage departmental devices and define which resources they can access.

### 2. Dynamic Host Configuration Protocol (DHCP)

DHCP was used to configure the network settings of the PCs automatically.

Instead of manually assigning every workstation an IP address, a device can request its configuration from the DHCP service.

The assignment documents PCs in all three departments receiving their network settings automatically.

**Benefits:**
- Reduces manual configuration.
- Simplifies IP address administration.
- Helps minimize configuration errors.
- Makes it easier to connect additional workstations.

### 3. Interdepartmental Routing

The Cisco 2911 router, named `Netcore-Router`, acts as the central gateway for the three departmental networks.

The router provides the routing infrastructure needed for communication between different IP subnets, subject to the configured security policies.

### 4. Network Connectivity Testing

The Windows-style command prompt in Cisco Packet Tracer was used to test connectivity between devices with the `ping` command.

For example:

```bash
ping 192.168.10.5
ping 192.168.10.6
```

The assignment records successful responses from both IT PCs during testing initiated from the HR department.

A separate test from a Sales PC produced a `Destination host unreachable` message when attempting to reach `192.168.10.6`.

These results demonstrate why connectivity tests are important for verifying reachability and identifying routing or access-control issues.

### 5. Extended Access Control Lists (ACLs)

An Extended ACL named `Sales-ACL` was configured on the router to control traffic between the Sales and IT networks.

The documented security policy is:

- Deny traffic originating from the Sales subnet and destined for the IT subnet.
- Permit other IP traffic covered by the subsequent permit rule.

The key documented command is:

```cisco
deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
permit ip any any
```

The wildcard mask `0.0.0.255` corresponds to a `/24` network.

**Security objective:** Restrict Sales-to-IT communication while allowing other traffic covered by the ACL's permit rule.

An ACL only has the intended effect when it is correctly applied to the appropriate router interface and direction. The complete running configuration and interface placement are not included in the assignment text.

### 6. HTTP Server Connectivity

The project includes a successful HTTP connectivity test in which PC3 accesses the NetCore Systems webpage using the server IP address:

```text
192.168.10.2
```

The webpage loads successfully, demonstrating that the tested PC can reach the HTTP service and that the required HTTP traffic is permitted along that communication path.

This test provides evidence that the web service and its tested network path are functioning.

---

## 🧪 Project Implementation and Testing

The assignment documents six main submissions covering network design, configuration, testing, and security.

| Test | Activity | Recorded Result |
|---|---|---|
| 1 | Built the three-department network topology | Devices and network links shown as active |
| 2 | Configured PCs to obtain network settings through DHCP | Automatic network configuration documented |
| 3 | Tested connectivity from HR to IT PCs at `192.168.10.5` and `192.168.10.6` | Successful ping responses; 0% packet loss |
| 4 | Tested Sales-to-IT connectivity using `ping 192.168.10.6` | `Destination host unreachable`; 100% packet loss |
| 5 | Created the `Sales-ACL` extended access control list | Deny rule for Sales-to-IT traffic and permit rule for other IP traffic |
| 6 | Tested HTTP access from PC3 to `192.168.10.2` | NetCore Systems webpage loaded successfully |

### 🔍 Understanding the Results

**Successful connectivity:** The HR-to-IT ping test showed that the tested devices could exchange ICMP packets successfully at the time of testing.

**Failed connectivity:** The Sales-to-IT test returned `Destination host unreachable` from `192.168.20.1`, identified in the assignment as the Sales gateway. This indicates that the destination was unreachable along the tested path. Although the ACL is designed to restrict Sales-to-IT traffic, the failed ping alone does not prove that the ACL caused the failure; the complete configuration and ACL counters would be needed to establish that conclusively.

**Successful HTTP access:** The browser test confirmed that PC3 could load the webpage hosted at `192.168.10.2` through the tested network path.

Together, these tests demonstrate practical experience with basic network validation, troubleshooting, and access-control configuration.

---

## 🔐 Network Security Considerations

Security was an important part of the proposed network design.

The use of separate departmental subnets provides a logical structure for applying access restrictions, while the Extended ACL introduces a policy for limiting communication between Sales and IT.

### Security Measures Demonstrated

- Departmental separation using distinct IP networks.
- IP-based traffic filtering through an Extended ACL.
- Restriction of traffic from the Sales subnet to the IT subnet.
- Connectivity testing to observe permitted and unsuccessful communication.
- Testing of HTTP service accessibility.

### Potential Future Improvements

The following are recommended enhancements rather than features confirmed as implemented in the assignment:

- Apply a default-deny approach where appropriate, followed by explicit rules for required services.
- Verify ACL placement, direction, rule order, and hit counters.
- Restrict access to sensitive servers and departmental resources based on business requirements.
- Add appropriate protections for FTP or replace traditional FTP with a secure alternative where supported.
- Implement network monitoring and logging to help identify unusual activity.
- Document a complete IP address plan, including gateways, DHCP pools, exclusions, and server addresses.
- Test all intended permitted and denied traffic paths before deployment.

These improvements would help strengthen the security posture and make the network easier to maintain.

---

## 🧠 What I Learned

Through this project, I gained practical exposure to the following networking concepts:

- Designing a logical network topology in Cisco Packet Tracer.
- Understanding how routers and switches connect departmental networks.
- Organizing devices into separate IP subnets.
- Configuring PCs to obtain network settings automatically through DHCP.
- Using `ping` to test connectivity between devices.
- Interpreting packet loss and `Destination host unreachable` messages.
- Creating an Extended ACL to restrict traffic based on source and destination networks.
- Testing access to an HTTP server using its IP address.
- Recognizing the importance of testing network behavior alongside security configuration.

The project also reinforced the importance of documenting network configurations and distinguishing between a test result and the underlying cause of that result.

---

## 🚀 Future Enhancements

If I extend this project, I would like to explore:

1. **VLAN implementation:** Create VLANs to improve logical segmentation and departmental management.
2. **Enhanced ACL policies:** Define more granular rules for access to specific servers and services.
3. **DHCP configuration documentation:** Record address pools, default gateways, DNS settings, and excluded addresses.
4. **DNS integration:** Allow users to access internal web services using names rather than IP addresses.
5. **Secure file services:** Explore secure alternatives to traditional FTP for file transfers.
6. **Network monitoring:** Introduce monitoring and logging to support troubleshooting and incident investigation.
7. **Comprehensive testing:** Develop a test matrix covering connectivity, denied traffic, allowed services, and failure scenarios.
8. **Configuration documentation:** Maintain router, switch, addressing, and security configuration records.

These enhancements would provide opportunities to deepen my knowledge of enterprise networking and network security.

---

## 🛠️ Skills and Tools

### Tools
- Cisco Packet Tracer
- Cisco 2911 Router
- Network command-line testing tools
- Web browser for HTTP validation

### Technical Skills Demonstrated
- LAN design and topology planning
- IPv4 addressing and subnetting
- DHCP concepts and automatic host configuration
- Interdepartmental routing concepts
- Network connectivity testing
- Basic network troubleshooting
- Extended ACL configuration
- Network segmentation concepts
- HTTP service testing
- Technical documentation

---

## 📂 Repository Structure

A suggested structure for organizing this GitHub repository is:

```text
netcore-systems-network-project/
│
├── README.md
├── packet-tracer/
│   └── netcore-network.pkt
│
├── screenshots/
│   ├── 01-network-topology.png
│   ├── 02-dhcp-configuration.png
│   ├── 03-successful-ping.png
│   ├── 04-failed-connectivity-test.png
│   ├── 05-sales-acl-configuration.png
│   └── 06-http-connectivity-test.png
│
└── documentation/
    └── network-design-notes.md
```

*This is a recommended repository structure, not a list of files confirmed to be included in the current project. Add the Packet Tracer file and screenshots only if they are available.*

---

## ▶️ How to Explore the Project

To reproduce or explore the project:

1. Install Cisco Packet Tracer.
2. Open the project `.pkt` file, if included in this repository.
3. Inspect the topology and identify the IT, Sales, and HR networks.
4. Review the IP configuration of the PCs and confirm whether DHCP is assigning network settings.
5. Use `ping` to test the documented device addresses.
6. Inspect the router's ACL configuration and verify its interface placement and direction.
7. Open the web browser on the test PC and navigate to `http://192.168.10.2` to check HTTP access, if the server and Packet Tracer configuration are available.

The actual Packet Tracer configuration file is needed to reproduce the topology and verify its full configuration.

---

## 🌟 Project Outcome

This project demonstrates how a structured LAN can support departmental communication, network administration, and access control within a business environment.

By designing three departmental networks, documenting DHCP-based configuration, testing connectivity, configuring an Extended ACL, and validating HTTP access, I explored several foundational networking concepts through a practical scenario.

The project also highlights the importance of troubleshooting and validating security policies instead of assuming that a configuration works solely because it has been entered.

---

## 🎯 My Learning Goals

I am continuing to build my technical foundation in networking and cybersecurity. My goals are to:

- Strengthen my understanding of network infrastructure and routing.
- Develop more advanced skills in network security and access control.
- Gain practical experience with network monitoring and troubleshooting.
- Explore how networking supports security operations and enterprise IT environments.
- Build a portfolio of hands-on projects that demonstrates my technical growth.

I believe that consistent practice, documentation, and project-based learning are essential to becoming a capable networking and cybersecurity professional.

---

## 👩🏽‍💻 About the Author

**Christiana Ofori Ansong**  
GRC Cohort — September 2026

I am a learner building practical skills in networking and cybersecurity through hands-on assignments and technical projects. I enjoy exploring how networks are designed, how devices communicate, and how security controls can help protect business systems.

This repository is part of my learning journey and serves as documentation of my work on the NetCore Systems Ltd. network design project.

### 📬 Connect With Me

- **GitHub:** [Add your GitHub profile URL]
- **LinkedIn:** [Add your LinkedIn profile URL]
- **Email:** [Add your professional email address]

---

## 📄 Acknowledgment

This project was completed as part of my *Introduction to Networking* assignment for the September 2026 GRC cohort. The project descriptions and reported test outcomes are based on my submitted assignment.

Thank you for visiting my repository. I welcome opportunities to learn, collaborate, and continue growing in networking and cybersecurity.

**#Networking #CiscoPacketTracer #Cybersecurity #LAN #IPAddressing #DHCP #ACL #NetworkSecurity #ITInfrastructure #GRC**
