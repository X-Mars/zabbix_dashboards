# Zabbix 8.0 Dashboard Templates

[简体中文](README.md) · **English**

This project provides 13 importable global dashboards for Zabbix 8.0. Each dashboard has Simplified Chinese and English source files. You can import either version or both.

## Import and use

1. In Zabbix, go to **Dashboards → All dashboards → Import** and select the source file for your preferred language. Enable **Create missing** on the first import. On subsequent imports, enabling **Update existing** replaces the pages and widgets of a dashboard with the same name.
2. Link the appropriate monitoring template to the target and verify its host tags and data collection status. File system, port, and container charts require the corresponding discovered items and historical data.
3. Open the dashboard and select a host or target on the left of each tab. Use the time selector in the upper-right corner to adjust the chart range. Custom titles use the language of the imported version. System menus and problem severity labels use your Zabbix interface language.

## Dashboards

### 1. Linux Server Monitoring

Designed for routine checks. The interactive overview shows CPU utilization, available memory, network interface traffic, and problem severity for the selected host. Use the honeycomb and CPU ranking to compare hosts.

Link the Linux monitoring template and use the `target=linux` host tag. Traffic charts require network interface discovery.

[Simplified Chinese source](zh-CN/linux-server-monitoring.zh-CN.yaml) · [English source](en/linux-server-monitoring.en.yaml)

![Linux Server Monitoring screenshot in Simplified Chinese](images/linux-server-monitoring.zh-CN.png)

![Linux Server Monitoring screenshot in English](images/linux-server-monitoring.en.png)

### 2. Linux Host Performance

Use this dashboard to troubleshoot performance on an individual host. Host Overview shows system load, CPU utilization and I/O wait, memory, swap, and processes. Storage and Network shows mount point capacity, free inodes, disk throughput and latency, and network traffic, errors, and dropped packets.

Link the Linux monitoring template and use the `target=linux` host tag. Storage and Network requires the corresponding discovery data.

[Simplified Chinese source](zh-CN/linux-host-performance.zh-CN.yaml) · [English source](en/linux-host-performance.en.yaml)

![Linux Host Performance screenshot in Simplified Chinese](images/linux-host-performance.zh-CN.png)

![Linux Host Performance screenshot in English](images/linux-host-performance.en.png)

### 3. Zabbix Server Status

Platform Health shows information about the current Zabbix instance and the selected host's collection rate, database write rate, queues, process busy time, and cache usage. Server Resources shows CPU, memory, system load, file systems, disks, and network interfaces.

Use the `target=zabbix` host tag. Platform Health requires the Zabbix server health template. Server Resources requires the Linux monitoring template.

[Simplified Chinese source](zh-CN/zabbix-server-status.zh-CN.yaml) · [English source](en/zabbix-server-status.en.yaml)

### 4. Windows System Monitoring

System and Compute shows agent availability, CPU time by category, the CPU queue, memory, page file usage, processes, and threads. Storage and Network shows volume usage, disk request latency, network traffic, and errors.

Link the Windows monitoring template and use the `target=windows` host tag. Volume, disk, and network metrics require discovery.

[Simplified Chinese source](zh-CN/windows-system.zh-CN.yaml) · [English source](en/windows-system.en.yaml)

### 5. SNMP Network Devices and Ports

Check device availability, uptime, and port status. Use inbound and outbound traffic, errors, and discards to identify problematic ports. The dashboard also shows probe round-trip time and packet loss.

Link the generic SNMP network device template, use the `target=generic` host tag, and configure an SNMP interface and port discovery.

[Simplified Chinese source](zh-CN/snmp-network-device.zh-CN.yaml) · [English source](en/snmp-network-device.en.yaml)

### 6. ICMP Reachability and Latency

Track reachability, round-trip time, and packet loss for the selected target. The packet loss ranking compares matching targets visible to the current user.

Link the ICMP probe template, use the `target=icmp` host tag, and configure a reachable probe target address.

[Simplified Chinese source](zh-CN/icmp-reachability.zh-CN.yaml) · [English source](en/icmp-reachability.en.yaml)

