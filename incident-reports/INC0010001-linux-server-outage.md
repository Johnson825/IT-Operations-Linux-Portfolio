# Incident Report: INC0010001 – Linux Server Outage

**Project:** IT Operations Incident Management Simulation  
**Incident ID:** INC0010001  
**Affected Server:** LINUX-WEB-01  
**Operating System:** Ubuntu Linux  
**Priority:** P2 – High  
**Incident Status:** Resolved  
**Environment:** Simulated Production Environment

---

## 1. Incident Overview

A production Linux server became unreachable after a virtual network adapter was temporarily disconnected during an infrastructure reconfiguration.

Monitoring detected the availability issue at 8:07 AM. The incident affected server connectivity and potentially interrupted application availability.

## 2. Incident Timeline

| Time | Event |
|---|---|
| 8:02:14 AM | Last successful network check |
| 8:06:54 AM | Infrastructure administrator initiated virtual network adapter reconfiguration |
| 8:06:55 AM | Virtual network adapter disconnected |
| 8:06:58 AM | Ubuntu detected network carrier loss |
| 8:07:01 AM | Network interface ens160 went down |
| 8:07:07 AM | ICMP monitoring check failed |
| 8:09:32 AM | Virtual network adapter reconnected |
| 8:09:35 AM | Ubuntu detected network carrier restoration |
| 8:09:38 AM | Network connectivity restored |

## 3. Investigation Findings

The investigation included reviewing monitoring alerts, infrastructure metrics, operating system availability, network interface status, Ubuntu system logs, and hypervisor audit records.

Key findings:

- The monitoring platform remained operational.
- Other monitored servers remained online.
- No obvious CPU, memory, or disk resource exhaustion was identified in the last recorded metrics.
- The virtual machine remained powered on and responsive through the hypervisor console.
- Network interface ens160 transitioned to a DOWN state.
- Ubuntu logs recorded network carrier loss.
- Hypervisor audit records identified a virtual network adapter reconfiguration immediately before the outage.

## 4. Root Cause

An infrastructure administrator reconfigured the virtual network adapter outside the server's scheduled maintenance window.

The temporary adapter disconnection caused Ubuntu to lose network connectivity, making the server unreachable through normal network monitoring and remote access.

## 5. Corrective Action

The virtual network adapter was reconnected.

Ubuntu detected the restored network carrier, and server connectivity returned.

## 6. Recovery Validation

The following checks were successful:

- Server network connectivity restored.
- SSH connectivity successful.
- Application health endpoint successful.
- Application response normal.
- Monitoring checks passing.

Application support confirmed that the application was responding normally.

## 7. Final Resolution

**Resolution Code:** Solved (Permanently)

**Final Status:** Resolved

Server connectivity and application functionality were verified as restored.

## 8. Lessons Learned

- Infrastructure changes should follow approved maintenance windows.
- Virtual network adapter changes can affect operating system connectivity.
- Monitoring alerts should be correlated with operating system logs and hypervisor events.
- Server recovery should be followed by application-level validation.
- Accurate incident documentation supports troubleshooting, accountability, and operational reporting.

---

**Portfolio Note:** This is a simulated incident investigation created for IT Operations training. It does not represent an actual production outage or access to a real production server.
