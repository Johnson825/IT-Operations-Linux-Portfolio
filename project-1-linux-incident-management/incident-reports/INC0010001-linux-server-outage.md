
# Incident Report: INC0010001 – Linux Server Unavailable

## 1. Incident Overview

| Field | Details |
|---|---|
| Incident ID | INC0010001 |
| Priority | P2 – High |
| Configuration Item | LINUX-WEB-01 |
| Operating System | Ubuntu Linux |
| Incident Type | Server Connectivity |
| Status | Resolved |
| Environment | Simulated |

## 2. Incident Summary

Monitoring detected that the Linux server LINUX-WEB-01 became unreachable at 8:07 AM. SSH and ICMP connectivity checks failed, while the virtual machine remained powered on and accessible through the hypervisor console.

## 3. Incident Timeline

| Time | Event |
|---|---|
| 8:02:14 AM | NetworkManager reports ens160 connected with DHCP and default route |
| 8:06:54 AM | Administrator initiates virtual network adapter reconfiguration |
| 8:06:55 AM | Virtual network adapter disconnected |
| 8:06:58 AM | Guest operating system reports carrier loss |
| 8:07:01 AM | Linux network interface goes down |
| 8:07:03 AM | NetworkManager reports device disconnected |
| 8:07:05 AM | SSH connectivity check fails |
| 8:07:07 AM | ICMP connectivity check fails |
| 8:09:32 AM | Virtual network adapter reconnected |
| 8:09:35 AM | Guest operating system detects carrier |
| 8:09:38 AM | Network connectivity restored |

## 4. Investigation Findings

- The virtual machine remained powered on.
- The hypervisor console was accessible.
- Ubuntu remained responsive.
- Network interface ens160 was DOWN.
- The interface had no IPv4 address or default gateway during the outage.
- CPU, memory, and disk metrics from the last successful monitoring check did not indicate resource exhaustion.
- Hypervisor events showed that the virtual network adapter was disconnected during reconfiguration.

## 5. Root Cause

An infrastructure administrator reconfigured the virtual network adapter outside the server's scheduled maintenance window. The adapter was temporarily disconnected, causing Ubuntu to lose network connectivity.

## 6. Corrective Action

The virtual network adapter was reconnected. The Ubuntu operating system detected the network carrier, and connectivity was restored.

## 7. Recovery Validation

Recovery was confirmed through the following checks:

- SSH connectivity successful.
- Application health endpoint successful.
- Application response returned to normal.
- Monitoring checks passed.
- Application support confirmed normal operation.

## 8. Resolution

The incident was marked Resolved in ServiceNow using the resolution code **Solved (Permanently)**.

Recorded incident duration: **2 minutes, 38 seconds**.

The precise end-user impact was not established.

## 9. Lessons Learned

- Align infrastructure maintenance activity with approved maintenance windows.
- Validate virtual network adapter connectivity after infrastructure changes.
- Monitor network interface state and server reachability.
- Document investigation findings, corrective actions, and recovery validation.

## 10. Project Disclaimer

This report documents a simulated IT operations incident created for independent learning and portfolio demonstration. It does not represent an actual production incident or access to a production server.
