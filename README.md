# odp-ansible-winlogbeat
This role installs, configures, and runs Winlogbeat as a service in Windows 2019 Server

## Winlogbeat Installation
Winlogbeat is used to ship event logs from Windows hosts to Logstash or Elasticsearch. It can be installed and run as a Windows service.

Winlogbeat that runs on a Windows server, watches for event logs real-time in the server, reads the event logs, filters the events based on user-configured criteria, and sends the event data to the configured outputs (Elasticsearch or Logstash). 

Winlogbeat helps capture the following type of events:

- application events
- hardware events
- security events
- system events

## Winlogbeat Configuration
This role by default configures to capture the following events:

- Systems
- Security
- Microsoft-Windows-WMI-Activity/Operational
- Microsoft-Windows-Diagnosis-PCW/Operational
- Microsoft-Windows-SystemDataArchiver/Diagnostic
- Forefront Identity Manager Synchronization/Operational
- Application
- Microsoft-Windows-Kernel-IO/Operational
- Microsoft-Windows-GroupPolicy/Operational
- Microsoft-Windows-NTLM/Operational
- Microsoft-Windows-Security-Mitigations/KernelMode
- Microsoft-Windows-WinRM/Operational
- Microsoft-Windows-MsLbfoProvider/Operational
- Microsoft-Windows-RemoteDesktopServices-RdpCoreTS/Operational
- Microsoft-Windows-TaskScheduler/Operational
- Microsoft-Windows-TaskScheduler/Maintenance
- Microsoft-Windows-Terminal Services-LocalSessionManager/Operational

However, these configurations can be modified in the template file.

## Role Requirements:
- This role needs to be run against a Windows Server
- Windows Server should be accessible via WinRM

## Role Variables:
```
version: 7.10.2
log_server: "your-log-server"
log_server_port: "your-log-server-port"
```

## Example Playbook
This role should be executed using a playbook as given below:
```
- hosts: remoteserver
  vars:
    version: 7.10.2
    log_server: 10.0.0.8
    log_server_port: 2076
  roles:
    - role: odp-ansible-winlogbeat
```