![ICMP Reachability and Latency screenshot in Simplified Chinese](images/icmp-reachability.zh-CN.png)

![ICMP Reachability and Latency screenshot in English](images/icmp-reachability.en.png)

### 7. Website Browser Performance

Breaks down page load time into DNS lookup, connection, TLS handshake, request, response, and DOM readiness timings. It also shows transfer and response body sizes.

Link the website browser monitoring template and use the `target=browser` host tag. Configure a working browser driver and a website address.

[Simplified Chinese source](zh-CN/website-browser-performance.zh-CN.yaml) · [English source](en/website-browser-performance.en.yaml)

### 8. TLS Certificate Expiry

Find certificates that expire soonest and review validation results, validity start dates, and signature algorithms for the selected host.

Link the website certificate monitoring template and use the `target=certificate` host tag. Zabbix agent 2 must be able to retrieve the certificates, and certificate discovery must be configured.

[Simplified Chinese source](zh-CN/tls-certificate-inventory.zh-CN.yaml) · [English source](en/tls-certificate-inventory.en.yaml)

### 9. MySQL Performance and Replication

Workload and Connections shows query rates, connection threads, slow queries, and network throughput. InnoDB and Replication shows buffer pool efficiency, row lock waits, database size, and replication lag.

Link the MySQL template for Zabbix agent 2 and use the `target=mysql` host tag. Database sizes require discovery. Select a replica to view replication lag.

[Simplified Chinese source](zh-CN/mysql-operations.zh-CN.yaml) · [English source](en/mysql-operations.en.yaml)

### 10. PostgreSQL Performance and Replication

Sessions and Transactions shows connection states, commit and rollback rates, cache hit ratio, deadlocks, and conflicts. Capacity and Replication shows database sizes, lock counts, and replication lag in time and bytes.

Link the PostgreSQL template for Zabbix agent 2 and use the `target=postgresql` host tag. Per-database and per-application metrics require the corresponding discovery rules.

[Simplified Chinese source](zh-CN/postgresql-operations.zh-CN.yaml) · [English source](en/postgresql-operations.en.yaml)

### 11. Redis Cache and Persistence

Track client connections and blocked clients, memory usage and resident set size, network throughput, cumulative hits and misses, key expirations and evictions, and key counts by logical database. The dashboard also shows the duration of the latest persistence operations.

Link the Redis template for Zabbix agent 2 and use the `target=redis` host tag. Key counts by logical database require database discovery.

[Simplified Chinese source](zh-CN/redis-operations.zh-CN.yaml) · [English source](en/redis-operations.en.yaml)

### 12. Docker Engine and Containers

Check engine status, container counts, and image and volume usage. For each container, review CPU, memory, network traffic, cumulative restart count, and health status.

Link the Docker template for Zabbix agent 2 and use the `target=docker` host tag. The agent needs access to the Docker API and container discovery.

[Simplified Chinese source](zh-CN/docker-runtime.zh-CN.yaml) · [English source](en/docker-runtime.en.yaml)

![Docker Engine and Containers screenshot in Simplified Chinese](images/docker-runtime.zh-CN.png)

![Docker Engine and Containers screenshot in English](images/docker-runtime.en.png)

### 13. VMware vSphere Hosts and VMs

ESXi Hosts shows CPU, memory, networking, and datastore latency. Virtual Machines shows CPU scheduling wait, guest and host memory, virtual disk latency, and guest file system space.

Link the VMware hypervisor and guest monitoring templates. Use `target=vmware-hypervisor` for hosts and `target=vmware-guest` for virtual machines.

[Simplified Chinese source](zh-CN/vmware-vsphere.zh-CN.yaml) · [English source](en/vmware-vsphere.en.yaml)

## Validation

All 38 pages across the 26 language variants were checked with data in the Zabbix 8.0.0 frontend. Linux, Zabbix server, network probes, websites, certificates, databases, and containers used collected data. MySQL was validated with MariaDB primary and replica instances, and Redis was validated with Valkey over the Redis protocol. Windows and VMware vSphere were validated with explicitly labeled simulated targets.
