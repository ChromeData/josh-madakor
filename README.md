# Azure SOC + Honeynet  
Building a SOC + Honeynet in Azure (Live Traffic)  

![Cloud Honeynet / SOC](images/architecture_before.png)  

## Introduction  

In this project, I build a mini honeynet in Azure and ingest log sources from various resources into a Log Analytics workspace. Microsoft Sentinel is utilized to build attack maps, trigger alerts, and create incidents. Metrics were gathered for an insecure environment over 24 hours, followed by the application of security controls, and metrics were gathered again.  

### Metrics Overview  

We measure the following security metrics:  
- **SecurityEvent**: Windows Event Logs  
- **Syslog**: Linux Event Logs  
- **SecurityAlert**: Log Analytics Alerts Triggered  
- **SecurityIncident**: Incidents created by Sentinel  
- **AzureNetworkAnalytics_CL**: Malicious Flows allowed into our honeynet  

---

## Architecture  

### Before Hardening / Security Controls  

![Architecture Diagram](images/architecture_before.png)  

### After Hardening / Security Controls  

![Architecture Diagram](images/architecture_after.png)  

---

## Metrics  

### Before Hardening  

| Metric                   | Count  
| ------------------------ | -----  
| SecurityEvent            | 19470  
| Syslog                   | 3028  
| SecurityAlert            | 10  
| SecurityIncident         | 348  
| AzureNetworkAnalytics_CL | 843  

### After Hardening  

| Metric                   | Count  
| ------------------------ | -----  
| SecurityEvent            | 8778  
| Syslog                   | 25  
| SecurityAlert            | 0  
| SecurityIncident         | 0  
| AzureNetworkAnalytics_CL | 0  

---

## Attack Maps  

### Before Hardening  

![NSG Allowed Inbound Malicious Flows](images/malicious_flows.png)  
![Linux Syslog Auth Failures](images/auth_failures_linux.png)  
![Windows RDP/SMB Auth Failures](images/auth_failures_windows.png)  

### After Hardening  

**No malicious activity detected in the 24-hour period after hardening.**  

---

## Conclusion  

This project demonstrates the effectiveness of security controls in reducing malicious activity in an Azure environment. Metrics collected before and after hardening show a significant decrease in security events and incidents.  

**Key Takeaways:**  
- Properly configuring Network Security Groups (NSGs) and firewalls greatly reduces attack vectors.  
- Implementing Private Endpoints secures Azure resources from internet exposure.  
- Using tools like Microsoft Sentinel can effectively monitor and respond to potential threats.  
