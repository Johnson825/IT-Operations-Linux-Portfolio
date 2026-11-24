# Linux Server Monitoring, Service Management & Health Check

## 1. Project Overview

This project demonstrates basic Linux server monitoring, service management, and health-check procedures using a LabEx practice environment.

The objective was to review system resources, inspect running processes, check service availability, and verify application connectivity.

**Environment:** LabEx Linux practice container  
**Hostname:** 6b04c31e44628d37030ea6b8  
**Purpose:** Hands-on technical learning and portfolio documentation

## 2. System Health Assessment

| Check | Result | Observation |
|---|---|---|
| CPU | Normal | 4 processing units available; CPU mostly idle |
| Load Average | Normal | Low system load |
| Memory | Normal | Approximately 12 GiB available |
| Swap | Not Configured | No swap space configured |
| Disk | Normal | Root filesystem approximately 1% used |
| Processes | Normal | No zombie processes observed |
| System Services | Limited | systemd unavailable in this container |

## 3. Service Management

**Service:** Nginx

Initial status check showed that Nginx was not running.

The configuration was tested using:

`sudo nginx -t`

Result: Configuration syntax was valid.

Nginx was then started using:

`sudo service nginx start`

A subsequent status check confirmed that Nginx was running.

## 4. Service Verification

The following checks were performed:

- Confirmed Nginx master and worker processes were running.
- Confirmed port 80 was listening.
- Tested the local web server using `curl -I http://localhost`.
- Received an HTTP 200 OK response.

These results confirmed that the Nginx service was responding successfully within the practice environment.

## 5. Monitoring Commands Used

| Command | Purpose |
|---|---|
| `hostname` | Identify the system |
| `uptime` | Review uptime and load average |
| `nproc` | Check available processing units |
| `free -h` | Review memory usage |
| `df -h` | Review filesystem capacity |
| `top` | Monitor system activity |
| `ps aux` | Inspect running processes |
| `ss -tulnp` | Review listening ports |
| `service nginx status` | Check Nginx status |
| `nginx -t` | Validate Nginx configuration |
| `curl -I http://localhost` | Verify HTTP response |

## 6. Environment Limitation

The container did not use systemd as its initialization system. Therefore, `systemctl` commands were unavailable.

This was an environment limitation, not evidence of failed services.

## 7. Conclusion

The health-check exercise demonstrated basic Linux system monitoring, resource assessment, process inspection, service startup, and application response verification.

All observations were collected from a LabEx practice environment. They do not represent production server monitoring or an actual production incident.
