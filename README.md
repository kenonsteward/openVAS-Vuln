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
![Unauthenticated Scan Against Vulnerable VM](https://github.com/kyiez/openVAS-Vuln/assets/90296943/01f2fbb1-f708-4e95-a9f5-54cd15a17af5">)<br>
![Unauthenticated Scan Against Vulnerable VM Results](https://github.com/kyiez/openVAS-Vuln/assets/90296943/22bbb845-62dd-41e3-b00e-5db861122301">)<br>


## Credentialed Scan Results Before Remediation
![Authenticated Scan Against Vulnerable VM](https://github.com/kyiez/openVAS-Vuln/assets/90296943/a1b860f6-8319-4522-9c0f-1f8a39699002">)<br>
![Authenticated Scan Against Vulnerable VM Results](https://github.com/kyiez/openVAS-Vuln/assets/90296943/5a9a93a1-8245-4011-8ffe-da3e06408b6c">)<br>
![](https://github.com/kyiez/openVAS-Vuln/assets/90296943/d0008c5e-4b2d-4ffb-88d5-e72ff6f65b6b">)<br>



## Credentialed Scan Results After Remediation
![Authenticated Scan Against Remediated VM](https://github.com/kyiez/openVAS-Vuln/assets/90296943/fbb4236b-49a2-498d-b6aa-dc68e40414eb">)<br>
![Authenticated Scan Against Remediated VM](https://github.com/kyiez/openVAS-Vuln/assets/90296943/8ca62c1c-c7ec-4233-b99b-8e4e55f0bd5e">">)<br>

<!--
As shown in the images, the unauthenticated scan gathers 3 of 34 items vs. the credentialed scan resulting in 86 of 137 items.

In the credentialed scan after remediation results in 7 of 55 items on the report.

-->



## Results Before Hardening & Remediation

The following table shows the metrics we measured in our insecure environment for 24 hours:

| Metric                                                         | Count
| ------------------------                                       | -----
| unauthenticated                                                | 3/37
| credentialed                                                   | 86/137


<!--## Attack Maps After Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```
-->
## Results After Hardening & Remediation

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:

| Metric                                                         | Count 
| ------------------------                                       | -----
| credentialed                                                   | 7/55

## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
