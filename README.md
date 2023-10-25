# Cybersecurity Vulnerability Management Project

## Introduction

In this project, I build an OpenVAS Vulnerability Management Scanner and use it to scan a vulnerable VM with outdated software, while also disabling some security controls on the VM. I then performed unauthenticated and credentialed scans using OpenVAS, and analyzed the results while highlighting the difference between the scans. Finally, I remediated several of the identified vulnerabilities and verify successful remediation through follow-up scans.

<!--
Set up a secure Azure network with an OpenVAS Vulnerability Management Scanner VM.
Developed a vulnerable Windows 10 VM, featuring outdated software and disabled security controls.
Performed unauthenticated and credentialed vulnerability scans using OpenVAS.
Analyzed scan results, highlighting the difference between unauthenticated and credentialed scans.
Remediated identified vulnerabilities, verified successful remediation through subsequent scans.
Created a list of remediable vulnerabilities to simulate realistic vulnerability remediation scenarios.
-->

The architecture in Azure consisted of 2 virtual machines, 1 windows (vulnerable) and 1 linux containing OpenVAS.

For the vulnerable machine, I turned off the built-in firewall and installed outdated software such as Adobe Reader, VLC Player, and Firefox.

After scanning, the vulnerable machine was hardened by uninstalling the outdated software and re-enabling the built-in firewall.

## Unauthenticated Scan Results Before Remediation
![Unauthenticated Scan Against Vulnerable VM](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/bfce0a20-cff2-42ce-bc76-e25a7482c3c3">)<br>
![Unauthenticated Scan Against Vulnerable VM Results](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/b292338b-e145-4d1d-a754-df8d729e6787">)<br>





## Credentialed Scan Results Before Remediation
![Authenticated Scan Against Vulnerable VM](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/ba0b57a3-a86c-41d9-b6b3-fb36188916d2">)<br>
![Authenticated Scan Against Vulnerable VM Results](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/c6a09f67-6d6d-4a74-891e-78ddb003f705">)<br>
![](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/7dd6e8c8-1d16-4752-862b-dfbe72571245">)<br>






## Credentialed Scan Results After Remediation
![Authenticated Scan Against Remediated VM](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/e11ac504-3705-48c6-9ff2-ee803046d945">)<br>
![Authenticated Scan Against Remediated VM](https://github.com/kenonsteward/openVAS-Vuln/assets/90296943/6df36607-ea74-46c4-b52f-27fe0ae61e9b">)<br>


<!--
As shown in the images, the unauthenticated scan gathers 34 items vs. the credentialed scan resulting in 137 items.

In the credentialed scan after remediation results in 55 items on the report.

-->



## Results Before Hardening & Remediation
<!--
The following shows the metrics prior to hardening and remediation:
-->

| Metric                                                         | Count
| ------------------------                                       | -----
| unauthenticated                                                | 34
| credentialed                                                   | 137


<!--## Attack Maps After Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```
-->
## Results After Hardening & Remediation
<!--
The following table shows the metrics after hardening and remediation:
-->
| Metric                                                         | Count 
| ------------------------                                       | -----
| credentialed                                                   | 55

## Conclusion
In this project, I establish a vnet containing a vulnerable Windows VM and employ a Linux machine containing OpenVAS in Microsoft Azure. OpenVAS was used to scan the vulnerable VM prior to remediation, and again after remediation and hardening. It is noteworthy that the number of events identified increased after initiating a credentialed scan, demonstrating the effectiveness vs. an unauthenticated scan.
<!--
In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
-->
