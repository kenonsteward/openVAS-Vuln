# Cybersecurity Vulnerability Management Project

# Building a SOC + Honeynet in Azure (Live Traffic)
![Cloud Honeynet / SOC](https://i.imgur.com/ZWxe03e.jpg)

## Introduction

In this project, I build an OpenVAS Vulnerability Management Scanner and use it to scan a vulnerable VM with outdated software, while also disabling some security controls on the VM. I then performed unauthenticated and credentialed scans using OpenVAS, and analyze the results while highlighting the difference between the scans. Finally, I remediated several of the identified vulnerabilities and verify successful remediation through follow-up scans.

Set up a secure Azure network with an OpenVAS Vulnerability Management Scanner VM.
Developed a vulnerable Windows 10 VM, featuring outdated software and disabled security controls.
Performed unauthenticated and credentialed vulnerability scans using OpenVAS.
Analyzed scan results, highlighting the difference between unauthenticated and credentialed scans.
Remediated identified vulnerabilities, verified successful remediation through subsequent scans.
Created a list of remediable vulnerabilities to simulate realistic vulnerability remediation scenarios.


## Architecture Before Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/aBDwnKb.jpg)

## Architecture After Hardening / Security Controls
![Architecture Diagram](https://i.imgur.com/YQNa9Pp.jpg)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the Internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Unauthenticated Scan Results Before Remediation
#### Unauthenticated Scan Against Vulnerable VM
![Unauthenticated Scan Against Vulnerable VM](https://github.com/kyiez/openVAS-Vuln/assets/90296943/01f2fbb1-f708-4e95-a9f5-54cd15a17af5">)<br>
#### Unauthenticated Scan Against Vulnerable VM Results
![Unauthenticated Scan Against Vulnerable VM Results](https://github.com/kyiez/openVAS-Vuln/assets/90296943/22bbb845-62dd-41e3-b00e-5db861122301">)<br>
#### Authenticated Scan Against Vulnerable VM
![Windows RDP/SMB Auth Failures](https://github.com/kyiez/openVAS-Vuln/assets/90296943/a1b860f6-8319-4522-9c0f-1f8a39699002">)<br>
#### Authenticated Scan Against Vulnerable VM Results
![Microsoft SQL Auth Failures](https://github.com/kyiez/openVAS-Vuln/assets/90296943/5a9a93a1-8245-4011-8ffe-da3e06408b6c">)<br>
![](https://github.com/kyiez/openVAS-Vuln/assets/90296943/d0008c5e-4b2d-4ffb-88d5-e72ff6f65b6b">)<br>


## Credentialed Scan Results Before Remediation


## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2023-08-04 20:45
Stop Time 2023-08-05 20:45

| Metric                                                         | Count
| ------------------------                                       | -----
| SecurityEvent (Windows VMs)                                    | 47595
| Syslog (Linux VMs)                                             | 3147
| SecurityAlert (Windows Defender for Cloud                      | 6
| SecurityIncident (Sentinel Incidents)                          | 348
| AzureNetworkAnalytics_CL (NSG Inbound Malicious Flows Allowed) | 366


## Attack Maps After Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2023-08-12 23:52
Stop Time	2023-08-13 23:52

| Metric                                                         | Count  | Change after securing environment  
| ------------------------                                       | -----  | ---- 
| SecurityEvent (Windows VMs)                                    | 8349   | -82.46%
| Syslog (Linux VMs)                                             | 1      | -99.97%
| SecurityAlert (Windows Defender for Cloud                      | 0      | -100.00%
| SecurityIncident (Sentinel Incidents)                          | 0      | -100.00%
| AzureNetworkAnalytics_CL (NSG Inbound Malicious Flows Allowed) | 0      | -100.00%


## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
