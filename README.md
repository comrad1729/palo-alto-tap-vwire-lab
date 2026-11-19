# Palo Alto Networks Firewall – TAP (Monitoring) Interface Lab

## Project Overview

This project demonstrates the configuration and implementation of a Palo Alto Networks VM-Series firewall in **TAP (Monitoring) mode** using GNS3.

The objective was to monitor mirrored network traffic, identify applications using Palo Alto App-ID, and inspect traffic sessions through the firewall's Session Browser and Traffic Logs.

The lab demonstrates passive network visibility without placing the firewall inline in the traffic forwarding path.

## Lab Environment

| Component | Details |
|---|---|
| Firewall | Palo Alto Networks VM-Series |
| Lab platform | GNS3 |
| Firewall interface | Ethernet1/1 |
| Interface mode | TAP |
| Security Zone | TAP |
| Endpoints | Windows 7 VMs |
| Network connectivity | GNS3 Ethernet switch and NAT |
| Management access | Dedicated management interface |

## Network Topology

The lab consists of Windows endpoints connected through a virtual switch, with a Palo Alto firewall connected to the switch for monitoring mirrored traffic.

A separate management connection provides access to the Palo Alto web interface.

**Traffic monitoring flow:**

Windows endpoints → Virtual Switch → SPAN / Port Mirroring → Palo Alto TAP interface

## Configuration and Implementation

### 1. Palo Alto Interface Configuration

- Configured Ethernet1/1 as a TAP interface.
- Assigned the interface to the TAP security zone.
- Kept the TAP interface without an IP address.
- Established separate management connectivity for firewall administration.

### 2. Switch SPAN Configuration

Configured a SPAN (Switched Port Analyzer) session on the virtual switch to mirror traffic from the source interface to the destination monitoring interface.

Example Cisco switch configuration:

```cisco
monitor session 1 source interface gigabitEthernet 0/0
monitor session 1 destination interface gigabitEthernet 0/1
```

The mirrored traffic was forwarded to the Palo Alto monitoring interface.

### 3. Traffic Monitoring and Application Identification

Accessed the Palo Alto web interface and navigated to:

**Monitor → Session Browser**

Observed network sessions and application identification, including:

- DNS
- SSL
- Web Browsing
- Google Base
- Facebook Base
- Instagram Base

Reviewed source and destination IP addresses, source and destination ports, protocols, ingress and egress interfaces, application identification and session byte counts.

## Testing and Validation

The following activities were performed:

1. Generated network traffic from Windows endpoints.
2. Configured traffic mirroring through the virtual switch.
3. Verified that mirrored sessions appeared in the Palo Alto Session Browser.
4. Observed DNS queries and HTTPS sessions.
5. Verified application identification using Palo Alto App-ID.
6. Reviewed traffic session details and exported Session Browser reports in PDF format.

## Key Learning Outcomes

- Understanding TAP interface operation and passive traffic monitoring.
- Configuring SPAN / port mirroring.
- Understanding the difference between inline firewall deployment and passive monitoring.
- Learning Palo Alto security zones and interface configuration.
- Understanding application identification using App-ID.
- Analysing network sessions through Session Browser and Traffic Logs.
- Understanding ingress and egress interface visibility.

## Screenshots and Evidence

The repository includes screenshots demonstrating:

- GNS3 network topology.
- Palo Alto TAP interface configuration.
- Session Browser traffic visibility.
- DNS and HTTPS sessions.
- Application identification, including Instagram, Facebook and Google-related traffic.
- Exported Session Browser report.

## Conclusion

Successfully implemented a Palo Alto Networks TAP monitoring lab using GNS3 and verified mirrored network traffic through the firewall's Session Browser.

This project provided practical exposure to passive traffic monitoring, SPAN configuration, Palo Alto interface configuration, and application-level network visibility using App-ID.

**Note:** This is a virtual lab environment built for learning and practical demonstration. It does not represent a production firewall deployment.
